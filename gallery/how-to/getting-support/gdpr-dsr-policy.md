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
ms.locfileid: "34189758"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Zgodność GDPR galerii programu PowerShell

## <a name="overview"></a>Przegląd

W 2018 maja prawo Europejskiego prywatności, ogólne dane ochrony rozporządzenia (GDPR), zostanie zastosowana.
GDPR nakłada nowe zasady dotyczące firmy, agencji rządowych z systemem innym niż zysków i innymi organizacjami, że oferta towarów i usług do osób w Unii Europejskiej (UE), lub że zbieranie i analizowanie danych powiązane mieszkańców Unii Europejskiej.
Stosuje GDPR niezależnie od tego, w którym znajduje się.

> [!NOTE]
> W tym artykule instrukcje dotyczące sposobu usunięcia danych osobowych z galerii programu PowerShell i może służyć do obsługi sieci zobowiązań GDPR. Jeśli szukasz informacji ogólnych o GDPR zobacz [GDPR części portalu zaufania usługi](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Identyfikowalne dane osobowe danych

Poniższe informacje, które mogą być udostępniane przez użytkowników, którzy mogą zawierać informacje osobiste są przechowywane w galerii programu PowerShell:

* Konto galerii programu PowerShell
* Elementy opublikowany w galerii programu PowerShell
* Wiadomości e-mail korespondencji z zespołem galerii programu PowerShell

Większość użytkowników nie należy tworzyć konta galerii programu PowerShell.
Konto nie jest wymagany, chyba że chcesz opublikować element lub funkcja "Skontaktuj się z właścicielem" w galerii programu PowerShell.
Inne niż wiadomości e-mail korespondencji zainicjowanej przez użytkownika galerii programu PowerShell nie przechowuje dane osobowe dla użytkowników, którzy nie utworzono konta.

Użytkownicy, którzy tworzą konta galerii programu PowerShell można publikować elementy galerii programu PowerShell.
Te elementy będą kod programu PowerShell, ale może zawierać inne informacje w tym informacji osobistych.
Poniższe informacje będą wyświetlane, jak wprowadzasz wszystkie elementy zostały opublikowane w galerii programu PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Eksport DSR danych galerii programu PowerShell

W poniższych sekcjach opisano sposób galerii programu PowerShell obsługuje żądania podmiotu danych (DSR), przez wyjaśniający wyeksportować informacje przechowywane w galerii programu PowerShell oraz sposobu zażądać usunięcia tych informacji.

### <a name="email"></a>Poczta e-mail

Zgodność poczty e-mail może zawierać żadnego z następujących czynności:

* Wysyłanie wiadomości e-mail do właścicieli galerii programu PowerShell, wystąpił problem z dowolny element, który został opublikowany w galerii programu PowerShell wykryte elementy, jeśli skanuje analizy kodu
* Wysyłanie wiadomości e-mail dla wszystkich użytkowników do zespołu galerii programu PowerShell przy użyciu adresu e-mail na stronie "Skontaktuj się z nami" (cgadmin@microsoft.com)
* Zarejestrowanych użytkowników, którzy korzystają z funkcji "Skontaktuj się z właścicielem" w galerii programu PowerShell do wysyłania wiadomości e-mail do właściciela elementu w galerii programu PowerShell

Wiadomości e-mail wysyłanych przez lub do galerii programu PowerShell mają zasady przechowywania 90 dni do obsługi dochodzenia potencjalne powinien odnajdowane złośliwego kodu w galerii programu PowerShell.
Wiadomości e-mail zostaną usunięte przez zasady po 90 dniach.

Aby zażądać kopie wszystkich wiadomości wysłanych do lub z adresu e-mail i galerii programu PowerShell w ciągu ostatnich 90 dni.
Aby zażądać tej korespondencji, Wyślij wiadomość e-mail do cgadmin@microsoft.com, o tytule: "Żądanie DSR odnoszących się do tego konta w wiadomości e-mail".
W treści komunikatu o stanie informacjach zażądano (na przykład: Wyślij wszystkie wiadomości e-mail wysyłane do lub z tego adresu e-mail.) Wszystkie wiadomości e-mail, obejmujących adres e-mail w ciągu 90 dni żądanie zostanie wysłane w ciągu 7 dni roboczych.

### <a name="powershell-gallery-account-information"></a>Informacje o koncie w galerii programu PowerShell

Jeśli po utworzeniu konta galerii programu PowerShell, można znaleźć wszystkie informacje osobiste, które były przechowywane w galerii programu PowerShell, wykonując następujące czynności:

1. Zaloguj się do galerii programu PowerShell, a następnie kliknij swoją nazwę użytkownika
2. Następna strona wyświetlana jest strona konta, przedstawiający adres e-mail dla konta galerii programu PowerShell

Jeśli więcej niż jedno konto utworzone w galerii programu PowerShell, należy powtórzyć te kroki dla każdego konta.

### <a name="items-in-the-powershell-gallery"></a>Elementy w galerii programu PowerShell

W celu ułatwienia eksportowanie elementów opublikowany w galerii programu PowerShell, możemy skryptu "GetPSGalleryItemsForAuthor" został opublikowany w galerii programu PowerShell.
Ten skrypt Eksportuje kopię każdej wersji każdy element umieścić w galerii programu PowerShell, na podstawie informacji autora przechowywane w elemencie.

> [!NOTE]
> Autor są przechowywane w manifeście elementu podczas publikowania tego elementu.
> Nie ma żadnej gwarancji, że autor jest tej samej tożsamości co konto, którego używasz w galerii programu PowerShell.
> Jeśli używasz inną wartość w polu Autor, należy podać tę wartość, korzystając z tego skryptu.

Skrypt może pobrać za pomocą następującego polecenia programu PowerShell:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

Skrypt może następnie uruchom bezpośrednio, uruchamiając następujące polecenia programu PowerShell:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

Pojawi się monit autora i folderze w systemie, w którym ma elementy do zapisania.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Usuwanie danych osobowych z galerii programu PowerShell

Aby usunąć konto galerii programu PowerShell lub dowolny element posiadanych w galerii programu PowerShell, Wyślij wiadomość e-mail do cgadmin@microsoft.com o tytule: "GDPR żądań dla elementów odnoszących się do tego konta".
W treści komunikatu stanu, jakie informacje mają być usunięte. Przykład:

* Usuń x.y.z wersji mojej elementu "Nazwa elementu"
* Usuń wszystkie wersje elemencie "Nazwa elementu"
* Usuń konto galerii programu PowerShell

Administratorzy galerii programu PowerShell odpowie w ciągu 7 dni roboczych.
Określone elementy zostaną usunięte w ciągu 30 dni, po wysłaniu żądania.
