---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Przykładowy szablon znanych writeup problem lub ograniczenie
ms.openlocfilehash: ed7ae3de392c8902917e5b98fd4fc9d5138ccaed
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688679"
---
>Uwaga: Podaj proponowaną opisowy tytuł i krótki opis

## <a name="example-erroneous-executionpolicy-errors"></a>Przykład: Błędne błędy ExecutionPolicy ##
Windows 7 korzystanie z modułów programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

### <a name="resolution"></a>Rozwiązanie

Aby rozwiązać problem, należy ustawić **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```
