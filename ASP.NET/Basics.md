# ASP.NET General

#### Navigation
- [ASP.NET Building Blocks](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-building-blocks)
- [ASP.NET Configuration File](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-configuration-file)
- [ASP.NET Application Deployment](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-application-deployment)
- [ASP.NET IIS & Compiler](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-iis--compiler)
- [ASP.NET Directives](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-directives)
- [ASP.NET Controls](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-controls)
- [ASP.NET Intrinsic Objects](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-intrinsic-objects)
- [ASP.NET Common Features](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/Basics.md#aspnet-common-features)

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

#### ASP.NET IIS & Compiler
- IIS/Application pool configuration
 - **Classic** pipeline mode (IIS 6): Client request -> IIS 6 -> aspnet_isapi.dll -> CLR
 - **Integrated** pipeline mode (IIS 7+): Client request -> IIS 7+ -> CLR

| IIS 6 | IIS 7+ |
| --- | --- |
| ISAPI filter (aspnet_filter.dll) | HttpModule |
| ISAPI extension (aspnet_isapi.dll) | HttpHandler |

- `aspnet_compiler.exe` tool - allows to compile web application
 - **In-place compilation** (if site already deployed to production)
 - **Non-updatable full compilation**
 - **Updatable compilation** (it is possible to modify view files, css styles, etc.)

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

#### ASP.NET Common Features
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
