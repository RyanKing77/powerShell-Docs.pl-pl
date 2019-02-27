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
# <a name="security-parameters"></a>Parametry zabezpieczeń

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów można uzyskać informacje dotyczące operacji, takich jak parametry, które określają informacje o certyfikacie klucza i uprawnień zabezpieczeń.

Typ danych listy ACL: Ciąg

Implementowanie tego parametru, aby określić poziom kontroli dostępu, ochrony dla wykazu lub uzyskać jednolite zasobów identyfikator (URI).

Typ danych CertFile: Ciąg

Implementowanie tego parametru, aby użytkownik może określić nazwę pliku, który zawiera jeden z następujących czynności:

- Certyfikatu x.509 z kodowaniem Base64 lub wyróżniającą reguły DER (Encoding)

- Plik publicznego klucza (PKCS Cryptography Standards) #12, który zawiera co najmniej jeden certyfikat i klucz

Typ danych CertIssuerName: Ciąg

Ten parametr należy zaimplementować tak, aby użytkownik może określić nazwę wystawcy certyfikatu lub dlatego, że użytkownik może określić podciąg.

Typ danych CertRequestFile: Ciąg

Implementuje ten parametr, aby określić nazwę pliku zawierającego żądanie certyfikatu w formacie Base64 lub PKCS #10 szyfrowanego algorytmem DER.

Typ danych CertSerialNumber: Ciąg

Implementuje ten parametr, aby określić numer seryjny, który został wystawiony przez urząd certyfikacji.

Typ danych elementy CertStoreLocation: Ciąg

Implementowanie tego parametru, użytkownik może określić lokalizację magazynu certyfikatów. Lokalizacja jest zwykle ścieżki do pliku.

Typ danych CertSubjectName: Ciąg

Ten parametr należy zaimplementować tak, aby użytkownik może określić wystawca certyfikatu, lub tak, aby użytkownik może określić podciąg.

Typ danych CertUsage: Ciąg

Implementuje ten parametr, aby określić użycia klucza lub rozszerzone użycie klucza. Klucz może być reprezentowany jako bit maski, nieco, identyfikator obiektu (OID) lub ciąg.

Dane poświadczeń, wpisz: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)

Implementowanie tego parametru polecenia cmdlet zostanie automatycznie wyświetlony monit o nazwę użytkownika lub hasło. Jeśli nie podano bezpośrednio pełne poświadczenia, zostanie wyświetlony monit dla obu.

Typ danych NazwaCSP: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwę dostawcy usług certyfikatów (CSP).

Typ danych CSPType: Liczba całkowita

Implementowanie tego parametru, użytkownik może określić typu dostawcy usług Kryptograficznych.

Typ danych grupy: Ciąg

Implementowanie tego parametru, użytkownik może określić zbiór jednostek, aby uzyskać dostęp. Aby uzyskać więcej informacji, zobacz opis `Principal` parametru.

Typ danych KeyAlgorithm: Ciąg

Implementowanie tego parametru, użytkownik może określić algorytm generowania kluczy, który ma być używany dla zabezpieczeń.

Typ danych NazwaKonteneraKlucza: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwę kontenera kluczy.

Typ danych długość klucza: Liczba całkowita

Implementowanie tego parametru, użytkownik może określić długość klucza w bitach.

Typ danych operacji: Ciąg

Implementowanie tego parametru, użytkownik może określić akcję, która może być wykonana w chronionym obiekcie.

Typ danych jednostki: Ciąg

Implementowanie tego parametru, użytkownik może określić unikatowe jednostki do zidentyfikowania dostępu.

Typ danych uprawnień: Ciąg

Implementowanie tego parametru, użytkownik może określić po prawej stronie, polecenie cmdlet musi wykonać operację dla określonego obiektu.

Typ danych uprawnień: Tablica uprawnień

Implementowanie tego parametru, użytkownik może określić prawa, które polecenie cmdlet musi wykonać jego działania dla określonego wpisu.

Typ danych dla roli: Ciąg

Implementowanie tego parametru, użytkownik może określić zestaw operacji, które mogą być wykonywane przez podmiot.

Typ danych SaveCred: SwitchParameter

Implementowanie tego parametru poświadczenia, które zostały wcześniej zapisane przez użytkownika będzie używany, gdy określono parametr.

Typ danych w zakresie: Ciąg

Implementowanie tego parametru, użytkownik może określić grupy chronionych obiektów polecenia cmdlet.

Typ danych identyfikator SID: Ciąg

Implementowanie tego parametru, użytkownik może określić unikatowy identyfikator, który reprezentuje podmiot zabezpieczeń.

Zaufane — typ danych: SwitchParameter

Implementowanie tego parametru, poziomy zaufania są obsługiwane, jeśli parametr jest określony.

Typ danych TrustLevel: Słowo kluczowe

Implementowanie tego parametru, użytkownik może określić poziom zaufania, który jest obsługiwany. Na przykład możliwe wartości to internet, intranet i fulltrust.

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
