---
title: Konfigurowanie autoryzacji opartej na rolach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080683"
---
# <a name="configuring-role-based-authorization"></a>Konfigurowanie autoryzacji opartej na rolach

W tym temacie przedstawiono sposób konfigurowania zasad autoryzacji opartej na rolach, na przykład implementacji [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interfejsu opisanego w [Implementowanie niestandardowego Autoryzacja rozszerzenie OData IIS zarządzania](./implementing-custom-authorization-for-a-management-odata-web-service.md).

W tym przykładzie skonfigurujesz pliku XML, który jest używany przez przykładową aplikację zarządzania OData do zdefiniowania zasad autoryzacji. Utworzysz dwie role i skojarzyć różne moduły programu Windows PowerShell, które zawierają przepływy pracy za pomocą tych ról. Schemat, który definiuje plik XML, który znajduje się na [schemat konfiguracji programu autoryzacji opartej na rolach](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modyfikowanie pliku RBacConfiguration.xml

Ten plik definiuje zasady autoryzacji dla aplikacji. Role są definiowane za pomocą `Group` węzłów. A `Group` węzeł definiuje poleceń programu Windows PowerShell, które użytkownicy przypisani do tej grupy mogą uruchamiać. Użytkownicy są przypisane do grup przy użyciu `User` węzłów.

W tych przykładach będzie Dodaj moduł do administratora `Group` węzła, a następnie dodanie użytkownika do każdej grupy.

#### <a name="adding-a-module-to-a-group-node"></a>Dodanie modułu do węzła grupy

1. Utwórz plik o nazwie **RBacConfiguration.xml** w edytorze tekstów. Ten plik powinien zostać zapisany do katalogu głównego aplikacji dla usługi sieci web. Wstaw następujący tekst w pliku.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. Ten plik zawiera dwa `Group` węzłów. Te reprezentują dwie role, które są używane w tym przykładzie `NonAdminGroup` i `AdminGroup` ról.

   Bezpośrednio po zamykającym `Cmdlets` tagu w pierwszym `Group` węzła, Dodaj następujący kod XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Dodanie użytkownika do węzła grupy

1. Otwórz **RBacConfiguration.xml** plik w edytorze tekstów. Ten plik znajduje się w folderze C:\\\inetpub\wwwroot\Modata Jeśli nazwa punktu końcowego przed rozpoczęciem instalacji nie została zmieniona.

2. Bezpośrednio po tagu zamykającego w `Users` węzła, Dodaj następujący kod XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Bezpośrednio po dodaniu pliku XML w poprzednim kroku, należy dodać następujący kod XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```