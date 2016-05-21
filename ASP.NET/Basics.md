# General
- ASP.NET building blocks
 - Web Forms (aspx)
 - MVC  (aspx, razor/.cshtml)
 - Web Pages (razor/.cshtml)
 - Single Page Application (WebAPI, js/ajax)
 
#### ASP.NET configuration
- %windir%\Microsoft.NET\Framework64\[version]\config\machine.config – global configuration
- site_root\web.config – site-specific configuration
- site_root\Views\web.config - Views-specific configuration (MVC)
- Configuration file skeleton

![ASP.NET configuration file skeleton](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/asp.net1.png)

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

![ASP.NET membership configuration](https://github.com/kakarotto67/KnowledgeBank/blob/master/ASP.NET/asp.net2.png)

- `<compilation .../>` – to specify which compilers to use and which assemblies to include into the package
```xml
<complication debug="false" defaultLanguage="CS">
 <compilers> ... </compilers>
</compilation>
```
- `<sessionState mode="..." />` – to enable session
 - `mode` values: **SQLServer** (in database), **InProc** (in memory of web server), **StateServer** (in separate process), **Custom** (custom provider), **Off** (session state is disabled)



