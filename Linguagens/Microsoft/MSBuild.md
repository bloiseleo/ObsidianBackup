MSBuild is the microsoft build system used to build and manage .NET projects. Their informations are stored in files that ends with `proj`. So, if you have a `Visual Basic` project, then you have a `vbproj`. If you have a `C#` project, so you have a `csproj` and so on.
Every project file starts with a root node called `Project`. Usually, they all have a property called `sdk`, it will determine some important stuff that we'll cover later on. 
## Build Properties
These properties are key-value pairs that guides and defines some variables that are important to the build itself. They're located inside a `PropertyGroup` and they can be user-defined and there're some properties that MSBuild uses to define some building behavior.
> The properties are defined and overwritten based on the order they're defined. So, if you have defined a property in the line 20, but, in the line 21, you had imported a file with the same property name, the value of the imported one will overwrite the old one defined by the line 20.

If you want to, you can access previously defined properties inside another properties using this notation:
```
<Target Name="HelloWorld">
	<Message Text="Hello World, MsBuild. We're using $(Configuration) to build this product"/>
</Target>
```
Besides accessing MSBuild properties, you can access environment variables inside the `csproj`. These variables are PascalCased. So, if you want to acess the PATH, you can do this by: `$(Path)`.
> If any value defined in `csproj` has the same name of the env var, it will override the value of the environment variable.
## Target and Task
A task is the smallest unit inside the `MSBuild` file. They're independent executable components that may include input or output. Besides, a target is a sequence of tasks. These tasks do something in order to achieve some result, so they're ordered inside a target that aims to build this something.
It would be very boring if we had to write all these tasks in every C# project, so, in order to simplify things, the `Sdk` attribute defines some implicit imports that imports targets and tasks needed to build a C# project.
> These imports are defined by the `Sdk` attribute and they'll differ project to project.
### Create new Target
To create a new target, you should do something like it:
```
<Target Name="HelloWorld">
  <Message Text="Hello World, MSBuild" />
  <Message Text="We are building with the configuration $(Configuration)" />
</Target>
```
Here we have defined a Target named `HelloWorld`. This target contains two `Message` tasks. They define a message to be prompted using the attribute `Text`.
> If you want to, you can take a look into all the 
## Items
An Item is some file that is used as input to the build system. They're grouped into `ItemGroup` tags and they all can have different types. In the example below, we're using the `ItemGroup` to declare a folder  called `assets`.
```
<ItemGroup>
  <Folder Include="assets\" />
</ItemGroup>
```