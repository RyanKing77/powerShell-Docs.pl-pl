---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Znane problemy w programie WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084967"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="2708e-103">Znane problemy w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2708e-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="2708e-104">Te informacje mogą się zmieniać.</span><span class="sxs-lookup"><span data-stu-id="2708e-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="2708e-105">Począwszy od skrótu programu PowerShell jako Administrator</span><span class="sxs-lookup"><span data-stu-id="2708e-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="2708e-106">Po zainstalowaniu programu WMF, jeśli zostanie podjęta próba Uruchom program PowerShell jako administrator za pomocą skrótu, może być wyświetlony komunikat "Z powodu nieokreślonego błędu".</span><span class="sxs-lookup"><span data-stu-id="2708e-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="2708e-107">Ponownie otwórz skrót jako użytkowników niebędących administratorami i działa teraz skrótów, nawet administrator.</span><span class="sxs-lookup"><span data-stu-id="2708e-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="2708e-108">Pester</span><span class="sxs-lookup"><span data-stu-id="2708e-108">Pester</span></span>

<span data-ttu-id="2708e-109">W tej wersji istnieją dwa problemy, których należy wiedzieć podczas na serwerze Nano Server przy użyciu usług Pester:</span><span class="sxs-lookup"><span data-stu-id="2708e-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="2708e-110">Uruchamianie testów przeciwko usług Pester sam może spowodować niektóre błędy z powodu różnic między CLR pełnej i CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="2708e-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="2708e-111">W szczególności metoda sprawdzania poprawności jest niedostępna dla typu obiektu XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="2708e-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="2708e-112">Wiadomo, że sześciu testy, które próbuje sprawdzić schematu NUnit dzienniki wyjściowe powinny się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="2708e-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="2708e-113">Jeden test pokrycia kodu nie działa obecnie, ponieważ *WindowsFeature* zasób DSC nie istnieje na serwerze Nano Server.</span><span class="sxs-lookup"><span data-stu-id="2708e-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="2708e-114">Jednak te błędy są zazwyczaj niegroźne i można bezpiecznie zignorować.</span><span class="sxs-lookup"><span data-stu-id="2708e-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="2708e-115">Sprawdzenie poprawności operacji</span><span class="sxs-lookup"><span data-stu-id="2708e-115">Operation Validation</span></span>

- <span data-ttu-id="2708e-116">`Update-Help` nie powiodło się dla modułu Microsoft.PowerShell.Operation.Validation ze względu na wolne od pracy Pomoc identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="2708e-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="2708e-117">DSC po Odinstaluj program WMF</span><span class="sxs-lookup"><span data-stu-id="2708e-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="2708e-118">Odinstalowywanie programu WMF nie powoduje usunięcia dokumentów DSC MOF z folderu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2708e-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="2708e-119">DSC nie będzie działać prawidłowo, jeśli dokumenty MOF zawiera nowszą właściwości, które nie są dostępne w starszych systemach.</span><span class="sxs-lookup"><span data-stu-id="2708e-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="2708e-120">W takim przypadku uruchom następujący skrypt z podwyższonym poziomem uprawnień konsoli PowerShell, aby wyczyścić stany DSC.</span><span class="sxs-lookup"><span data-stu-id="2708e-120">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="2708e-121">Kont wirtualnych JEA</span><span class="sxs-lookup"><span data-stu-id="2708e-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="2708e-122">Punktów końcowych JEA i konfiguracjami sesji skonfigurowany do używania kont wirtualnych w programie WMF 5.0 nie zostanie skonfigurowany do używania konta wirtualnego po uaktualnieniu do wersji programu WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="2708e-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="2708e-123">Oznacza to, że polecenia uruchamiane w sesjach JEA będzie uruchamiana tożsamości użytkownik nawiązujący połączenie, a nie tymczasowego konta administratora, potencjalnie uniemożliwianie uruchamiania poleceń, które wymagają podniesionych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2708e-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="2708e-124">Aby przywrócić kont wirtualnych, musisz wyrejestrować i ponownie zarejestrować konfiguracji sesji, które używać kont wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="2708e-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```