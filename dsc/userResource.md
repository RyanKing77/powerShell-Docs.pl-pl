---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób użytkownika DSC"
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a>Zasób użytkownika DSC #

 
>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0


__Użytkownika__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania kont użytkowników lokalnych w docelowym węźle.


##<a name="syntax"></a>Składnia ##

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
| UserName| Wskazuje nazwę konta, dla którego chcesz zapewnić z określonym stanem.| 
| Opis| Określa opis, który ma być używany dla konta użytkownika.| 
| Wyłączone| Wskazuje, czy konto jest włączone. Ta właściwość jest ustawiana __$true__ aby upewnić się, że to konto jest wyłączone i ustaw ją na __$false__ aby upewnić się, że jest włączone.| 
| Upewnij się| Wskazuje, czy konto istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że konto istnieje i ustaw ją na "Brak", aby upewnić się, że konto nie istnieje.| 
| Imię i nazwisko| Określa ciąg z pełną nazwę, który ma być używany dla konta użytkownika.| 
| Hasło| Wskazuje hasło, którego chcesz użyć dla tego konta. | 
| PasswordChangeNotAllowed| Wskazuje, czy użytkownik może zmienić hasło. Ta właściwość jest ustawiana __$true__ aby upewnić się, że użytkownik nie można zmienić hasło i ustaw ją na __$false__ umożliwia użytkownikowi zmianę hasła. Wartość domyślna to __$false__.| 
| PasswordChangeRequired| Wskazuje, czy użytkownik musi zmienić hasło przy następnym logowaniu. Ta właściwość jest ustawiana __$true__ Jeśli użytkownik musi zmienić hasło. Wartość domyślna to __$true__.| 
| PasswordNeverExpires| Wskazuje, czy hasło wygaśnie. Aby upewnić się, że hasło dla tego konta nigdy nie wygasa, ustawić tę właściwość na __$true__i ustaw ją na __$false__ Jeśli hasło wygaśnie. Wartość domyślna to __$false__.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.| 

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

