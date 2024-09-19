.NET is a developer platform to develop for building applications. When you develop an application for `.NET`, you are developing an application that targets one or more implementations of `.NET`. 
Each implementation includes:
- Runtime: The engine responsible for loading and executing your application.
- Class Library
- Application Frameworks: This is optional and it can be ASP.NET, Windows Forms or WPF.
- Dev Tools: Also optional.
There are some implementations and they are explained below.
## DOTNET 5
.NET 5, previously referred as .NET Core, is a cross-platform implementation of .NET that's designed to handle server and cloud workloads, including desktop apps. It also implements .NET Standard, so, if your application targets .NET Standard, it should run smoothly with .NET Core.
## DOTNET Framework 
.NET Framework was the original implementation of .NET. It contains additional Windows-Specific APIs, such as APIS for Windows desktop, WPF and etc. It's the main implementation for Windows based applications. Since 4.5 version, .NET Framework implements .NET Standard. Then, if your code targets .NET Standard, it should run smoothly on any other implementation that implements .NET Standard.

> If you are using any Windows-API, you'll have trouble while running this application.
## Mono
This is the smallest implementation of .NET. It's the runtime that powers Xamarin applications on mobile devices and games. It supports all .NET Standard versions.
## .NET Standard
.NET Standard is a set of contracts rather than an implementation of .NET platform. Every implementation of .NET platform must supports a set of these contracts. Therefore, every application that targets .NET Standard can run on any implementation that supports .NET Standard.
