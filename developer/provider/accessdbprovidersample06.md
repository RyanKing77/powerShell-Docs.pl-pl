---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 59832ed8a4fad3b07a171946bff28fb3e1dbe442
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845871"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

W tym przykładzie pokazano, jak zastąpić treści metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet. Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy która implementuje [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.

## <a name="demonstrates"></a>Przedstawiono

> [!IMPORTANT]
> Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy. Zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy. Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.
>
> Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).

W tym przykładzie pokazano poniżej:

- Deklarowanie `CmdletProvider` atrybutu.

- Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy i która deklaruje [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.

- Zastępowanie [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodę, aby zmienić zachowanie `Clear-Content` polecenia cmdlet, dzięki czemu użytkownik próbę usunięcia zawartości z elementu. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Clear-Content` polecenia cmdlet.)

- Zastępowanie [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodę, aby zmienić zachowanie `Get-Content` polecenia cmdlet, co pozwala na pobieranie zawartości elementu. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Content` polecenia cmdlet.).

- Zastępowanie [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) metodę, aby zmienić zachowanie `Set-Content` polecenia cmdlet, umożliwiając użytkownikowi na aktualizowanie zawartości elementu. (Ten przykład pokazuje, jak dodać parametry dynamiczne `Set-Content` polecenia cmdlet.)

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak zastąpić metody potrzebne do wyczyszczenia, pobieranie i ustawianie zawartość elementów danych Microsoft Access bazy.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Projektowanie dostawcą Windows PowerShell](./provider-types.md)