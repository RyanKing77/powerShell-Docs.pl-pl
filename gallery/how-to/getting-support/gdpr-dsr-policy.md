---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria programu powershell, galerii programu PowerShell, RODO
title: Zgodność z RODO galerii programu PowerShell
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687818"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Zgodność z RODO galerii programu PowerShell

## <a name="overview"></a>Omówienie

W maju 2018 europejskie prawo ochrony prywatności, ogólne danych (GDPR Protection Regulation), weszło w życie.
Rozporządzenie GDPR nakłada nowe zasady dotyczące firm, agencji rządowych, non-profit i innych organizacji oferty towary i usługi osobom w Unii Europejskiej (UE) lub że zbieranie i analizujących dane związane z osobami mieszkającymi w UE.
Niezależnie od tego, w którym znajduje się stosuje się GDPR.

> [!NOTE]
> Ten artykuł zawiera instrukcje dotyczące sposobu usuwania danych osobowych z galerii programu PowerShell i może służyć do obsługi zobowiązania w RODO. Jeśli szukasz ogólne informacje na temat rozporządzenia RODO, zobacz [RODO części portal zaufania usługi](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Identyfikowalnych danych umożliwiających identyfikację użytkownika

Następujące informacje, które mogą być udostępniane przez użytkowników, którzy mogą zawierać informacje osobiste są przechowywane w galerii programu PowerShell:

- Konta z galerii programu PowerShell
- Pakiety opublikowane w galerii programu PowerShell
- Adres e-mail korespondencji z zespołem galerii programu PowerShell

Większość użytkowników nie należy tworzyć konta galerii programu PowerShell.
Konto nie jest wymagany, chyba że zamierzasz opublikować pakiet lub funkcja "Skontaktuj się z właścicielem" w galerii programu PowerShell.
Inne niż korespondencja e-mail zainicjowanej przez użytkownika galerii programu PowerShell nie przechowuje identyfikowalne dane dla użytkowników, którzy nie zostały utworzone konto.

Użytkownicy, którzy Tworzenie konta galerii programu PowerShell mogą publikować pakiety galerii programu PowerShell.
Te pakiety powinny być kod programu PowerShell, ale może zawierać inne informacje w tym informacje osobiste.
Poniższe informacje pokaże, jak możesz uzyskać wszystkie pakiety zostały opublikowane w galerii programu PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Żądanie praw podmiotu danych Eksport danych galerii programu PowerShell

W poniższych sekcjach opisano, jak obsługuje żądania podmiotów danych (DSR) w galerii programu PowerShell, ponieważ wyjaśnia sposób eksportowania informacji przechowywanych w galerii programu PowerShell oraz zażądać usunięcia tych informacji.

### <a name="email"></a>Poczta e-mail

Korespondencja e-mail może zawierać żadnego z następujących czynności:

- Wysyłanie wiadomości e-mail do właścicieli z galerii programu PowerShell, pakietów, jeśli skanuje analizy kodu wykrył problem z dowolnego pakietu, który został opublikowany w galerii programu PowerShell
- Wysyłanie wiadomości e-mail dla wszystkich osób do zespołu galerii programu PowerShell przy użyciu adresu e-mail, na stronie "Skontaktuj się z nami" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Liczba zarejestrowanych użytkowników, którzy korzystają z funkcji "Skontaktuj się z właścicielem" w galerii programu PowerShell do wysyłania wiadomości e-mail do właściciela pakiet w galerii programu PowerShell

Wiadomości e-mail wysyłane przez lub w galerii programu PowerShell trzeba zasady przechowywania 90 dni obsługuje dochodzeń możliwych zabezpieczeniami powinny złośliwego kodu zostać wykryte w galerii programu PowerShell.
Wiadomości e-mail zostaną usunięte przez zasady po upływie 90 dni.

Może żądać kopiuje wszystkie wiadomości e-mail wysyłane do i z adresu e-mail i galerii programu PowerShell w ciągu ostatnich 90 dni.
Aby zażądać tej korespondencji, Wyślij wiadomość e-mail do [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), z tytułem: "DSR"żądania dla wiadomości e-mail, odnoszące się do tego konta.
W treści komunikatu o stanie informacjach żądasz (na przykład: Wyślij wszystkie wiadomości e-mail wysyłane do lub odebrane z tego adresu e-mail.) Wszystkie wiadomości e-mail, obejmujących adres e-mail w ciągu 90 dni żądanie zostanie wysłane w ciągu 7 dni roboczych.

### <a name="powershell-gallery-account-information"></a>Informacje o koncie w galerii programu PowerShell

Jeśli utworzono konto galerii programu PowerShell można znaleźć wszystkie informacje osobiste, które zostały zapisane w galerii programu PowerShell, wykonując następujące czynności:

1. Zaloguj się do galerii programu PowerShell, a następnie kliknij swoją nazwę użytkownika
2. Następnej stronie wyświetlana jest strona konta zawiera adres e-mail używany dla konta galerii programu PowerShell

Jeśli więcej niż jedno konto utworzone w galerii programu PowerShell, należy powtórzyć te kroki dla każdego konta.

### <a name="packages-in-the-powershell-gallery"></a>Pakiety w galerii programu PowerShell

W celu ułatwienia eksportowania pakiety opublikowane w galerii programu PowerShell, opublikowaliśmy skrypt "GetPSGalleryItemsForAuthor" w galerii programu PowerShell.
Ten skrypt Eksportuje kopię każdej wersji pakietu, co umieścić w galerii programu PowerShell, w oparciu o informacje o autorze znajdujące się w pakiecie.

> [!NOTE]
> Autor jest przechowywany w manifeście pakietu podczas publikowania pakietu.
> Nie ma żadnej gwarancji, że autor jest ta sama tożsamość jako konto, którego używasz w galerii programu PowerShell.
> Jeśli używasz inną wartość w polu autora, należy podać tę wartość, korzystając z tego skryptu.

Skrypt może pobrać za pomocą następującego polecenia programu PowerShell:

```powershell
Save-Script Get-repository psgallery
```

Skrypt można uruchomić następnie bezpośrednio, uruchamiając następujące polecenia środowiska PowerShell:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Zostanie wyświetlony monit podanie autora i folder w systemie, w którego pakiety mają być zapisywane.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Usuwanie danych osobowych z galerii programu PowerShell

Aby usunąć konto z galerii programu PowerShell lub dowolnego pakietu, jesteś właścicielem w galerii programu PowerShell, Wyślij wiadomość e-mail do cgadmin@microsoft.com o tytule: "RODO"żądania dla elementów odnoszących się do tego konta.
W treści komunikatu o stanie, jakie informacje mają być usunięte. Przykład:

- Usuń wersję x.y.z Mój pakiet "pakiet name"
- Usuń wszystkie wersje Mój pakiet "pakiet name"
- Usuń Moje konto galerii programu PowerShell

Administratorzy galerii programu PowerShell odpowie w ciągu 7 dni roboczych.
Pakiety określone zostaną usunięte w ciągu 30 dni po wysłaniu żądania.
