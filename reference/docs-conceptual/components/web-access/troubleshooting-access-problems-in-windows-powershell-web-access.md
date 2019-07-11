---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Rozwiązywanie problemów z dostępem w programie windows powershell web access
ms.openlocfilehash: 66e913504cf0c34f8d9ab18b088fb06173aca24c
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733867"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Rozwiązywanie problemów z programem Windows PowerShell Web Access

Zaktualizowano: Czerwiec 24 2013 (zaktualizowany 23 sierpnia 2017 r.)

Dotyczy: Windows Server 2012 R2, Windows Server 2012

W poniższych sekcjach zidentyfikować niektóre typowe problemy podczas próby połączenia z komputerem zdalnym za pomocą programu Windows PowerShell Web Access i zawiera sugestie dotyczące sposobu rozwiązania tych problemów.

## <a name="sign-in-failure"></a>Błąd logowania

Błąd logowania może wystąpić z następujących powodów.

- Nie istnieje reguła autoryzacji umożliwiająca użytkownikowi dostęp do komputera ani konfiguracja określonej sesji na komputerze zdalnym.

  Zabezpieczenia programu Windows PowerShell Web Access jest restrykcyjna; Użytkownicy muszą otrzymać jawny dostęp do komputerów zdalnych przy użyciu reguł autoryzacji.

  Aby uzyskać więcej informacji na temat tworzenia reguł autoryzacji, zobacz [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Użytkownik nie ma autoryzowanego dostępu do komputera docelowego. Jest to określane za pomocą list kontroli dostępu.

  Aby uzyskać więcej informacji, zobacz [logowanie do programu Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), lub w blogu zespołu programu Windows PowerShell.

- Zdalne zarządzanie programu Windows PowerShell może nie być włączona na komputerze docelowym.

  Sprawdź, czy zdalne zarządzanie jest włączone na komputerze, do której użytkownik próbuje nawiązać połączenie.

  Aby uzyskać więcej informacji, zobacz [jak skonfigurować komputer dla niego komunikację zdalną](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Wewnętrzny błąd serwera

Gdy użytkownicy próbują zalogować się do programu Windows PowerShell Web Access w oknie programu Internet Explorer, są one wyświetlane **wewnętrzny błąd serwera** strony, lub *programu Internet Explorer* przestaje odpowiadać.

Ten problem dotyczy programu Internet Explorer.

### <a name="possible-cause"></a>Możliwa przyczyna

Taka sytuacja może wystąpić w przypadku użytkowników, którzy zalogowali się przy użyciu nazwy domeny zawierającej znaki w języku chińskim, lub jeśli nazwa serwera bramy zawiera co najmniej jeden znak w języku chińskim.

#### <a name="workaround"></a>Obejście

1. [Zainstaluj i uruchom program Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Zmień program Internet Explorer **tryb dokumentu** ustawienie *IE10* standardy.
   1. Naciśnij klawisz **F12** aby otworzyć konsolę narzędzia deweloperskie
   1. W programie Internet Explorer 10 kliknij **tryb przeglądarki**, a następnie wybierz pozycję *programu Internet Explorer 10*.
   1. Kliknij przycisk **tryb dokumentu**, a następnie kliknij przycisk *IE10* standardy.
   1. Naciśnij klawisz **F12** ponownie, aby zamknąć konsolę narzędzia deweloperskie.
1. Wyłącz konfigurację automatyczną serwera proxy w programie Internet Explorer 10.
   1. Kliknij przycisk **narzędzia**, a następnie kliknij przycisk **Opcje internetowe**.
   1. W **Opcje internetowe** dialogowym **połączeń** kliknij pozycję **ustawienia sieci LAN**.
   1. Wyczyść **Automatycznie wykryj ustawienia** pole wyboru. Kliknij przycisk **OK**, a następnie kliknij przycisk **OK** ponownie, aby zamknąć *Opcje internetowe* okno dialogowe.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Nie można nawiązać połączenia ze zdalnym komputerem grupy roboczej

Jeśli komputer docelowy jest członkiem grupy roboczej, użyj następującej składni, aby podać nazwę użytkownika i zalogować się do komputera: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Nie można odnaleźć narzędzi do zarządzania serwerem sieci Web (IIS), nawet jeśli rola została zainstalowana

Jeśli został zainstalowany przy użyciu programu Windows PowerShell Web Access `Install-WindowsFeature` polecenia cmdlet zarządzania narzędzia nie są zainstalowane, chyba że `-IncludeManagementTools` parametr jest dodawany do polecenia cmdlet.

Aby uzyskać przykład, zobacz [do zainstalowania programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Możesz dodawać konsoli Menedżera usług IIS i narzędzi do zarządzania innych usług IIS należy, przez wybranie narzędzi w **Kreatora dodawania ról i funkcji** sesji, która jest skierowana na serwer bramy.
Dodaj role i funkcje kreatora jest otwierany z w Menedżerze serwera.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Witryny sieci Web programu Windows PowerShell Web Access jest niedostępny

Po włączeniu konfiguracji zwiększonych zabezpieczeń programu Internet Explorer (IE ESC) witryny sieci Web programu Windows PowerShell Web Access można dodać do listy zaufanych witryn.

Mniej, ze względu na zagrożenia bezpieczeństwa, zaleca się wyłączyć konfigurację IE ESC.
Konfigurację IE ESC można wyłączyć na kafelku właściwości na stronie serwera lokalnego w Menedżerze serwera.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Wystąpił błąd autoryzacji. Upewnij się, że masz uprawnienia do nawiązania połączenia z komputerem docelowym.

Powyższe komunikat o błędzie jest wyświetlany podczas próby nawiązania połączenia, gdy serwer bramy jest komputerem docelowym i jest również do grupy roboczej.

Gdy serwer bramy jest również serwerem docelowym i jest w grupie roboczej, określ nazwę użytkownika, nazwę komputera i nazwę grupy użytkowników.
Nie należy używać pojedynczego znaku kropki (.) przez siebie do reprezentowania nazwy komputera.

### <a name="scenarios-and-proper-values"></a>Scenariusze i odpowiednimi wartościami

#### <a name="all-cases"></a>Wszystkie przypadki

Parametr | Wartość
-- | --
UserName | Serwer\_nazwa\\użytkownika\_nazwy<br/>Localhost\\user\_name<br/>. \\użytkownika\_nazwy
UserGroup | Serwer\_nazwa\\użytkownika\_grupy<br/>Localhost\\user\_group<br/>. \\użytkownika\_grupy
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\computer\_group<br/>. \\komputera\_grupy

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
- Localhost\\user\_name
- . \\użytkownika\_nazwy

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Identyfikator zabezpieczeń (SID) jest wyświetlana w regule autoryzacji

Identyfikator zabezpieczeń (SID) jest wyświetlana w regule autoryzacji zamiast składni użytkownika\_nazwa, komputer\_nazwy.

Reguła nie jest już prawidłowa lub zapytanie usług Active Directory Domain Services nie powiodło się.
Zazwyczaj reguły autoryzacji nie jest prawidłowa w sytuacji, gdy serwer bramy należał do grupy roboczej, ale później został przyłączony do domeny

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Nie można zarejestrować się przy użyciu reguły jako adres IPv6 z domeną

Nie można zalogować się na komputerze docelowym, który został określony w regułach autoryzacji jako adres IPv6 z domeną.

Reguły autoryzacji nie obsługują adresów IPv6 w formie nazwy domeny.

Aby określić komputer docelowy przy użyciu adresu IPv6, należy użyć oryginalnego adresu IPv6 (zawierającego dwukropki) w regule autoryzacji.
Zarówno domeny, jak i adresy IPv6 wartości liczbowych (zawierające dwukropki) są obsługiwane jako nazwy komputera docelowego, na stronie logowania programu Windows PowerShell Web Access, ale nie w ramach reguł autoryzacji.

Aby uzyskać więcej informacji na temat adresów IPv6, zobacz [jak działa protokół IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Zobacz też

- [Reguły autoryzacji i funkcje zabezpieczeń programu Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Za pomocą konsoli programu PowerShell Windows opartej na sieci Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
