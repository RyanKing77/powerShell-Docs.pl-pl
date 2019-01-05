---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxUser
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048390"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC dla systemu Linux zasób nxUser

**NxUser** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania użytkowników lokalnych skonfigurowanych na węzeł systemu Linux.

## <a name="syntax"></a>Składnia

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Wskazuje nazwę konta, dla którego chcesz zapewnić określonego stanu. |
|---|---|
| UserName| Określa lokalizację, w którym chcesz upewnić się, stan dla pliku lub katalogu.|
| Upewnij się| Określa, czy konto istnieje. Ustaw tę właściwość na "Obecny", aby upewnić się, że konto istnieje i ustaw go na "Brak", aby upewnić się, że konto nie istnieje.|
| Imię i nazwisko| Ciąg, który zawiera pełną nazwę konta użytkownika.|
| Opis| Opis konta użytkownika.|
| Hasło| Skrót hasła użytkownika w odpowiednim formularzu komputera z systemem Linux. Zazwyczaj jest to solone algorytmu SHA-256 lub wyznaczania wartości skrótu SHA-512. W systemie Debian i Ubuntu Linux ta wartość może zostać wygenerowany za pomocą polecenia mkpasswd. Inne dystrybucje systemu Linux metoda crypt biblioteki kryptograficznego języka Python może służyć do generowania skrótów.|
| Wyłącz| Wskazuje, czy konto jest włączone. Ustaw tę właściwość na **$true** aby upewnić się, że to konto jest wyłączone i ustaw ją na **$false** aby upewnić się, że jest włączone.|
| PasswordChangeRequired| Wskazuje, czy użytkownik może zmienić hasła. Ustaw tę właściwość na **$true** aby upewnić się, że użytkownik nie może zmienić hasło i ustaw ją na **$false** umożliwia użytkownikowi zmianę hasła. Wartość domyślna to **$false**. Ta właściwość jest oceniane tylko, jeśli konto użytkownika nie istniał wcześniej i jest tworzona.|
| Parametr Katalog_macierzysty| Katalog macierzysty dla użytkownika.|
| Identyfikator grupy| Identyfikator grupy głównej dla użytkownika.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić najpierw jest "ResourceName" i jego typem jest "ResourceType", składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

Poniższy przykład zapewnia, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```