# General
- ASP.NET building blocks
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

 - `MSBuild.exe` tool (usage via `.deploy.cmd` file). `VS2015->Project Properties->Publish->Connection->Web Deploy Package->OK` flow creates the following files in specified location:
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
Where `/T` - trial run, `/Y` - production run. This command deploys website into default location which is `%windir%\inetpub\wwwroot\%sitename%`

- Typical deployment tasks
 - Re-configure production version of `web.config` file
 - Specify files/folders that should be copied to production
 - Set the permissions to specified files/folders
 - Precompile the project, etc.

#### ASP.NET Configuration
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

