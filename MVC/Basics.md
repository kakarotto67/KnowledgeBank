#ASP.NET/MVC General

#### Navigation
- [MVC Overview](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#mvc-overview)
 - [The Model](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#the-model)
 - [The View](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#the-view)
 - [The Controller](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#the-controller)
 - [Controllers, Views and Action Methods](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#controllers-views-and-action-methods)
 - [Passing Model to a View](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#passing-model-to-a-view)
 - [Passing Data via Dynamic Properties](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#passing-data-via-dynamic-properties)
 - [Special Views](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#special-views)
 - [Layout Page](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#layout-page)
- [Razor View Engine](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#razor-view-engine)
- [MVC Routing](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#mvc-routing)
- [MVC Filtering](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#mvc-filtering)
- [Deployment](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#deployment)
 - [Deployment to Azure - General Steps](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/Basics.md#deployment-to-azure---general-steps)

#### MVC Overview
###### The Model
- Model - a class with some business logic
- All models are located under `Models` folder in any ASP.NET MVC project
- Model class can contain different properties
- You can use different attributes from `System.ComponentModel.DataAnnotations` namespace to give some characteristics to each property of the model. Some of them are:
 - `StringLength` - specifies minimum and maximum length of the field's value
 - `Display` - specifies the alias name for the field
 - `DisplayFormat` - specifies how field's value is displayed and formatted
 - `DataType` - specifies additional type of the field
 - `RegularExpression` - specifies that field's value must match the specified regular expression
 - `Required` - specifies that field's value is required
- Typical model class is shown below

```cs
    public class Movie
    {
        public int ID { get; set; }
        
        [StringLength(60, MinimumLength = 3)]
        public string Title { get; set; }
        
        [Display(Name = "Release Date"), DataType(DataType.Date)]
        [DisplayFormat(DataFormatString = "{0:d}", ApplyFormatInEditMode = true)]
        public DateTime ReleaseDate { get; set; }
        
        [RegularExpression(@"^[A-Z]+[a-zA-Z''-'\s]*$")]
        [Required]
        [StringLength(30)]
        public string Genre { get; set; }
        
        [Range(1, 100), DataType(DataType.Currency)]
        public decimal Price { get; set; }
        
        [RegularExpression(@"^[A-Z]+[a-zA-Z''-'\s]*$")]
        [StringLength(5)]
        public string Rating { get; set; }
    }
```

###### The View
- View - an .aspx (Aspx engine) or, more commonly, .cshtml (Razor engine) page with HTML markup, scripts and styles that defines the HTML page. Basically, views represent the UI of any web application
- All views are located under `Views` folder in any ASP.NET MVC project
- Here is the example of simple Razor view (`Index.cshtml`)

```
@{
    ViewBag.Title = "Index";
}

<h2>Index</h2>
```

###### The Controller
- Controller - controls any type of interaction between views and business logic (models, etc.)
- All controllers are located under `Controllers` folder in any ASP.NET MVC project
- Each controller implements `System.Web.Mvc.Controller` class
- Each controller has **action methods** which typically return `System.Web.Mvc.ActionResult` instances and (if they return `ViewResult`, which is implementation of `ActionResult`) associated with corresponding views

###### Controllers, Views and Action Methods
- Each view is tied with its parent controller, so it is located under controller's subfolder inside `Views` folder. For example, if you have `MoviesController` controller, then all its views are located under `\Views\Movies\` folder
- Each view is tied with some **action method** from its parent controller. They are tied by name, e.g., `About` view under `\Views\Home` folder is tied with action method `About` from `HomeController` class
- Each action method which returns `ActionResult` (actually, `ViewResult`, which is implementation of abstract `ActionResult` class) is associated with some view (view name is exactly the same as action method name, e.g., if action method name is `About`, then view name is also `About`)

```cs
        public ActionResult About()
        {
            // Returns `ViewResult` instance which represents `About` view
            // If you return something else here, e.g., `EmptyResult`, then you do not need a view
            return View();
        }
```

- Some `ActionResult` implementations:
 - `ViewResult` (mentioned above)
 - `RedirectResult`
 - `JsonResult`
 - `JavaScriptResult`
 - `FileResult`
 - `EmptyResult`, etc.
- All relations mentioned above are illustrated at the image below. There is `MoviesController` controller inside `Controllers` folder. It has some action methods, such as `Index`, `Create`, `Delete`, etc. All those methods represent appropriate views from corresponding `Views\Movies` folder. The image also represents typical MVC project structure

![MVC project structure](https://github.com/kakarotto67/KnowledgeBank/blob/master/MVC/mvc-structure.png)

###### Passing Model to a View
- You can pass data between controller and view by using of view constructor

```cs
        public ActionResult Details(int id)
        {
            // Some implementation details
            Movie movie = database.Movies.Find(id);
            return View(movie); // Pass movie model into `Details` view
        }
```

- In this case, you can then use the model on a view via `@model` keyword. Note, how `@model` is initialized in the 1st line of the view

```
@model MvcMovie.Models.Movie

@{
    ViewBag.Title = "Details";
}

<h2>Details</h2>

<div>
    <h4>Movie</h4>
    <hr />
    <dl class="dl-horizontal">
        <dd>
            @Html.DisplayFor(model => model.Title)
        </dd>
        <dd>
            @Html.DisplayFor(model => model.ReleaseDate)
        </dd>
        <dd>
            @Html.DisplayFor(model => model.Genre)
        </dd>
        <dd>
            @Html.DisplayFor(model => model.Price)
        </dd>
    </dl>
</div>
```

###### Passing Data via Dynamic Properties
- Typically you use `@ViewBag` dynamic property to pass some data between view and controller, e.g., you set `@ViewBag.Title` on your page
- Also you can use `@ViewData` and `@TempData` properties

###### Special Views
- There is `_ViewStart.cshtml` view in the root of the `Views` folder. It is loaded before each your view, so typically you use it to set default layout for all views, as shown below

```
@{
    Layout = "~/Views/Shared/_Layout.cshtml";
}
```

- You place all general views into `Views\Shared` folder. E.g., `Views\Shared\_Layout.cshtml` typically plays role of default layout page for all views (aka `master page`)
- You start all `.cshtml` files with underscore (`_`) which you want to prevent browsing of
- You place sensitive infromation into `_AppStart.cshtml` file into the following structure:

```
@{
    // Sensitive code here
}
```

###### Layout Page
- Layout page plays role of master page in ASP.NET MVC
- Typically, you set default layout page in `Views\_ViewStart.cshtml` file
- Typically, you call default layout page as `_Layout.cshtml` and place it into `Views\Shared` folder
- Typically, your default layout page looks like this one:

```html
<!DOCTYPE html>
<html>
<head>
    <title>@ViewBag.Title</title> <!-- Application title -->
    @Styles.Render("~/Content/css") <!-- Add CSS styles -->
    @Scripts.Render("~/bundles/modernizr") <!-- Add JS scripts -->
</head>
<body>
    <!-- Any HTML here -->
    <div class="body-content">
        @RenderBody() <!-- Add body of particular view here -->
    </div>
    <!-- Any HTML here -->
</body>
</html>
```

#### Razor View Engine
- Razor is a modern view engine for ASP.NET MVC
- Razor uses `@` (`at`) character to add some dynamic code into views
- There is `System.Web.Mvc.HtmlHelper` (`@Html`) class which has a lot of useful methods
 - `BeginForm`
 - `EndForm`
 - `TextArea`, `TextAreaFor`
 - `CheckBox`, `CheckBoxFor`
 - `DropDownList`, `DropDownListFor`
 - `Hidden`, etc.
 - `ActionLink` - to create a link
 - `Partial` - to insert partial view (partial views  stored in `Views\Shared` folder)
- Layou-related helpers
 - `@RenderSection` - to insed a section into layout page
 - `@section MySection { ... }` - to create a section
 - `@RenderBody` - to insert view's body into layout page

#### MVC Routing
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

#### MVC Filtering
TBD

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
