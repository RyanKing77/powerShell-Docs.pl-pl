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
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

W tym przykładzie pokazano, jak zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody umożliwiające obsługę wywołań `Get-Item` i `Set-Item` polecenia cmdlet. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.

## <a name="demonstrates"></a>Demonstracje

> [!IMPORTANT]
> Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy. Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy. Zobacz [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).

W tym przykładzie pokazano poniżej:

- Deklarowanie `CmdletProvider` atrybutu.

- Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.

- Zastępowanie [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodę, aby zmienić zachowanie `New-PSDrive` polecenia cmdlet, co pozwala na tworzenie nowych dysków. (Ten przykład pokazuje, jak dodać parametry dynamiczne `New-PSDrive` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody w celu obsługi usuwania istniejących dysków.

- Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodę, aby zmienić zachowanie `Get-Item` polecenia cmdlet, dzięki czemu użytkownik pobierania elementów z magazynu danych. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Item` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodę, aby zmienić zachowanie `Set-Item` polecenia cmdlet, umożliwiając użytkownikowi na aktualizowanie elementów w magazynie danych. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Item` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodę, aby zmienić zachowanie `Test-Path` polecenia cmdlet. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Test-Path` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodę pozwala ustalić, czy podana ścieżka jest prawidłowa.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak zastąpić metody potrzebne do pobierania i ustawiania elementów danych Microsoft Access podstawowej.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Projektowanie dostawcą Windows PowerShell](./provider-types.md)