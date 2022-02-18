# Custom Checkstyle Config

Custom [Checkstyle](https://github.com/checkstyle/checkstyle) config for Java projects.

## Installation

1. Put [`checkstyle.xml`](config/checkstyle/checkstyle.xml) to `$rootDir/config/checkstyle`. 
2. Add the following to the Gradle build file:

#### Groovy DSL:

```groovy
plugins {
    id "checkstyle"
}

checkstyle {
    toolVersion "version"
    sourceSets = [] // Don't check anything with Checkstyle during 'check' task
}

task checkstyle(type: Checkstyle) {
    source "src"
    classpath = files()
}
```

#### Kotlin DSL:

```kotlin
plugins {
    checkstyle
}

checkstyle {
    toolVersion = "version"
    sourceSets = listOf() // Don't check anything with Checkstyle during 'check' task
}

tasks.register("checkstyle", Checkstyle::class) {
    source = fileTree("$rootDir/src")
    classpath = files()
}
```

Check last version here: https://checkstyle.sourceforge.io/releasenotes.html

## Usage

Run `./gradlew checkstyle`.
