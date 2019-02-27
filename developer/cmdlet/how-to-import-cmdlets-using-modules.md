---
title: Jak zaimportować polecenia cmdlet przy użyciu modułów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849014"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Jak importować polecenia cmdlet przy użyciu modułów

W tym temacie opisano jak zaimportować polecenia cmdlet do sesji środowiska Windows PowerShell przy użyciu modułu binarnego.

> [!NOTE]
> Może zawierać elementy członkowskie modułów, poleceń cmdlet, dostawców, funkcje, zmienne, aliasy i wiele więcej. Przystawek może zawierać tylko polecenia cmdlet i dostawców.

## <a name="how-to-load-cmdlets-using-a-module"></a>Ładowanie za pomocą modułu poleceń cmdlet

1. Utwórz folder modułu, który ma taką samą nazwę jak plik zestawu, w którym są implementowane polecenia cmdlet. W tej procedurze folder modułu jest tworzony w `system32` folderu.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Upewnij się, że `PSModulePath` zmienna środowiskowa zawiera ścieżkę do nowego folderu modułu. Domyślnie folder systemowy został już dodany do `PSModulePath` zmiennej środowiskowej.

3. Skopiuj zestaw polecenia cmdlet w folderze modułu.

4. Uruchom następujące polecenie, aby dodać polecenia cmdlet do sesji:

   `import-module [Module_Name]`

   Ta procedura może służyć do testowania poleceń cmdlet. Dodaje wszystkie polecenia cmdlet w zestawie do sesji. Aby uzyskać więcej informacji na temat modułów, zobacz różnych typów modułów, różne sposoby ładowanie modułów i jak ograniczyć elementy modułu, które są eksportowane [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Instalowanie modułów](../module/installing-a-powershell-module.md)