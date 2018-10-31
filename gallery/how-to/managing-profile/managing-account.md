---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Ustawienia konta galerii programu PowerShell
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002790"
---
# <a name="powershell-gallery-account-settings"></a>Ustawienia konta galerii programu PowerShell

Twoje konto galerii programu PowerShell jest widoczna publicznie nazwę, która jest połączona z tożsamością. Tej tożsamości jest albo identyfikator firmy Microsoft, takie jak `user@hotmail.com` lub `user@outlook.com`, lub konta usługi Azure Active Directory (AAD).

Galeria programu PowerShell udostępnia następujące ustawienia konta:

- Konto e-mail skojarzony z Twoim kontem galerii programu PowerShell
- Opcje powiadomień e-mail wysłanych z galerii programu PowerShell
- Konto użytkownika skojarzone z Twoim kontem galerii programu PowerShell
- Obraz skojarzony z Twoim kontem galerii programu PowerShell

## <a name="email-address"></a>Adres e-mail

Adres e-mail jest miejscem docelowym dla powiadomień o galerii programu PowerShell. Nie ma dopasowania konta logowania. Można użyć dowolnego konta poczty e-mail, do których masz dostęp do. Twój adres e-mail znajduje się nigdy bezpośrednio w galerii programu PowerShell do innych użytkowników.

![Zmiana adresu e-mail](../../Images/PSGallery_AcccountEmailAddress.png)

Po wprowadzeniu nowego adresu e-mail, galerii programu PowerShell wysyła wiadomość e-mail weryfikacji do tego adresu. Weryfikacji wiadomości e-mail zawiera link do galerii programu PowerShell w celu ukończenia procesu zmiany. Do czasu ukończenia procesu weryfikacji wszystkie powiadomienia są wysyłane do poprzedniego adresu.

## <a name="email-notifications"></a>Powiadomienia e-mail

Galeria programu PowerShell udostępnia następujące opcje powiadomień:

- Użytkownicy mogą kontaktować się ze mną za pośrednictwem galerii programu PowerShell
- Powiadom mnie, gdy pakiet zostanie przypisany do galerii programu PowerShell przy użyciu mojego konta

![Zmiana adresu e-mail](../../Images/PSGallery_AccountEmailOptions.png)

Jak wspomniano, na stronie, nie można wyłączyć powiadomienia o krytycznym znaczeniu z galerii programu PowerShell.
Należą do nich:

- Powiadomień o zabezpieczeniach
- Konto zarządzania powiadomienia administratorów o galerii programu PowerShell
- Powiadomienia o testy uruchamiane przez galerii programu PowerShell dla przesyłania wprowadzone przez użytkownika

## <a name="change-your-login-account"></a>Zmienianie konta logowania

Aby zmienić konto logowania, muszą być podpisane przy użyciu bieżącego konta. Wykonaj następujące kroki, aby dokonać zmiany.

![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountSettings.png)

1. Kliknij pozycję **zmienić konto**. Okno podręczne wyjaśniono, że zmiana konta logowania ma zastosowanie do wszystkich używa tego konta w galerii programu PowerShell. Zapoznaj się z informacjami, a następnie kliknij przycisk **OK** aby kontynuować.

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-1.png)

2. Następnie monit o zalogowanie się przy użyciu _nowe konto_.

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-2.png)

3. Po kliknięciu **dalej**, zostanie wyświetlony komunikat, że użytkownik jest zalogowany przy użyciu bieżącego konta.
   Kliknij przycisk **Zaloguj się poza i zaloguj się przy użyciu innego konta**.

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-3.png)

4. Wprowadź hasło dla nowego konta. Po wprowadzeniu hasła, nastąpi powrót do strony ustawień konta przedstawiający, że konto logowania został zaktualizowany.


## <a name="enable-two-factor-authentication-2fa"></a>Włączanie uwierzytelniania dwuskładnikowego (2FA)

Uwierzytelnianie dwuetapowe jest zalecana dla wszystkich użytkowników, którzy ręcznie publikować w galerii programu PowerShell. Aby włączyć uwierzytelnianie dwuskładnikowe, konto logowania musi mieć co najmniej dwie formy uwierzytelniania zarejestrowany. Jeden to hasło i mogą być inne formy:

- Numer telefonu, który może odbierać wiadomości SMS
- W przypadku aplikacji wystawcy uwierzytelnienia zarejestrowanego takich jak Microsoft Authenticator na telefonie komórkowym

Te rodzaje uwierzytelniania muszą być skonfigurowane w danych konta usługi AAD lub w ustawieniach zabezpieczeń konto Identyfikatora Microsoft.

Po włączeniu funkcji 2FA, są wymagane do uwierzytelniania za pomocą skonfigurowanego metod uwierzytelniania, za każdym razem, gdy zarejestrujesz się w galerii programu PowerShell.

> [!IMPORTANT]
> Włączanie uwierzytelniania dwuskładnikowego dla tej witryny galerii programu PowerShell nie wymaga włączenia funkcji 2FA, dla wszystkich zastosowań konta logowania. Aby uzyskać więcej informacji, zobacz [o weryfikacji dwuetapowej](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Zmień obraz profilu

Galeria programu PowerShell, zależy od Gravatar do przechowywania i wyświetlania obrazu skojarzonego z danym profilem. Aby zaktualizować swój obraz profilu, odwiedź stronę [Gravatar.com](http://www.gravatar.com/).
