---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Przekazywanie opinii za pośrednictwem mediów społecznościowych i komentarzy
ms.openlocfilehash: 9e2a5a246b1caa37ad7b03e20c8f543b9e5cf530
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Przekazywanie opinii za pośrednictwem mediów społecznościowych i komentarzy

Galerii programu Powershell obsługuje dwa podejścia do użytkowników w celu zapewnienia publicznego opinii w elemencie:

* Użyj łącza do lewej krawędzi "Udostępnianie" element witryn mediów społecznościowych usługi Facebook, LinkedIn i Twitter.
* Funkcja komentarz na wysyłanie komentarzy w elemencie i umożliwia autorom obserwować komentarze na elementach, które publikują one.

## <a name="social-media-feedback"></a>Opinie mediów społecznościowych
W lewej części strony dla każdego elementu w galerii programu PowerShell istnieją łącza dla usługi Facebook, LinkedIn i Twitter.
Kliknięcie łącza zostanie Otwórz witrynę mediów społecznościowych i umożliwia szybkie udostępnianie łącze do elementu.

Użytkownikom należy zalogować się do witryny, które wybrały w celu udostępnienia elementu galerii programu PowerShell.

Zaleca się jeśli one okazać, że element jest coś, co spowoduje zaleca się do innych użytkowników.
Galerii programu PowerShell zostanie Sprawdź każdej lokacji mediów społecznościowych dla "udziały" elementu i wyświetlania jak wiele razy element został udostępniony w każdej lokacji mediów społecznościowych.
Ponieważ ten pokazuje tylko liczbę razy został udostępniony coś, będzie interpretowany innym użytkownikom jako element "liking".


## <a name="comments"></a>Komentarze
Galerii programu PowerShell korzysta z usługi LiveFyre, aby użytkownicy mogli dodać komentarz dotyczący elementów.
Użytkownicy, którzy mają zalecenia lub opinie można użyć tej funkcji do przekazywania opinii, który jest widoczny dla wszystkich osób odwiedzających stronę elementu.
Właściciele elementów można wykonać tej opinii i otrzymać powiadomienie, gdy ktoś zapisuje komentarz.

System komentarz jest oparty na LiveFyre, czyli oddzielne usługa, która nie jest zarządzany przez firmę Microsoft i wymaga unikatowy logowanie.
Po raz pierwszy użytkownik zostawi komentarz lub wykonaj komentarze na jednym z elementów, zostanie wyświetlony monit o utworzenie konta LiveFyre.

Jeśli użytkownik utworzył konto LiveFyre i zalogowany, można sformułować komentarz, który wyświetla informacje o elemencie, należy kliknąć opcję "Post komentarz..." Komentarz nie będą widoczne natychmiast.
Komentarze dotyczące elementy galerii są moderowane przez administratorów galerii programu PowerShell, a wszystkie wpisy zostaną zweryfikowane przez moderatorów przed opublikowanych i są widoczne dla innych użytkowników.
Naszym celem w Moderowanie komentarzy jest upewnij się, że są wyrównane z publicznego zachowanie zgodne z galerii programu PowerShell [warunki użytkowania](https://www.powershellgallery.com/policies/Terms).

Właściciele elementów są zachęcani do wykonaj komentarze, które są wysyłane do LiveFyre.
Wymagane jest konto LiveFyre i zaleca się używają tego samego adresu e-mail używanego do publikowania w LiveFyre tego elementu.
Aby wykonać komentarze, zaloguj się do LiveFyre i przejdź do dowolny element, w którym są wyświetlane jako właściciela.
Poniżej pola komentarz u dołu każdego elementu można będzie się w temacie "+ wykonaj".
Po kliknięciu to LiveFyre spowoduje wysłanie wiadomości e-mail na adres e-mail zarejestrowany czas nowych uwag wprowadzone w elemencie.