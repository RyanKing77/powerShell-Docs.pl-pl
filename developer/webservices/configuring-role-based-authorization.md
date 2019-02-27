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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849329"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="7bfe7-102">Konfigurowanie autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="7bfe7-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="7bfe7-103">W tym temacie przedstawiono sposób konfigurowania zasad autoryzacji opartej na rolach, na przykład implementacji [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interfejsu opisanego w [Implementowanie niestandardowego Autoryzacja rozszerzenie OData IIS zarządzania](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="7bfe7-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="7bfe7-104">W tym przykładzie skonfigurujesz pliku XML, który jest używany przez przykładową aplikację zarządzania OData do zdefiniowania zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="7bfe7-105">Utworzysz dwie role i skojarzyć różne moduły programu Windows PowerShell, które zawierają przepływy pracy za pomocą tych ról.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="7bfe7-106">Schemat, który definiuje plik XML, który znajduje się na [schemat konfiguracji programu autoryzacji opartej na rolach](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="7bfe7-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="7bfe7-107">Modyfikowanie pliku RBacConfiguration.xml</span><span class="sxs-lookup"><span data-stu-id="7bfe7-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="7bfe7-108">Ten plik definiuje zasady autoryzacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="7bfe7-109">Role są definiowane za pomocą `Group` węzłów.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="7bfe7-110">A `Group` węzeł definiuje poleceń programu Windows PowerShell, które użytkownicy przypisani do tej grupy mogą uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="7bfe7-111">Użytkownicy są przypisane do grup przy użyciu `User` węzłów.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="7bfe7-112">W tych przykładach będzie Dodaj moduł do administratora `Group` węzła, a następnie dodanie użytkownika do każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="7bfe7-113">Dodanie modułu do węzła grupy</span><span class="sxs-lookup"><span data-stu-id="7bfe7-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="7bfe7-114">Utwórz plik o nazwie **RBacConfiguration.xml** w edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="7bfe7-115">Ten plik powinien zostać zapisany do katalogu głównego aplikacji dla usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="7bfe7-116">Wstaw następujący tekst w pliku.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="7bfe7-117">Ten plik zawiera dwa `Group` węzłów.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="7bfe7-118">Te reprezentują dwie role, które są używane w tym przykładzie `NonAdminGroup` i `AdminGroup` ról.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="7bfe7-119">Bezpośrednio po zamykającym `Cmdlets` tagu w pierwszym `Group` węzła, Dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="7bfe7-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="7bfe7-120">Dodanie użytkownika do węzła grupy</span><span class="sxs-lookup"><span data-stu-id="7bfe7-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="7bfe7-121">Otwórz **RBacConfiguration.xml** plik w edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="7bfe7-122">Ten plik znajduje się w folderze C:\\\inetpub\wwwroot\Modata Jeśli nazwa punktu końcowego przed rozpoczęciem instalacji nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="7bfe7-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="7bfe7-123">Bezpośrednio po tagu zamykającego w `Users` węzła, Dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="7bfe7-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="7bfe7-124">Bezpośrednio po dodaniu pliku XML w poprzednim kroku, należy dodać następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="7bfe7-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```