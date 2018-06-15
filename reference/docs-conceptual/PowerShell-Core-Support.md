# <a name="powershell-core-support-lifecycle"></a>Cykl życia pomocy technicznej programu PowerShell Core

Podstawowe środowisko PowerShell jest różne zestaw narzędzi i składników, które zostały wydane, zainstalowane i skonfigurowane oddzielnie od środowiska Windows PowerShell.
W związku z tym Core programu PowerShell nie jest uwzględniony w umowach licencjonowania systemu Windows 7/8.1/10 lub Windows Server.

Jednak Core programu PowerShell jest obsługiwany w ramach tradycyjnego umów pomocy technicznej firmy Microsoft, w tym [Premier][], [umowy Enterprise firmy Microsoft][enterprise-agreement]i [Microsoft Software Assurance][assurance].
Można również opłacać [asystowaną pomocą techniczną][] podstawowych programu PowerShell, zachowując żądania pomocy technicznej dla danego problemu.

Oferujemy również [techniczna dla społeczności][] w witrynie GitHub, w którym można pliku problemu, usterki lub żądanie funkcji.
Alternatywnie mogą znaleźć pomoc od innych członków społeczności ogólne [Społeczność Microsoft][] lub Microsoft [społeczność techniczna programu PowerShell][].
Firma Microsoft oferuje żadnej gwarancji, występuje problem opisany lub rozwiązane w odpowiednim czasie.
Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjny, płatną opcje pomocy technicznej.

## <a name="lifecycle-of-powershell-core"></a>Cykl życia podstawowych programu PowerShell

Wdraża PowerShell Core [Microsoft nowoczesnych technicznego][modern].
Ten cykl pomocy technicznej ma na celu aktualizowanie do najnowszej wersji klientów.

Rozgałęzienie 6.x wersji Core programu PowerShell zostanie zaktualizowany mniej więcej co sześć miesięcy (np. w wersji 6.0, 6.1, 6.2, itp.)

> [!IMPORTANT]
> Należy zaktualizować w ciągu sześciu miesięcy po każdej nowej wersji pomocniczej wersji nadal odbierać pomocy technicznej.

Na przykład jeśli 6.1 Core programu PowerShell jest wydanej w dniu 1 lipca 2018 możesz oczekuje się do aktualizacji do programu PowerShell Core 6.1 przez 1 stycznia 2019 do obsługi pomocy technicznej.

![Cykl życia gałęzi Core programu PowerShell][lifecycle-chart]

Nowoczesne technicznego wymaga również, że Microsoft zawiadamiać klientów 12 miesięcy przed zaprzestanie obsługę produktu (tj. podstawowej programu PowerShell).

Po pewnym czasie oczekujemy PowerShell Core przyjmie "długoterminowej obsługi" podejście, w którym firma Microsoft będzie wymagać tylko obsługi i zabezpieczeń aktualizuje pozostanie w pomocy technicznej na określonej gałęzi/wersji 6.x.

## <a name="supported-platforms"></a>Obsługiwane platformy

Podstawowe programu PowerShell oficjalnie jest obsługiwane na następujących platformach:

* Windows 7, 8.1 i 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Windows Server częściowo roczna kanału][semi-annual]
* Ubuntu 14.04 i 16.04, 17.04
* Debian 8.7 + i 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 27 28
* macOS 10.12+

Naszej społeczności przyczynił się również pakiety dla następujących platform, ale nie są one oficjalnie suppported:

* Arch Linux
* Kali Linux
* AppImage (działa na wielu platformach systemu Linux)

## <a name="notes-on-licensing"></a>Uwagi dotyczące licencjonowania

Z dodatkiem PowerShell Core [MIT licencji][].
W ramach tej licencji, a w przypadku braku umowy płatnej pomocy technicznej, użytkownicy są ograniczone do [techniczna dla społeczności][].
Z obsługą społeczności firma Microsoft nie udziela żadnych gwarancji, czas odpowiedzi lub poprawki.

## <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Obsługuje dla podstawowych programu PowerShell nie obejmuje innych modułów produktu, chyba że moduły jawnie obsługuje Core programu PowerShell.
Na przykład za pomocą `ActiveDirectory` moduł, który jest dostarczany jako część systemu Windows Server jest to nieobsługiwany scenariusz.

Jednak może być zgodne w niektórych przypadkach modułów, które nie obsługują jawnie Core programu PowerShell.
Instalując [ `WindowsPSModulePath` ][] moduł, możesz dołączyć programu Windows PowerShell `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.

Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Po zainstalowaniu tego modułu, uruchom `Add-WindowsPSModulePath` polecenia cmdlet programu Windows PowerShell Dodaj `PSModulePath` na rdzeń środowiska PowerShell:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[techniczna dla społeczności]: https://github.com/powershell/powershell/issues
[Społeczność Microsoft]: https://answers.microsoft.com/
[Społeczność techniczna programu PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[asystowaną pomocą techniczną]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT licencji]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
