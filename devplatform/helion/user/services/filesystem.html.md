---
layout: default-devplatform
permalink: /als/v1/user/services/filesystem/
---
<!--PUBLISHED-->

Persistent File System[](#persistent-file-system "Permalink to this headline")
===============================================================================

The file system of application containers are ephemeral. Any application
data or files stored locally within these containers is lost when the
instance is stopped or restarted. To solve this, Application Lifecycle Service provides a filesystem type of service that can be shared between application instances,
and even between applications deployed to the same space.

A persistent file system service allows apps to do the following:

1.  Share files across multiple instances of an app
2.  Store files that persist if an app is removed (providing the service
    is not deleted) or if the server is restarted.
3.  Conserve space on filesystems allocated within the VM instance by referencing the persistent filesystem instead.

Creating A Persistent File System[](#creating-a-persistent-file-system "Permalink to this headline")
-----------------------------------------------------------------------------------------------------

A filesystem service can be configured in your *manifest.yml* file:

    services:
        mydata: filesystem

You can also use the `helion create-service`
command:

    $ helion create-service filesystem mydata
        Creating Service: OK

        $ helion services

        =========== Provisioned Services ============

        +----------------+------------+
        | Name           | Service    |
        +----------------+------------+
        | mydata         | filesystem |
        +----------------+------------+

Using A Persistent File System[](#using-a-persistent-file-system "Permalink to this headline")
-----------------------------------------------------------------------------------------------

**Note**

File system service is available during pre-staging and shouldn't need
to be reconfigured when the application starts.

The filesystem service creates a path which your app can use to store
and read files.

If there is only one filesystem service, the
`HELION_FILESYSTEM` environment variable can be
used to get the path.

If there is more than one filesystem service,
`HELION_FILESYSTEM` is not available. Instead, a
custom environment variable `HELION_FILESYSTEM_*`
will be created based on the name of each filesystem service (with
hyphens replaced by underscores).

For example, if your *manifest.yml* file configures the following
services:

    services:
        my-data: filesystem
        plugins: filesystem

Two environment variables would be created:
`HELION_FILESYSTEM_MY_DATA` and
`HELION_FILESYSTEM_PLUGINS`.

This naming scheme can be used in conjunction with the
`HELION_APP_NAME_UPCASE` environment variable. For
example, in an app with the following filesystem service defined:

    services:
      ${name}-foo: filesystem
      ${name}-bar: filesystem

The filesystem mount point for the "foo" filesystem service can be
accessed within the container using constructs such as:

    FOO=HELION_FILESYSTEM_${HELION_APP_NAME_UPCASE}_FOO
    mkdir ${!FOO}/myapp

**Note**

To use declarations like these in
[*hooks*](/als/v1/user/deploy/manifestyml/#hooks), put them in a
separate bash script. Brace expansion and grouping cannot be used
directly in YAML files.

<!-- Does this also apply for VCAP services? if so should be rewritten perhaps. 
Alternatively, `STACKAT0_SERVICES` contains
information for all services:

    {
        "plugins": {
            "dir": "/home/helion/fs/plugins"
                },
                "my-data": {
                        "dir": "/home/helion/fs/my-data"
                },
                "mydb": {
                        "name": "db76e25bc8fc142858653a6cb8c643204",
                        "hostname": "192.168.0.112",
                        "host": "192.168.0.112",
                        "port": 3306,
                        "user": "u7Fjl8hdb4iNu",
                        "username": "u7Fjl8hdb4iNu",
                        "password": "p4XQAhZr8xfHg"
                }
        }
-->
Since the [*environment
variables*](/als/v1/user/reference/environment/#environment-variables) are
available during the staging process, it is possible to make use of them
in the [*manifest.yml*](/als/v1/user/deploy/manifestyml/) file to
configure a filesystem service and create a symlink to it for use by the
app. (see example below)

Example of Using A Persistent File System[](#example-of-using-a-persistent-file-system "Permalink to this headline")
---------------------------------------------------------------------------------------------------------------------

**Note**

When linking the file system service to the application, using symlinks
is strongly recommended.

We will go through how we customized our WordPress installation to use
the persistent file system. Before you begin, find out where all the
user generated contents are saved. You may have to make modifications to
this general approach if your application stores user generated content
in more than one location. In WordPress, they are stored in wp-content
folder.

We need to add the following to our manifest.yml:

    services:
        fs-wp: filesystem
    hooks:
        post-staging:
        # create wp-content in the shared filesystem
        - mkdir -p "$HELION_FILESYSTEM"/wp-content

        # migrate existing wp-content data into the shared filesystem
        - mv wp-content/* "$HELION_FILESYSTEM"/wp-content

        # remove unused wp-content directories
        - rm -rf wp-content

        # link to wp-content folder in the shared filesystem
        - ln -s "$HELION_FILESYSTEM"/wp-content wp-content

**Note**

When moving files onto the mounted filesystem with a `mv` hook, you may see an error message similar to:

    mv: failed to preserve ownership for... Permission denied

This is a misleading warning, as the files **will** actually be moved with
the correct permissions and ownership.