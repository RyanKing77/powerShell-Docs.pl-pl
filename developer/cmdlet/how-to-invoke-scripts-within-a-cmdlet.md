---
title: Wywoływanie skryptów w ramach polecenia Cmdlet jak | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055788"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Jak wywoływać skrypty w ramach polecenia cmdlet

W tym przykładzie przedstawiono sposób wywołania skryptu, który jest dostarczany do polecenia cmdlet. Skrypt zostanie wykonany przy użyciu polecenia cmdlet, a jego wyniki są zwracane do polecenia cmdlet jako kolekcja [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiektów.

## <a name="to-invoke-a-script-block"></a>Aby wywołać blok skryptu

1. Polecenie sprawdza, czy blok skryptu został dostarczony do polecenia cmdlet. Jeśli blok skryptu zostało dostarczone, polecenie wywołuje bloku skryptu z jego wymaganymi parametrami.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Następnie skrypt iteruje po kolekcji zwrócony z [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiektów i wykonania niezbędnych operacji.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
