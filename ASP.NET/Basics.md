# ASP.NET General

#### Navigation
- [ASP.NET Building Blocks](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-building-blocks)
- [ASP.NET Configuration File](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-configuration-file)
- [ASP.NET Application Deployment](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-application-deployment)
- [ASP.NET Directives](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-directives)
- [ASP.NET Controls](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-controls)
- [ASP.NET Intrinsic Objects](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-intrinsic-objects)
- [ASP.NET Common](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-common)
- [HTTP Handler (HttpHandler class)](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#http-handler-httphandler-class)
- [HTTP Module (HttpModule class)](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#http-module-httpmodule-class)
- [Master Pages, Themes and Skins](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#master-pages-themes-and-skins)
- [Globalization in ASP.NET](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#globalization-in-aspnet)
- [Application (System.Web.HttpApplication) Class](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#application-systemwebhttpapplication-class)
- [Page (System.Web.UI.Page) Class](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#page-systemwebuipage-class)
- [Control Adapters](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#control-adapters)
- [MobileCapabilities API (obsolete)](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#mobilecapabilities-api-obsolete)

#### ASP.NET Building Blocks
- Web Forms (aspx)
- MVC  (aspx, razor/.cshtml)
- Web Pages (razor/.cshtml)
- Single Page Application (WebAPI, js/ajax)

#### ASP.NET Configuration File
- %windir%\Microsoft.NET\Framework64\[version]\config\machine.config – global configuration
- site_root\web.config – site-specific configuration
- site_root\Views\web.config - Views-specific configuration (MVC)
- Configuration file skeleton is shown below:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
 <configSections> ... </configSections>
 <appSettings> ... </appSettings>
 <connectionStrings> ... </connectionStrings>
 
 <!-- Web configurations (legacy IIS) -->
 <system.web> ... </system.web>
 
 <!-- Web configurations (IIS 7+ ) -->
 <system.webServer> ... </system.webServer>
</configuration>
```
- `<authentication mode="..." />` - to configure authentication
 - `mode` values: **Windows**, **Forms**, **Passport**, **Federated**, **None**
- `<authorization .../>` - to configure authorization
```xml
<allow users="user1, user2" roles="role1, role2" verbs="GET, HEAD" />
<deny users="user1, user2" roles="role1, role2" verbs="POST, DEBUG" />
```
- `<identity .../>` - to run ASP.NET application under specified credentials (by default -  Network Service or ApplicationPoolIdentity, depending on IIS version)
```xml
<identity impersonate="true" username="admin" password="test1" />
```
- `<membership .../>` – enables users of the web site to create accounts (logins/passwords)
```xml
<membership defaultProvider="SqlMembershipProvider">
 <providers>
  <add name="SqlMembershipProvider"
       type="System.Web.Security.SqlMembershipProvider"
       connectionStringName="MyConnection1"
       applicationName="MyApp" />
 </providers>
</membership>
```
- `<compilation .../>` – to specify which compilers to use and which assemblies to include into the package
```xml
<complication debug="false" defaultLanguage="CS">
 <compilers> ... </compilers>
</compilation>
```
- `<sessionState mode="..." />` – to enable session
 - `mode` values: **SQLServer** (in database), **InProc** (in memory of web server), **StateServer** (in separate process), **Custom** (custom provider), **Off** (session state is disabled)

#### ASP.NET Application Deployment
- `XCopy` tool commands (direct copy of PE files)
- `VS->Build->Publish %MyWebApp%` option (for `Web Application` project type)
- `VS->Copy Website` option (for `Web Site` project type)
- `VS->ClickOnce Deployment` tool
 - Setup an account with a hosting company
 - Create publish profile
 - Start the deployment via `ClickOnce`
- `MSBuild.exe` tool (direct command):

```
msdeploy.exe -source:package="siteName.mvc.zip"
             -dest:auto,
                   computerName="https://...",
                   userName="...", password="...",
                   authType="Basic"
             -verb:sync
             -allowUntrusted
             -setParamFile:"...\...SetParameters.xml
```

 - `MSBuild.exe` tool (usage via `.deploy.cmd` file). `VS2015->Right-click on Project->Publish->Connection->Web Deploy Package->OK` flow creates the following files in specified location:
  - [siteName].deploy.cmd
  - [siteName].zip
  - [siteName].SetParameters.xml

 Then run the following command:
```
msdeploy.exe [siteName].deploy.cmd
             [/T | /Y]
             [/M:computerName]
             [/A:<basic> | <ntml>]
             [/U:userName]
             [/P:password]
```
Where `/T` - trial run, `/Y` - production run. This command deploys website into default location which is `%windir%\inetpub\wwwroot\%sitename%`.

- Typical deployment tasks
 - Re-configure production version of `web.config` file
 - Specify files/folders that should be copied to production
 - Set the permissions to specified files/folders
 - Precompile the project, etc.

#### ASP.NET Directives
- `<%@ Application ... %>` – to define application-specific data used for `global.asax`
- `<%@ Assembly ... %>` – to include specified assembly
- `<%@ Control ... %`> – to define user control
- `<%@ Implements ... %>` – to indicate that this page should implement specified interface
- `<%@ Import ... %>` – to import namespace
- `<%@ Master ... %>` – to define Master Page
- `<%@ OutputCache ... %>` – to control output caching
- `<%@ Page ... %>` – to define page-specific data and code behind for this page
- `<%@ Reference ... %>` – to include another page or control
- `<%@ Register ... %>` – to register a control on the page

#### ASP.NET Controls
###### Control Types
- HTML Controls – native HTML controls
- HTML Server Controls – native HTML controls with `runat="server"` option
- ASP.NET Server Controls – such as `<asp:Button />`
- ASP.NET Ajax Server Controls – such as `<asp:UpdatePanel />`
- ASP.NET User Controls – combination of existing controls located in `.ascx` file with `@Control` directive
- ASP.NET Custom Controls – custom implementation of `WebControl` class; can be included into a page using `@Register` directive

###### Standard Controls
- `Button`, `LinkButton`, `ImageButton`
- `Calendar`
- `CheckBox`, `CheckBoxList`
- `DropDownList`, `ListBox`
- `TextBox`, `Label`
- `Image`, `ImageMap`
- `RadioButton`, `RadioButtonList`
- `FileUpload`, `HiddenField`, `HyperLink`
- Other: `AdRotator`, `BulletedList`, `Localize`, `MultiView`, `PlaceHolder`, `Panel`, `Wizard`, etc.
- Typical controls’ properties: `ID`, `runat="server"`, `Width`, `Height`, `CssClass`, `Visible`, `BackColor`, `Tooltip`, etc.

###### Validation & Data Source Controls
- There are two types of validation:
 - Client Side (js)
 - Server Side (code behind)
- ASP.NET Validation Controls – used to validate other controls
 - `RequiredFieldValidator`, `RangeVaidator`, `ReqularExpressionValidator`, `CustomValidator`, `ValidationSummary`
 - Those controls use `ControlToValidate` property to specify the `ID` of the control they want to apply validation for
- ASP.NET Data Source Controls – allow binding to specified data source (file, database, xml)
 - Table-based Data Source Controls: `SqlDataSource`, `ObjectDataSource`, `LinqDataSource`, `AccessDataSource`
 - Hierarchical Data Source Controls: `XmlDataSource`, `SiteMapDataSource`
- Data-Bound Controls – the controls, which are bound to specified data source controls
 - `AdRotator` can be bound to table-based data sources via `AdvertisementFile` property
 - List controls (`ListBox`, `CheckBoxList`, `DropDownList`, etc.) and View controls (`GridView`, `FormView`, `DetailView`) can be bound to table-based data sources via `DataSourceID` property
 - `Menu`, `TreeView` and `SiteMapPath` controls can be bound to hierarchical data sources via `DataSourceID` property
- `Bind` and `Eval` methods – allow to bind data to controls
 - `Eval` – one-way binding, `Bind` – two-way binding
```asp
<asp:Label Text='<%# Eval("ProductID") %>' />
```

###### User Controls
- `<%@ Control ... %>` – define a user control in .ascx file (combination of any controls + code behind)
- `<%@ Register TagPrefix="MyControl1" Src="~/MyControl.ascx" %>` – register control on some page

###### Custom Controls
- Derive from `WebControl` class and implement its properties
- Override `RenderControl()` method
- Use `@Register` to add the control to some page

###### MS Ajax Controls
- `ScriptManager`
- `UpdatePanel`
- `UpdateProgress`
- `Timer`
- Ajax Control Toolkit

#### ASP.NET Intrinsic Objects
- `Page.Context` property of `System.Web.HttpContext` type
 - `Request` (`HttpRequest` type)
 - `Response` (`HttpResponse` type)
 - `Server` (`HttpServerUtility` type)
 - `Application` (`HttpApplicationState` type)
 - `Session` (`HttpSessionState` type)
 - `Profile` (`ProfileBase` type)
 - `Cache` (`Cache` type)
- `Control.ViewState` property of `System.Web.UI.StateBag` type
 - `ViewState` serializes and deserializes data into/from hidden fields (`__ViewState`, `base64` format)
 - `ViewState` uses `LosFormatter` and `ObjectStateFormatter` classes for serialization/deserialization
```cs
ViewState.TrackViewState(); // enable View State
ViewState["key1"] = 1; // add new key-value pair into View State
ViewState.IsItemDirty("key1"); // true, because key1 has been initialized after enabling of the View State
ViewState.SetItemDirty("key1", true); // mark item as dirty
ViewState.LoadViewState(); // load saved View State
```
- `ControlState` – stores internal control specific data (e.g., active control’s tab, etc.)

#### ASP.NET Common
###### File Types
- .ascx - user control
- .aspx - page
- .asmx - XML web service
- .ashx - generic handler

###### Storing of Data

| Object | Details |
| --- | --- |
| Application | Application-specific data; data is shared between all users; data is stored permanently |
| Session | User-specific data; data is available only during specific user session |
| Cookies | User-specific data; data is stored in user browser permanently until expiration date |
| Profile | User-specific data; data is stored in SQL Server; ASP.NET feature |
| Cache | Cached data; available to all users; stored on a Web Server |

###### Special Folders
- `Bin` folder – stores .dll files
- `App_Code` folder – stores sources, that will be automatically compiled

###### Error Handling
- Tracing	- allows to add specific information into tracing page
 - Enable tracing in web.config file - `<%@ Page ... Trace="true">`
 - Use `Trace.Write()` method to add extra information into tracing page
- Debugging
 - Enable debugging in web.config file - `<compilation debug="true" />`
- Custom error redirects
```xml
<customErrors defaultRedirects="errors\DefaultError.aspx" mode="On">
 <error statusCode="400" redirect="errors\ClientError.aspx" />
 <error statusCode="500" redirect="errors\ServerError.aspx" />
</customErrors>
```

###### ASP.NET IIS
- IIS/Application pool configuration
 - **Classic** pipeline mode (IIS 6): Client request -> IIS 6 -> aspnet_isapi.dll -> CLR
 - **Integrated** pipeline mode (IIS 7+): Client request -> IIS 7+ -> CLR

| IIS 6 | IIS 7+ |
| --- | --- |
| ISAPI filter (aspnet_filter.dll) | HttpModule |
| ISAPI extension (aspnet_isapi.dll) | HttpHandler |

###### ASP.NET Compiler
- `aspnet_compiler.exe` tool - allows to compile web application
 - **In-place compilation** (if site already deployed to production)
 - **Non-updatable full compilation**
 - **Updatable compilation** (it is possible to modify view files, css styles, etc.)

###### Environment Configuration
- Precompilation
- Recycling policies of pool
- Unexpected restarts
- Output caching
- Application warm-up and preloading

###### Monitoring
- Health Monitoring – monitor the status of the application, errors, etc.

```xml
<healthMonitoring enabled="true"> ... </healthMonitoring>
```

- Performance Monitoring
 - System Performance Counters (Performance Monitor window)
    - Requests disconnected, applications running, etc.
 - Application Performance Counters
    - Requests per second, number of hits from cache, etc.

###### Caching Options
- Output caching (rendered html pages caching)
- Data caching (caching the data from data source)
- Object caching (caching the objects on a page, such as data-bound controls)
- Class caching (caching the assembly in the server)
- Configuration caching (saving configuration information in the server memory)

###### Pass Values Between Pages
- GET method (from query string): `Request.QueryString["field1"];`
- POST method: `Request.Form.AllKeys[i];`
- Via `Session` object

###### Add JavaScript Dynamically
- To add JS into a page dynamically use `ClientScriptManager` class’ methods:
 - `RegisterClientScriptBlock()`
 - `RegisterClientScriptInclude()`
 - `RegisterStartupScript()`
 - `RegisterOnSubmitStatement()`

#### HTTP Handler (`HttpHandler` class)
- HTTP Handler - attached to specified requests of specified file extensions
- To create
 - Derive from `IHttpHandler` interface
 - Implement `ProcessRequest(HttpContext context)` method of that interface
 - Add handler into configuration file (see below)
- Usage: RSS feeds, image server, image water marks, etc.

```xml
<httpHandlers>
 <!-- This handler will be attached to each GET request of file with extension .jpg, .png or .gif -->
 <add verb="GET" path="*.jpg, *.png, *.gif" type="ImageHandler, MyApp.Common.Handlers" />
</httpHandlers>
```

###### Generic Handler
- Generic Handler should be called explicitly
- To create
 - Create .ashx file with `<%@ WebHandler ... >` header
 - Develop code behind similarly to common handlers
- Usage: Dynamic image generation (`src="Icon.ashx?username=roman"`), to return REST-base XML as JSON data, custom HTML, etc.

#### HTTP Module (`HttpModule` class)
- HTTP Module – attached to some specified event of each request
- To create
 - Derive from `IHttpModule` interface
 - Implement `Init()` method of that interface, then attach handler to event you want to change behavior of
 - Implement event handler

```cs
// Init() method
void Init(HttpApplication app)
{
    app.BeginRequest += OnBeginRequest;
}

// Custom event handler
void OnBeginRequest(...)
{
    // custom code
}
```

```xml
<httpModules>
 <!-- Registration of the module -->
 <add name="AuthModule" type="MyApp.Common.Modules.AuthModule" />
</httpModules>
```

- Usage: Security (e.g., authenticate user on `AuthenticateRequest` event), statistics, logging, custom handlers, footers, URL routing (on `BeginRequest` event), etc.

#### Master Pages, Themes and Skins
###### Master Pages
- Creation
 - Create a file with `<%@ Master ... >` header
 - Add HTML skeleton into it (`<html>`, `<head>`, etc.)
 - Add `<asp:ContentPlaceHolder ID="MainBlock" runat="server" >` into all places, where you need to insert specific content
- Usage
 - Place `<%@ Page MasterPageFile="Common.Master">` header into some page to use the Master Page
 - Use `<asp:Content ContentPlaceHolderId="MainBlock" runat="server"> ... </asp:Content>` to specify the data which should be inserted instead of corresponding `ContentPlaceHolder` control from Master Page

###### Skins
- Skin file (.skin) contains styles for controls
- Default style – for all controls
- Named style – applied to a control via `SkinID`

###### Themes
- `App_Themes` folder contains all themes. Each theme has its separate folder
 - BlueTheme
    - BlueTheme.css
    - Controls.skin
 - PinkTheme
    - PinkTheme.css
    - PinkTheme.skin
- Theme can be applied to the website via `<pages />` element in `web.config` file
- `<pages theme="BlueTheme" />` – own controls’ styles will be overridden
- `<pages stylesheettheme="BlueTheme"/>` – own controls’ styles will no be overridden

#### Globalization in ASP.NET
- Globalization - the code is separated from data, so it is possible to localize the application
- Localizability - how easy is it to localize the application
- Localization - the process of translation

###### Issues
- Language issues
- String-related issues
- UI-related issues
- Formatting issues

###### Accessibility
- Flexbile input & output
- Flexible UI
- Simplicity & intuitiveness
- Keyboard navigation support
- Less use of CSS
- Image use, standard fonts, controls, etc.

###### Helper Classes in .NET/C#
- `System.Globalization.CultureInfo` class
 - `CurrentCulture` property - the culture of the machine, time, currency and date format, etc.
 - `CurrentUICulture` property - language which is preferred by the application
- `System.Globalization.RegionInfo` class (properties: `CurrentRegion`, `CurrencySymbol`, etc.)
- `System.DateTime` class - date formatting options (examples for `en-US` culture)
 - `ToShortDateString` method (`M/d/yyyy` => `5/16/2016`)
 - `ToLongDateString` method (`dddd, MMMM dd, yyyy` => `Wednesday, May 16, 2016`)
 - `ToShortTimeString` method (`h:mm tt` => `3:02 AM`)
 - `ToLongTimeString` method (`h:mm:ss tt` => `3:02:15 AM`)

###### Localization Resources in ASP.NET
- Global Resources – stored in `App_GlobalResources` folder. Example – WebResources.resx, WebResources.de.resx, WebResources.fr.resx
- Local Resources – stored in `App_LocalResources` folder
 - Implicit resources (`<asp:Button ... meta:resourceKey = "button1" />`)
 - Explicit resources (`<asp:Button ... Text = "<%$ Resource:WebResources, button1 %>" />`)
 - Localize static text (`<asp:Localize ... />`)

#### Application (`System.Web.HttpApplication`) Class
- `System.Web.HttpApplication` class defines ASP.NET application
 - Properties
    - `Application` (`HttpApplicationState`)
    - `Context`, `Events`, `Modules`, `Request`, `Response`, `Server`, `Session`, etc.
 - Events (in global.asax)
    - `Application_Start`, `Application_End`
    - `Session_Start`, `Session_End`

###### Application Life Cycle
1. Request from Browser
2. ASP.NET AppDomain is created for the first time (`ApplicationManager` class)
3. Some top-level items are compiled (e.g., any stuff in `App_Code` folder). Such objects as `HttpContext`, `HttpRequest`, and `HttpResponse` are created
4. `HttpApplication` instance is created (it might be reused). `Global.asax` is initialized (if exists)
5. Request is processed by `HttpApplication`
 1. Validate request
 2. Perform URL mapping
 3. `HttpApplication` events (see below)
 4. Error event - occurs in case of any errors

###### Application Events
1. `BeginRequest` event
2. `AuthenticateRequest` event
3. `PostAuthenticateRequest` event
4. `AuthorizeRequest` event
5. `PostAuthorizeRequest` event
6. `ResolveRequestCache` event (if caching is enabled & caching page can be retrieved - go to event 21)
7. `PostResolveRequestCache` event
8. `MapRequestHandler` event
9. `PostMapRequestHandler` event
10. `AquireRequestState` event (`Application` and `Session` sates)
11. `PostAquireRequestState` event
12. `PreRequestHandlerExecute` event
13. `ExecuteRequestHandler` (execute `HttpHandler`, it’s time for **Page Life Cycle** events which are shown below)
14. `PostRequestHandlerExecute` event
15. `ReleaseRequestState` event
16. `PostReleaseRequestState` event
17. `UpdateRequestCache` event
18. `PostUpdateRequestCache` event
19. `LogRequest` event
20. `PostLogRequest` event
21. `EndRequest` event
22. `PreSendRequestHeader` event
23. `PreSendRequestContent` event

#### Page (`System.Web.UI.Page`) Class
- `System.Web.UI.Page` class defines main control, which processes a page
 - Properties
    - `Application` (`HttpApplicationState`)
    - `Cache`, `Context`, `EnableViewState`, `Events`
    - `Form`, `IsPostBack`, `IsCallback`, `IsCrossPagePostBack`
    - `Page`, `Response`, `Request`

###### Page Life Cycle Events
I. Setup Stage
 1. `PreInit` event
 2. `Init` event
 3. `InitComplete` event
 4. `ViewState` restoration and processing posted data
 5. `PreLoad` event
 6. `Load` event

II. Handling the PostBack Stage
 1. Detecting control state changes and executing the server-side postback event
 2. `LoadComplete` event

III. Page Finalization Stage
 1. `PreRender` event
 2. `PreRenderComplete` event
 3. `SaveStateComplete` event
 4. Generating the markup
 5. `Unload` event (free unmanaged resources, etc.)

#### Control Adapters
- Control adapter allows to render specific control differently in different browsers
- Standard control adapters for modern browsers are located in `%windir%\Microsoft.net\Framework\%version%\Config\Browsers\` folder
 - `blackberry.browser`
 - `chrome.browser`
 - `default.browser`
 - `firefox.browser`
 - `ie.browser`
 - `safari.browser`
 - `opera.browser`
 - `iphone.browser`, etc.
- To implement custom control adapter:
 - Inherit from `System.Web.UI.Adapters.ControlAdapter` class (it is `abstract`, also you can inherit from these classes - `WebControlAdapter`, `MenuAdapter`, `DataBoundControlAdapter`, `HierarchicalDataBoundControlAdapter`, etc.)
 - Implement `void Render(HtmlTextWriter writer)` method
 - Apply your custom adapter
    - Create `*.browser` file in `App_Browsers` directory
    - Add the following snippet into `web.config` file:

```xml
<browsers>
 <browser id="Default">
  <controlAdapter>
   <adapter controlType="System.Web.UI.WebControls.Menu"
            adapterType="MyAssembly.Adapters.MyMenuAdapter" />
  </controlAdapter>
 </browser>
</browsers>
```

#### `MobileCapabilities` API (`obsolete`)
- `System.Web.Mobile.MobileCapabilities` class - provides information about browser making the request
- To define new capability:
 - Create a method that returns `bool` and takes `MobileCapabilities` type as a parameter
 - Add `<filter>` element into `<deviceFilters>` section of `web.config` file
 - Use `((MobileCapabilities) Request.Browser).HasCapability("GpsEnabled", String.Empty);` method to check that new capability

```cs
public static bool IsGpsEnabled(MobileCapabilities mc, string someArg)
{
    // implementation details
}
```

```xml
<deviceFilters>
 <filter name="GpsEnabled"
         type="MyType, MyAssembly"
         method="IsGpsEnabled" />
</deviceFilters>
```

###### Built-in Capabilities of `MobileCapabilities` Class
- `CanInitiateVoiceCall`
- `CanSendMail`
- `HasBackButton`
- `IsMobileDevice`
- `MobileDeviceManufacturer`, `MobileDeviceModel`
- `ScreenCharactersHeight`, `ScreenCharactersWidth`
- `ScreenPixelsHeight`, `ScreenPixelsWidth`
- `SupportCss`, etc.
