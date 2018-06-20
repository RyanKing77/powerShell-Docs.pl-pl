---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Przykładowy szablon znany problem lub ograniczenie zapisywania
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221939"
---
>Uwaga: Podaj proponowanych opisowy tytuł i krótki opis

## <a name="example-erroneous-executionpolicy-errors"></a>Przykład: Błędne ExecutionPolicy błędów ##
W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

### <a name="resolution"></a>Rozwiązanie

Aby rozwiązać, ustaw **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```
