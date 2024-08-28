ASP.NET Core is the framework designed for web development using C# and .NET. It contains a lot of tools that you can use and install like modules. In order to create a project, you can use the dotnet cli command:  `dotnet new webapp`.

This will create a basic template with some generic configurations ready to go with a single page and error page.
## Entry point
The application starts in the file `Program.cs` in which you can define services required by your application, setup middleware and other infrastructure settings.

> ASP.NET Core uses the concept of Hosts. If you want to know more about it, see [[Hosts]]

There are three kinds of Hosts that are capable of running an ASP.NET Core app:
- ASP.NET Core WebApplication and WebApplicationBuilder. It's also known as Minimal Host.
- .NET Generic Host combined with ASP.NET Core's ConfigureWebHostDefaults.
- ASP.NET Core WebHost. It's only available for backwards compatibility.

The `WebApplication.CreateBuilder` configures a host with a set of default options, such as:
- Use Kestrel as web server and enable IIS integration.
- Load configuration from `appsettings.json` environment variables, command line arguments, and other configuration sources.
- Send logging output to the console and debug providers.

The underlying server sends the request to the application in the form of an object called `HttpContext` and the application parses this context to produce a response. 

There are kinds of ASP.NET Core applications and, so, we need to cover them one by one
## APIS
Application Programming Interface is a common pattern in which we can develop an application that is used by other applications through its API. We can create controllers using an MVC approach and create a Controller-Based API. The controller must derive from `ControllerBase`. (Yes, there's a class called `Controller`, but it's used for controller with view support).

For example, here is a Controller-Based API controller:
```
using Microsoft.AspNetCore.Mvc;

namespace hello_world.Controllers
{
    public class WeatherController: ControllerBase
    {
        public ActionResult<string> hello()
        {
            return Ok("Hello");
        }
    }
}
```
The method `Ok` comes from the `ControllerBase`. It defines a lot of other methods that exists to make the developer life easier. 
### Routing
Routing is the process of matching an specific controller and method to an specific controller. There are two kinds of routing in ASP.NET Core: Conventional and Attribute routing. The conventional routing is made out of a string pattern that will be used to find the right controller and the right action to be executed.

In order to use controllers, you need to specify in the `Program.cs` the middleware responsible for handling the `HttpContext` and map them to actions. The middleware uses the `Route Template` defined in the `Program.cs` or in attributes to match the controller and the action.

Before mapping the controllers, we need to add its services. Now, we are going to configure a Controller with support to views.

```
var builder = WebApplication.CreateBuilder(args); 

builder.Services.AddControllersWithViews(); // This maps the controllers and create the route table.

app.MapControllerRoute(
	"default", 
	"{controller=Home}/{action=Index}/{id?}"
);
```
### Attributes
#### ApiController
There're attributes that can be applied to certain controllers to specify some opinionated behaviors. For example, an attribute called `[ApiController]` can be used in any Controller-Based API class that extends the class `ControllerBase`. This attribute makes another attributes and configuration a requirement. 