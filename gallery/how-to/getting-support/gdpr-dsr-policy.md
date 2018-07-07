---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria programu powershell, galerii programu PowerShell, RODO
title: Zgodność z RODO galerii programu PowerShell
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893250"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="8c05a-103">Zgodność z RODO galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="8c05a-104">Przegląd</span><span class="sxs-lookup"><span data-stu-id="8c05a-104">Overview</span></span>

<span data-ttu-id="8c05a-105">W maju 2018 europejskie prawo ochrony prywatności, ogólne danych (GDPR Protection Regulation), staje się skuteczny.</span><span class="sxs-lookup"><span data-stu-id="8c05a-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="8c05a-106">Rozporządzenie GDPR nakłada nowe zasady dotyczące firm, agencji rządowych, non-profit i innych organizacji oferty towary i usługi osobom w Unii Europejskiej (UE) lub że zbieranie i analizujących dane związane z osobami mieszkającymi w UE.</span><span class="sxs-lookup"><span data-stu-id="8c05a-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="8c05a-107">Niezależnie od tego, w którym znajduje się stosuje się GDPR.</span><span class="sxs-lookup"><span data-stu-id="8c05a-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="8c05a-108">Ten artykuł zawiera instrukcje dotyczące sposobu usuwania danych osobowych z galerii programu PowerShell i może służyć do obsługi zobowiązania w RODO.</span><span class="sxs-lookup"><span data-stu-id="8c05a-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="8c05a-109">Jeśli szukasz ogólne informacje na temat rozporządzenia RODO, zobacz [RODO części portal zaufania usługi](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="8c05a-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="8c05a-110">Identyfikowalnych danych umożliwiających identyfikację użytkownika</span><span class="sxs-lookup"><span data-stu-id="8c05a-110">Personally identifiable data</span></span>

<span data-ttu-id="8c05a-111">Następujące informacje, które mogą być udostępniane przez użytkowników, którzy mogą zawierać informacje osobiste są przechowywane w galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c05a-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="8c05a-112">Konta z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="8c05a-113">Elementów opublikowanych w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-113">Items published to the PowerShell Gallery</span></span>
- <span data-ttu-id="8c05a-114">Adres e-mail korespondencji z zespołem galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="8c05a-115">Większość użytkowników nie należy tworzyć konta galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="8c05a-116">Konto nie jest wymagany, chyba że zamierzasz opublikować element możesz również użyć funkcji "Skontaktuj się z właścicielem" w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="8c05a-117">Inne niż korespondencja e-mail zainicjowanej przez użytkownika galerii programu PowerShell nie przechowuje identyfikowalne dane dla użytkowników, którzy nie zostały utworzone konto.</span><span class="sxs-lookup"><span data-stu-id="8c05a-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="8c05a-118">Użytkownicy, którzy Tworzenie konta galerii programu PowerShell można opublikować elementy w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="8c05a-119">Te elementy powinny być kod programu PowerShell, ale może zawierać inne informacje w tym informacje osobiste.</span><span class="sxs-lookup"><span data-stu-id="8c05a-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="8c05a-120">Poniższe informacje pokaże, jak możesz uzyskać wszystkie elementy zostały opublikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="8c05a-121">Żądanie praw podmiotu danych Eksport danych galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="8c05a-122">W poniższych sekcjach opisano, jak obsługuje żądania podmiotów danych (DSR) w galerii programu PowerShell, ponieważ wyjaśnia sposób eksportowania informacji przechowywanych w galerii programu PowerShell oraz zażądać usunięcia tych informacji.</span><span class="sxs-lookup"><span data-stu-id="8c05a-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="8c05a-123">Poczta e-mail</span><span class="sxs-lookup"><span data-stu-id="8c05a-123">Email</span></span>

<span data-ttu-id="8c05a-124">Korespondencja e-mail może zawierać żadnego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8c05a-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="8c05a-125">Wysyłanie wiadomości e-mail do właścicieli z galerii programu PowerShell, elementów, jeśli skanuje analizy kodu wykrył problem z dowolnego elementu, który został opublikowany w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="8c05a-126">Wysyłanie wiadomości e-mail dla wszystkich osób do zespołu galerii programu PowerShell przy użyciu adresu e-mail, na stronie "Skontaktuj się z nami" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="8c05a-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="8c05a-127">Liczba zarejestrowanych użytkowników, którzy korzystają z funkcji "Skontaktuj się z właścicielem" w galerii programu PowerShell do wysyłania wiadomości e-mail do właściciela elementu w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="8c05a-128">Wiadomości e-mail wysyłane przez lub w galerii programu PowerShell trzeba zasady przechowywania 90 dni obsługuje dochodzeń możliwych zabezpieczeniami powinny złośliwego kodu zostać wykryte w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="8c05a-129">Wiadomości e-mail zostaną usunięte przez zasady po upływie 90 dni.</span><span class="sxs-lookup"><span data-stu-id="8c05a-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="8c05a-130">Może żądać kopiuje wszystkie wiadomości e-mail wysyłane do i z adresu e-mail i galerii programu PowerShell w ciągu ostatnich 90 dni.</span><span class="sxs-lookup"><span data-stu-id="8c05a-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="8c05a-131">Aby zażądać tej korespondencji, Wyślij wiadomość e-mail do [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), o tytule: "Żądanie praw podmiotu danych dla wiadomości e-mail, odnoszące się do tego konta".</span><span class="sxs-lookup"><span data-stu-id="8c05a-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="8c05a-132">W treści komunikatu o stanie informacjach żądasz (na przykład: Wyślij wszystkie wiadomości e-mail wysyłane do lub odebrane z tego adresu e-mail.) Wszystkie wiadomości e-mail, obejmujących adres e-mail w ciągu 90 dni żądanie zostanie wysłane w ciągu 7 dni roboczych.</span><span class="sxs-lookup"><span data-stu-id="8c05a-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="8c05a-133">Informacje o koncie w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="8c05a-134">Jeśli utworzono konto galerii programu PowerShell można znaleźć wszystkie informacje osobiste, które zostały zapisane w galerii programu PowerShell, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8c05a-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="8c05a-135">Zaloguj się do galerii programu PowerShell, a następnie kliknij swoją nazwę użytkownika</span><span class="sxs-lookup"><span data-stu-id="8c05a-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="8c05a-136">Następnej stronie wyświetlana jest strona konta zawiera adres e-mail używany dla konta galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="8c05a-137">Jeśli więcej niż jedno konto utworzone w galerii programu PowerShell, należy powtórzyć te kroki dla każdego konta.</span><span class="sxs-lookup"><span data-stu-id="8c05a-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="8c05a-138">Elementy w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="8c05a-139">W celu ułatwienia eksportowanie elementów opublikowanych w galerii programu PowerShell, opublikowaliśmy skrypt "GetPSGalleryItemsForAuthor" w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="8c05a-140">Ten skrypt Eksportuje kopię każdej wersji każdego elementu, umieść w galerii programu PowerShell, na podstawie Autor informacji przechowywanych w elemencie.</span><span class="sxs-lookup"><span data-stu-id="8c05a-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="8c05a-141">Autor jest przechowywany w manifest elementu, po opublikowaniu usługi elementu.</span><span class="sxs-lookup"><span data-stu-id="8c05a-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="8c05a-142">Nie ma żadnej gwarancji, że autor jest ta sama tożsamość jako konto, którego używasz w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c05a-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="8c05a-143">Jeśli używasz inną wartość w polu autora, należy podać tę wartość, korzystając z tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="8c05a-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="8c05a-144">Skrypt może pobrać za pomocą następującego polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c05a-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="8c05a-145">Skrypt można uruchomić następnie bezpośrednio, uruchamiając następujące polecenia środowiska PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c05a-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="8c05a-146">Zostanie wyświetlony monit podanie autora i folder w systemie, którego elementy mają być zapisywane.</span><span class="sxs-lookup"><span data-stu-id="8c05a-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="8c05a-147">Usuwanie danych osobowych z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="8c05a-148">Aby usunąć konto z galerii programu PowerShell lub dowolny element właścicielem w galerii programu PowerShell, Wyślij wiadomość e-mail do cgadmin@microsoft.com o tytule: "Żądanie RODO elementów odnoszących się do tego konta".</span><span class="sxs-lookup"><span data-stu-id="8c05a-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="8c05a-149">W treści komunikatu o stanie, jakie informacje mają być usunięte.</span><span class="sxs-lookup"><span data-stu-id="8c05a-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="8c05a-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8c05a-150">For example:</span></span>

- <span data-ttu-id="8c05a-151">Usuń x.y.z wersji mojego elementu "element name"</span><span class="sxs-lookup"><span data-stu-id="8c05a-151">Please delete version x.y.z of my item "item name"</span></span>
- <span data-ttu-id="8c05a-152">Usuń wszystkie wersje Moje elementu "element name"</span><span class="sxs-lookup"><span data-stu-id="8c05a-152">Please delete all versions of my item "item name"</span></span>
- <span data-ttu-id="8c05a-153">Usuń Moje konto galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c05a-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="8c05a-154">Administratorzy galerii programu PowerShell odpowie w ciągu 7 dni roboczych.</span><span class="sxs-lookup"><span data-stu-id="8c05a-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="8c05a-155">Określone elementy zostaną usunięte w ciągu 30 dni po wysłaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="8c05a-155">The items specified will be deleted within 30 days after the request is sent.</span></span>