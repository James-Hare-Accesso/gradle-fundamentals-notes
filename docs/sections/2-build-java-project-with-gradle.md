# Build a Java Project with Gradle

Go to IntelliJ and create a new project with Gradle.

The build.gradle file will look like this:

```groovy
plugins {
    id 'java'
}

group 'org.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testCompile group: 'junit', name: 'junit', version: '4.12'
}

```

Group and Version follow the same concepts as Maven. The artifact name is sotred in the gradle.settings file instead of with the group and version tags.

Repositories is pointing to Maven Central, you can also point to other repos, including corp artifactory.

Dependencies has junit on the testCompile group.

I found a better example of a build.gradle file using the spring initializer.

```groovy
plugins {
    id 'org.springframework.boot' version '2.4.1'
    id 'io.spring.dependency-management' version '1.0.10.RELEASE'
    id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '8'

configurations {
    compileOnly {
        extendsFrom annotationProcessor
    }
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter'
    compileOnly 'org.projectlombok:lombok'
    annotationProcessor 'org.projectlombok:lombok'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

test {
    useJUnitPlatform()
}
```

To build gradle use the following command:

`gradle build`

## Learning Groovy for Gradle

Examining Java to Groovy: 

`System.out.println(); becomes just println()`

There's no need for semicolon at the end of statements.

If there's one arg in a method call, you don't need to have parentheses.

It's still compiled down to byte code, the syntax is just more simple.

```groovy
class MyClass {
    void doSomething(Closure closure) {
        closure.call()
    }
}

myObject = new MyClass()

myObject.doSomething{
    println new Date()
}
```

With closures in Groovy (and Java 8+), you can define a method body at run time to be called and executed.


## The Gradle Project Object Model

What is the POM?
* Is a Java object built by Gradle
* Represents the "things" in our application
* Is used by Gradle to build projects
* Is modifiable by developers

Objects in the POM:
* Project
    * One-to-one relationship with build.gradle
    * Assigned to a "project" reference variable
* Task
    * Project is a collection of tasks (compiler, create jar file, etc.)
    * Task is a collection of actions
    * Actions are functions performed by Gradle
    * Actions list tasks for project

The build.gradle file modifies the Project Object

`project.sourceCompatibility = 1.8`

`project.dependencies {}`

You don't have to specify the project object, but you can.

Run the following command to see the project properties available:

`gradle properties`

You can also view available properties at [https://docs.gradle.org/current/javadoc/org/gradle/api/Project.html](https://docs.gradle.org/current/javadoc/org/gradle/api/Project.html)

To view available tasks run the following command:

`gradle tasks`
