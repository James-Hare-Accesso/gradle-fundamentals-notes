# Gradle Project Structure

List of important files:

* settings.gradle
    * The most important gradle file
    * defines the root project name
    * can include other libraries
* buiild.gradle
    * Defines artifact info (groupa and version)
    * apply plugins (Java plugin)
    * define the source compatibility
    * declare repositories to use
    * declare dependencies
* src
    * normal java conventional dir structure
    * src
        * main
            * java
                * packages
                    * classes
            * resources
        * test
            * java
                * ...
            * test resources
* gradle directory
    * known as the gradle wrapper
    * provides a lightweight version of gradle to make sure that all devs are using the same version of gradle to work together.

# Gradle Build Directory

This is where the final artifact is saved.

Run `gradle -q clean` to clean out the build directory.

# The Gradle Wrapper

The gradle wrapper is a thin layer around gradle.

It checks that gradle is installed properly.

`gradlew` is for unix
`gradle.bat` is for Windows