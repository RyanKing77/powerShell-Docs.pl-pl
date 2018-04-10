---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Wbudowane żądany stan konfiguracji zasobów dla systemu Linux
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="f8bbc-103">Wbudowane żądany stan konfiguracji zasobów dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="f8bbc-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="f8bbc-104">Zasoby są bloki konstrukcyjne, które służy do zapisywania skryptu konfiguracji żądanego stanu środowiska PowerShell (DSC).</span><span class="sxs-lookup"><span data-stu-id="f8bbc-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="f8bbc-105">DSC dla systemu Linux zawiera zestaw wbudowanych funkcji do konfigurowania zasobów, takie jak pliki i foldery, pakiety, zmienne środowiskowe i usług i procesów.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="f8bbc-106">Zasoby wbudowane</span><span class="sxs-lookup"><span data-stu-id="f8bbc-106">Built-in resources</span></span>

<span data-ttu-id="f8bbc-107">Poniższa tabela zawiera listę tych zasobów i linków do tematów opisujących je szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="f8bbc-108">[nxArchive zasobów](lnxArchiveResource.md)— udostępnia mechanizm do rozpakowywania plików archiwów (tar, .zip) w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="f8bbc-109">[nxEnvironment zasobów](lnxEnvironmentResource.md)— zarządza zmiennych środowiskowych na węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="f8bbc-110">[nxFile zasobów](lnxFileResource.md)— zarządza Linux plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="f8bbc-111">[nxFileLine zasobów](lnxFileLineResource.md)— zarządza poszczególne wiersze w pliku systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="f8bbc-112">[nxGroup zasobów](lnxGroupResource.md)— zarządza grup lokalnych w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="f8bbc-113">[nxPackage zasobów](lnxPackageResource.md)— zarządza pakietów w węzłach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="f8bbc-114">[nxScript zasobów](lnxScriptResource.md)— uruchamia skrypty na węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="f8bbc-115">[nxService zasobów](lnxServiceResource.md)— zarządza usługi systemu Linux (demonów).</span><span class="sxs-lookup"><span data-stu-id="f8bbc-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="f8bbc-116">[nxSshAuthorizedKeys zasobów](lnxSshAuthorizedKeysResource.md)— zarządza publicznego ssh kluczy dla użytkownika w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="f8bbc-117">[nxUser zasobów](lnxUserResource.md)— zarządza lokalnych użytkowników systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f8bbc-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>