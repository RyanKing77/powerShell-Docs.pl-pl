---
title: Tworzenie pliku Web.config usługi sieci web OData zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847313"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Tworzenie pliku Web.config na potrzeby internetowej usługi OData zarządzania

Przed wdrożeniem usługi sieci web OData zarządzania, należy skonfigurować pliku web.config, aby wskazywały pliki schematów XML i bibliotek DLL, które implementują [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) i [ System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfejsów.

## <a name="sample-config-file"></a>Przykładowy plik konfiguracji

Oto przykład pliku web.config dla usługi sieci web wygląda następująco.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Zobacz też

[Implementowanie niestandardowego autoryzacji dla usługi sieci web OData zarządzania](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementowanie SessionConfiguration usługi sieci web OData zarządzania](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Tworzenie pliku schematu pliku MOF usługi sieci web OData zarządzania](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Tworzenie pliku schematu XML dla usługi sieci web OData zarządzania](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Tworzenie usługi sieci Web OData zarządzania](./creating-a-management-odata-web-service.md)