---
title: Wyświetlanie informacji o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068287"
---
# <a name="displaying-error-information"></a><span data-ttu-id="f4b2e-102">Wyświetlanie informacji o błędach</span><span class="sxs-lookup"><span data-stu-id="f4b2e-102">Displaying Error Information</span></span>

<span data-ttu-id="f4b2e-103">W tym temacie omówiono sposoby, w którym użytkownicy mogą wyświetlać informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="f4b2e-104">Gdy Twojego polecenia cmdlet napotka błąd, prezentacja informacji o błędach będą domyślnie przypominają następujące dane wyjściowe błędu.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="f4b2e-105">Jednak użytkownicy mogą wyświetlać błędy według kategorii, ustawiając `$ErrorView` zmienną `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="f4b2e-106">W widoku kategorii wyświetlane szczegółowe informacje z rekordu błędu zamiast niezależnego opisu błędu.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="f4b2e-107">Ten widok może być przydatne, jeśli masz długą listę błędów do skanowania.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="f4b2e-108">W widoku kategorii poprzedniego komunikat o błędzie jest wyświetlany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f4b2e-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="f4b2e-109">Aby uzyskać więcej informacji na temat kategorii błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="f4b2e-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4b2e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4b2e-110">See Also</span></span>

[<span data-ttu-id="f4b2e-111">Windows PowerShell błąd rekordów</span><span class="sxs-lookup"><span data-stu-id="f4b2e-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="f4b2e-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4b2e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
