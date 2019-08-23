---
title: Cykl życia pomocy technicznej programu PowerShell Core
description: Zasady rządzące obsługą programu PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 60999ed54ca3be15232ffee3ab0c49cb94873a8f
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986743"
---
# <a name="powershell-core-support-lifecycle"></a>Cykl życia pomocy technicznej programu PowerShell Core

Program PowerShell Core to odrębny zestaw narzędzi i składników, które są dostarczane, instalowane i konfigurowane niezależnie od programu Windows PowerShell. W związku z tym program PowerShell Core nie jest uwzględniony w umowach licencyjnych systemu Windows 7/8.1/10 lub Windows Server.

Jednak środowisko PowerShell Core jest obsługiwane w ramach tradycyjnych umów pomocy technicznej firmy Microsoft, w tym [Dotyczące][], [Microsoft Enterprise Agreement][enterprise-agreement]i [Microsoft Software Assurance][assurance].
Możesz również uregulować pomoc [Asystowana pomoc techniczna][] dla programu PowerShell Core, zgłaszając żądanie pomocy technicznej dotyczące problemu.

## <a name="community-support"></a>Wsparcie społeczności

Oferujemy również [wsparcie społeczności][] w usłudze GitHub, w której można zgłosić problem, usterkę lub żądanie funkcji.
Ponadto możesz uzyskać pomoc od innych członków społeczności w ogólnej [Społeczność firmy Microsoft][] lub w [Społeczność techniczna programu PowerShell][]programu Microsoft PowerShell. Firma Microsoft nie gwarantuje, że społeczność będzie w odpowiednim czasie rozwiązywać problemy. Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjnych, płatnych opcji pomocy technicznej.

## <a name="lifecycle-of-powershell-core"></a>Cykl życia programu PowerShell Core

Program PowerShell Core wdraża [zasady nowoczesnego cyklu życia firmy Microsoft][modern]. Ten cykl pomocy technicznej jest przeznaczony do zapewnienia aktualności klientom najnowszych wersji.

Gałąź w wersji 6. x programu PowerShell Core będzie aktualizowana co około sześciu miesięcy (przykłady: 6,0, 6,1, 6,2 itd.)

> [!IMPORTANT]
> Aby nadal otrzymywać pomoc techniczną, należy zaktualizować w ciągu sześciu miesięcy od każdej nowej wersji pomocniczej.

Na przykład jeśli program PowerShell Core 6,1 jest wydawany 1 lipca 2018, należy przeprowadzić aktualizację do programu PowerShell Core 6,1 do 1 stycznia 2019, aby zachować pomoc techniczną.

> [!IMPORTANT]
> Aby nadal otrzymywać pomoc techniczną, należy zaktualizować w ciągu 30 dni od każdej nowej wersji poprawki.

Na przykład jeśli korzystasz z programu PowerShell Core 6,1, a program 6.1.3 został zwolniony 19 lutego 2019, należy przeprowadzić aktualizację do programu PowerShell Core 6.1.3 do 21 marca 2019, czyli 30 dni od wydania do utrzymania pomocy technicznej. Jeśli okaże się wymagane, poprawki zostaną wydane w następnej aktualizacji zbiorczej.

Nowoczesne zasady cyklu życia wymagają również od firmy Microsoft udzielenia klientom 12 miesięcy przed kontynuowaniem wsparcia dla produktu (czyli programu PowerShell Core).

Wreszcie oczekujemy, że program PowerShell Core przyjmie długoterminowe podejście do obsługi. W ramach tego podejścia do obsługi będziemy musieli zachować pomoc techniczną i aktualizacje zabezpieczeń w odniesieniu do określonej gałęzi/wersji 6. x.

## <a name="supported-platforms"></a>Obsługiwane platformy

Aby upewnić się, że platforma i wersja programu PowerShell Core są oficjalnie obsługiwane, zobacz poniższą tabelę.

Nasza społeczność zawiera również pakiety dla niektórych platform, ale nie są oficjalnie obsługiwane. Te pakiety są oznaczone jako `Community` w tabeli.

Platformy wymienione jako `Experimental` nie są oficjalnie obsługiwane, ale są dostępne do eksperymentowania i przesyłania opinii.

