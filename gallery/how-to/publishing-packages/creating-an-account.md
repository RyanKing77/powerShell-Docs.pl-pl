---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Tworzenie konta galerii programu PowerShell
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084216"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="042b4-103">Tworzenie konta galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="042b4-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="042b4-104">Przed opublikowaniem niczego w galerii programu PowerShell, należy utworzyć konto galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="042b4-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="042b4-105">Konta galerii programu PowerShell musi być połączony z kontem e-mail logowania.</span><span class="sxs-lookup"><span data-stu-id="042b4-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="042b4-106">To konto może być kontem usługi Azure Active Directory lub Identyfikatora firmy Microsoft, takich jak konta e-mail z usługi outlook.com lub hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="042b4-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="042b4-107">Tworzenie konta galerii programu PowerShell, przejdź do [ https://PowerShellGallery.com ](https://PowerShellGallery.com) i kliknij pozycję **Zaloguj** jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="042b4-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Rejestrowanie nowego konta](../../Images/CreateAccount-Register.png)

<span data-ttu-id="042b4-109">Aby użyć konta usługi Azure Active Directory, zaznacz **konta służbowego**i zaloguj się przy użyciu swojego konta.</span><span class="sxs-lookup"><span data-stu-id="042b4-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="042b4-110">Aby użyć Identyfikatora firmy Microsoft, wybierz **konto osobiste** i zaloguj się.</span><span class="sxs-lookup"><span data-stu-id="042b4-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="042b4-111">Następnie monit Utwórz nazwę użytkownika dla galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="042b4-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="042b4-112">Przejrzyj warunki użytkowania i zasady zachowania poufności informacji, wprowadź nazwę użytkownika, a następnie kliknij **zarejestrować**.</span><span class="sxs-lookup"><span data-stu-id="042b4-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="042b4-113">Nie można zmienić nazwę konta, po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="042b4-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="042b4-114">Aby uzyskać więcej informacji, zobacz [właścicieli pakietu zarządzania](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="042b4-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="042b4-115">Zalecane praktyki dla kont z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="042b4-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="042b4-116">Jest to ważne, aby aktywnie monitoruje konto e-mail użyte przy użyciu konta z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="042b4-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="042b4-117">Cała komunikacja z właścicielami pakietów galerii programu PowerShell jest za pośrednictwem tego adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="042b4-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="042b4-118">Jeśli zespół operacyjny galerii programu PowerShell nie może skontaktować się z właścicielem pakietu, firma Microsoft może wymagać usunięcia pakietu.</span><span class="sxs-lookup"><span data-stu-id="042b4-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="042b4-119">Organizacje, które często publikowanie w galerii programu PowerShell utworzyć unikatowe konto zewnętrzne do tego celu.</span><span class="sxs-lookup"><span data-stu-id="042b4-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="042b4-120">Zaleca się, że używasz przesyłanie dalej poczty e-mail do przesyłania powiadomień na adres w Twojej organizacji.</span><span class="sxs-lookup"><span data-stu-id="042b4-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="042b4-121">W przypadku wielu właścicielom są skojarzone z pakietem, wszystkie powiadomienia galerii programu PowerShell są wysyłane do wszystkich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="042b4-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="042b4-122">Aby uzyskać więcej informacji, zobacz [właścicieli pakietu zarządzania](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="042b4-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
