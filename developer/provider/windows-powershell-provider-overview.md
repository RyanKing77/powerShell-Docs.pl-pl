---
title: Przegląd dostawcy programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080915"
---
# <a name="windows-powershell-provider-overview"></a>Omówienie dostawcy programu Windows PowerShell

Dostawca programu Windows PowerShell umożliwia dowolnego magazynu danych ujawnianie takich jak system plików, tak jakby był zainstalowany dysk. Na przykład, wbudowanego dostawcy rejestru pozwala przechodzić w rejestrze, jak należy przejść `c` dysku komputera. Dostawcę można też przesłonić `Item` polecenia cmdlet (na przykład `Get-Item`, `Set-Item`itd) tak, aby dane w magazynie danych może być traktowana tak, takich jak pliki i katalogi są traktowane podczas przechodzenia do systemu plików. Aby uzyskać więcej informacji o dostawcy i dyski i dostawców wbudowanych w programie Windows PowerShell, zobacz [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Dostawcy i dyski

Dostawca definiuje logiki, która umożliwia dostęp, przejdź i edytować magazynu danych, gdy dysk określa punktem wejścia określonym do magazynu danych (lub część magazynu danych), który jest typu zdefiniowanego przez dostawcę. Na przykład dostawca rejestru umożliwia dostęp do gałęzi i kluczy rejestru, a dyski HKLM a HKCU określ odpowiedni gałęzi w rejestrze. Dyski HKLM a HKCU korzystają z dostawcy rejestru.

Podczas pisania dostawcę, można określić domyślnego stacje dysków, które są tworzone automatycznie, gdy dostawca jest dostępny. Możesz również zdefiniować metodę, aby utworzyć nowe dyski, które używają tego dostawcy.

## <a name="type-of-providers"></a>Typ dostawcy

Istnieją różne typy dostawców, z których każdy z nich zapewnia inny poziom funkcjonalności. Dostawca jest implementowany jako klasa, która pochodzi z jednego z elementów podrzędnych elementu [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) klasy. Aby uzyskać informacje o różnych typach dostawców, zobacz [typy dostawców](./provider-types.md).

## <a name="provider-cmdlets"></a>Polecenia cmdlet dostawców

Dostawcy mogą implementować metody, które odpowiadają poleceń cmdlet, tworzenie niestandardowych zachowań dla tych poleceń cmdlet, gdy są używane w na dysku dla tego dostawcy. W zależności od typu dostawcy różne zestawy poleceń cmdlet są dostępne. Aby uzyskać pełną listę dostępnych do dostosowywania w dostawcy poleceń cmdlet, zobacz [polecenia cmdlet dostawcy](./provider-cmdlets.md).

## <a name="provider-paths"></a>Dostawca ścieżek

Użytkownicy przechodzą dostawcy dysków, na przykład systemy plików. W związku z tym spełniają oczekiwane składnia ścieżki odpowiadające im ścieżki używany w Nawigacja w systemie plików. Gdy użytkownik uruchamia polecenie cmdlet dostawcy, ich Określ ścieżkę do elementu, który ma być uzyskiwany dostęp. Ścieżka, który jest określony, mogą być interpretowane na kilka sposobów. Dostawca powinien obsługiwać co najmniej jeden z następujących typów ścieżki.

### <a name="drive-qualified-paths"></a>Ścieżki kwalifikowana dysku

Ścieżki kwalifikowana dysku jest kombinacją nazwy elementu, kontener i podkontenery, w których znajduje się element oraz dysk programu Windows PowerShell, za pomocą którego element jest dostępny. (Dyski są definiowane przez dostawcę, który służy do uzyskania dostępu do magazynu danych. Ta ścieżka zaczyna się od nazwy dysku z dwukropkiem (:). Na przykład: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Kwalifikowana przez dostawcę ścieżek

Aby umożliwić aparatu programu Windows PowerShell do inicjowania i uninitialize dostawcy, dostawca musi obsługiwać ścieżką kwalifikowana przez dostawcę. Na przykład użytkownik może zainicjować i uninitialize dostawcy systemu plików, ponieważ określa ona następującą ścieżkę kwalifikowana dostawcy: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Dostawca bezpośrednio ścieżki

Aby zezwolić na zdalny dostęp do dostawcy programu Windows PowerShell, jego powinien obsługiwać ścieżki dostawcy bezpośrednio przekazać bezpośrednio do dostawcy programu Windows PowerShell dla bieżącej lokalizacji. Na przykład, można użyć dostawcy programu Windows PowerShell rejestru `\\server\regkeypath` jako ścieżka dostawcy bezpośrednio.

### <a name="provider-internal-paths"></a>Ścieżki wewnętrznego dostawcy

Aby zezwolić na dostęp do danych za pomocą interfejsów programowania aplikacji (API) — Windows PowerShell polecenia cmdlet dostawcy, Twój dostawca programu Windows PowerShell powinien obsługiwać wewnętrzna dostawcy ścieżki. Ta ścieżka jest oznaczany po "::" w ścieżce kwalifikowana przez dostawcę. Na przykład ścieżka wewnętrzna dostawcy dla dostawcy programu Windows PowerShell system plików jest `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Zastępowanie parametrów polecenia cmdlet

Zachowanie niektórych poleceń cmdlet specyficznych dla dostawcy może być zastąpiona przez dostawcę. Aby uzyskać listę parametrów, które mogą zostać zastąpione i jak je zastąpić w klasie dostawcy, zobacz [parametry polecenia cmdlet dostawcy](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parametry dynamiczne

Dostawców można zdefiniować parametry dynamiczne, które są dodawane do polecenia cmdlet dostawcy, gdy użytkownik określi określoną wartość dla jednego statycznego parametrów polecenia cmdlet. Dostawca robi to poprzez implementację co najmniej jedną metodę parametrów dynamicznych. Aby uzyskać listę parametrów polecenia cmdlet, które mogą służyć do dodawania parametrów dynamicznych i metody używane do ich wykonania, zobacz [parametrów dynamicznych polecenia cmdlet dostawcy](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Możliwości dostawcy

[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenie definiuje kilka funkcji obsługujących dostawców. Obejmują one możliwość Użyj symboli wieloznacznych, filtrowania elementów i obsługi transakcji. Aby określić możliwości dla dostawcy, Dodaj listę wartości [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia, w połączeniu z logicznych `OR` operacji jako [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) właściwość (drugi parametr atrybutu) [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybutu dla klasy dostawcy. Na przykład następujący atrybut określa, że dostawca obsługuje [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) i [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) możliwości.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Pomocy dotyczącej poleceń cmdlet dostawcy

Podczas zapisywania dostawcy, można zaimplementować własną Pomoc dla polecenia cmdlet dostawcy, która jest obsługiwana. W tym pojedynczym temacie pomocy dla każdego polecenia cmdlet dostawcy lub wielu wersji tematu pomocy w sytuacjach, gdy polecenia cmdlet dostawcy działa inaczej w zależności od użycia parametrów dynamicznych. Aby zapewnić obsługę pomoc dotyczącą polecenia cmdlet dostawcy, Twój dostawca musi implementować [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interfejsu.

Wywołania aparatu programu Windows PowerShell [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) metodę, aby wyświetlić tematu pomocy dla poleceń cmdlet dostawcy. Aparat zawiera nazwę polecenia cmdlet, które użytkownik określił podczas uruchamiania `Get-Help` polecenia cmdlet i ścieżkę bieżącego użytkownika. Bieżąca ścieżka jest wymagany, jeśli Twój dostawca implementuje różne wersje tego samego polecenia cmdlet dostawcy, na różnych dyskach. Metoda musi zwracać ciąg, który zawiera kod XML dla polecenia cmdlet pomocy.

Zawartość pliku pomocy są zapisywane przy użyciu PSMAML XML. Jest to ten sam schemat XML, używany do zapisywania zawartości pomocy dla autonomicznych poleceń cmdlet. Dodaj zawartość niestandardowe polecenia cmdlet ułatwiają plik pomocy dla dostawcy w obszarze `CmdletHelpPaths` elementu. W poniższym przykładzie przedstawiono `command` element dla polecenia cmdlet jednego dostawcy i pokazuje, jak Podaj nazwę polecenia cmdlet dostawcy, Twój dostawca. Obsługuje

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Zobacz też

[Windows PowerShell dostawcy funkcji](./provider-types.md)

[Polecenia cmdlet dostawcy](./provider-cmdlets.md)

[Pisanie dostawcy programu PowerShell Windows](./writing-a-windows-powershell-provider.md)