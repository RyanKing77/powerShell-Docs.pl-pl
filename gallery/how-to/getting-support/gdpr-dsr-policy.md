---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galerii programu powershell, psgallery, GDPR
title: Zgodność GDPR galerii programu PowerShell
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="a70f6-103">Zgodność GDPR galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="a70f6-104">Przegląd</span><span class="sxs-lookup"><span data-stu-id="a70f6-104">Overview</span></span>

<span data-ttu-id="a70f6-105">W 2018 maja prawo Europejskiego prywatności, ogólne dane ochrony rozporządzenia (GDPR), zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="a70f6-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="a70f6-106">GDPR nakłada nowe zasady dotyczące firmy, agencji rządowych z systemem innym niż zysków i innymi organizacjami, że oferta towarów i usług do osób w Unii Europejskiej (UE), lub że zbieranie i analizowanie danych powiązane mieszkańców Unii Europejskiej.</span><span class="sxs-lookup"><span data-stu-id="a70f6-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="a70f6-107">Stosuje GDPR niezależnie od tego, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="a70f6-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="a70f6-108">W tym artykule instrukcje dotyczące sposobu usunięcia danych osobowych z galerii programu PowerShell i może służyć do obsługi sieci zobowiązań GDPR.</span><span class="sxs-lookup"><span data-stu-id="a70f6-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="a70f6-109">Jeśli szukasz informacji ogólnych o GDPR zobacz [GDPR części portalu zaufania usługi](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="a70f6-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="a70f6-110">Identyfikowalne dane osobowe danych</span><span class="sxs-lookup"><span data-stu-id="a70f6-110">Personally identifiable data</span></span>

<span data-ttu-id="a70f6-111">Poniższe informacje, które mogą być udostępniane przez użytkowników, którzy mogą zawierać informacje osobiste są przechowywane w galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a70f6-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="a70f6-112">Konto galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="a70f6-113">Elementy opublikowany w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="a70f6-114">Wiadomości e-mail korespondencji z zespołem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="a70f6-115">Większość użytkowników nie należy tworzyć konta galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="a70f6-116">Konto nie jest wymagany, chyba że chcesz opublikować element lub funkcja "Skontaktuj się z właścicielem" w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="a70f6-117">Inne niż wiadomości e-mail korespondencji zainicjowanej przez użytkownika galerii programu PowerShell nie przechowuje dane osobowe dla użytkowników, którzy nie utworzono konta.</span><span class="sxs-lookup"><span data-stu-id="a70f6-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="a70f6-118">Użytkownicy, którzy tworzą konta galerii programu PowerShell można publikować elementy galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="a70f6-119">Te elementy będą kod programu PowerShell, ale może zawierać inne informacje w tym informacji osobistych.</span><span class="sxs-lookup"><span data-stu-id="a70f6-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="a70f6-120">Poniższe informacje będą wyświetlane, jak wprowadzasz wszystkie elementy zostały opublikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="a70f6-121">Eksport DSR danych galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="a70f6-122">W poniższych sekcjach opisano sposób galerii programu PowerShell obsługuje żądania podmiotu danych (DSR), przez wyjaśniający wyeksportować informacje przechowywane w galerii programu PowerShell oraz sposobu zażądać usunięcia tych informacji.</span><span class="sxs-lookup"><span data-stu-id="a70f6-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="a70f6-123">Poczta e-mail</span><span class="sxs-lookup"><span data-stu-id="a70f6-123">Email</span></span>

<span data-ttu-id="a70f6-124">Zgodność poczty e-mail może zawierać żadnego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a70f6-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="a70f6-125">Wysyłanie wiadomości e-mail do właścicieli galerii programu PowerShell, wystąpił problem z dowolny element, który został opublikowany w galerii programu PowerShell wykryte elementy, jeśli skanuje analizy kodu</span><span class="sxs-lookup"><span data-stu-id="a70f6-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="a70f6-126">Wysyłanie wiadomości e-mail dla wszystkich użytkowników do zespołu galerii programu PowerShell przy użyciu adresu e-mail na stronie "Skontaktuj się z nami" (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="a70f6-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="a70f6-127">Zarejestrowanych użytkowników, którzy korzystają z funkcji "Skontaktuj się z właścicielem" w galerii programu PowerShell do wysyłania wiadomości e-mail do właściciela elementu w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="a70f6-128">Wiadomości e-mail wysyłanych przez lub do galerii programu PowerShell mają zasady przechowywania 90 dni do obsługi dochodzenia potencjalne powinien odnajdowane złośliwego kodu w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="a70f6-129">Wiadomości e-mail zostaną usunięte przez zasady po 90 dniach.</span><span class="sxs-lookup"><span data-stu-id="a70f6-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="a70f6-130">Aby zażądać kopie wszystkich wiadomości wysłanych do lub z adresu e-mail i galerii programu PowerShell w ciągu ostatnich 90 dni.</span><span class="sxs-lookup"><span data-stu-id="a70f6-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="a70f6-131">Aby zażądać tej korespondencji, Wyślij wiadomość e-mail do cgadmin@microsoft.com, o tytule: "Żądanie DSR odnoszących się do tego konta w wiadomości e-mail".</span><span class="sxs-lookup"><span data-stu-id="a70f6-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="a70f6-132">W treści komunikatu o stanie informacjach zażądano (na przykład: Wyślij wszystkie wiadomości e-mail wysyłane do lub z tego adresu e-mail.) Wszystkie wiadomości e-mail, obejmujących adres e-mail w ciągu 90 dni żądanie zostanie wysłane w ciągu 7 dni roboczych.</span><span class="sxs-lookup"><span data-stu-id="a70f6-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="a70f6-133">Informacje o koncie w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="a70f6-134">Jeśli po utworzeniu konta galerii programu PowerShell, można znaleźć wszystkie informacje osobiste, które były przechowywane w galerii programu PowerShell, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a70f6-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="a70f6-135">Zaloguj się do galerii programu PowerShell, a następnie kliknij swoją nazwę użytkownika</span><span class="sxs-lookup"><span data-stu-id="a70f6-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="a70f6-136">Następna strona wyświetlana jest strona konta, przedstawiający adres e-mail dla konta galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="a70f6-137">Jeśli więcej niż jedno konto utworzone w galerii programu PowerShell, należy powtórzyć te kroki dla każdego konta.</span><span class="sxs-lookup"><span data-stu-id="a70f6-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="a70f6-138">Elementy w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="a70f6-139">W celu ułatwienia eksportowanie elementów opublikowany w galerii programu PowerShell, możemy skryptu "GetPSGalleryItemsForAuthor" został opublikowany w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="a70f6-140">Ten skrypt Eksportuje kopię każdej wersji każdy element umieścić w galerii programu PowerShell, na podstawie informacji autora przechowywane w elemencie.</span><span class="sxs-lookup"><span data-stu-id="a70f6-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="a70f6-141">Autor są przechowywane w manifeście elementu podczas publikowania tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a70f6-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="a70f6-142">Nie ma żadnej gwarancji, że autor jest tej samej tożsamości co konto, którego używasz w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a70f6-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="a70f6-143">Jeśli używasz inną wartość w polu Autor, należy podać tę wartość, korzystając z tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="a70f6-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="a70f6-144">Skrypt może pobrać za pomocą następującego polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a70f6-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="a70f6-145">Skrypt może następnie uruchom bezpośrednio, uruchamiając następujące polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a70f6-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="a70f6-146">Pojawi się monit autora i folderze w systemie, w którym ma elementy do zapisania.</span><span class="sxs-lookup"><span data-stu-id="a70f6-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="a70f6-147">Usuwanie danych osobowych z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="a70f6-148">Aby usunąć konto galerii programu PowerShell lub dowolny element posiadanych w galerii programu PowerShell, Wyślij wiadomość e-mail do cgadmin@microsoft.com o tytule: "GDPR żądań dla elementów odnoszących się do tego konta".</span><span class="sxs-lookup"><span data-stu-id="a70f6-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="a70f6-149">W treści komunikatu stanu, jakie informacje mają być usunięte.</span><span class="sxs-lookup"><span data-stu-id="a70f6-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="a70f6-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a70f6-150">For example:</span></span>

* <span data-ttu-id="a70f6-151">Usuń x.y.z wersji mojej elementu "Nazwa elementu"</span><span class="sxs-lookup"><span data-stu-id="a70f6-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="a70f6-152">Usuń wszystkie wersje elemencie "Nazwa elementu"</span><span class="sxs-lookup"><span data-stu-id="a70f6-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="a70f6-153">Usuń konto galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a70f6-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="a70f6-154">Administratorzy galerii programu PowerShell odpowie w ciągu 7 dni roboczych.</span><span class="sxs-lookup"><span data-stu-id="a70f6-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="a70f6-155">Określone elementy zostaną usunięte w ciągu 30 dni, po wysłaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="a70f6-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
