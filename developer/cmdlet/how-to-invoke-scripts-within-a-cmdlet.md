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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="c04c2-102">Jak wywoływać skrypty w ramach polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c04c2-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="c04c2-103">W tym przykładzie przedstawiono sposób wywołania skryptu, który jest dostarczany do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c04c2-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="c04c2-104">Skrypt zostanie wykonany przy użyciu polecenia cmdlet, a jego wyniki są zwracane do polecenia cmdlet jako kolekcja [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) obiektów.</span><span class="sxs-lookup"><span data-stu-id="c04c2-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="c04c2-105">Aby wywołać blok skryptu</span><span class="sxs-lookup"><span data-stu-id="c04c2-105">To invoke a script block</span></span>

1. <span data-ttu-id="c04c2-106">Polecenie sprawdza, czy blok skryptu został dostarczony do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c04c2-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="c04c2-107">Jeśli blok skryptu zostało dostarczone, polecenie wywołuje bloku skryptu z jego wymaganymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="c04c2-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="c04c2-108">Następnie skrypt iteruje po kolekcji zwrócony z [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) obiektów i wykonania niezbędnych operacji.</span><span class="sxs-lookup"><span data-stu-id="c04c2-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c04c2-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c04c2-109">See Also</span></span>

[<span data-ttu-id="c04c2-110">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c04c2-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
