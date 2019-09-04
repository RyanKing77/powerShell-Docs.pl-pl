---
title: Jak zaimportować polecenia cmdlet przy użyciu modułów | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215264"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Jak importować polecenia cmdlet przy użyciu modułów

W tym artykule opisano sposób importowania poleceń cmdlet do sesji programu PowerShell przy użyciu modułu binarnego.

> [!NOTE]
> Elementy członkowskie modułów mogą zawierać polecenia cmdlet, dostawcy, funkcje, zmienne, aliasy i wiele innych. Przystawki mogą zawierać tylko polecenia cmdlet i dostawców.

## <a name="how-to-load-cmdlets-using-a-module"></a>Jak ładować polecenia cmdlet przy użyciu modułu

1. Utwórz folder modułu, który ma taką samą nazwę jak plik zestawu, w którym są zaimplementowane polecenia cmdlet. W tej procedurze folder module zostanie utworzony w folderze systemu Windows `system32` .

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Upewnij się, że `PSModulePath` zmienna środowiskowa zawiera ścieżkę do nowego folderu modułu. Domyślnie folder systemowy jest już dodany do `PSModulePath` zmiennej środowiskowej. Aby wyświetlić `PSModulePath`, wpisz: `$env:PSModulePath`.

1. Skopiuj zestaw poleceń cmdlet do folderu module.

1. Dodaj plik manifestu modułu (`.psd1`) w folderze głównym modułu. Program PowerShell używa manifestu modułu do zaimportowania modułu. Aby uzyskać więcej informacji, zobacz [jak napisać manifest modułu programu PowerShell](../module/how-to-write-a-powershell-module-manifest.md).

1. Uruchom następujące polecenie, aby dodać polecenia cmdlet do sesji:

   `Import-Module [Module_Name]`

   Ta procedura może służyć do testowania poleceń cmdlet. Dodaje wszystkie polecenia cmdlet w zestawie do sesji. Aby uzyskać więcej informacji o modułach, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zobacz też

[Jak napisać manifest modułu programu PowerShell](../module/how-to-write-a-powershell-module-manifest.md)

[Importowanie modułu programu PowerShell](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Instalowanie modułów](../module/installing-a-powershell-module.md)

[Modyfikowanie ścieżki instalacji PSModulePath](../module/modifying-the-psmodulepath-installation-path.md)

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