| Platforma                                          | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8,1 i 10                            | Obsługiwane   | Obsługiwane   |
| Windows Server 2008 R2, 2012 R2, 2016             | Obsługiwane   | Obsługiwane   |
| [Półroczny kanał systemu Windows Server][semi-annual] | Obsługiwane   | Obsługiwane   |
| Ubuntu 16,04 i 18,04                            | Obsługiwane   | Obsługiwane   |
| Ubuntu 18,10 (za pośrednictwem pakietu Snap)                   | Społeczność   | Społeczność   |
| Ubuntu 19,04 (za pośrednictwem pakietu Snap)                   | Społeczność   | Społeczność   |
| Debian 9                                          | Obsługiwane   | Obsługiwane   |
| CentOS 7                                          | Obsługiwane   | Obsługiwane   |
| Red Hat Enterprise Linux 7                        | Obsługiwane   | Obsługiwane   |
| openSUSE 42,3                                     | Obsługiwane   | Obsługiwane   |
| Fedora 28                                         | Obsługiwane   | Obsługiwane   |
| macOS 10.12+                                      | Obsługiwane   | Obsługiwane   |
| Przekroj                                              | Społeczność   | Społeczność   |
| Raspbian                                          | Społeczność   | Społeczność   |
| Kali                                              | Społeczność   | Społeczność   |
| AppImage (działa na wielu platformach systemu Linux)      | Społeczność   | Społeczność   |
| [Pakiet przyciągania](https://snapcraft.io/powershell)   | Zobacz Uwaga    | Zobacz Uwaga    |

> [!NOTE]
> Pakiety przyciągania są obsługiwane w taki sam sposób, jak w przypadku dystrybucji, w której uruchomiono pakiet.

## <a name="powershell-releases-end-of-life"></a>Program PowerShell zwalnia koniec cyklu życia

W oparciu o [cykl życia programu PowerShell Core](#lifecycle-of-powershell-core)w poniższej tabeli wymieniono daty, w których różne wersje nie będą już obsługiwane.

| Wersja | Koniec okresu użytkowania                   |
|---------|-------------------------------|
| 6.0     | 13 lutego 2019             |
| 6.1     | 28 września, 2019            |
| 6.2     | 6 miesięcy po 7 wersjach     |

## <a name="unsupported-platforms"></a>Nieobsługiwane platformy

Gdy wersja platformy osiągnie koniec okresu ważności określonego przez właściciela platformy, program PowerShell Core również przestanie obsługiwać tę wersję platformy. Wcześniej wydane pakiety pozostaną dostępne dla klientów potrzebujących dostępu, ale formalne wsparcie i aktualizacje dowolnego rodzaju nie będą już udostępniane.

Dlatego właściciele dystrybucji zakończyły obsługę następujących wersji i nie są obsługiwane.

| Platforma | Wersja | Koniec okresu istnienia                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [2017 sierpnia](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Grudzień 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [2018 maja](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [2017 maja](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42,2    | [Styczeń 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [Lipiec 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17,04   | [Styczeń 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17,10   | [Lipiec 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Czerwiec 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Listopad 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Kwiecień 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Uwagi dotyczące licencjonowania

Program PowerShell Core jest wydawany w ramach [Licencja MIT][]. W ramach tej licencji i bez płatnej umowy dotyczącej pomocy technicznej użytkownicy są ograniczeni do [Wsparcie społeczności][]. W przypadku pomocy technicznej przez społeczność firma Microsoft nie udziela żadnych gwarancji dotyczących czasu reakcji ani poprawek.

## <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Obsługa programu PowerShell Core nie obejmuje modułów produktu, chyba że te moduły jawnie nie obsługują programu PowerShell Core. Na przykład użycie `ActiveDirectory` modułu, który jest dostarczany jako część systemu Windows Server, jest nieobsługiwanym scenariuszem.

Jednak moduły, które nie obsługują jawnie środowiska PowerShell, mogą być zgodne w niektórych przypadkach. Instalując [`WindowsPSModulePath`][] moduł, można dodać środowisko Windows PowerShell `PSModulePath` do rdzenia `PSModulePath`programu PowerShell.

Najpierw zainstaluj `WindowsPSModulePath` moduł z Galeria programu PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Po zainstalowaniu tego modułu Uruchom `Add-WindowsPSModulePath` polecenie cmdlet, aby dodać środowisko Windows PowerShell `PSModulePath` do środowiska PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Funkcje eksperymentalne

[Funkcje eksperymentalne][] są ograniczone do [pomocy technicznej społeczności](#community-support).

[Dotyczące]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Wsparcie społeczności]: https://github.com/powershell/powershell/issues
[Społeczność firmy Microsoft]: https://answers.microsoft.com/
[Społeczność techniczna programu PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Asystowana pomoc techniczna]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licencja MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funkcje eksperymentalne]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
