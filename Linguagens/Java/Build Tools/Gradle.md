Gradle is a build tool that manages a project as a whole, such as an application or library code. But, we can have two kinds of projects:
- Single projects: There's only a single project called root project
- Multi projects: There're more than one root project and any number of subprojects.
## Project Structure
Every gradle project contains some common files and folders:
- `gradle`:  This folder store wrappers files and more.
- `gradle/libs.version.toml`: Version catalog for dependency management
- `gradlew and gradlew.bat`: Wrapper scripts
- `settings.gradle(.kts)`: Settings file to define the root project name and subprojects included.
- `build.gradle(.kts)`: Build scripts of the two subprojects.

## Settings Script
The settings script is the `settings.gradle` file in which we can define the `rootProject.name`, which is the project name and include the subprojects like:

```
rootProject.name = "bot"
include("bot")
```

The include statement will tell gradle that we want to include a subproject while building the whole project.

## Build Script
The build script is the `build.gradle(.kts)` file in which you will detail build configuration, tasks and plugins. In this kind of file, you can add two types of dependencies: 
- Libraries or plugins that Gradle and the build script needs.
- Libraries on which the project sources depend.

```
plugins {  
    kotlin("jvm") version "2.0.10"  
}  
  
group = "guaxinim.musical"  
version = "0.0.1"  
  
repositories {  
    mavenCentral()  
}  
  
dependencies {  
    testImplementation(kotlin("test"))  
}  
  
tasks.test {  
    useJUnitPlatform()  
}  
kotlin {  
    jvmToolchain(17)  
}
```

In the `plugin` area, you can add plugins. These plugins contribute and extend Gradle functionality. For example, the plugin `application` helps in creating JVM executables. Plugins can also add tasks and properties. The `application` plugin also adds  properties. These properties can be called and configured. For example, to determine the main class of the application, you could do something like that:
```
plugins {
	id("application")
}

application {
	mainClass = "org.example.Main"
}
```