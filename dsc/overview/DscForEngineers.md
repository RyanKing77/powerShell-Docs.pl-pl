---
ms.date: 10/13/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Omówienie platformy Desired State Configuration dla inżynierów
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684311"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Omówienie platformy Desired State Configuration dla inżynierów

Ten dokument jest przeznaczony dla zespołów deweloperów i operacji zrozumieć korzyści z programu PowerShell Desired State Configuration (DSC).
Dla zapewnia wyższy poziom Widok wartość DSC, zobacz [Przegląd Desired State Configuration dla osób podejmujących decyzje](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Zalety Desired State Configuration

Istnieje DSC:

- Zmniejsz złożoność obsługi skryptów w Windows
- Zwiększanie szybkości iteracji

Pojęcie "ciągłego wdrażania" staje się niezwykle ważne.
Ciągłe wdrażanie oznacza możliwość wdrażania częściej i potencjalnie wiele razy dziennie.
Cel wdrożenia są nie poprawki, ale coś szybko opublikowane.
Wprowadzenie nowych funkcji przez proces tworzenia operacji jako sprawnie i niezawodne, jak to możliwe, zmniejszyć czas do osiągnięcia korzyści z nowej logiki biznesowej.

Przejście do chmury obliczeniowej, oznacza to rozwiązanie wdrożenia, które korzysta z modelu "deklaratywnych" szablonów, gdzie środowisko stan końcowy jest zadeklarowany jako tekst, a publikowane w aparacie wdrażania.
Ta metoda wdrażania umożliwia dynamicznymi zmianami w dużej skali, przy użyciu odporność przed zagrożeniem awarii, ponieważ w dowolnym momencie wdrażania można spójnie powtórzyć, aby zagwarantować stanu końcowego.
Tworzenie narzędzi i usług, które obsługują ten styl operacji za pomocą automatyzacji to odpowiedzi na te zmiany.

DSC jest platforma, która zapewnia deklaracyjne i wdrażania (powtarzalne) idempotentne, konfiguracji i zgodności.
Platforma DSC umożliwia upewnij się, że składniki centrum danych prawidłowej konfiguracji, który uniemożliwia niepowodzeń wdrażania kosztowne i pozwala uniknąć błędów.
Traktując konfiguracje DSC jako część kodu aplikacji, DSC umożliwia ciągłe wdrażanie.
Konfiguracja DSC powinien zostać zaktualizowany w ramach aplikacji, zapewnia, że wiedzę potrzebną do wdrożenia aplikacji jest zawsze aktualny i gotowe do użycia.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Mam programu PowerShell, dlaczego należy Desired State Configuration?"

Celem oddzielne konfiguracje DSC lub "co warto zrobić", wykonania lub "jak chcę to zrobił."
Oznacza to, że logika wykonywania znajduje się w ramach zasobów.
Użytkownicy nie muszą wiedzieć, jak wdrożyć lub wdrożyć funkcję, gdy zasób DSC dla tej funkcji jest dostępny.
Dzięki temu użytkownikowi skupić się na strukturze ich wdrożenia.

Na przykład skrypty programu PowerShell powinna wyglądać następująco:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Ten skrypt jest proste, zrozumiałe i proste.
Jednak przy próbie umieszczenie tego skryptu do środowiska produkcyjnego, uruchomisz kilka problemy.
Co się stanie w przypadku skryptu uruchamianego dwa razy w wierszu?
Co się stanie, jeśli Bob wcześniej był pełny dostęp do udziału?

Aby zrekompensować te problemy, "członu real" wersji skryptu będzie wyglądać bliżej mniej więcej tak:
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

Ten skrypt jest bardziej złożone z dużą ilością logiki oraz obsługi błędów.
Skrypt jest bardziej złożone, ponieważ są już informujący, co ma gotowe, ale *jak to zrobić*.

DSC umożliwia określenie, co ma gotowe i podstawowej logiki jest wyodrębniony natychmiast.

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
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
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
Ścieżkami logiki oraz obsługi błędów, które występują w [zasobów](../resources/resources.md) implementacji, ale niewidoczna Autor skryptu.

## <a name="separating-environment-from-structure"></a>Oddzielanie środowiska na podstawie struktury

Typowym wzorcem w infrastrukturze DevOps jest wielu środowisk na potrzeby wdrożenia.
Na przykład może być środowisko "dev", umożliwia szybkie prototypów nowego kodu.
Kod w środowisku "dev" przechodzi do środowiska "test", gdzie Sprawdź nowe funkcje, inne osoby.
Na koniec kod przechodzi w stan "prod" lub w środowisku produkcyjnym działającej witryny.

Konfiguracje DSC obsłużyć ten potok dev-test-prod za pośrednictwem [dane konfiguracyjne](../configurations/configData.md).
Przenosi to dodatkowo różnica między struktury konfiguracji z węzłów, które są zarządzane.
Na przykład można zdefiniować konfigurację, która wymaga programu SQL server, serwer usług IIS i serwer warstwy środkowej.
Niezależnie od tego, jakie węzły odbierać różne części tej konfiguracji te trzy elementy zawsze będzie istnieć.
Dane konfiguracji można użyć aby wskazać wszystkie trzy elementy na tym samym komputerze dla środowiska deweloperskiego, oddzielne się trzy elementy do trzech różnych maszyn dla środowiska testowego, a na koniec na wszystkich serwerach produkcyjnych dla środowiska produkcyjnego.
Aby wdrożyć w różnych środowiskach, można wywołać **Start-DscConfiguration** z danymi prawidłowej konfiguracji dla środowisk docelowych.

## <a name="see-also"></a>Zobacz też

[Konfiguracje](../configurations/configurations.md)

[Dane konfiguracji](../configurations/configData.md)

[Zasoby](../resources/resources.md)
