---
title: Zdecydowanie zalecane wytyczne dotyczące projektowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067369"
---
# <a name="strongly-encouraged-development-guidelines"></a>Wskazówki dotyczące projektowania — użycie zdecydowanie zalecane

W tej sekcji opisano wskazówki, które należy wykonać podczas pisania poleceń cmdlet. Są one podzielone na wytyczne do projektowania, poleceń cmdlet i zalecenia dotyczące pisania kodu polecenie cmdlet. Może się okazać, że te wytyczne nie są odpowiednie dla każdego scenariusza. Jednak jeśli są one stosowane, a nie przestrzegać następujących wytycznych, że użytkownicy mają pogorszenie środowiska pracy podczas korzystania z poleceń cmdlet.

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

- [Użyj określonego rzeczownik nazwę polecenia Cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Użyj pisanymi wielkimi literami dla nazwy poleceń Cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Wytyczne dotyczące projektowania parametru (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Przesyłanie opinii do użytkownika (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Utwórz plik pomocy dotyczącej poleceń Cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Wytyczne dotyczące kodu

- [Kodowanie parametrów (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Obsługuje dobrze zdefiniowane potoku danych wejściowych (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Zapisz rekordy w jednym potoku (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Wprowadź polecenia cmdlet bez uwzględniania wielkości liter i zachowywanie (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Należy przestrzegać następujących wytycznych podczas projektowania poleceń cmdlet, aby zapewnić spójne środowisko użytkownika między przy użyciu poleceń cmdlet i inne polecenia cmdlet. Po znalezieniu wskazówek dotyczących projektu, która ma zastosowanie do konkretnej sytuacji, pamiętaj przyjrzeć się wskazówki dotyczące kodu podobne wskazówki dotyczące.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Użyj określonego rzeczownik nazwę polecenia Cmdlet (SD01)

Rzeczowniki używane w nazwach polecenia cmdlet muszą być bardzo szczegółowych, dzięki czemu użytkownik może odnajdować poleceń cmdlet programu. Prefiks rzeczowniki ogólnych, takich jak "server" z wersją skróconą nazwę produktu. Na przykład jeśli rzeczownik odwołuje się do serwera, na którym jest uruchomione wystąpienia programu Microsoft SQL Server, należy użyć rzeczownik, takie jak "SQLServer". Kombinacja określonych rzeczowniki i krótką listę zatwierdzonych czasowników umożliwiają użytkownikowi szybkie odnajdywanie i przewidywać funkcji unikając duplikatów między nazwy poleceń cmdlet.

Aby ulepszyć środowisko użytkownika, rzeczownik, wybranego przez użytkownika dla nazwy polecenia cmdlet powinny być pojedynczej. Na przykład użyj nazwy `Get-Process` zamiast **procesy Get**. Najlepiej wykonaj tę zasadę na potrzeby wszystkie nazwy poleceń cmdlet, nawet wtedy, gdy polecenie cmdlet prawdopodobnie może operować na więcej niż jeden element.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Użyj pisanymi wielkimi literami dla nazwy poleceń Cmdlet (SD02)

Użyj pisanymi wielkimi literami dla nazw parametrów. Innymi słowy wielką literą zlecenia i wszystkich terminów używanych w rzeczownikiem. Na przykład "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Wytyczne dotyczące projektowania parametru (SD03)

Polecenie cmdlet wymaga parametrów, które odbierać dane, na którym musi działać, a parametry wskazujące informacje, które służy do określania właściwości operacji. Na przykład, Niewykluczone, polecenia cmdlet `Name` może mieć parametr, który odbiera dane z potoku i polecenia cmdlet `Force` parametru, aby wskazać, że polecenia cmdlet aktualizację można wymusić przeprowadzić jego działania. Nie ma żadnego limitu liczby parametrów, które można zdefiniować polecenia cmdlet.

#### <a name="use-standard-parameter-names"></a>Użyj nazwy parametrów standardowe

Twojego polecenia cmdlet należy używać nazwy parametrów standardowe, dzięki czemu użytkownik może szybko określić, co oznacza określonego parametru. Jeśli wymagana jest bardziej szczegółową nazwę, użyj nazwy parametru standardowa, a następnie określ bardziej szczegółową nazwę jako alias. Na przykład `Get-Service` polecenie cmdlet ma parametr, który ma pod nazwą (`Name`) i dokładniejsze alias (`ServiceName`). Oba warianty pojęć może służyć do określenia parametru.

Aby uzyskać więcej informacji na temat nazw parametrów i ich typy danych, zobacz [Nazwa parametru polecenia Cmdlet i wskazówki dotyczące funkcji](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Użyj nazwy parametrów w liczbie pojedynczej

Unikaj korzystania z nazwy w liczbie mnogiej dla parametrów, którego wartością jest pojedynczy element. To zawiera parametry, które przyjmują tablic lub wyświetla ich listę, ponieważ użytkownik może dostarczyć tablicy lub listy za pomocą tylko jednego elementu.

Nazwy parametrów w liczbie mnogiej powinna służyć tylko w przypadkach, gdy wartość parametru jest zawsze wartość wieloelementowych. W takich przypadkach polecenia cmdlet należy sprawdzić, że podano wiele elementów, a polecenie cmdlet powinna być wyświetlana ostrzeżenia dla użytkownika, jeśli nie podano wiele elementów.

#### <a name="use-pascal-case-for-parameter-names"></a>Użyj pisanymi wielkimi literami dla nazw parametrów

Użyj pisanymi wielkimi literami dla nazw parametrów. Innymi słowy wielką pierwszą literę każdego wyrazu w nazwie parametru, łącznie z pierwszą literę nazwy. Na przykład nazwa parametru `ErrorAction` używa poprawny wielkość liter. Następujące nazwy parametrów używają notacji nieprawidłowa wielkość liter:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parametry, które prowadzi listę opcji

Istnieją dwa sposoby tworzenia parametru, w których wartość można wybrać z zestawu opcji.

- Zdefiniuj typ wyliczenia (lub użyj istniejącego typu wyliczenia), który określa prawidłowe wartości. Typ wyliczeniowy można następnie użyć do utworzenia tego typu parametru.

- Dodaj **ValidateSet** atrybutu deklaracji parametru. Aby uzyskać więcej informacji na temat tego atrybutu, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Użyj standardowych typów jako parametrów

W celu zapewnienia spójności z innymi poleceniami cmdlet, należy użyć standardowych typów parametrów gdzie odkąd jest możliwe. Aby uzyskać więcej informacji na temat typów, które powinny być używane dla różnych parametrów, zobacz [standardowe polecenia Cmdlet nazwy i typy parametrów](./standard-cmdlet-parameter-names-and-types.md). Ten temat zawiera łącza do różnych tematów, które opisują nazw i typów programu .NET Framework dla grup standardowe parametry, takie jak "Parametry działań".

#### <a name="use-strongly-typed-net-framework-types"></a>Użyj silnie Typizowane typy architektury .NET Framework

Parametry powinien być zdefiniowany jako typów programu .NET Framework w celu zapewnienia lepszej poprawność parametrów. Na przykład parametry, które są ograniczone do jednej wartości z zestawu wartości powinna być zdefiniowana jako typ wyliczenia. Aby obsługiwać wartość identyfikatora URI (Uniform Resource), zdefiniuj parametr jako [System.Uri](/dotnet/api/System.Uri) typu. Unikaj parametrów ciągu podstawowe właściwości wszystkie elementy oprócz dowolnego tekstu.

#### <a name="use-consistent-parameter-types"></a>Użyj parametru zgodne typy

Podczas tego samego parametru jest używany przez wielu poleceń cmdlet, należy zawsze używać tego samego typu parametru.  Na przykład jeśli `Process` parametr jest [System.Int16](/dotnet/api/System.Int16) wpisz jednego polecenia cmdlet, nie należy wprowadzać `Process` parametr innego polecenia cmdlet [System.Uint16](/dotnet/api/System.UInt16) typu.

#### <a name="parameters-that-take-true-and-false"></a>Parametry, które przyjmują wartość PRAWDA i FAŁSZ

Jeśli Twój Parametr przyjmuje tylko `true` i `false`, zdefiniuj parametr jako typ [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Parametr przełącznika jest traktowany jako `true` gdy określono za pomocą polecenia. Jeśli parametr nie jest uwzględniony w poleceniu, programu Windows PowerShell uwzględnia wartość parametru jako `false`. Nie należy definiować parametrów Boolean.

Jeśli Twój parametr potrzebuje do rozróżnienia między wartościami 3: $true $false i "nieokreślone", a następnie zdefiniuj parametr typu Nullable\<bool >.  Potrzebę 3 "nieokreślone" zazwyczaj występuje, gdy polecenia cmdlet można zmodyfikować właściwość logiczna obiektu. W tym przypadku "nieokreślone" oznacza, że nie zmienia bieżącą wartość właściwości.

#### <a name="support-arrays-for-parameters"></a>Obsługuje tablice parametrów

Często użytkownicy muszą wykonywać tej samej operacji względem wielu argumentów. Dla tych użytkowników polecenia cmdlet należy zaakceptować tablicę jako parametr wejściowy, tak aby użytkownik może przekazać argumenty do parametru jako zmienną środowiska Windows PowerShell. Na przykład [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet używa tablicę ciągów, określających nazwy procesów do pobrania.

#### <a name="support-the-passthru-parameter"></a>Obsługa parametru PassThru

Domyślnie wiele poleceń cmdlet, które modyfikują systemu, takie jak [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) polecenia cmdlet pełnić funkcję "sink" dla obiektów i zwraca wynik. Te polecenia cmdlet powinny implementować `PassThru` parametru, aby wymusić polecenia cmdlet, aby zwrócić obiekt. Gdy `PassThru` parametr jest określony, polecenie cmdlet zwraca obiekt, za pomocą wywołania [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody. Na przykład następujące polecenie zatrzymuje proces obliczenie i przekazuje wynikowe procesu do potoku.

```powershell
Stop-Process calc -passthru
```

W większości przypadków, Dodaj, zestaw i nowe polecenia cmdlet powinny obsługiwać `PassThru` parametru.

#### <a name="support-parameter-sets"></a>Obsługa zestawów parametrów

Polecenie cmdlet jest przeznaczony do wykonywania jednemu celowi. Jednak często istnieje więcej niż jeden sposób do opisu operacji lub obiekt docelowy operacji. Na przykład proces może zostać zidentyfikowany według jego nazwy, jego identyfikator lub obiektu procesu. Polecenia cmdlet powinny obsługiwać uzasadnione reprezentacje jego obiekty docelowe. Zazwyczaj polecenia cmdlet spełnia to wymaganie, określając zestawy parametrów (nazywane zestawów parametrów), które działają razem. Pojedynczy parametr mogą należeć do dowolnej liczby zestawów parametrów. Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [zestawy parametrów polecenia Cmdlet](./cmdlet-parameter-sets.md).

Podczas określania zestawów parametrów, należy ustawić tylko jeden parametr w zestawie do ValueFromPipeline. Aby uzyskać więcej informacji o tym, jak zadeklarować **parametru** atrybutów, zobacz [deklaracji ParameterAttribute](./parameter-attribute-declaration.md).

W przypadku używania zestawów parametrów domyślny zestaw parametrów jest definiowany przez **polecenia Cmdlet** atrybutu. Domyślny zestaw parametr powinien zawierać parametrów najbardziej mogą być używane w interaktywnej sesji programu Windows PowerShell. Aby uzyskać więcej informacji o tym, jak zadeklarować **polecenia Cmdlet** atrybutów, zobacz [deklaracji CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Przesyłanie opinii do użytkownika (SD04)

Użyj wytycznych w tej sekcji Opinie użytkownika. Opinia ta umożliwia użytkownikowi wiedzieć, co się dzieje w systemie i podejmować lepsze decyzje administracyjne.

Środowisko wykonawcze programu Windows PowerShell pozwala użytkownikowi określić sposób obsługi dane wyjściowe z każdego wywołania `Write` metoda przez ustawienie zmiennej preferencji. Użytkownik może ustawić kilka zmiennych preferencji, w tym zmienną, która określa, czy system powinien być wyświetlany, informacji i zmienna, która określa, czy system powinien zapytania użytkownika przed podjęciem dalszych działań.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Obsługuje WriteWarning WriteVerbose i metod WriteDebug

Polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody, gdy polecenie cmdlet ma wykonywać operacji, która może mieć niezamierzone wynik. Na przykład polecenia cmdlet powinna wywołać tę metodę, jeśli polecenie cmdlet ma zastąpić plik tylko do odczytu.

Polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody, gdy użytkownik wymaga niektóre informacje na temat działania polecenia cmdlet. Na przykład polecenia cmdlet powinny wywoływać te informacje, jeśli autor polecenia cmdlet czuje, że istnieją scenariusze, które mogą wymagać więcej informacji na temat działania polecenia cmdlet.

Polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody, gdy inżynier pomocy technicznej developer lub produktów należy zrozumieć, jakie zawiera uszkodzone działania polecenia cmdlet. Nie jest konieczne dla polecenia cmdlet do wywołania [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody w ten sam kod, który wywołuje [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) — metoda Ponieważ `Debug` parametru przedstawiono oba zestawy danych.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Obsługa WriteProgress operacje, które zająć dużo czasu

Polecenia cmdlet operacje które trwają długo i że nie można uruchomić w tle powinien obsługiwać raportowanie za pośrednictwem wywołania okresowe postępu [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metody.

#### <a name="use-the-host-interfaces"></a>Użyj interfejsów hosta

Od czasu do czasu, polecenie cmdlet musi komunikować się bezpośrednio z użytkownika, a nie przy użyciu różnych zapisu lub powinien metod obsługiwanych przez [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy. W takim przypadku polecenia cmdlet powinien pochodzić od [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy i użyć [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) właściwości. Ta właściwość obsługuje różne poziomy typu komunikacji, w tym typy PromptForChoice wiersza i WriteLine/ReadLine. Najbardziej określonego poziomu, udostępnia również sposoby do odczytu i zapisu poszczególnych kluczy i radzenia sobie z buforów.

Chyba że polecenie cmdlet jest specjalnie przeznaczona do generowania graficznego interfejsu użytkownika (GUI), go nie należy wykluczać hosta za pomocą [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) właściwości. Na przykład polecenia cmdlet, które jest przeznaczona do generowania interfejsu graficznego [GridView poza](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) polecenia cmdlet.

> [!NOTE]
> Nie należy używać poleceń cmdlet [System.Console](/dotnet/api/System.Console) interfejsu API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Utwórz plik pomocy dotyczącej poleceń Cmdlet (SD05)

Dla każdego zestawu polecenia cmdlet należy utworzyć plik Help.xml, który zawiera informacje dotyczące polecenia cmdlet. Informacje te obejmują opis polecenia cmdlet, opisy parametrów polecenia cmdlet, przykłady użycia polecenia cmdlet i więcej.

## <a name="code-guidelines"></a>Wytyczne dotyczące kodu

Należy przestrzegać następujących wytycznych podczas kodowania poleceń cmdlet, aby zapewnić spójne środowisko użytkownika między przy użyciu poleceń cmdlet i inne polecenia cmdlet. Po znalezieniu wytyczne kodu, która ma zastosowanie do danej sytuacji, pamiętaj przyjrzeć się podobne wytycznych dotyczących projektowania.

### <a name="coding-parameters-sc01"></a>Kodowanie parametrów (SC01)

Definiowanie parametru przez zadeklarowanie właściwości publicznej klasy polecenia cmdlet, które zostanie nadany **parametru** atrybutu. Parametry nie trzeba być statyczne elementy członkowskie klasy pochodnej .NET Framework dla polecenia cmdlet. Aby uzyskać więcej informacji o tym, jak zadeklarować **parametru** atrybutów, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Obsługa programu Windows PowerShell ścieżki

Ścieżka programu Windows PowerShell jest mechanizm normalizowanie dostęp do przestrzeni nazw. Po przypisaniu ścieżki programu Windows PowerShell z parametrem w poleceniu cmdlet użytkownika można zdefiniować niestandardowy "dysków", który działa jako skrót do określonej ścieżki. Gdy użytkownik wyznacza takich dysków, przechowywanych danych, takich jak dane w rejestrze może służyć w spójny sposób.

Jeśli Twoje polecenie cmdlet pozwala użytkownikowi na określenie pliku lub źródle danych, należy zdefiniować w niej parametr typu [System.String](/dotnet/api/System.String). Jeśli więcej niż jeden dysk jest obsługiwany, typ powinien być tablicą. Nazwa parametru powinna być `Path`, z aliasem `PSPath`. Ponadto `Path` parametru powinna obsługiwać znaki symboli wieloznacznych. Jeśli obsługa symboli wieloznacznych nie jest wymagane, zdefiniuj `LiteralPath` parametru.

Jeśli polecenie cmdlet operacja odczytu lub zapisu danych musi być plikiem, polecenia cmdlet, należy zaakceptować danych wejściowych ścieżka środowiska Windows PowerShell i polecenia cmdlet należy używać [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) właściwości do translacji Windows Ścieżki programu PowerShell do ścieżki, które rozpoznaje systemu plików. Określone mechanizmy to m.in. następujących metod:

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Jeśli dane polecenie cmdlet operacja odczytu lub zapisu jest tylko zestaw ciągów, a nie plikiem polecenia cmdlet należy używać dostawcy informacji o zawartości (`Content` elementu członkowskiego) do odczytu i zapisu. Te informacje są uzyskiwane z [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) właściwości. Te mechanizmy zezwala na inne magazyny danych uczestniczyć w do odczytywania i zapisywania danych.

#### <a name="support-wildcard-characters"></a>Obsługa symboli wieloznacznych

Polecenia cmdlet powinien obsługiwać znaki symboli wieloznacznych, jeśli jest to możliwe. Obsługa symboli wieloznacznych występuje w wielu miejscach w poleceniu cmdlet (szczególnie, gdy parametr przyjmuje ciąg do identyfikowania jeden obiekt z zestawu obiektów). Na przykład próbki **Stop-Proc** polecenia cmdlet z [samouczek StopProc](./stopproc-tutorial.md) definiuje `Name` parametru, aby obsługiwać ciągi, które reprezentują nazwy procesu. Ten parametr obsługuje znaki symboli wieloznacznych, aby użytkownik może łatwo określić procesy, aby zatrzymać.

Kiedy Obsługa symboli wieloznacznych znaków jest dostępny, działanie polecenia cmdlet zwykle generuje tablicę. Od czasu do czasu jej nie ma sensu obsługi tablicy, ponieważ użytkownik może użyć tylko pojedynczego elementu w danym momencie. Na przykład [Ustawianie lokalizacji](/powershell/module/Microsoft.PowerShell.Management/Set-Location) polecenie cmdlet nie trzeba obsługiwać tablicy, ponieważ użytkownik jest ustawienie tylko jednej lokalizacji. W tym wypadku polecenia cmdlet nadal obsługuje znaki symboli wieloznacznych, ale wymusza rozdzielczości w jednym miejscu.

Aby uzyskać więcej informacji na temat wzorców znaku wieloznacznego zobacz [obsługi symboli wieloznacznych w parametry polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definiowanie obiektów

Ta sekcja zawiera wskazówki dotyczące definiowania obiektów dla poleceń cmdlet i rozszerzania istniejących obiektów.

##### <a name="define-standard-members"></a>Zdefiniuj składniki standardowe

Zdefiniuj składniki standardowe rozszerzenie typu obiektu na niestandardowy plik Types.ps1xml (Użyj pliku programu Windows PowerShell Types.ps1xml jako szablonu). Składniki standardowe są definiowane przez węzeł o nazwie PSStandardMembers. Te definicje na inne polecenia cmdlet i środowisko wykonawcze programu Windows PowerShell do pracy z obiektu w spójny sposób.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Zdefiniuj ObjectMembers ma być używany jako parametrów

W przypadku projektowania obiekt do polecenia cmdlet upewnij się, że jego członków mapowane bezpośrednio do parametrów polecenia cmdlet, który zostanie użyty. To mapowanie umożliwia obiektu łatwo wysyłaniu ich do potoku i przekazać z jednego polecenia cmdlet do innego.

Istniejących obiektów .NET Framework, które są zwracane przez polecenia cmdlet często brakuje niektórych członków ważne lub wygodne, które są wymagane przez użytkownika lub dewelopera skryptu. Te brakujące elementy Członkowskie mogą być szczególnie ważne, do wyświetlania i tworzenia nazw poprawny element członkowski, tak, aby obiekt może być poprawnie przekazywane do potoku. Utwórz niestandardowy plik Types.ps1xml do dokumentowania tych wymaganych elementów. Podczas tworzenia tego pliku, firma Microsoft zaleca następującą Konwencję nazewnictwa: *< Your_Product_Name >*. Types.ps1xml.

Na przykład można dodać `Mode` skryptu właściwość [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) wpisz, aby wyświetlić atrybuty pliku wyraźniej. Ponadto można dodać `Count` właściwość alias [System.Array](/dotnet/api/System.Array) typu umożliwia spójne stosowanie tej nazwy właściwości (zamiast `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementuj interfejs IComparable

Implementowanie [System.IComparable](/dotnet/api/System.IComparable) interfejsu na wszystkich obiektach danych wyjściowych. Dzięki temu obiektów danych wyjściowych można łatwo go przesyłać potokiem do różnych poleceń cmdlet sortowania i analizy.

##### <a name="update-display-information"></a>Aktualizowanie wyświetlanych informacji

Jeśli wyświetlanie obiektu nie zapewnia oczekiwanych wyników, należy utworzyć niestandardową  *\<YourProductName >*. Plik format.ps1xml dla tego obiektu.

### <a name="support-well-defined-pipeline-input-sc02"></a>Obsługuje dobrze zdefiniowane potoku danych wejściowych (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementowanie do środka potoku

Implementowanie polecenia cmdlet przy założeniu, że będzie ona wywoływana ze środka potoku (oznacza to, inne polecenia cmdlet będą tworzyć dane wejściowe lub wykorzystają dane wyjściowe). Na przykład można zakładać, że `Get-Process` polecenia cmdlet, ponieważ generuje on danych, jest używany tylko jako pierwsze polecenie cmdlet w potoku. Jednak ponieważ to polecenie cmdlet jest przeznaczony do środka potoku, to polecenie cmdlet umożliwia poprzedniego polecenia cmdlet lub danych w potoku, aby określić procesy, które można pobrać.

#### <a name="support-input-from-the-pipeline"></a>Obsługa wprowadzania z potoku

Każdy zestaw parametrów dla polecenia cmdlet zawierać co najmniej jeden parametr, który obsługuje dane wejściowe z potoku. Obsługa danych wejściowych potoku zezwala użytkownikowi na pobieranie danych lub obiektów, aby wysłać je do zestawu prawidłowych parametrów i przekazać wyniki bezpośrednio do polecenia cmdlet.

Parametr akceptuje dane wejściowe z potoku, jeśli **parametru** atrybut zawiera `ValueFromPipeline` — słowo kluczowe, `ValueFromPipelineByPropertyName` atrybutu — słowo kluczowe lub oba słowa kluczowe w jego deklaracji. Jeśli żaden z parametrów w parametrze obsługę zestawu `ValueFromPipeline` lub `ValueFromPipelineByPropertyName` słów kluczowych, polecenia cmdlet znacząco nie można umieścić po inne polecenie cmdlet, ponieważ jej będzie ignorować wszystkie dane wejściowe w potoku.

#### <a name="support-the-processrecord-method"></a>Obsługuje metody ProcessRecord

Aby zaakceptować wszystkie rekordy z poprzedniego polecenia cmdlet w potoku, musi implementować Twojego polecenia cmdlet [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody. Program Windows PowerShell wywołuje tę metodę wielokrotnie, jeden raz dla każdego rekordu, który jest wysyłany do Twojego polecenia cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Zapisz rekordy w jednym potoku (SC03)

Gdy polecenie cmdlet zwraca obiekty, polecenia cmdlet należy zapisać obiekty natychmiast po ich wygenerowaniu. Polecenie cmdlet nie powinno zawierać ich w celu buforowania je do tablicy połączone. Polecenia cmdlet używane do odbierania obiektów jako dane wejściowe będą w stanie do przetworzenia, wyświetlać, lub przetwarzać i wyświetlać obiekty dane wyjściowe bez opóźnień. Polecenia cmdlet, które generuje dane wyjściowe obiekty pojedynczo powinny wywoływać [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody. Polecenia cmdlet, które generuje danych wyjściowych obiektów w partiach (na przykład, ponieważ interfejs API zwraca tablicę obiektów w danych wyjściowych) powinny wywoływać [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Ustaw metody z drugim parametrem Aby `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Wprowadź polecenia cmdlet bez uwzględniania wielkości liter i zachowywanie (SC04)

Domyślnie środowisko Windows PowerShell, sama nie uwzględnia wielkości liter. Jednak ponieważ dotyczy on wiele istniejących systemów, programu Windows PowerShell zachować wielkość liter w celu ułatwienia działania i zgodności. Innymi słowy Jeśli znak jest podany wielkimi literami, programu Windows PowerShell ma na wielkie litery. Systemów działał prawidłowo polecenie cmdlet musi przestrzegać tej Konwencji. Jeśli to możliwe powinna ona działać w taki sposób, bez uwzględniania wielkości liter. Jednak należy to zachować oryginalne przypadku poleceń cmdlet, które występują w dalszej części polecenia lub w potoku.

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące programowania wymagane](./required-development-guidelines.md)

[Wskazówki dotyczące porad dotyczących programowania](./advisory-development-guidelines.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
