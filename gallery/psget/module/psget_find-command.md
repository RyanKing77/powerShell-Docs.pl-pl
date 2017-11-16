---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Find — polecenie"
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="0270d-103">Find — polecenie</span><span class="sxs-lookup"><span data-stu-id="0270d-103">Find-Command</span></span>

<span data-ttu-id="0270d-104">Wyszukuje poleceń programu PowerShell w modułach.</span><span class="sxs-lookup"><span data-stu-id="0270d-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="0270d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0270d-105">Description</span></span>
<span data-ttu-id="0270d-106">Polecenia cmdlet polecenia Find znajduje poleceń programu PowerShell, takie jak polecenia cmdlet, aliasy, funkcje i przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="0270d-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="0270d-107">Polecenie Znajdź wyszukuje modułów w zarejestrowany repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="0270d-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="0270d-108">Dla każdego polecenia wyszukującą to polecenie cmdlet zwraca obiekt PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="0270d-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="0270d-109">Obiekt PSGetCommandInfo można przekazać do polecenia cmdlet Install-Module, zainstalować moduł, który zawiera polecenie.</span><span class="sxs-lookup"><span data-stu-id="0270d-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="0270d-110">Polecenie Znajdź można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="0270d-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="0270d-111">Parametry te wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="0270d-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="0270d-112">Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="0270d-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="0270d-113">Jeśli parametr RequiredVersion nie zostanie określony, polecenie Znajdź zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="0270d-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="0270d-114">Jeśli określono parametr RequiredVersion, Znajdź polecenie zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="0270d-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="0270d-115">Polecenie Znajdź można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="0270d-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="0270d-116">Polecenie Znajdź można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.</span><span class="sxs-lookup"><span data-stu-id="0270d-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="0270d-117">Polecenie Znajdź można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="0270d-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="0270d-118">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="0270d-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="0270d-119">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="0270d-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="0270d-120">Find — polecenie</span><span class="sxs-lookup"><span data-stu-id="0270d-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="0270d-121">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="0270d-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

