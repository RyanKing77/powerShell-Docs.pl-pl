---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Ustawienia konta galerii programu PowerShell
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687426"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="346ee-103">Ustawienia konta galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="346ee-104">Twoje konto galerii programu PowerShell jest widoczna publicznie nazwę, która jest połączona z tożsamością.</span><span class="sxs-lookup"><span data-stu-id="346ee-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="346ee-105">Tej tożsamości jest albo identyfikator firmy Microsoft, takie jak `user@hotmail.com` lub `user@outlook.com`, lub konta usługi Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="346ee-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="346ee-106">Galeria programu PowerShell udostępnia następujące ustawienia konta:</span><span class="sxs-lookup"><span data-stu-id="346ee-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="346ee-107">Konto e-mail skojarzony z Twoim kontem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="346ee-108">Opcje powiadomień e-mail wysłanych z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="346ee-109">Konto użytkownika skojarzone z Twoim kontem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="346ee-110">Obraz skojarzony z Twoim kontem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="346ee-111">Adres e-mail</span><span class="sxs-lookup"><span data-stu-id="346ee-111">Email address</span></span>

<span data-ttu-id="346ee-112">Adres e-mail jest miejscem docelowym dla powiadomień o galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="346ee-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="346ee-113">Nie ma dopasowania konta logowania.</span><span class="sxs-lookup"><span data-stu-id="346ee-113">It does not have to match the login account.</span></span> <span data-ttu-id="346ee-114">Można użyć dowolnego konta poczty e-mail, do których masz dostęp do.</span><span class="sxs-lookup"><span data-stu-id="346ee-114">You may use any email account you have access to.</span></span> <span data-ttu-id="346ee-115">Twój adres e-mail znajduje się nigdy bezpośrednio w galerii programu PowerShell do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="346ee-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Zmiana adresu e-mail](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="346ee-117">Po wprowadzeniu nowego adresu e-mail, galerii programu PowerShell wysyła wiadomość e-mail weryfikacji do tego adresu.</span><span class="sxs-lookup"><span data-stu-id="346ee-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="346ee-118">Weryfikacji wiadomości e-mail zawiera link do galerii programu PowerShell w celu ukończenia procesu zmiany.</span><span class="sxs-lookup"><span data-stu-id="346ee-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="346ee-119">Do czasu ukończenia procesu weryfikacji wszystkie powiadomienia są wysyłane do poprzedniego adresu.</span><span class="sxs-lookup"><span data-stu-id="346ee-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="346ee-120">Powiadomienia e-mail</span><span class="sxs-lookup"><span data-stu-id="346ee-120">Email notifications</span></span>

<span data-ttu-id="346ee-121">Galeria programu PowerShell udostępnia następujące opcje powiadomień:</span><span class="sxs-lookup"><span data-stu-id="346ee-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="346ee-122">Użytkownicy mogą kontaktować się ze mną za pośrednictwem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="346ee-123">Powiadom mnie, gdy pakiet zostanie przypisany do galerii programu PowerShell przy użyciu mojego konta</span><span class="sxs-lookup"><span data-stu-id="346ee-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Zmiana adresu e-mail](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="346ee-125">Jak wspomniano, na stronie, nie można wyłączyć powiadomienia o krytycznym znaczeniu z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="346ee-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="346ee-126">Należą do nich:</span><span class="sxs-lookup"><span data-stu-id="346ee-126">These include:</span></span>

- <span data-ttu-id="346ee-127">Powiadomień o zabezpieczeniach</span><span class="sxs-lookup"><span data-stu-id="346ee-127">Security notifications</span></span>
- <span data-ttu-id="346ee-128">Konto zarządzania powiadomienia administratorów o galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="346ee-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="346ee-129">Powiadomienia o testy uruchamiane przez galerii programu PowerShell dla przesyłania wprowadzone przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="346ee-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="346ee-130">Zmienianie konta logowania</span><span class="sxs-lookup"><span data-stu-id="346ee-130">Change your login account</span></span>

<span data-ttu-id="346ee-131">Aby zmienić konto logowania, muszą być podpisane przy użyciu bieżącego konta.</span><span class="sxs-lookup"><span data-stu-id="346ee-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="346ee-132">Wykonaj następujące kroki, aby dokonać zmiany.</span><span class="sxs-lookup"><span data-stu-id="346ee-132">Use the following steps to complete the change.</span></span>

![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="346ee-134">Kliknij pozycję **zmienić konto**.</span><span class="sxs-lookup"><span data-stu-id="346ee-134">Click on **Change Account**.</span></span> <span data-ttu-id="346ee-135">Okno podręczne wyjaśniono, że zmiana konta logowania ma zastosowanie do wszystkich używa tego konta w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="346ee-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="346ee-136">Zapoznaj się z informacjami, a następnie kliknij przycisk **OK** aby kontynuować.</span><span class="sxs-lookup"><span data-stu-id="346ee-136">Review the information, then click **OK** to continue.</span></span>

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="346ee-138">Następnie monit o zalogowanie się przy użyciu _nowe konto_.</span><span class="sxs-lookup"><span data-stu-id="346ee-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="346ee-140">Po kliknięciu **dalej**, zostanie wyświetlony komunikat, że użytkownik jest zalogowany przy użyciu bieżącego konta.</span><span class="sxs-lookup"><span data-stu-id="346ee-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="346ee-141">Kliknij przycisk **Zaloguj się poza i zaloguj się przy użyciu innego konta**.</span><span class="sxs-lookup"><span data-stu-id="346ee-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Ustawienia konta logowania](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="346ee-143">Wprowadź hasło dla nowego konta.</span><span class="sxs-lookup"><span data-stu-id="346ee-143">Enter the password of the new account.</span></span> <span data-ttu-id="346ee-144">Po wprowadzeniu hasła, nastąpi powrót do strony ustawień konta przedstawiający, że konto logowania został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="346ee-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="346ee-145">Włączanie uwierzytelniania dwuskładnikowego (2FA)</span><span class="sxs-lookup"><span data-stu-id="346ee-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="346ee-146">Uwierzytelnianie dwuetapowe jest zalecana dla wszystkich użytkowników, którzy ręcznie publikować w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="346ee-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="346ee-147">Aby włączyć uwierzytelnianie dwuskładnikowe, konto logowania musi mieć co najmniej dwie formy uwierzytelniania zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="346ee-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="346ee-148">Jeden to hasło i mogą być inne formy:</span><span class="sxs-lookup"><span data-stu-id="346ee-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="346ee-149">Numer telefonu, który może odbierać wiadomości SMS</span><span class="sxs-lookup"><span data-stu-id="346ee-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="346ee-150">W przypadku aplikacji wystawcy uwierzytelnienia zarejestrowanego takich jak Microsoft Authenticator na telefonie komórkowym</span><span class="sxs-lookup"><span data-stu-id="346ee-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="346ee-151">Te rodzaje uwierzytelniania muszą być skonfigurowane w danych konta usługi AAD lub w ustawieniach zabezpieczeń konto Identyfikatora Microsoft.</span><span class="sxs-lookup"><span data-stu-id="346ee-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="346ee-152">Po włączeniu funkcji 2FA, są wymagane do uwierzytelniania za pomocą skonfigurowanego metod uwierzytelniania, za każdym razem, gdy zarejestrujesz się w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="346ee-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="346ee-153">Włączanie uwierzytelniania dwuskładnikowego dla tej witryny galerii programu PowerShell nie wymaga włączenia funkcji 2FA, dla wszystkich zastosowań konta logowania.</span><span class="sxs-lookup"><span data-stu-id="346ee-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="346ee-154">Aby uzyskać więcej informacji, zobacz [o weryfikacji dwuetapowej](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="346ee-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="346ee-155">Zmień obraz profilu</span><span class="sxs-lookup"><span data-stu-id="346ee-155">Change your profile picture</span></span>

<span data-ttu-id="346ee-156">Galeria programu PowerShell, zależy od Gravatar do przechowywania i wyświetlania obrazu skojarzonego z danym profilem.</span><span class="sxs-lookup"><span data-stu-id="346ee-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="346ee-157">Aby zaktualizować swój obraz profilu, odwiedź stronę [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="346ee-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
