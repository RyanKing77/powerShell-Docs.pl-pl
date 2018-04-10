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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Wbudowane żądany stan konfiguracji zasobów dla systemu Linux

Zasoby są bloki konstrukcyjne, które służy do zapisywania skryptu konfiguracji żądanego stanu środowiska PowerShell (DSC). DSC dla systemu Linux zawiera zestaw wbudowanych funkcji do konfigurowania zasobów, takie jak pliki i foldery, pakiety, zmienne środowiskowe i usług i procesów.

## <a name="built-in-resources"></a>Zasoby wbudowane

Poniższa tabela zawiera listę tych zasobów i linków do tematów opisujących je szczegółowo.

* [nxArchive zasobów](lnxArchiveResource.md)— udostępnia mechanizm do rozpakowywania plików archiwów (tar, .zip) w określonej ścieżce.
* [nxEnvironment zasobów](lnxEnvironmentResource.md)— zarządza zmiennych środowiskowych na węzłach docelowych.
* [nxFile zasobów](lnxFileResource.md)— zarządza Linux plików i katalogów.
* [nxFileLine zasobów](lnxFileLineResource.md)— zarządza poszczególne wiersze w pliku systemu Linux.
* [nxGroup zasobów](lnxGroupResource.md)— zarządza grup lokalnych w systemie Linux.
* [nxPackage zasobów](lnxPackageResource.md)— zarządza pakietów w węzłach systemu Linux.
* [nxScript zasobów](lnxScriptResource.md)— uruchamia skrypty na węzłach docelowych.
* [nxService zasobów](lnxServiceResource.md)— zarządza usługi systemu Linux (demonów).
* [nxSshAuthorizedKeys zasobów](lnxSshAuthorizedKeysResource.md)— zarządza publicznego ssh kluczy dla użytkownika w systemie Linux.
* [nxUser zasobów](lnxUserResource.md)— zarządza lokalnych użytkowników systemu Linux.