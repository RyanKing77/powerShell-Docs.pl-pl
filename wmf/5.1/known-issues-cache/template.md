---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Przykładowy szablon znanych writeup problem lub ograniczenie
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794499"
---
 >Uwaga: Podaj proponowaną opisowy tytuł i krótki opis

## <a name="example-erroneous-executionpolicy-errors"></a>Przykład: Błędne błędy ExecutionPolicy
Windows 7 korzystanie z modułów programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

### <a name="resolution"></a>Rozwiązanie

Aby rozwiązać problem, należy ustawić **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```
