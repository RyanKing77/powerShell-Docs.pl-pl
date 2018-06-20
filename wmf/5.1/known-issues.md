---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Znane problemy w WMF 5.1
ms.openlocfilehash: d53031bea978087c68fcb22989c7cd2e2cf2d9fa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219457"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="f43d2-103">Znane problemy w WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f43d2-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="f43d2-104">Uwaga: Jest te informacje mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="f43d2-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="f43d2-105">Uruchamianie skrótów programu PowerShell jako Administrator</span><span class="sxs-lookup"><span data-stu-id="f43d2-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="f43d2-106">Po zainstalowaniu pakietu WMF, Jeśli spróbujesz Uruchom program PowerShell jako administrator z skrótu, może wystąpić komunikat "Nieokreślony błąd".</span><span class="sxs-lookup"><span data-stu-id="f43d2-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="f43d2-107">Otwórz ponownie skrót jako bez uprawnień administratora i działa teraz skrót nawet jako administrator.</span><span class="sxs-lookup"><span data-stu-id="f43d2-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="f43d2-108">Pester</span><span class="sxs-lookup"><span data-stu-id="f43d2-108">Pester</span></span>
<span data-ttu-id="f43d2-109">W tej wersji istnieją dwie kwestie, które należy zwrócić uwagę przy użyciu Pester na serwerze Nano:</span><span class="sxs-lookup"><span data-stu-id="f43d2-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="f43d2-110">Uruchamianie testów przed Pester się może spowodować niektóre błędy z powodu różnic między PEŁNĄ CLR i CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="f43d2-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="f43d2-111">W szczególności metodę sprawdzania poprawności nie jest dostępna w typie XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="f43d2-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="f43d2-112">Sześć testów, które będzie przeprowadzane sprawdzanie poprawności schematu dzienniki wyjściowe NUnit są znane się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f43d2-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
* <span data-ttu-id="f43d2-113">Jeden test pokrycie kodu nie działa obecnie, ponieważ *WindowsFeature* DSC zasób nie istnieje na serwerze Nano Server.</span><span class="sxs-lookup"><span data-stu-id="f43d2-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="f43d2-114">Jednak te błędy są zwykle niegroźne i można bezpiecznie zignorować.</span><span class="sxs-lookup"><span data-stu-id="f43d2-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="f43d2-115">Sprawdzenie poprawności operacji</span><span class="sxs-lookup"><span data-stu-id="f43d2-115">Operation Validation</span></span>

* <span data-ttu-id="f43d2-116">Update-Help Microsoft.PowerShell.Operation.Validation modułu z powodu wolnego pomocy identyfikator URI kończy się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="f43d2-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="f43d2-117">DSC po odinstalować WMF</span><span class="sxs-lookup"><span data-stu-id="f43d2-117">DSC after uninstall WMF</span></span>
* <span data-ttu-id="f43d2-118">Odinstalowywanie WMF nie powoduje usunięcia DSC MOF dokumentów z folderu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f43d2-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="f43d2-119">DSC nie będą działać prawidłowo, jeśli dokumenty MOF zawiera nowszą właściwości, które nie są dostępne w starszych systemach.</span><span class="sxs-lookup"><span data-stu-id="f43d2-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="f43d2-120">W takim przypadku uruchom następujący skrypt konsoli programu PowerShell z podwyższonym poziomem uprawnień, aby wyczyścić stanów DSC.</span><span class="sxs-lookup"><span data-stu-id="f43d2-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="f43d2-121">JEA kont wirtualnych</span><span class="sxs-lookup"><span data-stu-id="f43d2-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="f43d2-122">Punkty końcowe JEA i konfiguracjami sesji skonfigurowane do używania kont wirtualnych w programie WMF 5.0 nie zostanie skonfigurowany do używania konta wirtualnego po uaktualnieniu do wersji WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="f43d2-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="f43d2-123">Oznacza to, polecenia uruchamiane w sesji JEA będzie uruchamiana tożsamości łączącego się użytkownika zamiast tymczasowego konta administratora, potencjalnie uniemożliwia użytkownikowi uruchamianie poleceń, które wymagają podniesionych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="f43d2-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="f43d2-124">Aby przywrócić kont wirtualnych, należy wyrejestrować i Zarejestruj ponownie wszystkie konfiguracje sesji, które używają kont wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f43d2-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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
