---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów
ms.openlocfilehash: f1ac626c5ef18b7ed14f3754ab39139db2a2a2d7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222374"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Windows PowerShell Desired stan konfiguracji (DSC) ma wbudowane zasobów, które służy do konfigurowania środowiska. (Aby uzyskać więcej informacji, zobacz [wbudowanych zasobów systemu Windows PowerShell Desired stan konfiguracji](builtInResource.md).) W tym temacie omówiono tworzenie zasobów i linków do tematów z określone informacje i przykłady.

## <a name="dsc-resource-components"></a>Składniki zasobów DSC

Zasób DSC jest moduł programu Windows PowerShell. Moduł zawiera zarówno schematu (definicja konfigurowalne właściwości), jak i implementację (kod, który wykonuje faktyczną pracę określony w konfiguracji) dla zasobu. Schemat zasobów DSC można zdefiniować w pliku MOF i implementacji jest wykonywany przez moduł skryptu. Począwszy od pomocy technicznej dla klas programu PowerShell w wersji 5 schematu i wdrażania zarówno można zdefiniować w klasie. W następujących tematach opisano szczegółowo w sposób tworzenia zasobów usługi Konfiguracja DSC.

* [Pisanie niestandardowych zasobów DSC z MOF](authoringResourceMOF.md)
* [Wdrażanie zasobów DSC w języku C#](authoringResourceMofCS.md)
* [Pisanie niestandardowych zasobów DSC z klasami programu PowerShell](authoringResourceClass.md)
* [Zasoby złożonego: jako zasób przy użyciu konfiguracji DSC](authoringResourceComposite.md)
* [Przy użyciu narzędzia Projektant zasobów](authoringResourceMofDesigner.md)