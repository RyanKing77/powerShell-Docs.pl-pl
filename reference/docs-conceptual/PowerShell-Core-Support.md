# <a name="powershell-core-support-lifecycle"></a>Cykl życia pomocy technicznej programu PowerShell Core

PowerShell Core to zestaw różne narzędzia i składniki, które są dostarczane, zainstalować i skonfigurować oddzielnie, za pomocą programu Windows PowerShell.
W związku z tym program PowerShell Core nie są objęte umowami licencjonowania Windows 7/8.1/10 lub Windows Server.

Jednak program PowerShell Core jest obsługiwane w ramach tradycyjnego umowy pomocy technicznej firmy Microsoft, w tym [W wersji Premier][], [umowy Microsoft Enterprise Agreement][enterprise-agreement]i [Microsoft Software Assurance][assurance].
Można również płacisz [asystowanej pomocy technicznej][] dla programu PowerShell Core, rejestrując żądanie pomocy technicznej dla danego problemu.

Oferujemy również [pomoc techniczna w społeczności][] w serwisie GitHub, w którym mogą zgłaszać problem lub usterki zgłoszenie dotyczące funkcji.
Alternatywnie pomocy z innymi członkami społeczności może się okazać ogólne [Microsoft Community][] lub Microsoft [Społeczność techniczna programu PowerShell][].
Firma Microsoft nie oferuje żadnej gwarancji, istnieje problem rozwiązany lub rozwiązane w określonym czasie.
Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjny, płatnych opcji pomocy technicznej.

## <a name="lifecycle-of-powershell-core"></a>Cykl życia programu PowerShell Core

Program PowerShell Core jest przyjęcie [nowoczesne zasady cyklu życia firmy Microsoft][modern].
Ten cykl wsparcia technicznego jest przeznaczona dla aktualnych klientów przy użyciu najnowszej wersji.

Gałęzi wersji 6.x, programu PowerShell Core będą aktualizowane mniej więcej co sześć miesięcy (np. w wersji 6.0, 6.1, 6.2, itp.)

> [!IMPORTANT]
> Należy zaktualizować w ciągu sześciu miesięcy po każdej nowej wersji pomocniczej wersji, aby nadal otrzymywać pomocy technicznej.

Na przykład jeśli program PowerShell Core 6.1 jest wydanej w dniu 1 lipca 2018 r. Możesz oczekuje się do aktualizacji do programu PowerShell Core 6.1 1 stycznia 2019 r do obsługi pomocy technicznej.

![Cykl życia gałęzi programu PowerShell Core][lifecycle-chart]

Nowoczesne zasady cyklu życia wymaga również, że Microsoft zawarcia klientów przez 12 miesięcy przed zaprzestaniem pomocy technicznej dla produktu (np. programu PowerShell Core).

Po pewnym czasie oczekujemy, że program PowerShell Core przyjmie "długoterminowej obsługi" podejścia, w którym firma Microsoft wymaga tylko Obsługa i bezpieczeństwo aktualizacji na bieżąco w obsłudze w określonej gałęzi/wersji 6.x.

## <a name="supported-platforms"></a>Obsługiwane platformy

Zobacz poniższą tabelę, aby wyświetlić wersję programu PowerShell Core, którego używasz jest oficjalnie obsługiwane platformy.

Naszej społeczności współtworzonej również pakiety dla niektórych platform, ale nie jest oficjalnie obsługiwana.
Te pakiety są oznaczone jako `Community` w tabeli.

Platformy wymienione jako `Experimental` oficjalnie nie są obsługiwane, ale są dostępne do eksperymentowania i przesyłania opinii.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 i 10                            | Obsługiwane   | Obsługiwane   |
| Windows Server 2008 R2, 2012 R2, 2016             | Obsługiwane   | Obsługiwane   |
| [Półroczny kanał dystrybucji systemu Windows Server][semi-annual] | Obsługiwane   | Obsługiwane   |
| Ubuntu 14.04 i 16.04                           | Obsługiwane   | Obsługiwane   |
| Ubuntu 17.10 i 18.04                           |             | Obsługiwane   |
| Debian 8.7 + i 9                                | Obsługiwane   | Obsługiwane   |
| CentOS 7                                          | Obsługiwane   | Obsługiwane   |
| Red Hat Enterprise Linux 7                        | Obsługiwane   | Obsługiwane   |
| OpenSUSE 42.3                                     | Obsługiwane   | Obsługiwane   |
| Fedora 27                                         | Obsługiwane   | Obsługiwane   |
| Fedora 28                                         |             | Obsługiwane   |
| macOS 10.12+                                      | Obsługiwane   | Obsługiwane   |
| Architektura                                              | Społeczność   | Społeczność   |
| Raspbian                                          | Eksperymentalne| Społeczność   |
| Kali                                              | Społeczność   | Społeczność   |
| AppImage (działa na wielu platformach systemu Linux)     | Społeczność   | Społeczność   |

## <a name="platform-which-are-out-of-support"></a>Platforma, której znajdą się poza pomocy technicznej

Gdy wersja platformy osiągnie zakończenia eksploatacji zgodnie z definicją właściciela platformy, program PowerShell Core również przestaną zapewnienia obsługi tej wersji platformy. Wcześniej wydane pakiety, pozostaną dostępne dla klientów wymagające dostępu, ale obsługa formalne i aktualizacje dowolnego rodzaju już nie będą udostępniane.

W związku z tym obsługę następujących wersji oprogramowania została zakończona przez właścicieli dystrybucji i nie są obsługiwane.

| System operacyjny       | Wersja | Koniec cyklu życia                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 26      | [Maja 2018 r.](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| Fedora   | 25      | [Grudnia 2017 r.](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 24      | [Sierpnia 2017 r.](https://fedoramagazine.org/fedora-24-eol/)                                    |
| OpenSUSE | 42.2    | [Stycznia 2018 r.](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| OpenSUSE | 42.1    | [Maja 2017 r.](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| Ubuntu   | 17.04   | [Stycznia 2018 r.](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 16.10   | [Lipca 2017 r.](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a>Uwagi dotyczące licencjonowania

Program PowerShell Core jest wydawane na mocy [Licencja MIT][].
W ramach niniejszej licencji, a w przypadku braku zgody płatnej pomocy technicznej, użytkownicy są ograniczone do [pomoc techniczna w społeczności][].
Za pomocą pomoc techniczna w społeczności firmy Microsoft nie udziela żadnych gwarancji czasu odpowiedzi lub poprawki.

## <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Pomocy technicznej dla programu PowerShell Core nie obejmuje inne moduły produktu, chyba że moduły jawnego zapewnienia obsługi programu PowerShell Core.
Na przykład za pomocą `ActiveDirectory` modułu, który jest dostarczany jako część systemu Windows Server jest to nieobsługiwany scenariusz.

Jednak może być zgodny w niektórych przypadkach moduły, które nie obsługują jawnie programu PowerShell Core.
Instalując [ `WindowsPSModulePath` ][] modułu programu Windows PowerShell można dołączyć `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.

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

[W wersji Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
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
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
