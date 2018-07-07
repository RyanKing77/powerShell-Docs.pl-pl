---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Uruchamianie platformy DSC przy użyciu poświadczeń użytkownika
ms.openlocfilehash: 4a6c3d8b561cd0a27be07a68f1b577f7bf764254
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893913"
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="6ca81-103">Uruchamianie platformy DSC przy użyciu poświadczeń użytkownika</span><span class="sxs-lookup"><span data-stu-id="6ca81-103">Running DSC with user credentials</span></span>

> <span data-ttu-id="6ca81-104">Dotyczy: Windows PowerShell 5.0, programu Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="6ca81-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="6ca81-105">Zasób DSC określony zestaw poświadczeń, można uruchomić za pomocą automatycznego **PsDscRunAsCredential** właściwości w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6ca81-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="6ca81-106">Domyślnie DSC jest uruchamiane poszczególne zasoby za pomocą konta system.</span><span class="sxs-lookup"><span data-stu-id="6ca81-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="6ca81-107">Istnieją terminy, podczas udostępniania działający jako użytkownik, jest to konieczne, takich jak instalowanie pakietów MSI w kontekście określonego użytkownika, ustawienie kluczy rejestru użytkownika, uzyskiwanie dostępu do określonego katalogu lokalnego użytkownika lub uzyskiwania dostępu do sieci.</span><span class="sxs-lookup"><span data-stu-id="6ca81-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="6ca81-108">Każdy zasób DSC ma **PsDscRunAsCredential** właściwości, które można ustawić żadnych poświadczeń użytkownika ( [PSCredential](/dotnet/api/system.management.automation.pscredential) obiektu).</span><span class="sxs-lookup"><span data-stu-id="6ca81-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="6ca81-109">Poświadczenia mogą być zakodowane jako wartość właściwości w konfiguracji lub wartość można ustawić, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), który zostanie wyświetlony monit o poświadczenia podczas kompilowania (Aby uzyskać informacje o konfiguracji kompilowanie konfiguracji, zobacz [konfiguracje](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6ca81-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE] 
> <span data-ttu-id="6ca81-110">W programie PowerShell 5.0, za pomocą **PsDscRunAsCredential** właściwości w konfiguracji wywoływania zasoby złożone nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="6ca81-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="6ca81-111">W programie PowerShell 5.1 **PsDscRunAsCredential** właściwość jest obsługiwana w konfiguracjach wywoływania zasoby złożone.</span><span class="sxs-lookup"><span data-stu-id="6ca81-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="6ca81-112">**PsDscRunAsCredential** właściwość nie jest dostępna w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6ca81-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="6ca81-113">W poniższym przykładzie `Get-Credential` jest używany w celu wyświetlenia monitu o podanie poświadczeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6ca81-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="6ca81-114">[Rejestru](registryResource.md) zasobów służy do zmiany klucza rejestru, który określa kolor tła okna wiersza polecenia Windows.</span><span class="sxs-lookup"><span data-stu-id="6ca81-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="6ca81-115">W tym przykładzie założono, że prawidłowy certyfikat na `C:\publicKeys\targetNode.cer`, i że odcisk palca certyfikatu jest wartość wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="6ca81-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="6ca81-116">Aby dowiedzieć się, jak szyfrowania poświadczeń w plikach MOF konfiguracji DSC, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6ca81-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>
