---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Uruchamianie platformy DSC przy użyciu poświadczeń użytkownika
ms.openlocfilehash: b2992ad562dea375aba980611312c7b96a23189c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="7d3cb-103">Uruchamianie platformy DSC przy użyciu poświadczeń użytkownika</span><span class="sxs-lookup"><span data-stu-id="7d3cb-103">Running DSC with user credentials</span></span>

> <span data-ttu-id="7d3cb-104">Dotyczy: Środowiska Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1</span><span class="sxs-lookup"><span data-stu-id="7d3cb-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="7d3cb-105">Zasób DSC pod określony zestaw poświadczeń, można uruchomić przy użyciu automatycznego **PsDscRunAsCredential** właściwości w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="7d3cb-106">Domyślnie DSC uruchamiane każdego zasobu jako konta systemowego.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="7d3cb-107">Brak razy podczas udostępniania działający jako użytkownik jest to konieczne, takich jak instalowanie pakiety MSI w kontekście użytkownika, ustawienie kluczy rejestru użytkownika, uzyskiwanie dostępu do określonego katalogu lokalnego użytkownika lub uzyskiwania dostępu do sieci.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="7d3cb-108">Każdy zasób DSC ma **PsDscRunAsCredential** właściwość, która może być ustawiony na wszystkie poświadczenia użytkownika ( [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) obiektu).</span><span class="sxs-lookup"><span data-stu-id="7d3cb-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="7d3cb-109">Poświadczenia mogą być ustalony jako wartość właściwości w konfiguracji lub możesz ustawić wartość [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), który zostanie monit o podanie poświadczeń podczas kompilowania (Aby uzyskać informacje o konfiguracji Trwa kompilowanie konfiguracji, zobacz [konfiguracje](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="7d3cb-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="7d3cb-110">**Uwaga:** w programie PowerShell 5.0, za pomocą **PsDscRunAsCredential** właściwości w konfiguracjach wywoływania złożonego zasobów nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
><span data-ttu-id="7d3cb-111">W programie PowerShell 5.1 **PsDscRunAsCredential** właściwość jest obsługiwana w konfiguracjach wywoływania złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="7d3cb-112">**Uwaga:** **PsDscRunAsCredential** właściwość nie jest dostępna w programie PowerShell w wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="7d3cb-113">W poniższym przykładzie **Get-Credential** jest używany w celu monitowania użytkownika o podanie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span>
<span data-ttu-id="7d3cb-114">[Rejestru](registryResource.md) zasobu służy do zmiany klucza rejestru, który określa kolor tła dla okna wiersza polecenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="7d3cb-115">**Uwaga:** w tym przykładzie założono, że prawidłowy certyfikat w `C:\publicKeys\targetNode.cer`, oraz że odcisk palca certyfikatu jest wartość wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="7d3cb-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="7d3cb-116">Aby uzyskać informacje dotyczące szyfrowania poświadczeń w pliki MOF konfiguracji DSC, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="7d3cb-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>