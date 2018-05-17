---
ms.date: 10/13/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Omówienie platformy Desired State Configuration dla osób podejmujących decyzje
ms.openlocfilehash: f8a851c5fbc5165ebe9642c5cd60964f1584efab
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Omówienie platformy Desired State Configuration dla inżynierów

Ten dokument jest przeznaczony dla zespołów deweloperów i operacji korzyści z programu PowerShell żądanego stanu konfiguracji (DSC).
Dla zapewnia wyższy widok poziomu wartości DSC, można znaleźć pod adresem [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Korzyści wynikające z konfiguracji żądanego stanu

Istnieje DSC do:

- Zmniejszanie złożoności skryptów w systemie Windows
- Przyspieszenie iteracji

Pojęcie "ciągłe wdrażanie" staje się coraz większe znaczenie.
Ciągłe wdrażanie oznacza możliwość wdrażania często, potencjalnie wiele razy dziennie.
Cel wdrożenia są nie rozwiązać coś, ale coś szybko opublikowane.
Pobieranie nowych funkcji do rozwoju do operacji możliwie najsprawniej i niezawodny sposób, jak to możliwe, ograniczenie czasu na wartość nowego logiki biznesowej.

Przejście do chmury obliczeniowej oznacza wdrażania rozwiązania, które korzysta z modelu szablonu "deklaratywne", gdy środowisko stan końcowy został zadeklarowany jako tekst i opublikowane w aparacie wdrażania.
Ta metoda wdrażania umożliwia szybkie zmiany na dużą skalę, z odporności przed zagrożeniem awarii, ponieważ w dowolnym momencie wdrożenia można spójnie powtórzyć, aby zagwarantować stanu końcowego.
Tworzenie narzędzi i usług, które obsługują ten styl operacji za pomocą automatyzacji jest odpowiedzi na te zmiany.

DSC jest platforma, która zapewnia deklaratywne i wdrażania (powtarzalne) idempotentności, konfiguracji i zgodności.
Platforma DSC umożliwia zapewnienia prawidłowej konfiguracji, co pozwala uniknąć błędów i niepowodzeń wdrażania kosztowne uniemożliwia składniki centrum danych.
Traktując konfiguracji DSC jako części kodu aplikacji, DSC umożliwia ciągłego wdrażania.
Powinny zostać uaktualnione konfiguracji DSC jako część aplikacji, zapewnia, że informacje potrzebne do wdrożenia aplikacji jest zawsze aktualne i gotowa do użycia.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Mam programu PowerShell, dlaczego należy konfiguracji żądanego stanu"?

Oddzielne opcje konfiguracji DSC lub "co warto zrobić", z wykonywania lub "jak I chcesz to zrobić."
Oznacza to, że logika wykonywania jest zawarty w zasoby.
Użytkownicy nie muszą znać sposób wdrożenia lub funkcji jest wdrażany, kiedy zasób DSC tej funkcji jest dostępny.
Dzięki temu użytkownikowi skupić się na strukturze ich wdrażania.

Na przykład skrypty programu PowerShell powinna wyglądać następująco:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Ten skrypt jest proste, zrozumiałe i bezpośrednie.
Jednak jeśli wprowadzenie tego skryptu do produkcji, należy uruchomić na kilka problemów.
Co się stanie w przypadku skryptu uruchamianego dwa razy pod rząd?
Co się stanie, jeśli Bob wcześniej ma pełny dostęp do udziału?

Kompensacji tych problemów, "rzeczywiste" wersji skryptu będzie wyglądać bliżej wyglądać mniej więcej tak:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Ten skrypt jest bardziej złożonych z dużą ilością logiki oraz obsługi błędów.
Skrypt jest bardziej złożony, ponieważ są już ostrzegający, co ma gotowe, ale *jak to zrobić*.

DSC umożliwia określenie, co ma gotowe i podstawowej logiki jest pobieranej optymalizacji.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Ten skrypt jest prawidłowo sformatowany i prostego do odczytu.
Ścieżkami logiki oraz obsługi błędów są nadal dostępne w [zasobów](resources.md) implementacji, ale niewidoczna Autor skryptu.

## <a name="separating-environment-from-structure"></a>Oddzielanie środowiska ze struktury

Wspólnego wzorca w DevOps ma wiele środowisk dla wdrożenia.
Na przykład może być środowisku "dev" pozwala szybko prototypu nowy kod.
Kod ze środowiska "dev" przechodzi w stan środowiska "test", gdzie inne osoby zweryfikować nowych funkcji.
Na koniec kod przechodzi w stan "produkcyjnego" lub działającą witrynę środowiska produkcyjnego.

Konfiguracji DSC zmieścił się w tym potoku deweloperów test produkcyjną za pośrednictwem [dane konfiguracji](configData.md).
To dodatkowe abstracts różnica między struktury konfiguracji z węzłów, które są zarządzane.
Na przykład można zdefiniować konfigurację, która wymaga programu SQL server, serwer usług IIS i serwer warstwy środkowej.
Niezależnie od tego, jakie węzłów odbierać różne tej konfiguracji te trzy elementy zawsze będzie obecne.
Dane konfiguracji umożliwia punktu wszystkie trzy elementy do tej samej maszynie w środowisku deweloperów, oddzielne limit trzy elementy do trzech różnych maszyn dla środowiska testowego, a na koniec na wszystkich serwerach produkcyjnych środowiska produkcyjną.
Aby wdrożyć w różnych środowiskach, można wywołać **Start DscConfiguration** z danymi prawidłowej konfiguracji środowiska docelową.

## <a name="see-also"></a>Zobacz też

[Konfiguracje](configurations.md)

[Dane konfiguracji](configData.md)

[Zasoby](resources.md)