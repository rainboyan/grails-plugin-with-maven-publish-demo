# Grails Plugin Demo

Create a Grails Plugin with `maven-publish` feature, use `maven-publish` gradle plugin to publish plugin.

## Grails Version

- Grails **5.1.3**

## Usage

Grails `plubin` profile provide `maven-publish` feature, we could use it to install it to the local Maven repository. Grails Commands - [create-plugin](https://docs.grails.org/latest/ref/Command%20Line/create-plugin.html) dosen't describe this feature.

### Create plugin

```
grails create-plugin --features maven-publish org.grails.demo.grails-plugin-with-maven-publish-demo
cd grails-plugin-with-maven-publish-demo
./gradlew publishToMavenLocal
```

### Grails install command not found

When execute `grails help`

```
Usage (optionals marked with *):'
grails [environment]* [target] [arguments]*'

| Examples:
$ grails dev run-app
$ grails create-app books

| Available Commands (type grails help 'command-name' for more info):
| Command Name                          Command Description
----------------------------------------------------------------------------------------------------
assemble                                Creates a JAR or WAR archive for production deployment
bug-report                              Creates a zip file that can be attached to issue reports for the current project
clean                                   Cleans a Grails application's compiled sources
compile                                 Compiles a Grails application
console                                 Runs the Grails interactive console
create-command                          Creates an Application Command
create-controller                       Creates a controller
create-domain-class                     Creates a Domain Class
create-integration-test                 Creates an integration test
create-interceptor                      Creates an interceptor
create-scaffold-controller              Creates a scaffolded controller
create-script                           Creates a Grails script
create-service                          Creates a Service
create-taglib                           Creates a Tag Library
create-unit-test                        Creates a unit test
dependency-report                       Prints out the Grails application's dependencies
generate-all                            Generates a controller that performs CRUD operations and the associated views
generate-async-controller               Generates an asynchronous controller that performs CRUD operations
generate-controller                     Generates a controller that performs CRUD operations
generate-views                          Generates GSP views for the specified domain class
gradle                                  Allows running of Gradle tasks
help                                    Prints help information for a specific command
install                                 Installs a plugin into the local Maven cache
install-templates                       Installs scaffolding templates that use f:all to render properties
list-plugins                            Lists available plugins from the Plugin Repository
open                                    Opens a file in the project
package-plugin                          Packages the plugin into a JAR file
plugin-info                             Prints information about the given plugin
publish-plugin                          Publishes the plugin to the Grails central repository
run-app                                 Runs a Grails application
run-command                             Executes Grails commands
run-script                              Executes Groovy scripts in a Grails context
shell                                   Runs the Grails interactive shell
stats                                   Prints statistics about the project
stop-app                                Stops the running Grails application
test-app                                Runs the applications tests
url-mappings-report                     Prints out a report of the project's URL mappings

| Detailed usage with help [command]
```


But unfortunately, the `install` was not exist any more! So, We add it to Gradle in `build.gradle`.

```
task install(dependsOn: 'publishToMavenLocal') {
    description 'Installs a plugin into the local Maven Repository'
}
```

## Links

- [Grails](https://grails.org)
- [Grails Github](https://github.com/grails)
- [Grails Commands - create-plugin](https://docs.grails.org/latest/ref/Command%20Line/create-plugin.html)
- [Grails Plugins Docs](https://docs.grails.org/latest/guide/plugins.html)