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
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846697"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Jak wywoływać skrypty w ramach polecenia cmdlet

W tym przykładzie przedstawiono sposób wywołania skryptu, który jest dostarczany do polecenia cmdlet. Skrypt zostanie wykonany przy użyciu polecenia cmdlet, a jego wyniki są zwracane do polecenia cmdlet jako kolekcja [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) obiektów.

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

2. Następnie skrypt iteruje po kolekcji zwrócony z [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) obiektów i wykonania niezbędnych operacji.

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
