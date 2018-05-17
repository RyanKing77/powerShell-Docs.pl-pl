---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxUser zasobów
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC dla systemu Linux nxUser zasobów

**NxUser** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania użytkowników lokalnych w węźle systemu Linux.

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

|  Właściwość |  Wskazuje nazwę konta, dla którego chcesz zapewnić z określonym stanem. |
|---|---|
| UserName| Określa lokalizację, w której chcesz zapewnić stan pliku lub katalogu.|
| Upewnij się| Określa, czy konto istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że konto istnieje i ustaw ją na "Brak", aby upewnić się, że konto nie istnieje.|
| Imię i nazwisko| Ciąg, który zawiera pełną nazwę dla konta użytkownika.|
| Opis| Opis konta użytkownika.|
| Hasło| Skrót hasła użytkownika w postaci odpowiednie dla tego komputera. Zazwyczaj jest to solone algorytmu SHA-256 lub wyznaczania wartości skrótu SHA-512. Debian i Ubuntu Linux tę wartość można wygenerować za pomocą polecenia mkpasswd. Dla innych dystrybucjach systemu Linux można wygenerować skrót metoda crypt biblioteki Crypt języka Python.|
| Wyłączone| Wskazuje, czy konto jest włączone. Ta właściwość jest ustawiana **$true** aby upewnić się, że to konto jest wyłączone i ustaw ją na **$false** aby upewnić się, że jest włączone.|
| PasswordChangeRequired| Wskazuje, czy użytkownik może zmienić hasło. Ta właściwość jest ustawiana **$true** aby upewnić się, że użytkownik nie można zmienić hasło i ustaw ją na **$false** umożliwia użytkownikowi zmianę hasła. Wartość domyślna to **$false**. Ta właściwość jest oceniana tylko wtedy, jeśli konto użytkownika nie istniał wcześniej i jest tworzona.|
| Parametr Katalog_macierzysty| Katalogu macierzystego użytkownika.|
| Identyfikator grupy| Identyfikator grupy podstawowej dla użytkownika.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić jest najpierw "ResourceName", jego typ to "Typu zasobu" Składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

Poniższy przykład gwarantuje, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".

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