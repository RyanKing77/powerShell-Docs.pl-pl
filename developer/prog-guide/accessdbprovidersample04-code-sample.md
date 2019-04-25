---
title: Przykładowy kod AccessDbProviderSample04 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081958"
---
# <a name="accessdbprovidersample04-code-sample"></a>Przykładowy kod AccessDbProviderSample04

Poniższy kod przedstawia implementację dostawcy środowiska Windows PowerShell opisanego w [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Ten dostawca działa w przypadku magazynów danych w wielu warstwach. Dla tego typu magazynu danych najwyższy poziom magazynu zawiera elementy katalogu głównego, a każdy kolejnych poziom jest określany jako węzeł elementów podrzędnych. Przez umożliwienie użytkownikowi pracować nad tych węzłów podrzędnych, użytkownik może wchodzić hierarchicznie przez Magazyn danych.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)