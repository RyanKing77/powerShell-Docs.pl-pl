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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057624"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

W tym przykładzie pokazano, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet. Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery. Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.

## <a name="demonstrates"></a>Przedstawiono

> [!IMPORTANT]
> Klasa dostawcy najprawdopodobniej będzie dziedziczyć [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

W tym przykładzie pokazano poniżej:

- Deklarowanie `CmdletProvider` atrybutu.

- Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.

- Zastępowanie [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodę, aby zmienić zachowanie `Copy-Item` polecenia cmdlet, który umożliwia użytkownikowi kopiowanie elementów z jednej lokalizacji do innej. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Copy-Item` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodę, aby zmienić zachowanie polecenia cmdlet Get-ChildItems, który umożliwia użytkownikom pobieranie elementów podrzędnych elementu nadrzędnego . (Ten przykład pokazuje, jak dodawanie parametrów dynamicznych do polecenia cmdlet Get-ChildItems.)

- Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodę, aby zmienić zachowanie polecenia cmdlet Get-ChildItems podczas `Name` określono parametr polecenia cmdlet.

- Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodę, aby zmienić zachowanie `New-Item` polecenia cmdlet, co pozwala użytkownikowi na dodawanie elementów do magazynu danych. (Ten przykład pokazuje, jak dodać parametry dynamiczne `New-Item` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metodę, aby zmienić zachowanie `Remove-Item` polecenia cmdlet. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Remove-Item` polecenia cmdlet.)

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak zastąpić metody potrzebne, aby skopiować, tworzenie i usuwanie elementów, a także metody pobierania podrzędnych elementów elementu nadrzędnego.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Projektowanie dostawcą Windows PowerShell](./provider-types.md)