---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320554"
---
# <a name="powershell-remoting-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell

Komunikacja zdalna programu PowerShell jest zalecanym sposobem zarządzania systemami Windows. Komunikacja zdalna programu PowerShell jest włączona domyślnie w systemie Windows Server 2012 R2. W tym dokumencie opisano zagadnienia dotyczące zabezpieczeń, zalecenia i najlepsze rozwiązania w przypadku korzystania z komunikacji zdalnej programu PowerShell.

## <a name="what-is-powershell-remoting"></a>Co to jest komunikacji zdalnej programu PowerShell?

Korzysta z komunikacji zdalnej programu PowerShell [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), który jest implementacja firmy Microsoft [Web Services for Management (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protokołu, aby zezwolić użytkownikom na uruchamianie programu PowerShell polecenia na komputerach zdalnych. Można znaleźć więcej informacji na temat przy użyciu komunikacji zdalnej programu PowerShell w [uruchamianie poleceń zdalnych](https://technet.microsoft.com/library/dd819505.aspx).

Komunikacja zdalna programu PowerShell nie jest taka sama jak za pomocą **ComputerName** parametru polecenia cmdlet, aby uruchomić go na komputerze zdalnym, który używa zdalnego wywołania procedury (RPC) jako jego podstawowy protokół.

## <a name="powershell-remoting-default-settings"></a>Ustawienia domyślne komunikacji zdalnej programu PowerShell

Komunikacja zdalna programu PowerShell (i usługi WinRM) nasłuchiwania następujące porty:

- HTTP: 5985
- HTTPS: 5986

Domyślnie Komunikacja zdalna programu PowerShell tylko zezwala na połączenia z członkowie grupy Administratorzy. Sesje na rynek w kontekście użytkownika, dzięki czemu wszystkie kontroli dostępu systemu operacyjnego stosowane do poszczególnych użytkowników i grupy nadal stosować wobec nich po nawiązaniu połączenia za pośrednictwem komunikacji zdalnej programu PowerShell.

W sieciach prywatnych domyślne reguły zapory Windows dla komunikacji zdalnej programu PowerShell akceptuje wszystkie połączenia. W sieciach publicznych domyślną regułę zapory Windows umożliwia komunikacji zdalnej programu PowerShell na połączenia tylko z tej samej podsieci. Musisz jawnie zmiany tej reguły, aby otworzyć komunikacji zdalnej programu PowerShell do wszystkich połączeń w sieci publicznej.

>**Ostrzeżenie:** reguły zapory dla sieci publicznych jest przeznaczona do ochrony komputera przed atakami potencjalnie złośliwych połączenia zewnętrznego. Usunięcie tej reguły, należy zachować ostrożność.

## <a name="process-isolation"></a>Izolacja procesu

Korzysta z komunikacji zdalnej programu PowerShell [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) do komunikacji między komputerami.
Usługa WinRM działa jako usługa w ramach konta Usługa sieciowa i spowoduje utworzenie procesach izolowanych, uruchomione jako konta użytkowników do wystąpień programu PowerShell hosta. Wystąpienie programu PowerShell działających jako jeden użytkownik nie ma dostępu do procesu uruchomionego wystąpienia programu PowerShell jako inny użytkownik.

## <a name="event-logs-generated-by-powershell-remoting"></a>Dzienniki zdarzeń generowane przez komunikacji zdalnej programu PowerShell

FireEye udostępnił dobre podsumowanie dzienników zdarzeń i inne dokumenty zabezpieczeń generowane przez sesje komunikacji zdalnej programu PowerShell, dostępne pod adresem [badania ataków PowerShell](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Szyfrowanie i mechanizm transportu protokołów

Warto wziąć pod uwagę zabezpieczeń połączenia komunikacji zdalnej programu PowerShell z dwóch perspektyw: początkowe uwierzytelnianie i utrzymują stałą łączność.

Komunikacja zdalna programu PowerShell niezależnie od tego, transport protokół (HTTP lub HTTPS), jest zawsze szyfruje cała komunikacja po początkowego uwierzytelniania przy użyciu klucza symetrycznego AES-256 sesji.

### <a name="initial-authentication"></a>Początkowe uwierzytelnianie

Uwierzytelnianie potwierdza tożsamość klienta do serwera —, a najlepiej — serwera do klienta.

Gdy klient nawiąże połączenie do serwera domeny, przy użyciu nazwy komputera (czyli: serwer01, lub server01.contoso.com), domyślnym protokołem uwierzytelniania jest [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Protokół Kerberos gwarantuje tożsamość użytkownika i tożsamości serwera bez wysyłania dowolny rodzaj do ponownego użycia poświadczeń.

Gdy klient łączy się z serwerem domeny, przy użyciu jego adresu IP lub nawiązanie połączenia z serwerem grupy roboczej, uwierzytelnianie Kerberos nie jest możliwe. W takim przypadku komunikacji zdalnej programu PowerShell opiera się na [protokół uwierzytelniania NTLM](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). Protokół uwierzytelniania NTLM gwarantuje tożsamość użytkownika, bez wysyłania dowolny rodzaj delegowalne poświadczeń. Potwierdzenie tożsamości użytkownika, protokół NTLM wymaga, że klient i serwer obliczenia klucza sesji z hasła użytkownika bez kiedykolwiek wymiana samego hasła. Serwer zazwyczaj nie zna hasło użytkownika, więc komunikuje się ona z kontrolerem domeny, którego znasz hasło użytkownika, a następnie oblicza klucza sesji dla serwera.

Protokół NTLM, jednak gwarantuje tożsamość serwera. Podobnie jak w przypadku wszystkich protokołów, który jest używany do uwierzytelniania NTLM, osoba nieuprawniona uzyska dostęp do komputera przyłączonego do domeny, konto komputera może wywołać kontrolera domeny w celu obliczenia klucza sesji protokołu NTLM i tym samym personifikacji serwera.

Uwierzytelnianie NTLM jest domyślnie wyłączona, ale może być dozwolony, przez albo Konfigurowanie protokołu SSL na serwerze docelowym lub przez skonfigurowanie ustawienia TrustedHosts usługi WinRM na komputerze klienckim.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Korzystania z certyfikatów SSL w celu zweryfikowania tożsamości serwera podczas połączeń opartych na NTLM

Ponieważ protokół uwierzytelniania NTLM nie mogą zapewnić tożsamości na serwerze docelowym (tylko on już zna hasło), można skonfigurować serwery docelowe, które używają protokołu SSL dla komunikacji zdalnej programu PowerShell. Przypisywanie certyfikatu SSL na serwerze docelowym (jeśli jest wystawiony przez urząd certyfikacji, który ma także zaufany) umożliwia uwierzytelnianie NTLM, który gwarantuje tożsamość użytkownika i tożsamości serwera.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorowanie błędów tożsamości oparte na NTLM serwera

W przypadku wdrażania certyfikatu SSL na serwerze sieci dla połączeń protokołu NTLM niewykonalne, może pominąć wynikowe błędy tożsamości przez dodanie serwera do usługi WinRM **TrustedHosts** listy. Należy pamiętać, że dodanie nazwę serwera do listy TrustedHosts nie należy w jakiejkolwiek formy instrukcji wiarygodności hosty, samodzielnie — jak protokół uwierzytelniania NTLM nie gwarantuje, że w rzeczywistości łączysz na hoście są Pomyślny przebieg operacji nawiązać połączenie.
Zamiast tego należy rozważyć ustawienie TrustedHosts listy hostów, dla których chcesz pominąć błędów generowanych przez nie będzie w stanie zweryfikować tożsamość serwera.


### <a name="ongoing-communication"></a>Trwającą komunikacji

Po zakończeniu początkowego uwierzytelniania [protokołu komunikacji zdalnej programu PowerShell](https://msdn.microsoft.com/library/dd357801.aspx) szyfruje wszystkie trwające komunikacji przy użyciu klucza symetrycznego AES-256 sesji.


## <a name="making-the-second-hop"></a>Wykonywanie drugiego przeskoku

Domyślnie do uwierzytelniania komunikacji zdalnej programu PowerShell używa protokołu Kerberos (jeśli jest dostępny) lub NTLM. Obu tych protokołów uwierzytelniania do maszyny zdalnej bez wysyłania poświadczeń do niego.
Jest to najbezpieczniejsza metoda uwierzytelniania, ale ponieważ Maszyna zdalna nie ma poświadczeń użytkownika, nie może uzyskać dostępu innych komputerów i usług w imieniu użytkownika.
Jest to nazywane "problem drugiego przeskoku".

Istnieje kilka sposobów, aby uniknąć tego problemu. Opisy tych metod i zalet i wad każdego z nich, zobacz [wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell](PS-remoting-second-hop.md).