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
# <a name="save-script"></a>Save-Script

Zapisz skrypt cmdlet umożliwia przejrzenie pliku skryptu przez zapisanie go w określonej lokalizacji.

## <a name="description"></a>Opis

Zapisz skrypt cmdlet zapisuje określony skrypt.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Przykładowe polecenia

### <a name="example-1-save-a-script-from-a-repository"></a>Przykład 1: Zapisać skrypt z repozytorium
To polecenie zapisuje najnowszą wersję skryptu Fabrikam ClientScript z repozytorium GalleryINT na folder lokalny C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Przykład 2: Zapisywanie wersji skryptu przez potokowanie z polecenia cmdlet Znajdź skryptu

Pierwsze polecenie wersji 1.5 Fabrikam-ClientScript z repozytorium GalleryINT i zapisuje go w folderze C:\ScriptSharingDemo

Drugie polecenie weryfikuje metadanych zapisanego skryptu.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Przykład 3: Zapisz wersji wstępnej programu skryptu z repozytorium
To polecenie zapisuje najnowszą wersję skryptu Fabrikam ClientScript z repozytorium GalleryINT na folder lokalny C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```