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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059477"
---
# <a name="confirmation-messages"></a>Komunikaty z potwierdzeniem

Poniżej przedstawiono komunikaty z różnych potwierdzenia, które mogą być wyświetlane w zależności od warianty [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, które są wywoływane.

> [!IMPORTANT]
> Aby uzyskać przykładowy kod, który pokazuje, jak żądania potwierdzenia, zobacz [jak żądania potwierdzenia](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Określenie zasobu

Można określić zasób, który ma zostać zmieniony przez wywołanie metody [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metody. W takim przypadku użytkownik poda zasobu za pomocą `target` dodano parametr metody i działania programu Windows PowerShell. W następujący komunikat tekst "MyResource" jest zasób zrealizowany i operacji jest nazwa polecenia, która wywołuje tę funkcję.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Jeśli użytkownik wybierze **tak** lub **tak na wszystko** na potwierdzenie żądania (jak pokazano w poniższym przykładzie), po wywołaniu [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)dokonywane jest metoda, co powoduje, że drugi komunikat z potwierdzeniem mają być wyświetlane.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Określanie operacji i zasobów

Można określić zasób, który ma zostać zmieniony i operacji, która ma wykonać, wywołując polecenie [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metody. W takim przypadku użytkownik poda zasobu za pomocą `target` parametr i operację, używając `target` parametru. W następujący komunikat tekst "MyResource" jest zasób zrealizowany, i "MyAction" jest operacja do wykonania.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Jeśli użytkownik wybierze **tak** lub **tak na wszystko** do poprzedniej wiadomości wywołanie [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody dokonuje się, co powoduje, że drugi komunikat potwierdzający, który ma być wyświetlany.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
