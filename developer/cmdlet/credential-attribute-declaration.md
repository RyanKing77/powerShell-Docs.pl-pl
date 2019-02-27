---
title: Poświadczenie deklaracji atrybutu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851989"
---
# <a name="credential-attribute-declaration"></a>Credential, deklaracja atrybutu

Atrybut poświadczeń jest opcjonalny atrybut, który może być używany z parametrami typu poświadczeń [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) tak, aby ciąg również może być przekazywany jako argument do parametru. Ten atrybut jest dodawany do deklaracji parametru, programu Windows PowerShell konwertuje ciąg wejściowy w [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu. Na przykład [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) polecenie cmdlet używa tego atrybutu, aby wygenerować w programie Windows PowerShell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiekt, który jest zwracany przez polecenie cmdlet.
Atrybut poświadczeń jest opcjonalny atrybut, który może być używany z parametrami typu poświadczeń [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) tak, aby ciąg również może być przekazywany jako argument do parametru. Ten atrybut jest dodawany do deklaracji parametru, programu Windows PowerShell konwertuje ciąg wejściowy w [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu. Na przykład [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) polecenie cmdlet używa tego atrybutu, aby wygenerować w programie Windows PowerShell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiekt, który jest zwracany przez polecenie cmdlet.

## <a name="syntax"></a>Składnia

```csharp
[Credential]
```

## <a name="remarks"></a>Uwagi

- Zazwyczaj ten atrybut jest używany przez parametry typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) tak, aby ciąg również może być przekazywany jako argument do parametru. Gdy [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiekt jest przekazywany do parametru, nic nie robi w programie Windows PowerShell.

- Podczas tworzenia [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu programu Windows PowerShell wyświetla odpowiednie monity użytkownika przy użyciu bieżącego hosta. Na przykład domyślnie wyświetlany monit o podanie nazwy użytkownika i hasła, gdy ten atrybut jest używany. Jednak jeśli jest używany niestandardowy host definiujący innego wiersza, a następnie będzie można wyświetlić tego wiersza.

- Ten atrybut jest używany z atrybutem parametru. Aby uzyskać więcej informacji na temat tego atrybutu, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

- Ten atrybut poświadczeń jest definiowany przez [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[Parametr aliasów](./parameter-aliases.md)

[Deklaracji atrybutu parametru](./parameter-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
