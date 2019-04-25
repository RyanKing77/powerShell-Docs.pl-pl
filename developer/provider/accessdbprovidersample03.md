---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081074"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="f106b-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="f106b-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="f106b-103">W tym przykładzie pokazano, jak zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody umożliwiające obsługę wywołań `Get-Item` i `Set-Item` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f106b-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="f106b-104">Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="f106b-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f106b-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="f106b-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f106b-106">Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:</span><span class="sxs-lookup"><span data-stu-id="f106b-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="f106b-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="f106b-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="f106b-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="f106b-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="f106b-109">Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="f106b-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="f106b-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="f106b-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="f106b-111">Zobacz [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="f106b-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="f106b-112">Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="f106b-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="f106b-113">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="f106b-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f106b-114">Deklarowanie `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f106b-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f106b-115">Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="f106b-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="f106b-116">Zastępowanie [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodę, aby zmienić zachowanie `New-PSDrive` polecenia cmdlet, co pozwala na tworzenie nowych dysków.</span><span class="sxs-lookup"><span data-stu-id="f106b-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="f106b-117">(Ten przykład pokazuje, jak dodać parametry dynamiczne `New-PSDrive` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f106b-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="f106b-118">Zastępowanie [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody w celu obsługi usuwania istniejących dysków.</span><span class="sxs-lookup"><span data-stu-id="f106b-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="f106b-119">Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodę, aby zmienić zachowanie `Get-Item` polecenia cmdlet, dzięki czemu użytkownik pobierania elementów z magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="f106b-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="f106b-120">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Item` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f106b-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="f106b-121">Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodę, aby zmienić zachowanie `Set-Item` polecenia cmdlet, umożliwiając użytkownikowi na aktualizowanie elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="f106b-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="f106b-122">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Item` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f106b-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="f106b-123">Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodę, aby zmienić zachowanie `Test-Path` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f106b-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="f106b-124">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Test-Path` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f106b-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="f106b-125">Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodę pozwala ustalić, czy podana ścieżka jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="f106b-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="f106b-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f106b-126">Example</span></span>

<span data-ttu-id="f106b-127">W tym przykładzie pokazano, jak zastąpić metody potrzebne do pobierania i ustawiania elementów danych Microsoft Access podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f106b-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="f106b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f106b-128">See Also</span></span>

[<span data-ttu-id="f106b-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f106b-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f106b-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f106b-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f106b-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f106b-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f106b-132">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f106b-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)