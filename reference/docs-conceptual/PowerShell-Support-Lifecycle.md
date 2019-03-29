---
title: Cykl życia pomocy technicznej programu PowerShell Core
description: Zasady dotyczące pomocy technicznej dla programu PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623862"
---
# <a name="powershell-core-support-lifecycle"></a>Cykl życia pomocy technicznej programu PowerShell Core

PowerShell Core to zestaw różne narzędzia i składniki, które są dostarczane, zainstalować i skonfigurować oddzielnie, za pomocą programu Windows PowerShell.
Tak program PowerShell Core nie są objęte umowami licencjonowania Windows 7/8.1/10 lub Windows Server.

Jednak program PowerShell Core jest obsługiwane w ramach tradycyjnego umowy pomocy technicznej firmy Microsoft, w tym [Premier][], [umowy Microsoft Enterprise Agreement][enterprise-agreement]i [Microsoft Software Assurance][assurance].
Można również płacisz [asystowanej pomocy technicznej][] dla programu PowerShell Core, rejestrując żądanie pomocy technicznej dla danego problemu.

## <a name="community-support"></a>Pomoc techniczna w społeczności

Oferujemy również [pomoc techniczna w społeczności][] w serwisie GitHub, w którym mogą zgłaszać problem lub usterki zgłoszenie dotyczące funkcji.
Ponadto Pomoc z innymi członkami społeczności może się okazać ogólne [Microsoft Community][] lub Microsoft [Społeczność techniczna programu PowerShell][].
Firma Microsoft nie oferuje żadnej gwarancji, istnieje czy społeczności zostanie adres lub rozwiązać problem w odpowiednim czasie.
Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjny, płatnych opcji pomocy technicznej.

## <a name="lifecycle-of-powershell-core"></a>Cykl życia programu PowerShell Core

Program PowerShell Core jest przyjęcie [nowoczesne zasady cyklu życia firmy Microsoft][modern].
Ten cykl wsparcia technicznego jest przeznaczona dla aktualnych klientów przy użyciu najnowszej wersji.

Gałęzi wersji 6.x, programu PowerShell Core będą aktualizowane mniej więcej co sześć miesięcy (przykłady: w wersji 6.0, 6.1, 6.2, itp.)

> [!IMPORTANT]
> Należy zaktualizować w ciągu sześciu miesięcy po każdej nowej wersji pomocniczej wersji, aby nadal otrzymywać pomocy technicznej.

Na przykład jeśli program PowerShell Core 6.1 jest wydanej w dniu 1 lipca 2018 r. można oczekuje się do aktualizacji do programu PowerShell Core 6.1 1 stycznia 2019 r do obsługi pomocy technicznej.

> [!IMPORTANT]
> Należy zaktualizować w ciągu 30 dni po każdej nowej wersji poprawki wersji, aby nadal otrzymywać pomocy technicznej.

Na przykład jeśli używasz programu PowerShell Core 6.1 i 6.1.3 została wydana 19 lutego 2019 r można oczekuje się do aktualizacji do programu PowerShell Core 6.1.3 21 marca 2019 r, czyli 30 dni po wydaniu do obsługi pomocy technicznej.
Jeśli wymagana znajdują się wszystkie poprawki, poprawki zostaną wydane w następną aktualizację zbiorczą.

![Cykl życia gałęzi programu PowerShell Core][lifecycle-chart]

Nowoczesne zasady cyklu życia wymaga również, że Microsoft zawarcia klientów przez 12 miesięcy przed zaprzestaniem pomocy technicznej dla produktu (oznacza to, programu PowerShell Core).

Po pewnym czasie oczekujemy, że program PowerShell Core przyjmie "długoterminowej obsługi" podejście.
W tym podejściu obsługi będzie wymagamy tylko obsługi i aktualizacje zabezpieczeń pozostanie w pomocy technicznej w określonej gałęzi/wersji 6.x.

## <a name="supported-platforms"></a>Obsługiwane platformy

Poniższej tabeli, aby wyświetlić wersję programu PowerShell Core w przypadku korzystania z platformy jest oficjalnie obsługiwany.

Naszej społeczności współtworzonej również pakiety dla niektórych platform, ale nie jest oficjalnie obsługiwana.
Te pakiety są oznaczone jako `Community` w tabeli.

