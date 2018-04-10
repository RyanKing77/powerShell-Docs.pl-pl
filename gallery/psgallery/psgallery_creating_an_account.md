---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Tworzenie konta galerii programu PowerShell
ms.openlocfilehash: c9c263a1926957cbdf059e062326b1903c117f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="c201c-103">Tworzenie konta galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c201c-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="c201c-104">Przed opublikowaniem niczego w galerii programu PowerShell, należy ustanowić konto galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c201c-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="c201c-105">Konta galerii programu PowerShell muszą być połączone z konta z włączoną obsługą poczty e-mail usługi Azure Active Directory lub konta e-mail firmy Microsoft (z domeny outlook.com, hotmail.com itp.)</span><span class="sxs-lookup"><span data-stu-id="c201c-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="c201c-106">Aby utworzyć konto w galerii programu PowerShell, przejdź do https://PowerShellGallery.com i wybierz polecenie "Register" (zobacz obraz poniżej).</span><span class="sxs-lookup"><span data-stu-id="c201c-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Zarejestruj nowe konto](./images/CreatingAccount-Register.png)

<span data-ttu-id="c201c-108">Na następnej stronie do korzystania z konta usługi Azure Active Directory, wybierz "Pracy lub konto służbowe" i zaloguj się przy użyciu swojego konta.</span><span class="sxs-lookup"><span data-stu-id="c201c-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="c201c-109">Aby użyć konta Microsoft - taki w domenie Hotmail.com lub Outlook.com — wybierz opcję "Osobiste konto" i logowania.</span><span class="sxs-lookup"><span data-stu-id="c201c-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="c201c-110">Po zalogowaniu, zostanie wyświetlony monit o utworzenie nazwę użytkownika dla galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c201c-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="c201c-111">Przejrzyj warunki użytkowania i zasady zachowania poufności informacji, które są połączone w, wprowadź nazwę użytkownika i kliknij przycisk Zarejestruj.</span><span class="sxs-lookup"><span data-stu-id="c201c-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="c201c-112">Uwaga: Nie można zmienić nazwy tego konta, po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="c201c-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="c201c-113">Zobacz [Zarządzanie właścicieli elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) Aby uzyskać więcej informacji związanych z tym.</span><span class="sxs-lookup"><span data-stu-id="c201c-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="c201c-114">Zalecane rozwiązania dla kont w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c201c-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="c201c-115">Należy pamiętać, że aktywnie monitorowanych konto e-mail używany przy użyciu konta z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c201c-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="c201c-116">Wszystkie komunikat z właściciele elementów galerii programu PowerShell jest za pośrednictwem poczty e-mail, przy użyciu adresu skojarzonych z Twoim kontem galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c201c-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="c201c-117">Nie możemy skontaktować się z właścicielem elementu, zespół operacyjny może być konieczna usuwanie elementu w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="c201c-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="c201c-118">Organizacje, które publikują w galerii programu PowerShell często tworzyć unikatowe konto w tym celu w usłudze Outlook.com lub innej domeny konta Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c201c-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="c201c-119">W wielu przypadkach to konto nie jest regularnie monitorowane.</span><span class="sxs-lookup"><span data-stu-id="c201c-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="c201c-120">W takim przypadku najlepszym rozwiązaniem jest Wyślij wiadomość e-mail na inne konto, zazwyczaj w jednej organizacji, który ma być monitorowany przez jego właściciela elementu za pomocą programu Outlook przekazywania.</span><span class="sxs-lookup"><span data-stu-id="c201c-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="c201c-121">W przypadku wielu właścicieli skojarzony z elementem korespondencji, które pochodzą z galerii programu PowerShell przejdzie do wszystkich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="c201c-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="c201c-122">Zobacz [Zarządzanie właścicieli elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) Aby uzyskać więcej informacji na temat dodawania właścicieli do elementu.</span><span class="sxs-lookup"><span data-stu-id="c201c-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>