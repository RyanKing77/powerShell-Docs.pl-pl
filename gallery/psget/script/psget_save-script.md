---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="928ab-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="928ab-103">Save-Script</span></span>

<span data-ttu-id="928ab-104">Zapisz skrypt cmdlet umożliwia przejrzenie pliku skryptu przez zapisanie go w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="928ab-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="928ab-105">Opis</span><span class="sxs-lookup"><span data-stu-id="928ab-105">Description</span></span>

<span data-ttu-id="928ab-106">Zapisz skrypt cmdlet zapisuje określony skrypt.</span><span class="sxs-lookup"><span data-stu-id="928ab-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="928ab-107">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="928ab-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="928ab-108">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="928ab-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="928ab-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="928ab-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="928ab-110">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="928ab-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="928ab-111">Przykład 1: Zapisać skrypt z repozytorium</span><span class="sxs-lookup"><span data-stu-id="928ab-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="928ab-112">To polecenie zapisuje najnowszą wersję skryptu Fabrikam ClientScript z repozytorium GalleryINT na folder lokalny C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="928ab-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="928ab-113">Przykład 2: Zapisywanie wersji skryptu przez potokowanie z polecenia cmdlet Znajdź skryptu</span><span class="sxs-lookup"><span data-stu-id="928ab-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="928ab-114">Pierwsze polecenie wersji 1.5 Fabrikam-ClientScript z repozytorium GalleryINT i zapisuje go w folderze C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="928ab-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="928ab-115">Drugie polecenie weryfikuje metadanych zapisanego skryptu.</span><span class="sxs-lookup"><span data-stu-id="928ab-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="928ab-116">Przykład 3: Zapisz wersji wstępnej programu skryptu z repozytorium</span><span class="sxs-lookup"><span data-stu-id="928ab-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="928ab-117">To polecenie zapisuje najnowszą wersję skryptu Fabrikam ClientScript z repozytorium GalleryINT na folder lokalny C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="928ab-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```