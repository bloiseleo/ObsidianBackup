ASP.NET Core is the framework designed for web development using C# and .NET. It contains a lot of tools that you can use and install like modules. In order to create a project, you can use the dotnet cli command:  `dotnet new webapp`.

This will create a basic template with some generic configurations ready to go with a single page and error page.
## Entry point
The application starts in the file `Program.cs` in which you can define services required by your application, setup middleware and other infrastructure settings.

> ASP.NET Core uses the concept of Hosts. If you want to know more about it, see [[Hosts]]
