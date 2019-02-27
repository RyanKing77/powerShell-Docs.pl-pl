---
title: Tworzenie dostawcy programu PowerShell Windows podstawowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850848"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Tworzenie podstawowego dostawcy programu Windows PowerShell

Ten temat jest punktem początkowym nauka tworzenia dostawcy środowiska Windows PowerShell. Podstawowy dostawca opisane w tym miejscu zawiera metody służące do uruchamiania i zatrzymywania dostawcy i mimo że ten dostawca nie zapewnia sposób dostępu do magazynu danych lub pobrać lub ustawić dane w magazynie danych, zapewnia podstawową funkcjonalność, która jest wymagana przez wszystkich dostawców.

Jak wspomniano wcześniej, Dostawca podstawowej opisane tutaj implementuje metody, uruchamianie i zatrzymywanie dostawcy. Środowisko wykonawcze programu Windows PowerShell wywołuje te metody do inicjowania i uninitialize dostawcy.

> [!NOTE]
> Przykładem tego dostawcy można znaleźć w pliku AccessDBSampleProvider01.cs dostarczonego przez środowisko Windows PowerShell.

Następujące sekcje w tym temacie:

- [Definiowanie klasy dostawcy programu PowerShell Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definiowanie informacji o stanie specyficzne dla dostawcy](#Defining-Provider-Specific-State-Information)

- [Inicjowanie dostawcy](#Initializing-the-Provider)

- [Rozpocznij parametrów dynamicznych](#Start-Dynamic-Parameters)

- [Cofanie inicjowania dostawcy](#Uninitializing-the-Provider)

- [Przykładowy kod](#Code-Sample)

- [Testowanie dostawcy programu Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definiowanie klasy dostawcy programu PowerShell Windows

Jest pierwszym krokiem w tworzeniu dostawcy środowiska Windows PowerShell do definiowania jego klasa platformy .NET. Ten podstawowy dostawca definiuje klasę o nazwie `AccessDBProvider` który pochodzi od klasy [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy bazowej.

Zaleca się umieszczenie swojej klasy dostawców w `Providers` przestrzeni nazw w Twojej przestrzeni nazw interfejsu API, na przykład: xxx. PowerShell.Providers. Ten dostawca używa `Microsoft.Samples.PowerShell.Provider` przestrzeni nazw, w którym są uruchomione wszystkie przykłady dostawcy środowiska Windows PowerShell.

> [!NOTE]
> Klasa dostawcy środowiska Windows PowerShell muszą być jawnie oznaczone jako publiczne. Klasy, które nie są oznaczone jako publiczne będą domyślnie wewnętrznego i nie zostanie znaleziony w czasie wykonywania programu Windows PowerShell.

Oto definicji klasy dla tego dostawcy podstawowe:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Bezpośrednio przed definicją klasy, należy zadeklarować [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybutu za pomocą składni [CmdletProvider()].

Można ustawić atrybutu słów kluczowych, aby dodatkowo zadeklarować klasy, jeśli to konieczne. Należy zauważyć, że [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybutów zadeklarowany w tym miejscu zawiera dwa parametry. Pierwszy parametr atrybutu określa domyślne — przyjazna nazwa dla dostawcy, który użytkownik może zmodyfikować później. Drugi parametr określa możliwości zdefiniowane w programie Windows PowerShell, które dostawca udostępnia do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Możliwe wartości dla funkcji dostawcy są definiowane przez [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. Ponieważ jest to podstawowy dostawca, obsługuje nie możliwości.

> [!NOTE]
> W pełni kwalifikowaną nazwę dostawcy programu Windows PowerShell zawiera nazwę zestawu i inne atrybuty określone przez środowisko Windows PowerShell po rejestracji dostawcy.

## <a name="defining-provider-specific-state-information"></a>Definiowanie informacji o stanie specyficzne dla dostawcy

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy bazowej oraz wszystkich klas pochodnych są traktowane jako bezstanowej ponieważ środowisko wykonawcze programu Windows PowerShell tworzy dostawcę wystąpień tylko zgodnie z potrzebami. W związku z tym, jeśli Twój dostawca wymaga pełnej kontroli i stanu konserwacji właściwe dla dostawcy danych, musi pochodzić z klasy [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) klasy. Pochodne klasy należy zdefiniować elementy członkowskie, niezbędne do obsługi stanu, tak aby dane specyficzne dla dostawcy będą dostępne, gdy środowisko wykonawcze programu Windows PowerShell wywołuje [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, aby zainicjować dostawcy.

Dostawca programu Windows PowerShell można również zarządzania stanem opartego na połączeniach. Aby uzyskać więcej informacji na temat obsługi stan połączenia zobacz [Tworzenie dostawcy dysku środowiska PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Inicjowanie dostawcy

Do zainicjowania dostawcy środowiska Windows PowerShell środowisko uruchomieniowe wywołuje [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metody po uruchomieniu programu Windows PowerShell. W większości przypadków użyć dostawcy Domyślna implementacja tej metody, która po prostu zwraca [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) obiekt, który opisuje Twój dostawca. Jednak w przypadku, w której chcesz dodać informacje o dodatkowych inicjowania, należy zaimplementować własny [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, która zwraca zmodyfikowaną wersję [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) obiektu, który jest przekazywany do dostawcy. Ogólnie rzecz biorąc, ta metoda powinna zwracać podane [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) obiekt przekazany do niej lub zmodyfikowane [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) obiekt zawiera informacje o innych inicjowania.

Ten podstawowy dostawca nie zastępuje tę metodę. Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Dostawca może zachować stan informacje specyficzne dla dostawcy, zgodnie z opisem w [definiujący właściwe dla dostawcy danych stanu](#Defining-Provider-Specific-State-Information). W takim przypadku należy zastąpić implementacji [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, aby zwrócić wystąpienia klasy pochodnej.

## <a name="start-dynamic-parameters"></a>Rozpocznij parametrów dynamicznych

Implementacja dostawcy [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metoda może wymagać dodatkowych parametrów. W takim przypadku należy zastąpić dostawcę [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) metody i obiekt, który ma właściwości i pola za pomocą analizy atrybuty podobne do zwrócenia Klasa polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu.

Ten podstawowy dostawca nie zastępuje tę metodę. Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Cofanie inicjowania dostawcy

Aby zwolnić zasoby, które korzysta z dostawcy programu Windows PowerShell, Twój dostawca powinny implementować własne [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) metody. Ta metoda jest wywoływana przez środowisko uruchomieniowe programu Windows PowerShell, aby uninitialize dostawcy z końcem sesji.

Ten podstawowy dostawca nie zastępuje tę metodę. Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testowanie dostawcy programu Windows PowerShell

Po zarejestrowaniu dostawcy środowiska Windows PowerShell przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia. Dla tego dostawcy podstawowe, należy uruchomić nowej powłoki i użyć `Get-PSProvider` polecenia cmdlet do pobierania listy dostawców i upewnij się, że dostawca AccessDb istnieje.

```powershell
Get-PSProvider
```

Zostaną wyświetlone następujące dane wyjściowe:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Zobacz też

[Tworzenie programu Windows PowerShell dostawców](./how-to-create-a-windows-powershell-provider.md)

[Projektowanie dostawcą Windows PowerShell](./designing-your-windows-powershell-provider.md)