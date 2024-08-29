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

