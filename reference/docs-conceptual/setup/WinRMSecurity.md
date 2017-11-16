---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: WinRMSecurity
ms.openlocfilehash: 65cf12466c9dc8fc8b77d79b0d63a6ae61e64d60
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="powershell-remoting-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń usługi zdalne środowiska PowerShell

Usługi zdalne środowiska PowerShell jest zalecanym sposobem zarządzania komputerami z systemem Windows. Usługi zdalne środowiska PowerShell jest domyślnie włączone w systemie Windows Server 2012 R2. W tym dokumencie opisano problemy z zabezpieczeniami, zalecenia i najlepsze rozwiązania w przypadku korzystania z usługi zdalne środowiska PowerShell.

## <a name="what-is-powershell-remoting"></a>Co to jest obsługę zdalną środowiska PowerShell?

Korzysta z komunikacji zdalnej programu PowerShell [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx), który jest przez firmę Microsoft implementacją [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protokołu, aby zezwolić użytkownikom na uruchamianie programu PowerShell poleceń na komputerach zdalnych. Można znaleźć więcej informacji o korzystaniu z usługi zdalne środowiska PowerShell w [uruchamiania poleceń zdalnych](https://technet.microsoft.com/en-us/library/dd819505.aspx).

Usługi zdalne środowiska PowerShell nie jest taka sama, jak za pomocą **ComputerName** parametru polecenia cmdlet, aby uruchomić go na komputerze zdalnym, który używa zdalnego wywoływania procedur (RPC), jako jego podstawowy protokół.

## <a name="powershell-remoting-default-settings"></a>Ustawienia domyślne obsługę zdalną środowiska PowerShell

Usługi zdalne środowiska PowerShell (i WinRM) nasłuchiwania następujące porty:

- HTTP: 5985
- HTTPS: 5986

Domyślnie usługi zdalne środowiska PowerShell tylko zezwala na połączenia z członkami grupy Administratorzy. Sesje będą uruchamiane w kontekście użytkownika, dzięki czemu wszystkie formanty dostępu do systemu operacyjnego stosowane do poszczególnych użytkowników i grup nadal stosuje się do nich nawiązaniu połączenia za pośrednictwem usługi zdalne środowiska PowerShell.

W sieciach prywatnych domyślne reguły zapory systemu Windows dla niego komunikację zdalną środowiska PowerShell akceptuje wszystkie połączenia. W sieciach publicznych domyślna reguła zapory systemu Windows umożliwia obsługę zdalną środowiska PowerShell połączenia tylko z tej samej podsieci. Należy jawnie zmienić tej reguły, aby otworzyć komunikacji zdalnej programu PowerShell do wszystkich połączeń w sieci publicznej.

>**Ostrzeżenie:** reguły zapory dla sieci publicznych mają na celu ochronę komputera przed atakami połączenie zewnętrzne mogą okazać się złośliwe. Należy zachować ostrożność podczas usuwania tej reguły.

## <a name="process-isolation"></a>Izolacja procesu

Korzysta z komunikacji zdalnej programu PowerShell [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) do komunikacji między komputerami. Usługa WinRM działa jako usługa na koncie Usługa sieciowa, a spowoduje utworzenie procesach izolowanych uruchomione jako konta użytkowników do hosta programu PowerShell wystąpień. Wystąpienie programu PowerShell uruchomione jako jeden użytkownik nie ma dostępu do procesu uruchomionego wystąpienia programu PowerShell jako inny użytkownik.

## <a name="event-logs-generated-by-powershell-remoting"></a>Dzienniki zdarzeń generowanych przez usługi zdalne środowiska PowerShell

FireEye udostępnił dobrej podsumowanie dzienniki zdarzeń i inne dowodów zabezpieczeń wygenerowane przez sesje komunikacji zdalnej programu PowerShell, dostępne pod adresem  
[Badanie środowiska PowerShell ataków](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Protokołów transportu i szyfrowania

Warto wziąć pod uwagę zabezpieczeń połączenia komunikacji zdalnej programu PowerShell z dwóch perspektyw: początkowe uwierzytelnianie i stałą łączność. 

Niezależnie od protokołu transportu używanego (HTTP lub HTTPS) usługi zdalne środowiska PowerShell zawsze szyfruje cała komunikacja po początkowego uwierzytelniania za pomocą klucza symetrycznego AES 256 sesji.
    
### <a name="initial-authentication"></a>Początkowe uwierzytelnianie

Uwierzytelnianie potwierdza tożsamość klienta do serwera — oraz w idealnym przypadku - serwera do klienta.
    
Gdy klient nawiąże połączenie z serwerem domeny przy użyciu nazwy komputera (np.: serwer01, lub server01.contoso.com), jest domyślnym protokołem uwierzytelniania [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx).
Kerberos gwarantuje tożsamość serwera i tożsamości użytkowników bez wysyłania dowolny rodzaj wielokrotnego poświadczenie.

Gdy klient łączy się z serwerem domeny przy użyciu jego adresu IP lub łączy się z serwerem grupy roboczej, uwierzytelnianie Kerberos nie jest możliwe. W takim przypadku obsługę zdalną środowiska PowerShell zależy od [protokół uwierzytelniania NTLM](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx). Protokół uwierzytelniania NTLM gwarantuje tożsamość użytkownika bez wysyłania dowolny rodzaj możliwe poświadczeń. Do potwierdzenia tożsamości użytkownika, protokół NTLM wymaga, że klient i serwer obliczeniowe klucza sesji z hasła bez kiedykolwiek wymiana samego hasła. Serwer zwykle nie zna hasło użytkownika, więc komunikuje się z kontrolerem domeny, które znać hasło użytkownika, a następnie oblicza klucza sesji dla serwera. 
      
Protokół NTLM, jednak gwarantuje tożsamość serwera. Podobnie jak w przypadku wszystkich protokołów, który jest używany do uwierzytelniania NTLM, osoba atakująca z dostępem do konta komputera komputer przyłączony do domeny może wywołać kontrolera domeny w celu obliczania klucza sesji uwierzytelniania NTLM i tym samym podszyć się pod serwer.

Uwierzytelnianie NTLM jest domyślnie wyłączona, ale może być dozwolony przez albo Konfigurowanie protokołu SSL na serwerze docelowym lub przez skonfigurowanie ustawienia WinRM TrustedHosts na komputerze klienckim.
    
#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Aby sprawdzić tożsamość serwera podczas połączenia oparte na protokole NTLM przy użyciu certyfikatów SSL

Ponieważ protokół uwierzytelniania NTLM nie Sprawdź tożsamość serwera docelowego (tylko że on już zna hasło), można skonfigurować serwery docelowe, które używają protokołu SSL dla komunikacji zdalnej programu PowerShell. Przypisanie certyfikatu SSL na serwerze docelowym (jeśli wystawiony przez urząd certyfikacji, któremu ufa również klient) umożliwia uwierzytelnianie oparte na protokole NTLM, który gwarantuje tożsamość serwera i tożsamości użytkowników.
    
#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorowanie błędów tożsamości serwera opartego na NTLM
      
W przypadku wdrażania certyfikatu SSL do serwera dla połączeń protokołu NTLM praktyce, może pominąć zwrócone błędy tożsamości przez dodanie serwera do usługi WinRM **TrustedHosts** listy. Należy pamiętać, że dodanie nazwę serwera do listy TrustedHosts nie należy traktować jako dowolnej formy instrukcji wiarygodności hostów, same — jak protokół uwierzytelniania NTLM nie może zagwarantować, że w rzeczywistości łączysz na hoście są ZAMIERZAJĄC nawiązać połączenie.
Zamiast tego należy rozważyć ustawienie TrustedHosts listy hostów, dla których chcesz pominąć błędów wygenerowanych przez nie można zweryfikować tożsamości serwera.
    
    
### <a name="ongoing-communication"></a>Stałe komunikacji

Po zakończeniu uwierzytelniania początkowego [protokołu komunikacji zdalnej programu PowerShell](https://msdn.microsoft.com/en-us/library/dd357801.aspx) szyfruje wszystkie stałą łączność z sesji klucza symetrycznego AES 256.  


## <a name="making-the-second-hop"></a>Co drugi przeskok

Domyślnie usługi zdalne środowiska PowerShell użyje do uwierzytelniania NTLM lub Kerberos (jeśli jest dostępna). Oba te protokoły uwierzytelniania komputer zdalny bez wysyłania poświadczeń do niego.
Jest to najbezpieczniejszy sposób uwierzytelniania, ale ponieważ komputer zdalny nie ma poświadczeń użytkownika, nie ma dostępu do innych komputerów i usług w imieniu użytkownika. Jest to nazywane "drugi problem przeskoku".

Istnieje kilka sposobów, aby uniknąć tego problemu. Opisy tych metod i zalet i wad każdej zobacz [co drugi przeskok w komunikacji zdalnej programu PowerShell](PS-remoting-second-hop.md).










