---
title: Parametry zabezpieczeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849028"
---
# <a name="security-parameters"></a><span data-ttu-id="9f1bc-102">Parametry zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9f1bc-102">Security Parameters</span></span>

<span data-ttu-id="9f1bc-103">W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów można uzyskać informacje dotyczące operacji, takich jak parametry, które określają informacje o certyfikacie klucza i uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

<span data-ttu-id="9f1bc-104">Typ danych listy ACL: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-104">ACL Data type: String</span></span>

<span data-ttu-id="9f1bc-105">Implementowanie tego parametru, aby określić poziom kontroli dostępu, ochrony dla wykazu lub uzyskać jednolite zasobów identyfikator (URI).</span><span class="sxs-lookup"><span data-stu-id="9f1bc-105">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="9f1bc-106">Typ danych CertFile: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-106">CertFile Data type: String</span></span>

<span data-ttu-id="9f1bc-107">Implementowanie tego parametru, aby użytkownik może określić nazwę pliku, który zawiera jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9f1bc-107">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span>

- <span data-ttu-id="9f1bc-108">Certyfikatu x.509 z kodowaniem Base64 lub wyróżniającą reguły DER (Encoding)</span><span class="sxs-lookup"><span data-stu-id="9f1bc-108">A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span>

- <span data-ttu-id="9f1bc-109">Plik publicznego klucza (PKCS Cryptography Standards) #12, który zawiera co najmniej jeden certyfikat i klucz</span><span class="sxs-lookup"><span data-stu-id="9f1bc-109">A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>

<span data-ttu-id="9f1bc-110">Typ danych CertIssuerName: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-110">CertIssuerName Data type: String</span></span>

<span data-ttu-id="9f1bc-111">Ten parametr należy zaimplementować tak, aby użytkownik może określić nazwę wystawcy certyfikatu lub dlatego, że użytkownik może określić podciąg.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-111">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="9f1bc-112">Typ danych CertRequestFile: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-112">CertRequestFile Data type: String</span></span>

<span data-ttu-id="9f1bc-113">Implementuje ten parametr, aby określić nazwę pliku zawierającego żądanie certyfikatu w formacie Base64 lub PKCS #10 szyfrowanego algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-113">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>

<span data-ttu-id="9f1bc-114">Typ danych CertSerialNumber: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-114">CertSerialNumber Data type: String</span></span>

<span data-ttu-id="9f1bc-115">Implementuje ten parametr, aby określić numer seryjny, który został wystawiony przez urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-115">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>

<span data-ttu-id="9f1bc-116">Typ danych elementy CertStoreLocation: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-116">CertStoreLocation Data type: String</span></span>

<span data-ttu-id="9f1bc-117">Implementowanie tego parametru, użytkownik może określić lokalizację magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-117">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="9f1bc-118">Lokalizacja jest zwykle ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-118">The location is typically a file path.</span></span>

<span data-ttu-id="9f1bc-119">Typ danych CertSubjectName: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-119">CertSubjectName Data type: String</span></span>

<span data-ttu-id="9f1bc-120">Ten parametr należy zaimplementować tak, aby użytkownik może określić wystawca certyfikatu, lub tak, aby użytkownik może określić podciąg.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-120">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="9f1bc-121">Typ danych CertUsage: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-121">CertUsage Data type: String</span></span>

<span data-ttu-id="9f1bc-122">Implementuje ten parametr, aby określić użycia klucza lub rozszerzone użycie klucza.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-122">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="9f1bc-123">Klucz może być reprezentowany jako bit maski, nieco, identyfikator obiektu (OID) lub ciąg.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-123">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>

<span data-ttu-id="9f1bc-124">Dane poświadczeń, wpisz: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="9f1bc-124">Credential Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>

<span data-ttu-id="9f1bc-125">Implementowanie tego parametru polecenia cmdlet zostanie automatycznie wyświetlony monit o nazwę użytkownika lub hasło.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-125">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="9f1bc-126">Jeśli nie podano bezpośrednio pełne poświadczenia, zostanie wyświetlony monit dla obu.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-126">A prompt for both is displayed if a full credential is not supplied directly.</span></span>

<span data-ttu-id="9f1bc-127">Typ danych NazwaCSP: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-127">CSPName Data type: String</span></span>

<span data-ttu-id="9f1bc-128">Implementowanie tego parametru, użytkownik może określić nazwę dostawcy usług certyfikatów (CSP).</span><span class="sxs-lookup"><span data-stu-id="9f1bc-128">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>

<span data-ttu-id="9f1bc-129">Typ danych CSPType: Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="9f1bc-129">CSPType Data type: Integer</span></span>

<span data-ttu-id="9f1bc-130">Implementowanie tego parametru, użytkownik może określić typu dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-130">Implement this parameter so that the user can specify the type of CSP.</span></span>

<span data-ttu-id="9f1bc-131">Typ danych grupy: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-131">Group Data type: String</span></span>

