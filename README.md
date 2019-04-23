CRMSvcUtilExtensions
====================

[![Build status](https://ci.appveyor.com/api/projects/status/ra3tvaflxufktox0/branch/master?svg=true)](https://ci.appveyor.com/project/bassetassen/crmsvcutilextensions/branch/master)

A library with extensions to CRMSvcUtil.

Copy crmsvcutilextensions.dll to the same folder as CrmSvcUtil. Call CrmSvcUtil with /codefilter parameter

Available code filters:
* EntityFilter - Generates the entities only listed in the filter.xml file
* VanillaFilter - Filters out any custom entity, attribute and relationships
* SolutionFilter - Generates only entities that is incuded in the solution that is specified

EntityFilter:
```
CrmSvcUtil.exe /codewriterfilter:"CRMSvcUtilExtensions.EntityFilter,CRMSvcUtilExtensions" /url:... /out:D:\Entities.cs /username:... /password:... /namespace:...
```

VanillaFilter:
```
CrmSvcUtil /codewriterfilter:"CRMSvcUtilExtensions.VanillaFilter,CRMSvcUtilExtensions"
/url:... /out:D:\Entities.cs /username:... /password:... /namespace:...
```

SolutionFilter:
A valid Solution argument must be unique a comma-separated list of unique solution names.
```
CrmSvcUtil /codewriterfilter:"CRMSvcUtilExtensions.SolutionFilter,CRMSvcUtilExtensions"
/solution:uniquename /url:... /out:D:\Entities.cs /username:... /password:... /namespace:...
```

To use username, password, and connection string parameters:
```
CrmSvcUtil /codewriterfilter:"CRMSvcUtilExtensions.SolutionFilter,CRMSvcUtilExtensions"
/solution:uniquename /connectionstring:"AuthType=Office365;Username=jsmith@contoso.onmicrosoft.com; Password=passcode;Url=https://contoso.crm.dynamics.com" /out:D:\Entities.cs /namespace:...
```

If you are running the CodeGeneration tool behind a proxy, edit CrmSvcUtil.exe.config and add the following block within the configuration block:
```
<system.net>
<defaultProxy useDefaultCredentials="true"/>
</system.net>
```
