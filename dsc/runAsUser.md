---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Uruchomiony przy użyciu poświadczeń użytkownika usługi Konfiguracja DSC"
ms.openlocfilehash: 11c13d852b506be3e202b798d135eba73d84cfe0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="running-dsc-with-user-credentials"></a>Uruchomiony przy użyciu poświadczeń użytkownika usługi Konfiguracja DSC 

> Dotyczy: Środowiska Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1

Zasób DSC pod określony zestaw poświadczeń, można uruchomić przy użyciu automatycznego **PsDscRunAsCredential** właściwości w konfiguracji. Domyślnie DSC uruchamiane każdego zasobu jako konta systemowego.
Brak razy podczas udostępniania działający jako użytkownik jest to konieczne, takich jak instalowanie pakiety MSI w kontekście użytkownika, ustawienie kluczy rejestru użytkownika, uzyskiwanie dostępu do określonego katalogu lokalnego użytkownika lub uzyskiwania dostępu do sieci.

Każdy zasób DSC ma **PsDscRunAsCredential** właściwość, która może być ustawiony na wszystkie poświadczenia użytkownika ( [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) obiektu).
Poświadczenia mogą być ustalony jako wartość właściwości w konfiguracji lub możesz ustawić wartość [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), który zostanie monit o podanie poświadczeń podczas kompilowania (Aby uzyskać informacje o konfiguracji Trwa kompilowanie konfiguracji, zobacz [konfiguracje](configurations.md).

>**Uwaga:** w programie PowerShell 5.0, za pomocą **PsDscRunAsCredential** właściwości w konfiguracjach wywoływania złożonego zasobów nie jest obsługiwana. 
>W programie PowerShell 5.1 **PsDscRunAsCredential** właściwość jest obsługiwana w konfiguracjach wywoływania złożonego zasobów.

>**Uwaga:** **PsDscRunAsCredential** właściwość nie jest dostępna w programie PowerShell w wersji 4.0.

W poniższym przykładzie **Get-Credential** jest używany w celu monitowania użytkownika o podanie poświadczeń. [Rejestru](registryResource.md) zasobu służy do zmiany klucza rejestru, który określa kolor tła dla okna wiersza polecenia systemu Windows.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Uwaga:** w tym przykładzie założono, że prawidłowy certyfikat w `C:\publicKeys\targetNode.cer`, oraz że odcisk palca certyfikatu jest wartość wyświetlana.
>Aby uzyskać informacje dotyczące szyfrowania poświadczeń w pliki MOF konfiguracji DSC, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).

