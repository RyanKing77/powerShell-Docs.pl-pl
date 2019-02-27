---
title: Przykłady dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844800"
---
# <a name="provider-samples"></a>Przykłady dostawców

Ta sekcja zawiera przykłady dostawców uzyskujących dostęp do bazy danych programu Microsoft Access. Te przykłady obejmują klasy dostawców, które pochodzą z klasy bazowej dostawcy.

## <a name="in-this-section"></a>W tej sekcji

Ta sekcja zawiera następujące tematy:

[Przykładowe AccessDBProviderSample01](./accessdbprovidersample01.md) ten przykład pokazuje sposób deklarowania klas dostawcy, który pochodzi bezpośrednio z [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy. Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.

[AccessDBProviderSample02](./accessdbprovidersample02.md) w tym przykładzie pokazano, jak zastąpić [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody umożliwiające obsługę wywołań `New-PSDrive` i `Remove-PSDrive` polecenia cmdlet. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy.

[AccessDBProviderSample03](./accessdbprovidersample03.md) w tym przykładzie pokazano, jak zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody umożliwiające obsługę wywołań `Get-Item` i `Set-Item` polecenia cmdlet. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.

[AccessDBProviderSample04](./accessdbprovidersample04.md) w tym przykładzie pokazano, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet. Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery. Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.

[AccessDBProviderSample05](./accessdbprovidersample05.md) w tym przykładzie pokazano, jak zastąpić obsługuje wywołań metod kontener `Move-Item` i `Join-Path` polecenia cmdlet. Metody te powinny być zrealizowane, gdy użytkownik chce przenieść elementy znajdujące się w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.

[AccessDBProviderSample06](./accessdbprovidersample06.md) w tym przykładzie pokazano, jak zastąpić treści metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet. Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych. Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy która implementuje [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.

## <a name="see-also"></a>Zobacz też

[Pisanie dostawcy programu PowerShell Windows](./writing-a-windows-powershell-provider.md)