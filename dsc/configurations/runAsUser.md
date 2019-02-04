---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Używanie poświadczeń z zasobami DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686852"
---
# <a name="use-credentials-with-dsc-resources"></a>Używanie poświadczeń z zasobami DSC

> Dotyczy: Windows PowerShell 5.0, Windows PowerShell 5.1

Zasób DSC określony zestaw poświadczeń, można uruchomić za pomocą automatycznego **PsDscRunAsCredential** właściwości w konfiguracji.
Domyślnie DSC jest uruchamiane poszczególne zasoby za pomocą konta system.
Istnieją terminy, podczas udostępniania działający jako użytkownik, jest to konieczne, takich jak instalowanie pakietów MSI w kontekście określonego użytkownika, ustawienie kluczy rejestru użytkownika, uzyskiwanie dostępu do określonego katalogu lokalnego użytkownika lub uzyskiwania dostępu do sieci.

Każdy zasób DSC ma **PsDscRunAsCredential** właściwości, które można ustawić żadnych poświadczeń użytkownika ( [PSCredential](/dotnet/api/system.management.automation.pscredential) obiektu).
Poświadczenia mogą być zakodowane jako wartość właściwości w konfiguracji lub wartość można ustawić, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), który zostanie wyświetlony monit o poświadczenia podczas kompilowania (Aby uzyskać informacje o konfiguracji kompilowanie konfiguracji, zobacz [konfiguracje](configurations.md).

> [!NOTE]
> W programie PowerShell 5.0, za pomocą **PsDscRunAsCredential** właściwości w konfiguracji wywoływania zasoby złożone nie jest obsługiwana.
> W programie PowerShell 5.1 **PsDscRunAsCredential** właściwość jest obsługiwana w konfiguracjach wywoływania zasoby złożone.
> **PsDscRunAsCredential** właściwość nie jest dostępna w programie PowerShell 4.0.

W poniższym przykładzie `Get-Credential` jest używany w celu wyświetlenia monitu o podanie poświadczeń użytkownika.
**Rejestru** zasobów służy do zmiany klucza rejestru, który określa kolor tła okna wiersza polecenia Windows.

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

> [!NOTE]
> W tym przykładzie założono, że prawidłowy certyfikat na `C:\publicKeys\targetNode.cer`, i że odcisk palca certyfikatu jest wartość wyświetlana.
> Aby dowiedzieć się, jak szyfrowania poświadczeń w plikach MOF konfiguracji DSC, zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md).
