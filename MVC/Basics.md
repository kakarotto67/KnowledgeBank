#ASP.NET/MVC General

#### Navigation
- [ASP.NET MVC Routing](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#aspnet-mvc-routing)
- [Deployment](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#deployment)
 - [Deployment to Azure - General Steps](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#deployment-to-azure---general-steps)

#### ASP.NET MVC Routing
- Routing allows you to use friendly and logical and URLs
- The following actions will initialize your routing scheme:

```cs
    // 1. Register your routes (typically performed in `App_Start\RouteConfig.cs` static class)
    public class RouteConfig
    {
        public static void RegisterRoutes(RouteCollection routes)
        {
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

            routes.MapRoute(
                name: "Default",
                url: "{controller}/{action}/{id}",
                defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
            );
        }
    }
```

```cs
    // 2. Add registered routes into route table (typically performed in `global.asax.cs` code-behind)
    public class MvcApplication : HttpApplication
    {
        protected void Application_Start()
        {
            RouteConfig.RegisterRoutes(RouteTable.Routes); // Registration of routes
            // Any other registrations...
        }
    }
```

- Accodring to code snippets above, if you request `/Home/Index/3`, the following code will be executed - `HomeController.Index(3);`, where:
 - `HomeController` - MVC controller
 - `Index` - action method of that controller, which takes `3` as a parameter
- Here is the whole code of the `HomeController` and `Index` action method:
```cs
    public class HomeController : Controller
    {
        public ActionResult Index(string id)
        {
            // Do something with `id` parameter
            return View();
        }
    }
```

#### Deployment
- Check [this link](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-application-deployment) to get more information

###### Deployment to Azure - General Steps
1. Register on [MS Azure](https://azure.microsoft.com) website
2. Buy license or start 15-days trial
3. Prepare some web application (MVC, WebAPI, WCF, etc.)
4. Create new application in MS Azure
 1. Choose plan (free trial, license) and location for it (US, EU, Brasil, China, etc.)
 2. Buy domain for you application
5. Deploy web application to MS Azure using `Publish`->`MS Azure...` options in Visual Studio or just using `MSBuild.exe` utility
6. Monitor your application using MS Azure administration panels (load, errors, status, stop/restart, etc.)
