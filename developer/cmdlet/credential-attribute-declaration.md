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
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068321"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="2b783-102">Credential, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="2b783-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="2b783-103">Atrybut poświadczeń jest opcjonalny atrybut, który może być używany z parametrami typu poświadczeń [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) tak, aby ciąg również może być przekazywany jako argument do parametru.</span><span class="sxs-lookup"><span data-stu-id="2b783-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="2b783-104">Ten atrybut jest dodawany do deklaracji parametru, programu Windows PowerShell konwertuje ciąg wejściowy w [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu.</span><span class="sxs-lookup"><span data-stu-id="2b783-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="2b783-105">Na przykład [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) polecenie cmdlet używa tego atrybutu, aby wygenerować w programie Windows PowerShell [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) obiekt, który jest zwracany przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b783-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b783-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b783-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="2b783-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b783-107">Remarks</span></span>

- <span data-ttu-id="2b783-108">Zazwyczaj ten atrybut jest używany przez parametry typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) tak, aby ciąg również może być przekazywany jako argument do parametru.</span><span class="sxs-lookup"><span data-stu-id="2b783-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="2b783-109">Gdy [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) obiekt jest przekazywany do parametru, nic nie robi w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b783-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="2b783-110">Podczas tworzenia [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu programu Windows PowerShell wyświetla odpowiednie monity użytkownika przy użyciu bieżącego hosta.</span><span class="sxs-lookup"><span data-stu-id="2b783-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="2b783-111">Na przykład domyślnie wyświetlany monit o podanie nazwy użytkownika i hasła, gdy ten atrybut jest używany.</span><span class="sxs-lookup"><span data-stu-id="2b783-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="2b783-112">Jednak jeśli jest używany niestandardowy host definiujący innego wiersza, a następnie będzie można wyświetlić tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="2b783-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="2b783-113">Ten atrybut jest używany z atrybutem parametru.</span><span class="sxs-lookup"><span data-stu-id="2b783-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="2b783-114">Aby uzyskać więcej informacji na temat tego atrybutu, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="2b783-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="2b783-115">Ten atrybut poświadczeń jest definiowany przez [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="2b783-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b783-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b783-116">See Also</span></span>

[<span data-ttu-id="2b783-117">Parametr aliasów</span><span class="sxs-lookup"><span data-stu-id="2b783-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="2b783-118">Deklaracji atrybutu parametru</span><span class="sxs-lookup"><span data-stu-id="2b783-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="2b783-119">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b783-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
