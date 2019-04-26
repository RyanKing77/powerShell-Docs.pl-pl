---
title: Potwierdzenie wiadomości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068372"
---
# <a name="confirmation-messages"></a><span data-ttu-id="3392f-102">Komunikaty z potwierdzeniem</span><span class="sxs-lookup"><span data-stu-id="3392f-102">Confirmation Messages</span></span>

<span data-ttu-id="3392f-103">Poniżej przedstawiono komunikaty z różnych potwierdzenia, które mogą być wyświetlane w zależności od warianty [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, które są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="3392f-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3392f-104">Aby uzyskać przykładowy kod, który pokazuje, jak żądania potwierdzenia, zobacz [jak żądania potwierdzenia](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="3392f-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="3392f-105">Określenie zasobu</span><span class="sxs-lookup"><span data-stu-id="3392f-105">Specifying the Resource</span></span>

<span data-ttu-id="3392f-106">Można określić zasób, który ma zostać zmieniony przez wywołanie metody [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metody.</span><span class="sxs-lookup"><span data-stu-id="3392f-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="3392f-107">W takim przypadku użytkownik poda zasobu za pomocą `target` dodano parametr metody i działania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3392f-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="3392f-108">W następujący komunikat tekst "MyResource" jest zasób zrealizowany i operacji jest nazwa polecenia, która wywołuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="3392f-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="3392f-109">Jeśli użytkownik wybierze **tak** lub **tak na wszystko** na potwierdzenie żądania (jak pokazano w poniższym przykładzie), po wywołaniu [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)dokonywane jest metoda, co powoduje, że drugi komunikat z potwierdzeniem mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="3392f-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="3392f-110">Określanie operacji i zasobów</span><span class="sxs-lookup"><span data-stu-id="3392f-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="3392f-111">Można określić zasób, który ma zostać zmieniony i operacji, która ma wykonać, wywołując polecenie [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metody.</span><span class="sxs-lookup"><span data-stu-id="3392f-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="3392f-112">W takim przypadku użytkownik poda zasobu za pomocą `target` parametr i operację, używając `target` parametru.</span><span class="sxs-lookup"><span data-stu-id="3392f-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="3392f-113">W następujący komunikat tekst "MyResource" jest zasób zrealizowany, i "MyAction" jest operacja do wykonania.</span><span class="sxs-lookup"><span data-stu-id="3392f-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="3392f-114">Jeśli użytkownik wybierze **tak** lub **tak na wszystko** do poprzedniej wiadomości wywołanie [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody dokonuje się, co powoduje, że drugi komunikat potwierdzający, który ma być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="3392f-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="3392f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3392f-115">See Also</span></span>

[<span data-ttu-id="3392f-116">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3392f-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
