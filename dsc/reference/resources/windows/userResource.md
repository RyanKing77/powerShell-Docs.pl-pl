---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC użytkownika
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048569"
---
# <a name="dsc-user-resource"></a>Zasób DSC użytkownika

Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

**Użytkownika** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania kont użytkowników lokalnych w docelowym węźle.

## <a name="syntax"></a>Składnia

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| UserName| Wskazuje nazwę konta, dla którego chcesz zapewnić określonego stanu.|
| Opis| Określa opis, który ma być używana dla konta użytkownika.|
| Wyłącz| Wskazuje, czy konto jest włączone. Ustaw tę właściwość na `$true` aby upewnić się, że to konto jest wyłączone i ustaw ją na `$false` aby upewnić się, że jest włączone.|
| Upewnij się| Wskazuje, czy konto istnieje. Ustaw tę właściwość na "Obecny", aby upewnić się, że konto istnieje i ustaw go na "Brak", aby upewnić się, że konto nie istnieje.|
| Imię i nazwisko| Określa ciąg pełną nazwą, który ma być używana dla konta użytkownika.|
| Hasło| Wskazuje hasło, którego chcesz użyć dla tego konta. |
| PasswordChangeNotAllowed| Wskazuje, jeśli użytkownik może zmienić hasła. Ustaw tę właściwość na `$true` aby upewnić się, że użytkownik nie może zmienić hasło i ustaw ją na `$false` umożliwia użytkownikowi zmianę hasła. Wartość domyślna to `$false`.|
| PasswordChangeRequired| Wskazuje, jeśli użytkownik musi zmienić hasło podczas następnego logowania. Ustaw tę właściwość na `$true` Jeśli użytkownik musi zmienić hasło. Wartość domyślna to `$true`.|
| PasswordNeverExpires| Wskazuje, jeśli hasło wygaśnie. Aby upewnić się, że hasło dla tego konta nigdy nie wygasa, ustaw tę właściwość na `$true`i ustaw ją na `$false` Jeśli hasło wygaśnie. Wartość domyślna to `$false`.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```