---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Tworzenie konta galerii programu PowerShell
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084216"
---
# <a name="creating-a-powershell-gallery-account"></a>Tworzenie konta galerii programu PowerShell

Przed opublikowaniem niczego w galerii programu PowerShell, należy utworzyć konto galerii programu PowerShell.
Konta galerii programu PowerShell musi być połączony z kontem e-mail logowania. To konto może być kontem usługi Azure Active Directory lub Identyfikatora firmy Microsoft, takich jak konta e-mail z usługi outlook.com lub hotmail.com.

Tworzenie konta galerii programu PowerShell, przejdź do [ https://PowerShellGallery.com ](https://PowerShellGallery.com) i kliknij pozycję **Zaloguj** jak pokazano na poniższej ilustracji.

![Rejestrowanie nowego konta](../../Images/CreateAccount-Register.png)

Aby użyć konta usługi Azure Active Directory, zaznacz **konta służbowego**i zaloguj się przy użyciu swojego konta. Aby użyć Identyfikatora firmy Microsoft, wybierz **konto osobiste** i zaloguj się.

Następnie monit Utwórz nazwę użytkownika dla galerii programu PowerShell. Przejrzyj warunki użytkowania i zasady zachowania poufności informacji, wprowadź nazwę użytkownika, a następnie kliknij **zarejestrować**.

> [!NOTE]
> Nie można zmienić nazwę konta, po jego utworzeniu. Aby uzyskać więcej informacji, zobacz [właścicieli pakietu zarządzania](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Zalecane praktyki dla kont z galerii programu PowerShell

Jest to ważne, aby aktywnie monitoruje konto e-mail użyte przy użyciu konta z galerii programu PowerShell. Cała komunikacja z właścicielami pakietów galerii programu PowerShell jest za pośrednictwem tego adresu e-mail. Jeśli zespół operacyjny galerii programu PowerShell nie może skontaktować się z właścicielem pakietu, firma Microsoft może wymagać usunięcia pakietu.

Organizacje, które często publikowanie w galerii programu PowerShell utworzyć unikatowe konto zewnętrzne do tego celu. Zaleca się, że używasz przesyłanie dalej poczty e-mail do przesyłania powiadomień na adres w Twojej organizacji.

W przypadku wielu właścicielom są skojarzone z pakietem, wszystkie powiadomienia galerii programu PowerShell są wysyłane do wszystkich właścicieli. Aby uzyskać więcej informacji, zobacz [właścicieli pakietu zarządzania](managing-package-owners.md).
