# Dependencies

Run `gradle projects` to see a list of dependencies and other info about a project.

Run `gradle dependencies` to view all dependencies.

Run `gradle dependencies --configuration compile` to view all dependencies in the compile configuration.

Run `gradle dependencies --configuration testCompile` to view all dependencies in the testCompile configuration (will also include all regular compile dependencies). This will also bring in transitive dependencies in a basic starter project.

There is a way to specify version versions of transitive dependencies, which the instructor will explain later.

Add `apply plugin: 'project-report` to gradle.build and then run `gradle htmlDependencyReport` to create a report file that lists the dependencies.

## Creating Library Modules

Steps:
* Define a new module
* Code the module
* Assign the dependency for the module
* Extract the JSON display code into a separate module

Add a new module to IntelliJ and take a look at the settings.gradle file in the root directory. You will notice that the new module has been added as follows:

`include 'project-name'`

If you want to pull in the new module (library) into another module or the root project if you have one, you can add it as a dependency as follows:

```groovy
project.dependencies {
    compile project(':project-name')
}
```

