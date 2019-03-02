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
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251306"
---
# <a name="security-parameters"></a>Parametry zabezpieczeń

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów można uzyskać informacje dotyczące operacji, takich jak parametry, które określają informacje o certyfikacie klucza i uprawnień zabezpieczeń.

|Parametr|Funkcja|
|---|---|
|**LISTY ACL**<br>Typ danych: Ciąg|Implementowanie tego parametru, aby określić poziom kontroli dostępu, ochrony dla wykazu lub uzyskać jednolite zasobów identyfikator (URI).|
|**CertFile**<br>Typ danych: Ciąg|Implementowanie tego parametru, aby użytkownik może określić nazwę pliku, który zawiera jeden z następujących czynności:<br>-Base64 lub wyróżniającą reguły DER (Encoding) certyfikatu x.509 z kodowaniem<br>-Publiczny klucz (PKCS Cryptography Standards) #12 pliku, który zawiera co najmniej jeden certyfikat i klucz|
|**CertIssuerName**<br>Typ danych: Ciąg|Ten parametr należy zaimplementować tak, aby użytkownik może określić nazwę wystawcy certyfikatu lub dlatego, że użytkownik może określić podciąg.|
|**CertRequestFile**<br>Typ danych: Ciąg|Implementuje ten parametr, aby określić nazwę pliku zawierającego żądanie certyfikatu w formacie Base64 lub PKCS #10 szyfrowanego algorytmem DER.|
|**CertSerialNumber**<br>Typ danych: Ciąg|Implementuje ten parametr, aby określić numer seryjny, który został wystawiony przez urząd certyfikacji.|
|**CertStoreLocation**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić lokalizację magazynu certyfikatów. Lokalizacja jest zwykle ścieżki do pliku.|
|**CertSubjectName**<br>Typ danych: Ciąg|Ten parametr należy zaimplementować tak, aby użytkownik może określić wystawca certyfikatu, lub tak, aby użytkownik może określić podciąg.|
|**CertUsage**<br>Typ danych: Ciąg|Implementuje ten parametr, aby określić użycia klucza lub rozszerzone użycie klucza. Klucz może być reprezentowany jako bit maski, nieco, identyfikator obiektu (OID) lub ciąg.|
|**Poświadczenie**<br>Typ danych: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementowanie tego parametru polecenia cmdlet zostanie automatycznie wyświetlony monit o nazwę użytkownika lub hasło. Jeśli nie podano bezpośrednio pełne poświadczenia, zostanie wyświetlony monit dla obu.|
|**CSPName**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę dostawcy usług certyfikatów (CSP).|
|**CSPType**<br>Typ danych: Liczba całkowita|Implementowanie tego parametru, użytkownik może określić typu dostawcy usług Kryptograficznych.|
|**Grupa**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić zbiór jednostek, aby uzyskać dostęp. Aby uzyskać więcej informacji, zobacz opis **jednostki** parametru.|
|**KeyAlgorithm**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić algorytm generowania kluczy, który ma być używany dla zabezpieczeń.|
|**KeyContainerName**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę kontenera kluczy.|
|**Długość klucza**<br>Typ danych: Liczba całkowita|Implementowanie tego parametru, użytkownik może określić długość klucza w bitach.|
|**Operacja**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić akcję, która może być wykonana w chronionym obiekcie.|
|**Jednostki**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić unikatowe jednostki do zidentyfikowania dostępu.|
|**uprawnienie**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić po prawej stronie, polecenie cmdlet musi wykonać operację dla określonego obiektu.|
|**Uprawnienia**<br>Typ danych: Tablica uprawnień|Implementowanie tego parametru, użytkownik może określić prawa, które polecenie cmdlet musi wykonać jego działania dla określonego wpisu.|
|**Rola**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić zestaw operacji, które mogą być wykonywane przez podmiot.|
|**SaveCred**<br>Typ danych: SwitchParameter|Implementowanie tego parametru poświadczenia, które zostały wcześniej zapisane przez użytkownika będzie używany, gdy określono parametr.|
|**Zakres**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić grupy chronionych obiektów polecenia cmdlet.|
|**IDENTYFIKATOR SID**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić unikatowy identyfikator, który reprezentuje podmiot zabezpieczeń.|
|**Zaufany**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, poziomy zaufania są obsługiwane, jeśli parametr jest określony.|
|**TrustLevel**<br>Typ danych: Słowo kluczowe|Implementowanie tego parametru, użytkownik może określić poziom zaufania, który jest obsługiwany. Na przykład możliwe wartości to internet, intranet i fulltrust.|

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
