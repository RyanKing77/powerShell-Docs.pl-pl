---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Obsługa wersji modułu Side-By-Side dla zasobów usługi Konfiguracja DSC

Moduły zawierającego zasoby DSC mogą być zainstalowane side-by-side i konfiguracji DSC można użyć określonej wersji zasobu, który jest zainstalowany w systemie.

Aby uzyskać więcej informacji, zobacz [przy użyciu zasobów z wieloma wersjami](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Znane problemy

W tej wersji poniżej przedstawiono znane problemy side-by-side instalacji:

-   Używanie dwie różne wersje zasobu usługi Konfiguracja DSC w tej samej konfiguracji nie jest obsługiwane.