---
title: Przykłady dla programu Windows PowerShell interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082587"
---
# <a name="windows-powershell-api-samples"></a>Przykłady interfejsów API programu Windows PowerShell

Ta sekcja zawiera przykładowy kod, który przedstawia sposób tworzenia obszarach działania, który ogranicza funkcję oraz asynchronicznie Uruchom polecenia przy użyciu puli obszarem działania umożliwiają określanie wartości obszary działania. Microsoft Visual Studio umożliwia tworzenie aplikacji konsolowej, a następnie skopiować kod z tematy w tej sekcji, w aplikacji hosta.

## <a name="in-this-section"></a>W tej sekcji

[Przykładowe PowerShell01](./windows-powershell01-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt, aby ograniczyć funkcjonalność obszaru działania. Dane wyjściowe w tym przykładzie pokazano, jak ograniczyć tryb języka w obszarze działania, jak Oznacz jako prywatne polecenia cmdlet, jak dodać i polecenia cmdlet remove i dostawców, jak dodać polecenia serwera proxy i nie tylko.

[Przykładowe PowerShell02](./windows-powershell02-sample.md) ten przykład pokazuje sposób uruchamiania poleceń asynchronicznie przy użyciu obszary działania puli obszaru działania. Przykład generuje listę poleceń, a następnie uruchomić tych poleceń, podczas gdy aparatu programu Windows PowerShell otwiera obszarem działania z puli, gdy jest to konieczne.