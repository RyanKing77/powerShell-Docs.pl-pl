---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847299"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="1f991-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="1f991-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="1f991-103">W tym przykładzie pokazano, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f991-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="1f991-104">Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery.</span><span class="sxs-lookup"><span data-stu-id="1f991-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="1f991-105">Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1f991-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="1f991-106">Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="1f991-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1f991-107">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="1f991-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f991-108">Klasa dostawcy najprawdopodobniej będzie dziedziczyć [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="1f991-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="1f991-109">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="1f991-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="1f991-110">Deklarowanie `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1f991-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="1f991-111">Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="1f991-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="1f991-112">Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodę, aby zmienić zachowanie `Copy-Item` polecenia cmdlet, który umożliwia użytkownikowi kopiowanie elementów z jednej lokalizacji do innej.</span><span class="sxs-lookup"><span data-stu-id="1f991-112">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="1f991-113">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Copy-Item` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="1f991-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="1f991-114">Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodę, aby zmienić zachowanie polecenia cmdlet Get-ChildItems, który umożliwia użytkownikom pobieranie elementów podrzędnych elementu nadrzędnego .</span><span class="sxs-lookup"><span data-stu-id="1f991-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="1f991-115">(Ten przykład pokazuje, jak dodawanie parametrów dynamicznych do polecenia cmdlet Get-ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="1f991-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="1f991-116">Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodę, aby zmienić zachowanie polecenia cmdlet Get-ChildItems podczas `Name` określono parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f991-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="1f991-117">Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodę, aby zmienić zachowanie `New-Item` polecenia cmdlet, co pozwala użytkownikowi na dodawanie elementów do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="1f991-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="1f991-118">(Ten przykład pokazuje, jak dodać parametry dynamiczne `New-Item` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="1f991-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="1f991-119">Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metodę, aby zmienić zachowanie `Remove-Item` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f991-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="1f991-120">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Remove-Item` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="1f991-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="1f991-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f991-121">Example</span></span>

<span data-ttu-id="1f991-122">W tym przykładzie pokazano, jak zastąpić metody potrzebne, aby skopiować, tworzenie i usuwanie elementów, a także metody pobierania podrzędnych elementów elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1f991-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="1f991-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f991-123">See Also</span></span>

[<span data-ttu-id="1f991-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="1f991-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="1f991-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="1f991-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="1f991-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="1f991-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="1f991-127">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f991-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)