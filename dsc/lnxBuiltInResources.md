---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Wbudowane żądany stan konfiguracji zasobów dla systemu Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Wbudowane żądany stan konfiguracji zasobów dla systemu Linux

Zasoby są bloki konstrukcyjne, które służy do zapisywania skryptu konfiguracji żądanego stanu środowiska PowerShell (DSC). DSC dla systemu Linux zawiera zestaw wbudowanych funkcji do konfigurowania zasobów, takie jak pliki i foldery, pakiety, zmienne środowiskowe i usług i procesów.

## <a name="built-in-resources"></a>Wbudowane zasobów 

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
  
