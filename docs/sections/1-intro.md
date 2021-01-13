# What is Gradle?

Applications can be pretty complicated and involve lots of files and artifacts. They may contain java src, java byte code, xml files, etc. So building a deployable application can be pretty difficult.

Gradle's purpose is to build and deploy the application once we've written it.

Gradle is a framework for building applications and managing dependencies.

Source code --> Gradle --> Deployable artifacts.

What are dependencies?

* Third party jars
* Internal/ Proprietary artifacts

Gradle uses Groovy instead of a declarative XML language (like Ant and Maven use).

6 Key features of Gradle:

* Build File
    * Human and machine readable file
    * Declarative and programmatic
    * Uses DSL and Groovy (or Kotlin if you want)
    * Default name is build.gradle
* Graph of the Tasks
    * Tasks are the detailed build steps
    * Gradle parses the build.gradle file to get the tasks
    * Creates a DAG (directed acryilic graph) a set of tasks that only go in one direction (acyclic)
* Gradle executes the tasks
    * In the order that it has figured out that they have to be executed
    * Each task gets some input and produces some output to be used by the next task
* Manages dependencies
    * Dependencies are jars outside the code
        * May be transitive dependencies (additional dependencies internal to that jar)
    * Can get the specific version of the dependency
* Uses repositories
    * Storehouses of external dependencies
        * Out on the Internet
        * In our corp artifactory
* Self-updating
    * Gradle can retrieve new versions of gradle itself
    * auto-retrieval of new dependencies that we define