Platformy wymienione jako `Experimental` oficjalnie nie są obsługiwane, ale są dostępne do eksperymentowania i przesyłania opinii.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 i 10                            | Obsługiwane   | Obsługiwane   |
| Windows Server 2008 R2, 2012 R2, 2016             | Obsługiwane   | Obsługiwane   |
| [Półroczny kanał dystrybucji systemu Windows Server][semi-annual] | Obsługiwane   | Obsługiwane   |
| Ubuntu 16.04 i 18.04                            | Obsługiwane   | Obsługiwane   |
| Ubuntu 18.10 (za pośrednictwem przyciągania pakiet)                   | Społeczność   | Społeczność   |
| Debian 9                                          | Obsługiwane   | Obsługiwane   |
| CentOS 7                                          | Obsługiwane   | Obsługiwane   |
| Red Hat Enterprise Linux 7                        | Obsługiwane   | Obsługiwane   |
| openSUSE 42.3                                     | Obsługiwane   | Obsługiwane   |
| Fedora 28                                         | Obsługiwane   | Obsługiwane   |
| macOS 10.12+                                      | Obsługiwane   | Obsługiwane   |
| Architektura                                              | Społeczność   | Społeczność   |
| Raspbian                                          | Społeczność   | Społeczność   |
| Kali                                              | Społeczność   | Społeczność   |
| AppImage (działa na wielu platformach systemu Linux)     | Społeczność   | Społeczność   |
| [Przyciągaj pakietu](https://snapcraft.io/powershell)   | Patrz Uwaga    | Patrz Uwaga    |

> [!NOTE]
> Przyciągaj pakietów takie same jak w przypadku dystrybucji korzystania z pakietu.

## <a name="powershell-release-end-of-life"></a>Program PowerShell wersji koniec cyklu życia

Na podstawie [cyklu życia programu PowerShell Core](#lifecycle-of-powershell-core), Poniższa tabela zawiera daty, kiedy różnych wersji będzie nie będzie już obsługiwana.

| Wersja | Koniec cyklu życia                   |
|---------|-------------------------------|
| 6.0     | 13 lutego 2019 r.             |
| 6.1     | 28 września 2019 r.            |
| 6.2     | zwalnia 6 miesięcy od 6.3   |

## <a name="platforms-which-are-out-of-support"></a>Platform, które są poza pomocy technicznej

Gdy wersja platformy osiągnie wycofanych z eksploatacji, zgodnie z definicją właściciela platformy, program PowerShell Core przestaną się również do obsługi tej wersji platformy.
Wcześniej wydane pakiety, pozostaną dostępne dla klientów wymagające dostępu, ale obsługa formalne i aktualizacje dowolnego rodzaju już nie będą udostępniane.

Dlatego właściciele dystrybucji zakończone obsługę następujących wersji i nie są obsługiwane.

| System operacyjny       | Wersja | Koniec cyklu życia                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Sierpnia 2017 r.](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Grudnia 2017 r.](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maja 2018 r.](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maja 2017 r.](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Stycznia 2018 r.](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Lipca 2017 r.](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Stycznia 2018 r.](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Lipca 2018 r.](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Czerwca 2018 r.](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Listopada 2018 r.](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [2019 kwietnia](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Uwagi dotyczące licencjonowania

Program PowerShell Core jest wydawane na mocy [Licencja MIT][].
W ramach niniejszej licencji, a nie towarzyszy stosowna umowa płatnej pomocy technicznej, użytkownicy są ograniczone do [pomoc techniczna w społeczności][].
Za pomocą pomoc techniczna w społeczności firmy Microsoft nie udziela żadnych gwarancji czasu odpowiedzi lub poprawki.

## <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Pomocy technicznej dla programu PowerShell Core nie obejmuje moduły produktu, chyba że moduły jawnego zapewnienia obsługi programu PowerShell Core.
Na przykład za pomocą `ActiveDirectory` modułu, który jest dostarczany jako część systemu Windows Server jest to nieobsługiwany scenariusz.

Jednak może być zgodny w niektórych przypadkach moduły, które nie obsługują jawnie programu PowerShell Core.
Instalując [ `WindowsPSModulePath` ][] modułu programu Windows PowerShell można dodać `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.

Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Po zainstalowaniu tego modułu, należy uruchomić `Add-WindowsPSModulePath` polecenie cmdlet programu Windows PowerShell dodanie `PSModulePath` do programu PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Funkcje eksperymentalne

[Funkcje eksperymentalne][] są ograniczone do [pomoc techniczna w społeczności](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Pomoc techniczna w społeczności]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Społeczność techniczna programu PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[asystowanej pomocy technicznej]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licencja MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funkcje eksperymentalne]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