<span data-ttu-id="9f1bc-132">Implementowanie tego parametru, użytkownik może określić zbiór jednostek, aby uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-132">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="9f1bc-133">Aby uzyskać więcej informacji, zobacz opis `Principal` parametru.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-133">For more information, see the description of the `Principal` parameter.</span></span>

<span data-ttu-id="9f1bc-134">Typ danych KeyAlgorithm: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-134">KeyAlgorithm Data type: String</span></span>

<span data-ttu-id="9f1bc-135">Implementowanie tego parametru, użytkownik może określić algorytm generowania kluczy, który ma być używany dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-135">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>

<span data-ttu-id="9f1bc-136">Typ danych NazwaKonteneraKlucza: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-136">KeyContainerName Data type: String</span></span>

<span data-ttu-id="9f1bc-137">Implementowanie tego parametru, użytkownik może określić nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-137">Implement this parameter so that the user can specify the name of the key container.</span></span>

<span data-ttu-id="9f1bc-138">Typ danych długość klucza: Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="9f1bc-138">KeyLength Data type: Integer</span></span>

<span data-ttu-id="9f1bc-139">Implementowanie tego parametru, użytkownik może określić długość klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-139">Implement this parameter so that the user can specify the length of the key in bits.</span></span>

<span data-ttu-id="9f1bc-140">Typ danych operacji: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-140">Operation Data type: String</span></span>

<span data-ttu-id="9f1bc-141">Implementowanie tego parametru, użytkownik może określić akcję, która może być wykonana w chronionym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-141">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>

<span data-ttu-id="9f1bc-142">Typ danych jednostki: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-142">Principal Data type: String</span></span>

<span data-ttu-id="9f1bc-143">Implementowanie tego parametru, użytkownik może określić unikatowe jednostki do zidentyfikowania dostępu.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-143">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>

<span data-ttu-id="9f1bc-144">Typ danych uprawnień: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-144">Privilege Data type: String</span></span>

<span data-ttu-id="9f1bc-145">Implementowanie tego parametru, użytkownik może określić po prawej stronie, polecenie cmdlet musi wykonać operację dla określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-145">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>

<span data-ttu-id="9f1bc-146">Typ danych uprawnień: Tablica uprawnień</span><span class="sxs-lookup"><span data-stu-id="9f1bc-146">Privileges Data type: Array of privileges</span></span>

<span data-ttu-id="9f1bc-147">Implementowanie tego parametru, użytkownik może określić prawa, które polecenie cmdlet musi wykonać jego działania dla określonego wpisu.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-147">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>

<span data-ttu-id="9f1bc-148">Typ danych dla roli: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-148">Role Data type: String</span></span>

<span data-ttu-id="9f1bc-149">Implementowanie tego parametru, użytkownik może określić zestaw operacji, które mogą być wykonywane przez podmiot.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-149">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>

<span data-ttu-id="9f1bc-150">Typ danych SaveCred: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9f1bc-150">SaveCred Data type: SwitchParameter</span></span>

<span data-ttu-id="9f1bc-151">Implementowanie tego parametru poświadczenia, które zostały wcześniej zapisane przez użytkownika będzie używany, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-151">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>

<span data-ttu-id="9f1bc-152">Typ danych w zakresie: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-152">Scope Data type: String</span></span>

<span data-ttu-id="9f1bc-153">Implementowanie tego parametru, użytkownik może określić grupy chronionych obiektów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-153">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>

<span data-ttu-id="9f1bc-154">Typ danych identyfikator SID: Ciąg</span><span class="sxs-lookup"><span data-stu-id="9f1bc-154">SID Data type: String</span></span>

<span data-ttu-id="9f1bc-155">Implementowanie tego parametru, użytkownik może określić unikatowy identyfikator, który reprezentuje podmiot zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-155">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>

<span data-ttu-id="9f1bc-156">Zaufane — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9f1bc-156">Trusted Data type: SwitchParameter</span></span>

<span data-ttu-id="9f1bc-157">Implementowanie tego parametru, poziomy zaufania są obsługiwane, jeśli parametr jest określony.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-157">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>

<span data-ttu-id="9f1bc-158">Typ danych TrustLevel: Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="9f1bc-158">TrustLevel Data type: Keyword</span></span>

<span data-ttu-id="9f1bc-159">Implementowanie tego parametru, użytkownik może określić poziom zaufania, który jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-159">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="9f1bc-160">Na przykład możliwe wartości to internet, intranet i fulltrust.</span><span class="sxs-lookup"><span data-stu-id="9f1bc-160">For example, possible values include internet, intranet, and fulltrust.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f1bc-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f1bc-161">See Also</span></span>

[<span data-ttu-id="9f1bc-162">Parametry polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f1bc-162">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="9f1bc-163">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f1bc-163">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9f1bc-164">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f1bc-164">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
