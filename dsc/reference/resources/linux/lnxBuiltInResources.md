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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="d9818-103">Wbudowane Desired State Configuration zasoby dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d9818-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="d9818-104">Zasoby są bloków konstrukcyjnych, których można napisać skrypt programu PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d9818-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="d9818-105">DSC dla systemu Linux zawiera zestaw wbudowanych funkcji do konfigurowania zasobów, takich jak pliki i foldery, pakiety, zmienne środowiskowe i usług i procesów.</span><span class="sxs-lookup"><span data-stu-id="d9818-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="d9818-106">Zasoby wbudowane</span><span class="sxs-lookup"><span data-stu-id="d9818-106">Built-in resources</span></span>

<span data-ttu-id="d9818-107">Poniższa tabela zawiera listę tych zasobów i łącza do tematów, w których opisano je szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="d9818-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="d9818-108">[zasób nxArchive](lnxArchiveResource.md)— udostępnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="d9818-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="d9818-109">[zasób nxEnvironment](lnxEnvironmentResource.md)— zarządza zmiennych środowiskowych na węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="d9818-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="d9818-110">[zasób nxFile](lnxFileResource.md)— Linux zarządza pliki i katalogi.</span><span class="sxs-lookup"><span data-stu-id="d9818-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="d9818-111">[zasób nxFileLine](lnxFileLineResource.md)— zarządza poszczególnych wierszy w pliku systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d9818-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="d9818-112">[zasób nxGroup](lnxGroupResource.md)— zarządza grup lokalnych w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="d9818-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="d9818-113">[zasób nxPackage](lnxPackageResource.md)— zarządza pakiety na węzłów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d9818-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="d9818-114">[nxScript zasobów](lnxScriptResource.md)— uruchamia skrypty na węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="d9818-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="d9818-115">[zasób nxService](lnxServiceResource.md)— zarządza usług systemu Linux (demonów).</span><span class="sxs-lookup"><span data-stu-id="d9818-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="d9818-116">[zasób nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)— zarządza publicznego ssh klucze dla użytkownika w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="d9818-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="d9818-117">[zasób nxUser](lnxUserResource.md)— zarządza lokalnych użytkowników systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d9818-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>