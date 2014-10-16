---
layout: default
title: "Application Lifecycle Service Client Command Reference"
permalink: /als/v1/user/reference/client-ref/
product: 


---
<!--UNDER REVISION-->

Application Lifecycle Service Client Command Reference[](#helion-client-command-reference "Permalink to this headline")
=====================================================================================================

- [Usage](#usage)   
- [Getting Started](#getting-started)
- [Applications](#applications)
- [Services](#services)
- [Organizations](#organizations)
- [Spaces](#spaces)
- [Routes](#routes)
- [Domains](#domains)
- [Administration](#administration)
- [Convenience](#convenience)
- [Miscellaneous](#miscellaneous)


Usage[](#usage "Permalink to this headline")
---------------------------------------------

**helion** [*options*] *command* [*arguments*] [*command-options*]

For more information., use the `helion help`,
`helion help [command]`, and
`helion options` commands.

Many of the informational commands take a `--json`
option if you wish to generate machine-parseable output. In some cases
the `--json` option reveals additional details.

Note that Administrative user privileges are required for some commands.

## Getting Started[](#getting-started "Permalink to this headline")

### helion login ###

Logs in to the current or specified target with the named user.

<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--credentials</td>
    <td>The credentials to use. Each use of the option declares a single element, using the form "key: value" for the argument. This is an ALS 3-specific option</td>
    </tr><tr>
    <td>--group</td>
    <td>The group to use for the login. This is an ALS 2-specific option.</td>
    </tr><tr>
    <td>--ignore-missing</td>
    <td>Disable errors generated for missing organization and/or space.</td>
    </tr>
    <tr>
    <td>--no-prompt, --noprompt,<br> 
		--n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr><tr>
    <td>--non-interactive</td>
    <td>Same as no-prompt.</td>
    </tr><tr>
    <td>--organization,<br> --o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--password, --passwd</td>
    <td>The password to use. For ALS 3, this is a shorthand for <i>--credentials 'password:</i></td>
    </tr><tr>
    <td>--space</td>
    <td>The space (in the organization) to use. This is an ALS 3-specific option. If not specified the user is prompted to choose among the possible s in the organization if specified. If the organization is not specified, the user is prompted to choose from all spaces in all organizations the user belongs to.</td>
    </tr><tr>
    <td>--target</td>
    <td>The one-off target to use for the current operation only.</td>
    </tr><tr>
    <td>--token</td>
    <td>The one-off authentication token to use for the current operation only.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, --t</td>
    <td>Originally used to activate tracing of the issued REST requests and responses; tracing is always active now. See the <i>trace</i> command to print the saved trace to <i>stdout</i>.</td>
    </tr>
</table>


###helion logout *\<target\>*###
Logs out of the current, specified, or all targets.

<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--all</td>
    <td>log out of all targets we know. Cannot be used together with a target.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, --n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, --t</td>
    <td>Originally used to activate tracing of the issued REST requests and responses; tracing is always active now. See the <i>trace</i> command to print the saved trace to <i>stdout</i>.</td>
    </tr>
</table>

### helion target *\<url\>*###
Set the target API endpoint for the client or report the current target.

<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td width=200>--allow-http</td>
    <td>Required to prevent the client from rejecting http URLs.</td>
    </tr>
    <tr>
    <td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, -n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--organization, -o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--space, -s</td>
    <td>The space (in the organization) to use. This is an ALS 3-specific option. If not specified the user is prompted to choose among the possible spaces in the organization if specified. If the organization is not specified, the user is prompted to choose from all spaces in all organizations the user belongs to.</td>
    </tr><tr>
    <td>--trace, -t</td>
    <td>Originally used to activate tracing of the issued REST requests and responses; tracing is always active now. See the <i>trace</i> command to print the saved trace to <i>stdout</i>.</td></tr>
    <tr><td>--verbose</td>
    <td>More verbose operation.</td>
    </tr>
</table>

## Applications[](#applications "Permalink to this headline")##
###helion apps###
Lists the applications deployed to the target.
<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--all</td>
    <td>Show all applications instead of just those associated with the current space.</td>
    </tr>
    <tr>
    <td>--group</td>
    <td>The once-off group to use for the current operation. This is an ALS 2-specific option.</td>
    </tr>
    <tr>
    <td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, -n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--organization, -o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--space, -s</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--space-guid</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--target</td>
    <td>The one-off target to use for the current operation only.</td>
    </tr><tr>
    <td>--token</td>
    <td>The one-off authentication token to use for the current operation only.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, -t</td>
    <td>The once-off space to use for the current operation, specified by guid. This is an ALS 3-specific option. Cannot be used together with `--space`.</td>
    </tr><tr>
    <td>--verbose</td>
    <td>More verbose operation.</td>
    </tr>
</table>

###helion app *\<application\>*###
Shows the information of the specified application.

<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--group</td>
    <td>The once-off group to use for the current operation. This is an ALS 2-specific option.</td>
    </tr>
    <tr>
    <td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>
    <tr>
    <td>--manifest</td>
    <td>Path of the manifest file to use. If not specified, a search is performed.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, -n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--organization, -o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--path</td>
    <td>Path of the directory holding the application files to push. Defaults to the current working directory.</td>
    </tr><tr>
    <td>--space, -s</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--space-guid</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--target</td>
    <td>The one-off target to use for the current operation only.</td>
    </tr><tr>
    <td>--token</td>
    <td>The one-off authentication token to use for the current operation only.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, -t</td>
    <td>The once-off space to use for the current operation, specified by guid. This is an ALS 3-specific option. Cannot be used together with `--space`.</td>
    </tr><tr>
    <td>--verbose</td>
    <td>More verbose operation.</td>
    </tr>
</table>

### helion list###
List the applications deployed to the target.
<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--all</td>
    <td>Show all applications instead of just those associated with the current space.</td>
    </tr>
    <tr>
    <td>--group</td>
    <td>The once-off group to use for the current operation. This is an ALS 2-specific option.</td>
    </tr>
    <tr>
    <td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, -n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--organization, -o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--space, -s</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--space-guid</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--target</td>
    <td>The one-off target to use for the current operation only.</td>
    </tr><tr>
    <td>--token</td>
    <td>The one-off authentication token to use for the current operation only.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, -t</td>
    <td>The once-off space to use for the current operation, specified by guid. This is an ALS 3-specific option. Cannot be used together with `--space`.</td>
    </tr>
</table>

##Information##
###helion crashes *\<application\>*###
List recent application crashes.
<table>
    <tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr>
    <tr>
    <td>--group</td>
    <td>The once-off group to use for the current operation. This is an ALS 2-specific option.</td>
    </tr>
    <tr>
    <td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>
    <tr>
    <td>--manifest</td>
    <td>Path of the manifest file to use. If not specified, a search is performed.</td>
    </tr>
    <tr>
    <td>--no-prompt, --non-interactive, --noprompt, -n</td>
    <td>Disable all prompts (interactive queries) that would normally be seen by the user.</td>
    </tr><tr>
    <td>--no-tail</td>
    <td>Complementary alias of <i>--tail</i>.</td>
    </tr><td>--no-trace</td>
    <td>Complementary alias of <i>--trace</i>.</td>
    </tr><tr>
    <td>--organization, -o</td>
    <td>The organization to use. This is an ALS 3-specific option. If not specified programmatically, the user is prompted to choose an organization.</td>
    </tr><tr>
    <td>--path</td>
    <td>Path of the directory holding the application files to push. Defaults to the current working directory.</td>
    </tr><tr>
    <td>--space, -s</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--space-guid</td>
    <td>The one-off space to use for the current operation, specified by name. This is an ALS 3-specific option. Cannot be used together with `--space-guid`.</td>
    </tr><tr>
    <td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr><tr>
    <td>--target</td>
    <td>The one-off target to use for the current operation only.</td>
    </tr><tr>
    <td>--token</td>
    <td>The one-off authentication token to use for the current operation only.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </tr><tr>
    <td>--trace, -t</td>
    <td>The once-off space to use for the current operation, specified by guid. This is an ALS 3-specific option. Cannot be used together with `--space`.</td>
    </tr>
</table>

### helion crashlogs *\<application\>*###
Display log information for the application. An alias of 'logs'.
<table><tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr><tr>
    <td>--all</td>
    <td>Retrieve the logs from all instances. Before 2.3 only.</td>
    </tr><tr>
    <td>--filename</td>
    <td>Filter the log stream by origin file (glob pattern). Target version 2.4+ only.</td>
    </tr><tr>
    <td>--follow</td>
    <td>Tail -f the log stream. Target version 2.4+ only.</td>
    </tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is an ALS 2-specific option.</td>
    </tr>
    <tr>
    <td>
    </td>

    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option. </td></tr>
    <td>--instance</td>

    <td> The id of the instance to filter the log stream for, or (before
            2.3), to retrieve the logs of. </td></tr>
    <tr><td>--json</td>

    <td>  Print the raw json log stream, not human-formatted data.
    </td></tr>
    <tr><td> --manifest</td>

    <td>Path of the manifest file to use. If not specified a search is
    done. </td></tr>

    <tr><td> --no-prompt </td>

    <td>Disable interactive queries.</td></tr>

    <tr><td>  --no-tail</td>

    <td> Complementary alias of --tail.</td></tr>

    <tr><td> --no-trace</td>

    <td> Complementary alias of --trace.</td></tr>

    <tr><td> --non-interactive</td>

    <td> Alias of --no-prompt.</td></tr>

    <tr><td> --noprompt </td>

    <td> Alias of --no-prompt. </td></tr>

    <tr><td>     --num </td>
    <td>  Show the last num entries of the log stream. Target version 2.4+
    only. </td></tr>
    <tr><td>--organization</td>

    <td> The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td></tr>
    <tr><td>    --path </td>
    <td>    Path of the directory holding the application files to push.
    Defaults to the current working directory.</td></tr>
    <tr><td>  --prefix </td>
    <td> Put instance information before each line of a shown log file.
    Before 2.3 only.</td></tr>
    <tr><td>   --prefix-logs </td>
    <td>    Alias of --prefix.</td></tr>
    <tr><td>  --prefixlogs </td>
    <td>     Alias of --prefix.</td></tr>
    <tr><td>  --source </td>
    <td> Filter the log stream by origin stage (glob pattern). Target
    version 2.4+ only.</td></tr>
    <tr><td>  --space </td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td></tr>
    <tr><td>--space-guid </td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td></tr>

    <tr><td>--tail</td>

    <td>Request target to stream the log.</td></tr>

    <tr><td>--target</td>

    <td>The once-off target to use for the current operation.</td></tr>

    <tr><td>--text</td>

    <td> Filter the log stream by log entry text (glob pattern).</td></tr> Target
    version 2.</td></tr>4+ only.</td></tr>

    <tr><td>--token</td>

    <td>The once-off authentication token to use for the current
    operation.</td></tr>

    <tr><td>--token-file</td>

    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td></tr>

    <tr><td>--trace</td>

    <td>Activate tracing of the issued REST requests and responses.</td></tr> This
    option is a no-op now.</td></tr> Tracing is always active.</td></tr> See the 'trace'
    command to print the saved trace to stdout.</td></tr>

    <tr><td> -n</td>
    <td>  Alias of --no-prompt.</td></tr>
    <tr><td>  -o</td>
    <td>  Alias of --organization.</td></tr>
    <tr><td>-t</td>
    <td> Alias of --trace.</td></tr>
</table>

### helion disk *\<application\>*###
Show the disk reservation for a deployed application.


<table><tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr><tr> <td> --group</td>
    <td>  The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td></tr>

    <tr> <td> --manifest </td>
    <td>Path of the manifest file to use. If not specified a search is done.</td>
    </tr>
    <tr><td>  --no-prompt</td>
    <td> Disable interactive queries.</td></tr>
    <tr><td>  --no-tail</td>
    <td> Complementary alias of --tail.</td></tr>
    <tr><td>  --no-trace</td>
    <td>  Complementary alias of --trace.

    <tr><td> --non-interactive</td>
    <td>  Alias of --no-prompt.</td></tr>

    <tr><td>--noprompt</td>
    <td>  Alias of --no-prompt.</td></tr>

    <tr><td> --organization</td>

    <td> The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td></tr>

    <tr><td> --path</td>
    <td> Path of the directory holding the application files to push.
    Defaults to the current working directory.</td></tr>

    <tr><td> --space</td>
    <td>  The once-off space to use for the current operation, specified by name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td></tr>

    <tr><td> --space-guid</td>
    <td> The once-off space to use for the current operation, specified by guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td></tr>

    <tr><td> --tail</td>
    <td>   Request target to stream the log.</td></tr>

    <tr><td> --target</td>
    <td>The once-off target to use for the current operation.</td></tr>
    <tr><td>    --token</td>
    <td>The once-off authentication token to use for the current operation.</td></tr>
    <tr><td> --token-file</td>
    <td>Path to an existing and readable file containing the targets and athorization tokens.</td></tr>
    <tr><td>   --trace</td>
    <td>Activate tracing of the issued REST requests and responses. This option is a no-op now. Tracing is always active. See the 'trace' command to print the saved trace to stdout.</td></tr>
    <tr><td>    -n</td>
    <td> Alias of --no-prompt.</td></tr>
    <tr><td>   -o</td>
    <td> Alias of --organization.</td></tr>
    <tr><td>    -t</td>
    <td> Alias of --trace.</td>
    </tr>
</table>


### helion drain list *\<application\>*###
Show the list of drains attached to the application.
    
<table><tr>
    <td><b>Option</b></td>
    <td><b>Description</b></td>
    </tr><tr> <td> --group
    <td> The once-off group to use for the current operation. This is an Application Lifecycle Service 2 option.
    </td>
    </tr>    <tr><td>
    </td>
    </tr>    <tr><td>--json </td>
    <td>Print raw json as output, not human-formatted data.</td>
    </td>
    </tr>    <tr><td> --manifest</td>
    <td>    Path of the manifest file to use. If not specified a search is done.</td>
    </td>
    </tr>    <tr><td> --no-prompt</td>
    <td> Disable interactive queries.</td>
    </td>
    </tr>    <tr><td>--no-tail</td>
    <td> Complementary alias of --tail.</td>
    </td>
    </tr>    <tr><td> --no-trace</td>
    <td> Complementary alias of --trace.</td>
    </td>
    </tr>    <tr><td>--non-interactive</td>
    <td> Alias of --no-prompt.</td>
    </td>
    </tr>    <tr><td> --noprompt</td>
    <td>Alias of --no-prompt.</td>
    </td>
    </tr>    <tr><td> --organization</td>
    <td> The once-off organization to use for the current operation. This is an Application Lifecycle Service 3 option.</td>
    </td>
    </tr>    <tr><td> --path</td>
    <td> Path of the directory holding the application files to push. Defaults to the current working directory.</td>
    </td>
    </tr>    <tr><td> --space</td>
    <td> The once-off space to use for the current operation, specified by name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </td>
    </tr>    <tr><td> --space-guid</td>
    <td>The once-off space to use for the current operation, specified by guid. This is an Application Lifecycle Service 3 option. Cannot be used together with 
    --space.</td>
    </td>
    </tr>    <tr><td> --tail</td>
    <td>Request target to stream the log.</td>
    </td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </td>
    </tr>    <tr><td> --token</td>
    <td> The once-off authentication token to use for the current operation.</td>
    </td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and authorization tokens.</td>
    </td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This option is a no-op now. Tracing is always active. See the 'trace' command to print the saved trace to stdout.</td>
    </td>
    </tr>    <tr><td>     -n</td>
    <td>Alias of --no-prompt.</td>
    </td>
    </tr>    <tr><td>   -o</td>
    <td> Alias of --organization.</td>
    </td>
    </tr>    <tr><td>    -t</td>
    <td> Alias of --trace.</td>
    </tr>
</table>
### helion drains *\<application\*###
Show the list of drains attached to the application.</td>
    
   
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is an
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    </tr>    <tr><td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>


### helion env *\<application\* ###
List the application's environment variables.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr></table>
### helion events *\<application\*###
Show recorded application events, for application or space.
    Without an application given the current or specified space is
    used, otherwise that application. This is an Application Lifecycle Service 3 specific
    command.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr>
    <td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr></tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr></table>

### helion files *\<application\* *\<apath\* ###
Display directory listing or file.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr>
    <td>--all</td>
    <td>When present, access all instances for the file or directory.
    Cannot be used together with --instance.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>When present the instance to query. Cannot be used together with
    --all. Defaults to 0 (except when --all is present).</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--prefix</td>
    <td>Put instance information before each line of a shown file or
    directory listing. Effective only for --all.</td>
    </tr>    <tr><td>--prefix-logs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--prefixlogs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with
    --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with
    --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr></table>
### helion file *\<application\* *\<apath\*  ###
Display directory listing or file.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>When present, access all instances for the file or directory.
    Cannot be used together with --instance.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>When present the instance to query. Cannot be used together with --all. Defaults to 0 (except when --all is present).</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--prefix</td>
    <td>Put instance information before each line of a shown file or
    directory listing. Effective only for --all.</td>
    </tr>    <tr><td>--prefix-logs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--prefixlogs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr></table>
### helion health *\<application\* ###
Report the health of the specified application(s).</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Report on all applications in the current space. Cannot be used
    together with application names.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr> </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>
### helion instances *\<application\*###
List application instances for a deployed application.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr> </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>
###helion logs *\<application\*###
Display the application log stream.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Retrieve the logs from all instances. Before 2.3 only.</td>
    </tr>    <tr><td>--filename</td>
    <td>Filter the log stream by origin file (glob pattern). Target
    version 2.4+ only.</td>
    </tr>    <tr><td>--follow</td>
    <td>Tail -f the log stream. Target version 2.4+ only.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>The id of the instance to filter the log stream for, or (before
            2.3), to retrieve the logs of.</td>
    </tr>    <tr><td>--json</td>
    <td>Print the raw json log stream, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--num</td>
    <td>Show the last num entries of the log stream. Target version 2.4+
    only.</td>
    </tr>    <tr><td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--prefix</td>
    <td>Put instance information before each line of a shown log file.
    Before 2.3 only.</td>
    </tr>    <tr><td>--prefix-logs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--prefixlogs</td>
    <td>Alias of --prefix.</td>
    </tr>    <tr><td>--source</td>
    <td>Filter the log stream by origin stage (glob pattern). Target
    version 2.4+ only.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--text</td>
    <td>Filter the log stream by log entry text (glob pattern). Target
    version 2.4+ only.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr> </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>

### helion mem *\<application\*###
Show the memory reservation for a deployed application.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr> </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>
### helion stats *\<application\*###
Display the resource usage for a deployed application.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>

    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>

### helion tail *\<application\* *\<apath\*###
Monitor file for changes and stream them.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>When present the instance to query. Cannot be used together with --all. Defaults to 0 (except when --all is present).</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr> </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>
##**Management**##
### helion create-app *\<application\*###
Create an empty application with the specified configuration.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--buildpack</td>
    <td>Url of a custom buildpack. This is an Application Lifecycle Service 3 specific option.</td>
    </tr>    <tr><td>--command</td>
    <td>The application's start command. Defaults to a framework-specific
    value if required and not specified by manifest.yml.</td>
    </tr>    <tr><td>--disk</td>
    <td>The application's per-instance disk allocation. Defaults to a
    framework-specific value if not specified by manifest.yml.</td>
    </tr>    <tr><td>--env</td>
    <td>Environment variable overrides. These are always applied
    regardless of --env-mode. The mode is restricted to the variable
    declarations found in the manifest.</td>
    </tr>    <tr><td>--env-mode</td>
    <td>Environment replacement mode. One of preserve, or replace. The
    default is "preserve". Using mode "replace" implies --reset as
    well, for push. Note that new variables are always set. Preserve
    only prevents update of existing variables. This setting applies
    only to the variable declarations found in the manifest. Overrides
    made with --env are always applied.</td>
    </tr>    <tr><td>--framework</td>
    <td>Specify the framework to use. Cannot be used together with --no-framework. Defaults to a heuristically chosen value if not
    specified, and none for --no-framework. This is an Application Lifecycle Service 2
    specific option.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instances</td>
    <td>The number of application instances to create. Defaults to 1, if
    not specified by a manifest.yml.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--mem</td>
    <td>The application's per-instance memory allocation. Defaults to a
    framework-specific value if not specified by manifest.yml.</td>
    </tr>    <tr><td>--no-framework</td>
    <td>Create application without any framework. Cannot be used together
    with --framework. This is an Application Lifecycle Service 2 specific option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--reset</td>
    <td>Analogue of --env-mode, for the regular settings.</td>
    </tr>    <tr><td>--runtime</td>
    <td>The name of the runtime to use. Default is framework specific, if
    not specified by a manifest.yml. This is an Application Lifecycle Service 2 specific
    option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--stack</td>
    <td>The OS foundation the application will run on. This is an Application Lifecycle Service
    3 specific option.</td>
    </tr>    <tr><td>--helion-debug</td>

    <td>host:port of the Komodo debugger listener to inject into the
    application as environment variables.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--url</td>
    <td>The urls to map the application to. I.e. can be specified muliple
    times.</td>
    </tr><tr>
    <td>-d</td>
<td>Set up debugging through an application-specific harbor (port)
    service. Target version 2.8+ only.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr></tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>

### helion dbshell *\<application\* *\<service\*###
Invoke interactive db shell for a bound service.</td>
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--dry</td>
    <td>Print the low-level ssh command to stdout instead of executing it.</td>
    </tr>    <tr><td>--dry-run</td>
    <td>Alias of --dry.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td> </tr></table>
### helion delete *\<application\*###
Delete the specified application(s).
    
<table>
    <tr><td>--all</td>
    <td>Delete all applications. Cannot be used together with application
    names.</td>
    </tr>    <tr><td>--force</td>
    <td>Force deletion.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion drain add *\<application\* *\<drain\* *\<uri\*###
Attach a new named drain to the application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>The drain target takes raw json log entries.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td></tr>
</table>
###helion drain delete *\<application\* *\<drain\*###
Remove the named drain from the application.</td>

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td> </tr></table>
### helion env-add *\<application\* *\<varname\* *\<value\*###
Add the specified environment variable to the named application.</td>

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion env-del *\<application\* *\<varname\*###
Remove the specified environment variable from the named
application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion map *\<application\* *\<url\*###
Make the application accessible through the specified URL (a route
consisting of host and domain)

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion open *\<application\*###
Open the url of the specified application in the default web browser. If 'api' is specified as the app name, the Management Console is opened. With no arguments, the 'name' value from the manifest.yml in the current directory is used (if            present). 

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion push *\<application\*###
Configure, create, push, map, and start a new application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--as</td>
    <td>The name of the application to push/update the selected
    application as. Possible only if a single application is pushed or
    updated.</td>
    </tr>    <tr><td>--buildpack</td>
    <td>Url of a custom buildpack. This is an Application Lifecycle Service 3 specific option.</td>
    </tr>    <tr><td>--command</td>
    <td>The application's start command. Defaults to a framework-specific
    value if required and not specified by manifest.yml.</td>
    </tr>    <tr><td>--copy-unsafe-links</td>

    <td>Links pointing outside of the application directory are copied
    into the application.</td>
    </tr>    <tr><td>--disk</td>
    <td>The application's per-instance disk allocation. Defaults to a
    framework-specific value if not specified by manifest.yml.</td>
    </tr>    <tr><td>--env</td>
    <td>Environment variable overrides. These are always applied
    regardless of --env-mode. The mode is restricted to the variable
    declarations found in the manifest.</td>
    </tr>    <tr><td>--env-mode</td>
    <td>Environment replacement mode. One of preserve, or replace. The
    default is "preserve". Using mode "replace" implies --reset as
    well, for push. Note that new variables are always set. Preserve
    only prevents update of existing variables. This setting applies
    only to the variable declarations found in the manifest. Overrides
    made with --env are always applied.</td>
    </tr>    <tr><td>--force-start</td>
    <td>Push, and start the application, even when stopped.</td>
    </tr>    <tr><td>--framework</td>
    <td>Specify the framework to use. Cannot be used together with --no-framework. Defaults to a heuristically chosen value if not
    specified, and none for --no-framework. This is an Application Lifecycle Service 2
    specific option.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instances</td>
    <td>The number of application instances to create. Defaults to 1, if
    not specified by a manifest.yml.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--mem</td>
    <td>The application's per-instance memory allocation. Defaults to a
    framework-specific value if not specified by manifest.yml.</td>
    </tr>    <tr><td>--no-framework</td>
    <td>Create application without any framework. Cannot be used together
    with --framework. This is an Application Lifecycle Service 2 specific option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-resources</td>
    <td>Do not optimize upload by checking for existing file resources.</td>
    </tr>    <tr><td>--no-start</td>
    <td>Push, but do not start the application.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noresources</td>
    <td>Alias of --no-resources.</td>
    </tr>    <tr><td>--nostart</td>
    <td>Alias of --no-start.</td>
    </tr>    <tr><td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--reset</td>
    <td>Analogue of --env-mode, for the regular settings.</td>
    </tr>    <tr><td>--runtime</td>
    <td>The name of the runtime to use. Default is framework specific, if
    not specified by a manifest.yml. This is an Application Lifecycle Service 2 specific
    option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--stack</td>
    <td>The OS foundation the application will run on. This is an Application Lifecycle Service
    3 specific option.</td>
    </tr>    <tr><td>--helion-debug</td>

    <td>host:port of the Komodo debugger listener to inject into the
    application as environment variables.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--url</td>
    <td>The urls to map the application to. I.e. can be specified muliple
    times.</td>
    </tr><tr>
    <td>-d</td>
    <td>Set up debugging through an application-specific harbor (port)
    service. Target version 2.8+ only.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>

### helion rename *\<application\* *\<name\*###
Rename the specified application. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion restart *\<application\*###
Stop and restart a deployed application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion run *\<command\*###
Run an arbitrary command on a running instance.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Run the command on all instances. Cannot be used together with --instance.</td>
    </tr>    <tr><td>--application</td>
    <td>Name of the application to operate on.</td>
    </tr>    <tr><td>--banner</td>
    <td>Show the leading and trailing banner to separate instance data.
    Applies only when --all is used. Defaults to on.</td>
    </tr>    <tr><td>--dry</td>
    <td>Print the low-level ssh command to stdout instead of executing it.</td>
    </tr>    <tr><td>--dry-run</td>
    <td>Alias of --dry.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>The instance to access with the command. Defaults to 0. Cannot be
    used together with --all.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-banner</td>
    <td>Complementary alias of --banner.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-a</td>
    <td>Alias of --application.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion scale *\<application\*###
Update the number of instances, memory and/or disk reservation for a deployed application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--disk</td>
    <td>The new disk reservation to use.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instances</td>
    <td>Absolute number of instances to scale to, or relative change.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--mem</td>
    <td>The new memory reservation to use.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-d</td>
    <td>Alias of --disk.</td> </tr><tr>
    <td>-i</td>
    <td>Alias of --instances.</td>
    </tr><tr>
    <td>-m</td>
    <td>Alias of --mem.</td>
    </tr><tr>
    <td>-n</td>
    
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion scp *\<paths\*###
Copy source files and directories to the destination.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--application</td>
    <td>Name of the application to operate on.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>The instance to access with the command. Defaults to 0.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-a</td>
    <td>Alias of --application.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion set-env *\<application\* *\<varname\* *\<value\*###
Add the specified environment variable to the named application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion ssh *\<command\*###
SSH to a running instance (or target), or run an arbitrary command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Run the command on all instances. Cannot be used together with --instance.</td>
    </tr>    <tr><td>--application</td>
    <td>Name of the application to operate on, or "api" to talk to the
    cloud controller node.</td>
    </tr>    <tr><td>--banner</td>
    <td>Show the leading and trailing banner to separate instance data.
    Applies only when --all is used. Defaults to on.</td>
    </tr>    <tr><td>--dry</td>
    <td>Print the low-level ssh command to stdout instead of executing it.</td>
    </tr>    <tr><td>--dry-run</td>
    <td>Alias of --dry.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--instance</td>
    <td>The instance to access with the command. Defaults to 0. Cannot be
    used together with --all.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-banner</td>
    <td>Complementary alias of --banner.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-a</td>
    <td>Alias of --application.</td> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion start *\<application\*###
Start a deployed application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion stop *\<application\*###
Stop a deployed application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unmap *\<application\* *\<url\*###
Unregister the application from a URL.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unset-env *\<application\* *\<varname\*###
Remove the specified environment variable from the named application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    <Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
## Services[](#services "Permalink to this headline")##
###helion service-plans###
List all available plans of the supported services. This is an
Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion services###
List the supported and provisioned services of the target.

<table>     <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion service *\<name\*###
Show the information about the named service.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>

**Authentication Tokens**
### helion create-service-auth-token *\<label\* *\<provider\*###
Create a new service authentication token. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auth-token</td>
    <td>Value of the new token.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion delete-service-auth-token *\<label\*###
Delete the specified service authentication token. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion service-auth-tokens###
Show all service authentication tokens knowns to the target. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr> <td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion update-service-auth-token *\<label\*###
Update the specified service authentication token. This is a
    Application Lifecycle Service 3 specific command.
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auth-token</td>
    <td>New value of the specified token.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
##**Brokers**##
### helion add-service-broker *\<name\*###
Make the named service broker known. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--broker-token</td>
    <td>Value of the broker's token.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--url</td>
    <td>Location of the broker.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion delete-service-broker *\<name\*###
Remove the named service broker from the target. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion remove-service-broker *\<name\*###
Remove the named service broker from the target. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion service-brokers###
Show the list of known service brokers. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion update-service-broker *\<name\* *\<newname\*###
Update the target's knowledge of the named service broker. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--broker-token</td>
    <td>New value of the broker's token.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--url</td>
    <td>New location of the broker.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
##**Management**##
### helion bind-service *\<service\* *\<application\*###
Bind the named service to the specified application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes. 
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion clone-services *\<source\* *\<application\*###
Copy the service bindings of the source application to the destination application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion create-service *\<vendor\* *\<name\* *\<application\*###
Create a new provisioned service, and optionally bind it to an application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--credentials</td>
    <td>The credentials to use. Each use of the option declares a single
    element, using the form "key: value" for the argument. This is a
    Application Lifecycle Service 3 specific option. This is restricted to user-provided
    services.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--plan</td>
    <td>The service plan to use. This is an Application Lifecycle Service 3 specific option.</td>
    </tr>    <tr><td>--provider</td>
    <td>The service provider. Use this to disambiguate between multiple
    providers of the same vendor/type. This is an Application Lifecycle Service 3 specific
    option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--version</td>
    <td>The service version. Use this to disambiguate between multiple
    versions of the same vendor/type. This is an Application Lifecycle Service 3 specific
    option.</td> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion delete-service *\<service\*###
Delete the named provisioned service.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td>
    </tr>    <tr><td>--all</td>
    <td>Delete all services. Cannot be used together with named service
    instances.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--unbind</td>
    <td>Unbind service from applications before deleting. By default bound
    services are skipped and not deleted. This is an Application Lifecycle Service 3
    specific option.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion rename-service *\<service\* *\<name\*###
Rename the specified service instance. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion tunnel *\<service\* *\<tunnelclient\*###
Create a local tunnel to a service, optionally start a local client as well.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--allow-http</td>
    <td>Required to prevent the client from rejecting http urls.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--port</td>
    <td>Port used for the tunnel.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--url</td>
    <td>Url the tunnel helper application is mapped to and listens on.
    Relevant if and only if the helper has to be pushed,i.e. on first
    use of the tunnel command.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unbind-service *\<service\* *\<application\*###
Disconnect the named service from the specified application.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--manifest</td>
    <td>Path of the manifest file to use. If not specified a search is
    done.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-tail</td>
    <td>Complementary alias of --tail.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--path</td>
    <td>Path of the directory holding the application files to push.
    Defaults to the current working directory.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--tail</td>
    <td>Request target to stream the log.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--timeout</td>
    <td>The time the client waits for an application to start before
    giving up and returning, in seconds. Note that this is measured
    from the last entry seen in the log stream. While there is
    activity in the log the timeout is reset.
    The default is 2 minutes.
    Use the suffixes 'm', 'h', and 'd' for the convenient
    specification of minutes, hours, and days. The optional suffix 's'
    stands for seconds.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
## Organizations<a name="organizations"></a>
### helion create-org *\<name\*###
Create a new organization. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--activate</td>
    <td>Switch the current organization to the newly created one. Done by
    default.</td>
    </tr>    <tr><td>--add-self</td>
    <td>Add yourself to the new organization, as developer. Done by
    default.</td>
    </tr>    <tr><td>--no-activate</td>
    <td>Complementary alias of --activate.</td>
    </tr>    <tr><td>--no-add-self</td>
    <td>Complementary alias of --add-self.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--quota</td>
    <td>The named quota of the new organization. Default is the target's
    choice.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion delete-org *\<name\*###
Delete the named organization. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--recursive</td>
    <td>Remove all sub-ordinate parts, and relations.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-r</td>
    <td>Alias of --recursive.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion link-user-org *\<user\* *\<org\*###
Add the specified user to the named organization, in various roles. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auditor</td>
    <td>Affect the auditor role</td>
    </tr>    <tr><td>--billing</td>
    <td>Affect the billing manager role</td>
    </tr>    <tr><td>--manager</td>
    <td>Affect the manager role</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion orgs###
List the available organizations. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td>
    </tr>    <tr><td>--full</td>
    <td>Show more details.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion org *\<name\*###
Show the named organization's information. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--full</td>
    <td>Show more details.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota-org *\<name\* *\<quota\*###
Set the quotas for the current or named organization. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion rename-org *\<name\* *\<newname\*###
Rename the named organization. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion switch-org *\<name\*###
Switch the current organization to the named organization. This invalidates the current space. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unlink-user-org *\<user\* *\<org\*###
Remove the specified user from the named organization, in various roles. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auditor</td>
    <td>Affect the auditor role</td>
    </tr>    <tr><td>--billing</td>
    <td>Affect the billing manager role</td>
    </tr>    <tr><td>--manager</td>
    <td>Affect the manager role</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr></table>
## Spaces<a name="spaces"></a>
### helion create-space *\<name\*###
Create a new space. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--activate</td>
    <td>Switch the current space to the newly created one. Done by
    default.</td>
    </tr>    <tr><td>--auditor</td>
    <td>Add yourself to the new space, as auditor. By request.</td>
    </tr>    <tr><td>--developer</td>
    <td>Add yourself to the new space, as developer. Done by default.</td>
    </tr>    <tr><td>--manager</td>
    <td>Add yourself to the new space, as manager. Done by default.</td>
    </tr>    <tr><td>--no-activate</td>
    <td>Complementary alias of --activate.</td>
    </tr>    <tr><td>--no-auditor</td>
    <td>Complementary alias of --auditor.</td>
    </tr>    <tr><td>--no-developer</td>
    <td>Complementary alias of --developer.</td>
    </tr>    <tr><td>--no-manager</td>
    <td>Complementary alias of --manager.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion delete-space *\<name\*###
Delete the named space. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--recursive</td>
    <td>Remove all sub-ordinate parts, and relations.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-r</td>
    <td>Alias of --recursive.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion link-user-space *\<user\* *\<space\*###
Add the specified user to the named space, in various roles. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auditor</td>
    <td>Affect the auditor role</td>
    </tr>    <tr><td>--developer</td>
    <td>Affect the developer role</td>
    </tr>    <tr><td>--manager</td>
    <td>Affect the manager role</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion rename-space *\<name\* *\<newname\*###
Rename the named space. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion spaces###
List the available spaces in the specified organization. See --organization for details This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--full</td>
    <td>Show more details.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion space *\<name\*###
Show the named space's information. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--full</td>
    <td>Show more details.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion switch-space *\<name\*###
Switch from the current space to the named space. This may switch the organization as well. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unlink-user-space *\<user\* *\<space\*###
Remove the specified user from the named space, in various roles. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--auditor</td>
    <td>Affect the auditor role</td>
    </tr>    <tr><td>--developer</td>
    <td>Affect the developer role</td>
    </tr>    <tr><td>--manager</td>
    <td>Affect the manager role</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>

### Routes[](#routes "Permalink to this headline")###
### helion delete-route *\<name\*###
Delete the named route. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--space</td>
    <td>The name of the space to use as context.
    Defaults to the current space.
    A current space is automatically set if there is none, either by
    taking the one space the user has, or asking the user to choose
    among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion routes###
List all available routes. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>

### Domains[](#domains "Permalink to this headline")###
### helion domains###
List the available domains in the specified space, or all. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Query information about all domains. Cannot be used together with
    a space.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--space</td>
    <td>The name of the space to use as context.
    Defaults to the current space.
    A current space is automatically set if there is none, either by
    taking the one space the user has, or asking the user to choose
    among the possibilities. Cannot be used together with --all.</td> 

    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion map-domain *\<name\*###
Add the named domain to an organization or space. This is a Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--space</td>
    <td>The name of the space to use as context.
    Defaults to the current space.
    A current space is automatically set if there is none, either by
    taking the one space the user has, or asking the user to choose
    among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion unmap-domain *\<name\*###
Remove the named domain from an organization or space. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The name of the parent organization to use as context.
    Defaults to the current organization.
    A current organization is automatically set if there is none,
    either by taking the one organization the user belongs to, or
    asking the user to choose among the possibilities.</td>
    </tr>    <tr><td>--space</td>
    <td>The name of the space to use as context.
    Defaults to the current space. 
    A current space is automatically set if there is none, either by
    taking the one space the user has, or asking the user to choose
    among the possibilities.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>

### Administration[](#administration "Permalink to this headline")
### helion admin grant *\<email\*
Grant the named user administrator privileges for the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion admin list###
Show a list of the administrators for the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion admin patch *\<patch\*###
Apply a patch to the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--dry</td>
    <td>Print the low-level ssh command to stdout instead of executing it.</td>
    </tr>    <tr><td>--dry-run</td>
    <td>Alias of --dry.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion admin report *\<destination\*###
Retrieve a report containing the logs of the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion admin revoke *\<email\*###
Revoke administrator privileges for the named user at the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion frameworks###
List the supported frameworks of the target. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups add-user *\<group\* *\<user\*###
Add the named user to the specified group. This is an Application Lifecycle Service 2
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion groups create *\<name\*###
Create a new group with the specified name. This is an Application Lifecycle Service 2
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups delete-user *\<group\* *\<user\*###
Remove the named user from the specified group. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups delete *\<name\*###
Delete the named group. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups limits *\<group\*###
Show and/or modify the limits applying to applications in the named group. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--apps</td>
    <td>Limit for the number of applications in the group.</td>
    </tr>    <tr><td>--appuris</td>
    <td>Limit for the number of mapped uris per application.</td>
    </tr>    <tr><td>--drains</td>
    <td>Limit for the number of drains in the group.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-sudo</td>
    <td>Complementary alias of --sudo.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--services</td>
    <td>Limit for the number of services in the group.</td>
    </tr>    <tr><td>--sudo</td>
    <td>Applications can use sudo (or not).</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups show###
Show the list of groups known to the target. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion groups users *\<group\*###
Show the list of users in the named group. This is an Application Lifecycle Service 2
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion group *\<name\*###
Report the current group, or (un)set it. This is an Application Lifecycle Service 2
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--reset</td>
    <td>Reset the current group to nothing. Cannot be used together with
    name.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion info###
Show the basic system and account information.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion limits *\<group\*###
Show and/or modify the limits applying to applications in the named group. This is an Application Lifecycle Service 2 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--apps</td>
    <td>Limit for the number of applications in the group.</td>
    </tr>    <tr><td>--appuris</td>
    <td>Limit for the number of mapped uris per application.</td>
    </tr>    <tr><td>--drains</td>
    <td>Limit for the number of drains in the group.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-sudo</td>
    <td>Complementary alias of --sudo.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--services</td>
    <td>Limit for the number of services in the group.</td>
    </tr>    <tr><td>--sudo</td>
    <td>Applications can use sudo (or not).</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota configure *\<name\*###
Reconfigure the named quota definition. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--allow-sudo</td>
    <td>Applications can use sudo in their container.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-allow-sudo</td>

    <td>Complementary alias of --allow-sudo.</td>
    </tr>    <tr><td>--no-paid-services-allowed</td>

    <td>Complementary alias of --paid-services-allowed.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--no-trial-db-allowed</td>

    <td>Complementary alias of --trial-db-allowed.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--paid-services-allowed</td>

    <td>Applications can use non-free services.</td>
    </tr>    <tr><td>--services</td>
    <td>Limit for the number of services in the quota.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--trial-db-allowed</td>

    <td>Applications can use trial databases.</td> </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota create *\<name\*###
Create a new quota definition. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--allow-sudo</td>
    <td>Applications can use sudo in their container.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-allow-sudo</td>

    <td>Complementary alias of --allow-sudo.</td>
    </tr>    <tr><td>--no-paid-services-allowed</td>

    <td>Complementary alias of --paid-services-allowed.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--no-trial-db-allowed</td>

    <td>Complementary alias of --trial-db-allowed.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--paid-services-allowed</td>

    <td>Applications can use non-free services.</td>
    </tr>    <tr><td>--services</td>
    <td>Limit for the number of services in the quota.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    </tr>    <tr><td>--trial-db-allowed</td>

    <td>Applications can use trial databases.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota delete *\<name\*###
Delete the named quota definition. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota list###
List the available quota definitions. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota rename *\<name\* *\<newname\*###
Rename the named quota definition. This is an Application Lifecycle Service 3 specific
command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quota show *\<name\*###
Show the details of the named quota definition. If not specified it will be asked for interactively (menu). This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion quotas###
List the available quota definitions. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion runtimes###
List the supported runtimes of the target. This is an Application Lifecycle Service 2
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion stacks###
List the supported stacks of the target. This is an Application Lifecycle Service 3
specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion targets###
List the available targets, and their authorization tokens, if any.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
###helion tokens###
List the available targets, and their authorization tokens, if any.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion usage *\<userOrGroup\*###
Show the current memory allocation and usage of the active or specified user/group (Application Lifecycle Service 2), or the specified or current space (Application Lifecycle Service 3).

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--all</td>
    <td>Query information about everything. Cannot be used together with
    userOrGroup.</td>
    </tr>    <tr><td>--group</td>
    <td>The once-off group to use for the current operation. This is a
    Application Lifecycle Service 2 option.</td>
    </tr>    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The once-off organization to use for the current operation. This
    is an Application Lifecycle Service 3 option.</td>
    </tr>    <tr><td>--space</td>
    <td>The once-off space to use for the current operation, specified by
    name. This is an Application Lifecycle Service 3 option. Cannot be used together with --space-guid.</td>
    </tr>    <tr><td>--space-guid</td>
    <td>The once-off space to use for the current operation, specified by
    guid. This is an Application Lifecycle Service 3 option. Cannot be used together with --space.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion user-info *\<name\*###
Shows the information of a user in the current or specified target. Defaults to the current user. Naming a specific user requires an Application Lifecycle Service 3 target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion user###
Show the name of the current user in the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion version###
Print the version number of the client.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>

**User Management**
### helion add-user *\<name\*
Register a new user in the current or specified target. This operation requires administrator privileges, except if "allow\_registration" is set server-side.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--admin</td>
    <td>Give the newly created user administrator privileges.</td>
    </tr>    <tr><td>--apps</td>
    <td>Limit for the number of applications in the group.</td>
    </tr>    <tr><td>--appuris</td>
    <td>Limit for the number of mapped uris per application.</td>
    </tr>    <tr><td>--drains</td>
    <td>Limit for the number of drains in the group.</td>
    </tr>    <tr><td>--email</td>
    <td>The email of the user to create. This is an Application Lifecycle Service 3 specific
    option.</td>
    </tr>    <tr><td>--group</td>
    <td>The group to put the new user into. This is an Application Lifecycle Service 2 specific
    option.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-sudo</td>
    <td>Complementary alias of --sudo.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The organization to place the new user into. Defaults to the
    current organization. This is an Application Lifecycle Service 3 specific option.</td>
    </tr>    <tr><td>--passwd</td>
    <td>Alias of --password.</td>
    </tr>    <tr><td>--password</td>
    <td>The password to use.</td>
    </tr>    <tr><td>--services</td>
    <td>Limit for the number of services in the group.</td>
    </tr>    <tr><td>--sudo</td>
    <td>Applications can use sudo (or not).</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion delete-user *\<email\*###
Delete the named user, and the user's applications and services from the current or specified target. This operation requires administrator privileges.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
###helion login-fields###
Show the names of the credential fields needed for a login. This is an Application Lifecycle Service 3 specific command.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion passwd###
Change the password of the current user in the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--passwd</td>
    <td>Alias of --password.</td>
    </tr>    <tr><td>--password</td>
    <td>The new password. If not present it will be interactively asked
    for.</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion register *\<name\*###
Register a new user in the current or specified target. This operation requires administrator privileges, except if "allow\_registration" is set server-side.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--admin</td>
    <td>Give the newly created user administrator privileges.</td>
    </tr>    <tr><td>--apps</td>
    <td>Limit for the number of applications in the group.</td>
    </tr>    <tr><td>--appuris</td>
    <td>Limit for the number of mapped uris per application.</td>
    </tr>    <tr><td>--drains</td>
    <td>Limit for the number of drains in the group.</td>
    </tr>    <tr><td>--email</td>
    <td>The email of the user to create. This is an Application Lifecycle Service 3 specific
    option.</td>
    </tr>    <tr><td>--group</td>
    <td>The group to put the new user into. This is an Application Lifecycle Service 2 specific
    option.</td>
    </tr>    <tr><td>--mem</td>
    <td>Amount of memory applications can use.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-sudo</td>
    <td>Complementary alias of --sudo.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--organization</td>
    <td>The organization to place the new user into. Defaults to the
    current organization. This is an Application Lifecycle Service 3 specific option.</td>
    </tr>    <tr><td>--passwd</td>
    <td>Alias of --password.</td>
    </tr>    <tr><td>--password</td>
    <td>The password to use.</td>
    </tr>    <tr><td>--services</td>
    <td>Limit for the number of services in the group.</td>
    </tr>    <tr><td>--sudo</td>
    <td>Applications can use sudo (or not).</td>
    </tr>    <tr><td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-o</td>
    <td>Alias of --organization.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion token###
Interactively set authentication token.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion unregister *\<email\*###
Delete the named user, and the user's applications and services from the current or specified target. This operation requires administrator privileges.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion users###
Show the list of users known to the current or specified target.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### Convenience[](#convenience "Permalink to this headline")###
### helion aliases###
List the known aliases (shortcuts).

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion alias *\<name\* *\<command\*###
Create a shortcut for a command (prefix).

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion unalias *\<name\*###
Remove a shortcut by name.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>

### Miscellaneous[](#miscellaneous "Permalink to this headline")###
### helion admin exit###
Exit the shell. No-op if not in a shell.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
###helion admin help *\<cmdname\*###
Retrieve help for a command or command set. Without arguments help for all commands is given. The default format is --full.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--by-category</td>
    <td>Activate by-category form of the help.</td>
    </tr>    <tr><td>--full</td>
    <td>Activate full form of the help.</td>
    </tr>    <tr><td>--json</td>
    <td>Activate json form of the help.</td>
    </tr>    <tr><td>--list</td>
    <td>Activate list form of the help.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--short</td>
    <td>Activate short form of the help.</td>
    </tr>    <tr><td>--width</td>
    <td>The line width to format the help for. Defaults to the terminal
    width, or 80 when no terminal is available.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-w</td>
    <td>Alias of --width.</td>
    </tr>
</table>
###helion curl *\<operation\* *\<path\* *\<header\*###
Run a raw rest request against the chosen target

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--no-trace</td>
    <td>Complementary alias of --trace.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--target</td>
    <td>The once-off target to use for the current operation.</td>
    </tr>    <tr><td>--token</td>
    <td>The once-off authentication token to use for the current
    operation.</td>
    </tr>    <tr><td>--token-file</td>
    <td>Path to an existing and readable file containing the targets and
    authorization tokens.</td>
    </tr>    <tr><td>--trace</td>
    <td>Activate tracing of the issued REST requests and responses. This
    option is a no-op now. Tracing is always active. See the 'trace'
    command to print the saved trace to stdout.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-t</td>
    <td>Alias of --trace.</td>
    </tr>
</table>
### helion debug-packages###
Show the packages used the client, and their versions.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion drain exit###
Exit the shell. No-op if not in a shell.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion drain help *\<cmdname\*###
Retrieve help for a command or command set. Without arguments help for all commands is given. The default format is --full.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--by-category</td>
    <td>Activate by-category form of the help.</td>
    </tr>    <tr><td>--full</td>
    <td>Activate full form of the help.</td>
    </tr>    <tr><td>--json</td>
    <td>Activate json form of the help.</td>
    </tr>    <tr><td>--list</td>
    <td>Activate list form of the help.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--short</td>
    <td>Activate short form of the help.</td>
    </tr>    <tr><td>--width</td>
    <td>The line width to format the help for. Defaults to the terminal
    width, or 80 when no terminal is available.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-w</td>
    <td>Alias of --width.</td>
    </tr>
</table>
### helion exit###
Exit the shell. No-op if not in a shell.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion groups exit###
Exit the shell. No-op if not in a shell.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion groups help *\<cmdname\*###
Retrieve help for a command or command set. Without arguments help for all commands is given. The default format is --full.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--by-category</td>
    <td>Activate by-category form of the help.</td>
    </tr>    <tr><td>--full</td>
    <td>Activate full form of the help.</td>
    </tr>    <tr><td>--json</td>
    <td>Activate json form of the help.</td>
    </tr>    <tr><td>--list</td>
    <td>Activate list form of the help.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--short</td>
    <td>Activate short form of the help.</td>
    </tr>    <tr><td>--width</td>
    <td>The line width to format the help for. Defaults to the terminal
    width, or 80 when no terminal is available.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-w</td>
    <td>Alias of --width.</td>
    </tr>
</table>
###helion guid *\<type\* *\<name\*###
Map the specified name into a uuid, given the type. This is an Application Lifecycle Service 3 specific command.
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion help *\<cmdname\*###
Retrieve help for a command or command set. Without arguments help for all commands is given. The default format is --full.

<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--by-category</td>
    <td>Activate by-category form of the help.</td>
    </tr>    <tr><td>--full</td>
    <td>Activate full form of the help.</td>
    </tr>    <tr><td>--json</td>
    <td>Activate json form of the help.</td>
    </tr>    <tr><td>--list</td>
    <td>Activate list form of the help.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--short</td>
    <td>Activate short form of the help.</td>
    </tr>    <tr><td>--width</td>
    <td>The line width to format the help for. Defaults to the terminal
    width, or 80 when no terminal is available. </tr><tr>td></tr><tr>
    <td>-w</td>
    <td>Alias of --width.</td>
    </tr>
</table>
### helion named-entities###
List the entity types usable for 'guid'. I.e. the types of the
    named entities known to the client.
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--json</td>
    <td>Print raw json as output, not human-formatted data.</td>
    </tr>    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion quota exit###
Exit the shell. No-op if not in a shell.
    
<table>
    <tr><td><b>Option</b></td><td><b>Description</b></td></tr>
    <tr><td>--no-prompt</td>
    <td>Disable interactive queries.</td>
    </tr>    <tr><td>--non-interactive</td>

    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>--noprompt</td>
    <td>Alias of --no-prompt.</td>
    </tr><tr>
    <td>-n</td>
    <td>Alias of --no-prompt.</td>
    </tr>
</table>
### helion quota help *\<cmdname\>*###
Retrieve help for a command or command set. Without arguments, help for all commands is given. The default format is --full.
    
<table>
<tr><td><b>Option</b></td><td><b>Description</b></td></tr>
<tr><td>--by-category</td>
<td>Activate by-category form of the help.</td>
</tr>    <tr><td>--full</td>
<td>Activate full form of the help.</td>
</tr>    <tr><td>--json</td>
<td>Activate json form of the help.</td>
</tr>    <tr><td>--list</td>
<td>Activate list form of the help.</td>
</tr>    <tr><td>--no-prompt</td>
<td>Disable interactive queries.</td>
</tr>    <tr><td>--non-interactive</td>
<td>Alias of --no-prompt.</td>
</tr><tr>
<td>--noprompt</td>
<td>Alias of --no-prompt.</td>
</tr><tr>
<td>--short</td>
<td>Activate short form of the help.</td>
</tr>    <tr><td>--width</td>
<td>The line width to format the help for. Defaults to the terminal
width, or 80 when no terminal is available.</td> </tr><tr>
<td>-n</td>
<td>Alias of --no-prompt.</td>
</tr><tr>
<td>-w</td>
<td>Alias of --width.</td>
</tr>
</table>
### helion trace###
Print the saved REST trace for the last client command to stdout.
    
<table>
<tr><td><b>Option</b></td><td><b>Description</b></td></tr>
<tr><td>--no-prompt</td>
<td>Disable interactive queries.</td>
</tr>    <tr><td>--non-interactive</td>
<td>Alias of --no-prompt.</td>
</tr><tr>
<td>--noprompt</td>
<td>Alias of --no-prompt.</td>
</tr><tr>
<td>-n</td>
<td>Alias of --no-prompt.</td>
</tr></table>