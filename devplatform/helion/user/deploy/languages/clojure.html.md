---
layout: default-devplatform
permalink: /als/v1/user/deploy/languages/clojure/
product: devplatform
title: "Clojure"
---
<!--PUBLISHED-->

# HP Helion Development Platform: Clojure {#clojure}

Application Lifecycle Service supports deploying Clojure applications using
[leiningen](https://github.com/technomancy/leiningen).

To create a new Clojure web application, install leiningen and
[Noir](http://webnoir.org/) (a Clojure web framework):

    $ lein plugin install lein-noir 1.1.0

Create a Noir project:

    $ lein noir new myapp
    ...
    $ cd myapp/

Now deploy to Application Lifecycle Service. Accept the defaults for each prompt:

    $ helion push myapp
    [...]
    Application Deployed URL: 'myapp.helion-xxxx.local'?
    [...]
    Starting Application: OK

Open the application's URL in your browser to see the default Noir welcome
page.

Clojure Database Services Example[](#clojure-database-services-example "Permalink to this headline")
-----------------------------------------------------------------------------------------------------

Taken from the [4clojure sample
app](https://github.com/Stackato-Apps/4clojure/blob/stackato/src/foreclojure/config.clj#L6):

    (defn assoc-cloud-env
      "Import Cloud Foundry / Application Lifecycle Service environment settings"
      [config]
      (let [port (Integer/parseInt (System/getenv "PORT"))
            srv  (parse-string (System/getenv "VCAP_SERVICES"))
            cred ((first (srv "mongodb-1.8")) "credentials")]
        (assoc config
          :jetty-port port
          :db-host    (cred "host")
          :db-port    (cred "port")
          :db-user    (cred "username")
          :db-pwd     (cred "password")
          :db-dbname  (cred "db"))))