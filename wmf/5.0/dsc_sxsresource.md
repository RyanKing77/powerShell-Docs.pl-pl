---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218437"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Obsługa wersji modułu Side-By-Side dla zasobów usługi Konfiguracja DSC

Moduły zawierającego zasoby DSC mogą być zainstalowane side-by-side i konfiguracji DSC można użyć określonej wersji zasobu, który jest zainstalowany w systemie.

Aby uzyskać więcej informacji, zobacz [przy użyciu zasobów z wieloma wersjami](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Znane problemy

W tej wersji poniżej przedstawiono znane problemy side-by-side instalacji:

-   Używanie dwie różne wersje zasobu usługi Konfiguracja DSC w tej samej konfiguracji nie jest obsługiwane.
