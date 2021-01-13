# Gradle Tasks

Functions performed by gradle

Consists of one of more actions

Tell gradle what to do

Can depend on other tasks

e.g. `gradle build`

To view tasks run `gradle tasks`

# Gradle View Tool

Provides an alternate way to running Gradle tasks

Has its own GUI

Is useful when you are first learning Gradle

Is available in IntelliJ just the same as Maven

# Create a New Gradle Task

Example task that prints the current date:

```groovy
task showDate {
    dependsOn build
    group = 'my tasks'
    description = "Show current date"
    doLast {
        println 'Current Date: ' + new Date()
    }
}
```

Run `gradle showDate` in terminal to run the task.

To make it depend on another task, add the dependsOn var. This means that build needs to run before showTask will run, meaning that gradle showDate will run the build and then showDate tasks.

`group` assigns the task to a group and `description` offers a description in the task view.

If you don't assign a task to a group, it won't show up when running `gradle tasks`. To show the task you will either have to run `gradle tasks --all` or just add the task to a group.

# Extend Existing Tasks

```groovy
class ShowDate extends DefaultTask {

    String dataMessage = "Date is: "

    @TaskAction
    void showDate() {
        println dateMessage + new Date()
    }
}

task showDate(type: ShowDate)
```

In the code above, we define a class that extends the DefaultTask class. We define what we want the task to do in a method annotated with @TaskAction and pull it all into the build.gradle file with a task.

Other methods available in the Task interface that DefaultTask implements:

* configure(Closure configureClosure)
* deleteAllActions()
* doFirst(Closure action)
* doLast(Closure action)

You can override an extending task. An example would be:

```groovy
task customShowDate(type: ShowDate) {
    dateMessage = "Custom time is: "
}
```

# Creating Gradle Plugins

Reasons for creating a plugin:
* To stop from repeating yourself
* Allows resuse within project and enterprise

```groovy
buildscript {
    dependencies {
        classpath files('module-name/build/libs/module-project-name-1.0-SNAPSHOT.jar')
    }
}

apply plugin: 'module-project-name-plugin'
```

To run the plugin use `gradle moduleName`
