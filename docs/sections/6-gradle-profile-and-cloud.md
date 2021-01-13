# Gradle Profile

A gradle profile:

* Lets you report on the build highlighting performance
* Can be created any time you run a task
* Can be saved permanently to record a history of the build performance

Use `grade build --profile` to run a build and enable the profile.

Every time you run the build task with profile enabled, it will output a profile report which lists the name, duration and results of each task.

# Gradle Cloud Build Scan

The cloud build scan:
* a new capability
* a set of build reports
* saved to the cloud instead of the local machine

Add the plugin to your plugins section:

```groovy
plugin {
    id 'com.gradle.build-scan' version '1.6'
}
```

Add the build scan itself:

```groovy
buildScan {
    licenseAgreementUrl = 'https://gradle.com/terms-of-service'
    licenseAgree = 'yes'
}
```

Run with `gradle build --scan` to publish the build scan to the cloud.