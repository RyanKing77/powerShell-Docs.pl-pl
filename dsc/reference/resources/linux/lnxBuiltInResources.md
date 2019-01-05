---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Wbudowane Desired State Configuration zasoby dla systemu Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048476"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Wbudowane Desired State Configuration zasoby dla systemu Linux

Zasoby są bloków konstrukcyjnych, których można napisać skrypt programu PowerShell Desired State Configuration (DSC). DSC dla systemu Linux zawiera zestaw wbudowanych funkcji do konfigurowania zasobów, takich jak pliki i foldery, pakiety, zmienne środowiskowe i usług i procesów.

## <a name="built-in-resources"></a>Zasoby wbudowane

Poniższa tabela zawiera listę tych zasobów i łącza do tematów, w których opisano je szczegółowo.

* [zasób nxArchive](lnxArchiveResource.md)— udostępnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce.
* [zasób nxEnvironment](lnxEnvironmentResource.md)— zarządza zmiennych środowiskowych na węzłach docelowych.
* [zasób nxFile](lnxFileResource.md)— Linux zarządza pliki i katalogi.
* [zasób nxFileLine](lnxFileLineResource.md)— zarządza poszczególnych wierszy w pliku systemu Linux.
* [zasób nxGroup](lnxGroupResource.md)— zarządza grup lokalnych w systemie Linux.
* [zasób nxPackage](lnxPackageResource.md)— zarządza pakiety na węzłów systemu Linux.
* [nxScript zasobów](lnxScriptResource.md)— uruchamia skrypty na węzłach docelowych.
* [zasób nxService](lnxServiceResource.md)— zarządza usług systemu Linux (demonów).
* [zasób nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)— zarządza publicznego ssh klucze dla użytkownika w systemie Linux.
* [zasób nxUser](lnxUserResource.md)— zarządza lokalnych użytkowników systemu Linux.