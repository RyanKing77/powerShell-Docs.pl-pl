---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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