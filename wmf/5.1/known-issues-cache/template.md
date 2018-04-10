---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Przykładowy szablon znany problem lub ograniczenie zapisywania
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
>Uwaga: Podaj proponowanych opisowy tytuł i krótki opis

## <a name="example-erroneous-executionpolicy-errors"></a>Przykład: Błędne ExecutionPolicy błędów ##
W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

### <a name="resolution"></a>Rozwiązanie

Aby rozwiązać, ustaw **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```