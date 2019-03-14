---
title: Przykładowy kod AccessDbProviderSample02 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795491"
---
# <a name="accessdbprovidersample02-code-sample"></a>Przykładowy kod AccessDbProviderSample02

Poniższy kod przedstawia implementację dostawcy środowiska Windows PowerShell opisanego w [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md). Ta implementacja powoduje utworzenie ścieżki, nawiązuje połączenie z bazą danych programu Access, a następnie usuwa dysk.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider02.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)