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
## <a name="creating-a-powershell-gallery-account"></a>Tworzenie konta galerii programu PowerShell

Przed opublikowaniem niczego w galerii programu PowerShell, należy ustanowić konto galerii programu PowerShell.
Konta galerii programu PowerShell muszą być połączone z konta z włączoną obsługą poczty e-mail usługi Azure Active Directory lub konta e-mail firmy Microsoft (z domeny outlook.com, hotmail.com itp.)

Aby utworzyć konto w galerii programu PowerShell, przejdź do https://PowerShellGallery.com i wybierz polecenie "Register" (zobacz obraz poniżej).

![Zarejestruj nowe konto](./images/CreatingAccount-Register.png)

Na następnej stronie do korzystania z konta usługi Azure Active Directory, wybierz "Pracy lub konto służbowe" i zaloguj się przy użyciu swojego konta.
Aby użyć konta Microsoft - taki w domenie Hotmail.com lub Outlook.com — wybierz opcję "Osobiste konto" i logowania.

Po zalogowaniu, zostanie wyświetlony monit o utworzenie nazwę użytkownika dla galerii programu PowerShell.
Przejrzyj warunki użytkowania i zasady zachowania poufności informacji, które są połączone w, wprowadź nazwę użytkownika i kliknij przycisk Zarejestruj.

Uwaga: Nie można zmienić nazwy tego konta, po jego utworzeniu.
Zobacz [Zarządzanie właścicieli elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) Aby uzyskać więcej informacji związanych z tym.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Zalecane rozwiązania dla kont w galerii programu PowerShell

Należy pamiętać, że aktywnie monitorowanych konto e-mail używany przy użyciu konta z galerii programu PowerShell.
Wszystkie komunikat z właściciele elementów galerii programu PowerShell jest za pośrednictwem poczty e-mail, przy użyciu adresu skojarzonych z Twoim kontem galerii programu PowerShell.
Nie możemy skontaktować się z właścicielem elementu, zespół operacyjny może być konieczna usuwanie elementu w pewnych okolicznościach.

Organizacje, które publikują w galerii programu PowerShell często tworzyć unikatowe konto w tym celu w usłudze Outlook.com lub innej domeny konta Microsoft.
W wielu przypadkach to konto nie jest regularnie monitorowane.
W takim przypadku najlepszym rozwiązaniem jest Wyślij wiadomość e-mail na inne konto, zazwyczaj w jednej organizacji, który ma być monitorowany przez jego właściciela elementu za pomocą programu Outlook przekazywania.

W przypadku wielu właścicieli skojarzony z elementem korespondencji, które pochodzą z galerii programu PowerShell przejdzie do wszystkich właścicieli.
Zobacz [Zarządzanie właścicieli elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) Aby uzyskać więcej informacji na temat dodawania właścicieli do elementu.