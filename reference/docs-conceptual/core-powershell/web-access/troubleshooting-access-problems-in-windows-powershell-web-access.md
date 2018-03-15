---
ms.date: 2017-08-23
keywords: polecenia cmdlet programu PowerShell
title: "Rozwiązywanie problemów z dostępem w programie windows powershell web access"
ms.openlocfilehash: 6e51df3f4c6ac196c855ad918a91394d02c7d75e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Rozwiązywanie problemów z programem Windows PowerShell Web Access

Aktualizacja: 24 czerwiec 2013 (zaktualizowany 23 sierpnia 2017 r.)

Dotyczy: Windows Server 2012 R2, Windows Server 2012

W poniższych sekcjach zidentyfikować niektóre typowe problemy podczas próby nawiązania połączenia z komputerem zdalnym za pomocą programu Windows PowerShell Web Access i zawiera sugestie dotyczące rozwiązywania problemów.

## <a name="sign-in-failure"></a>Błąd logowania

Błąd logowania może wystąpić z następujących powodów.

- Nie istnieje reguła autoryzacji umożliwiająca użytkownikowi dostęp do komputera ani konfiguracja określonej sesji na komputerze zdalnym.

  Zabezpieczenia programu Windows PowerShell Web Access jest restrykcyjna; Użytkownicy muszą otrzymać jawny dostęp do komputerów zdalnych przy użyciu reguł autoryzacji.

  Aby uzyskać więcej informacji na temat tworzenia reguł autoryzacji, zobacz [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Użytkownik nie ma autoryzowanego dostępu do komputera docelowego. Jest to określane za pomocą list kontroli dostępu.

  Aby uzyskać więcej informacji, zobacz [rejestrowania się w programie Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), lub Blog zespołu programu Windows PowerShell.

- Zdalne zarządzanie programu Windows PowerShell może nie być włączone na komputerze docelowym.

  Sprawdź, czy zdalne zarządzanie jest włączone na komputerze, z którym użytkownik próbuje się połączyć.

  Aby uzyskać więcej informacji, zobacz [jak skonfigurować komputer dla niego komunikację zdalną](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Wewnętrzny błąd serwera

Gdy użytkownicy próbują zalogować się do programu Windows PowerShell Web Access w oknie programu Internet Explorer, są one wyświetlane **wewnętrzny błąd serwera** strony, lub *programu Internet Explorer* przestaje odpowiadać.

Ten problem dotyczy programu Internet Explorer.

### <a name="possible-cause"></a>Możliwa przyczyna

Taka sytuacja może wystąpić w przypadku użytkowników, którzy zalogowali się przy użyciu nazwy domeny zawierającej znaki w języku chińskim, lub jeśli nazwa serwera bramy zawiera co najmniej jeden znak w języku chińskim.

#### <a name="workaround"></a>Obejście problemu

1. [Zainstaluj i uruchom program Internet Explorer 10](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Zmień programu Internet Explorer **tryb dokumentu** ustawienie *IE10* standardów.
   1. Naciśnij klawisz **F12** aby otworzyć konsolę narzędzia deweloperskie
   1. W programie Internet Explorer 10 kliknij **tryb przeglądarki**, a następnie wybierz *programu Internet Explorer 10*.
   1. Kliknij przycisk **tryb dokumentu**, a następnie kliknij przycisk *IE10* standardów.
   1. Naciśnij klawisz **F12** ponownie, aby zamknąć konsolę narzędzia deweloperskie.
1. Wyłącz konfigurację automatyczną serwera proxy w programie Internet Explorer 10.
   1. Kliknij przycisk **narzędzia**, a następnie kliknij przycisk **Opcje internetowe**.
   1. W **Opcje internetowe** na okna dialogowego **połączeń** , kliknij pozycję **ustawienia sieci LAN**.
   1. Wyczyść **Automatycznie wykryj ustawienia** pole wyboru. Kliknij przycisk **OK**, a następnie kliknij przycisk **OK** ponownie, aby zamknąć *Opcje internetowe* okno dialogowe.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Nie można nawiązać połączenia ze zdalnym komputerem grupy roboczej

Jeśli komputer docelowy jest członkiem grupy roboczej, aby podać nazwę użytkownika i zaloguj się do komputera należy użyć następującej składni: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Nie można odnaleźć narzędzi do zarządzania serwerem sieci Web (IIS), nawet jeśli rola została zainstalowana

Po zainstalowaniu programu Windows PowerShell Web Access za pomocą `Install-WindowsFeature` polecenia cmdlet, o ile nie są zainstalowane narzędzia zarządzania `-IncludeManagementTools` do polecenia cmdlet zostanie dodany parametr.

Na przykład zobacz [do zainstalowania programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Umożliwia dodanie konsoli Menedżer usług IIS i zarządzania usługami IIS w innych narzędzi, potrzebnych, przez wybranie narzędzi w **Kreatora dodawania ról i funkcji** sesji, która jest skierowana na serwer bramy.
Dodaj role i funkcje kreatora jest otwierany z Menedżera serwera.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Witryny sieci Web Windows PowerShell Web Access jest niedostępny

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (nazywana konfiguracją IE ESC), możesz dodać witrynę sieci Web Windows PowerShell Web Access do listy zaufanych witryn.

Jest mniej zalecane podejście, ze względu na zagrożenia bezpieczeństwa, aby wyłączyć konfigurację IE ESC.
Konfigurację IE ESC można wyłączyć na kafelku właściwości na stronie serwera lokalnego w Menedżerze serwera.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Wystąpił błąd autoryzacji. Upewnij się, że masz uprawnienia do nawiązania połączenia z komputerem docelowym.

Powyżej komunikat o błędzie jest wyświetlany podczas próby nawiązania połączenia, gdy serwer bramy jest komputerem docelowym oraz należy w grupie roboczej.

Gdy serwer bramy jest również serwerem docelowym i jest w grupie roboczej, określ nazwę użytkownika, nazwę komputera i nazwę grupy użytkowników.
Nie należy używać pojedynczego znaku kropki (.) przez samego siebie do reprezentowania nazwy komputera.

### <a name="scenarios-and-proper-values"></a>Scenariusze i odpowiednie wartości

#### <a name="all-cases"></a>Wszystkich przypadkach

Parametr | Wartość
-- | --
UserName | Serwer\_nazwa\\użytkownika\_nazwy<br/>Localhost\\użytkownika\_nazwy<br/>. \\użytkownika\_nazwy
Grupa_użytkowników | Serwer\_nazwa\\użytkownika\_grupy<br/>Localhost\\użytkownika\_grupy<br/>. \\użytkownika\_grupy
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\komputera\_grupy<br/>. \\komputera\_grupy

#### <a name="gateway-server-is-in-a-domain"></a>Serwer bramy znajduje się w domenie

Parametr | Wartość
-- | --
ComputerName | W pełni kwalifikowana nazwa serwera bramy lub Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Serwer bramy znajduje się w grupie roboczej

Parametr | Wartość
-- | --
ComputerName | Nazwa serwera

### <a name="gateway-credentials"></a>Poświadczeń bramy

Zaloguj się do serwera bramy jako komputera docelowego przy użyciu poświadczeń sformatowanych w jeden z następujących sposobów.

- Serwer\_nazwa\\użytkownika\_nazwy
- Localhost\\użytkownika\_nazwy
- . \\użytkownika\_nazwy

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Identyfikator zabezpieczeń (SID) jest wyświetlany w regule autoryzacji

Identyfikator zabezpieczeń (SID) jest wyświetlany w regule autoryzacji zamiast składni użytkownika\_nazwy i komputera\_nazwy.

Reguła nie jest już prawidłowa lub zapytanie usług domenowych Active Directory nie powiodło się.
Zazwyczaj reguły autoryzacji nie jest prawidłowa w sytuacji, gdy serwer bramy należał do grupy roboczej, ale później został przyłączony do domeny

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Nie można zarejestrować się przy użyciu reguły jako adres IPv6 z domeną

Nie można zalogować się na komputerze docelowym, który został określony w regułach autoryzacji jako adres IPv6 z domeną.

Reguły autoryzacji nie obsługują adresów IPv6 w formie nazwy domeny.

Aby określić komputer docelowy przy użyciu adresu IPv6, należy użyć oryginalnego adresu IPv6 (zawierającego dwukropki) w regule autoryzacji.
Zarówno domeny, jak i numeryczne adresy IPv6 (zawierające dwukropki) są obsługiwane jako nazwy komputera docelowego na stronie logowania programu Windows PowerShell Web Access, ale nie w ramach reguł autoryzacji. 

Aby uzyskać więcej informacji na temat adresów IPv6, zobacz [jak działa protokół IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Zobacz też

- [Reguły autoryzacji i funkcje zabezpieczeń programu Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Za pomocą konsoli programu PowerShell Windows opartych na sieci Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
