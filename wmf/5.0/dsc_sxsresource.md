---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057931"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Obsługa wersji modułu Side-By-Side dla zasobów DSC

Moduły zawierające zasoby DSC może być instalowany side-by-side i konfiguracjach DSC można użyć określonej wersji zasobu, który jest zainstalowany w systemie.

Aby uzyskać więcej informacji, zobacz [korzystanie z zasobów z wieloma wersjami](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Znane problemy

W tej wersji następujące znane problemy side-by-side instalacji:

-   Używających dwóch różnych wersji zasobów DSC w ramach tej samej konfiguracji nie jest obsługiwana.
