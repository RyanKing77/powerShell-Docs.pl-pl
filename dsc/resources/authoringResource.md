---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404741"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) ma wbudowane zasoby, których można użyć, aby skonfigurować środowisko. Ten temat zawiera omówienie związanych z tworzeniem zasobów i łącza do tematów, przy użyciu określonych informacji i przykładów.

## <a name="dsc-resource-components"></a>Składniki zasobów DSC

Zasób DSC jest moduł programu Windows PowerShell. Moduł zawiera zarówno schematu (definicja konfigurowalne właściwości), jak i implementację (kod, który wykonuje faktyczną pracę określony w konfiguracji) dla zasobu. Schemat zasobów DSC można zdefiniować w pliku MOF i wykonania, odbywa się przez moduł skryptu. Począwszy od obsługi klas programu PowerShell w wersji 5 schematu i implementację zarówno można zdefiniować w klasie. W następujących tematach opisano bardziej szczegółowo, jak tworzyć zasoby DSC.

* [Pisanie zasobu DSC niestandardowych z pliku MOF](authoringResourceMOF.md)
* [Wdrażanie zasobu DSC wC#](authoringResourceMofCS.md)
* [Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](authoringResourceClass.md)
* [Zasoby złożone: Przy użyciu konfiguracji DSC jako zasób](authoringResourceComposite.md)
* [Przy użyciu narzędzia Projektant zasobów](../authoringResourceMofDesigner.md)
