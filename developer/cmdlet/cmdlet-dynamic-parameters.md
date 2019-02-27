---
title: Parametry polecenia cmdlet dynamiczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845276"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="ed002-102">Dynamiczne parametry poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="ed002-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="ed002-103">Polecenia cmdlet można zdefiniować parametry, które są dostępne dla użytkownika w warunkach specjalne, np. gdy argument innego parametru jest określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="ed002-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="ed002-104">Te parametry są dodawane w czasie wykonywania i są określane jako *parametrów dynamicznych* ponieważ są one dodawane tylko wtedy, gdy są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ed002-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="ed002-105">Na przykład można zaprojektować polecenia cmdlet, który dodaje kilka parametrów, tylko wtedy, gdy określono parametr określonego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ed002-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="ed002-106">Dostawcy i funkcje programu Windows PowerShell można również definiować parametry dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="ed002-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="ed002-107">Parametry dynamiczne w poleceniach cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed002-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="ed002-108">Program Windows PowerShell używa parametrów dynamicznych w kilka z jego poleceń cmdlet dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed002-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="ed002-109">Na przykład `Get-Item` i `Get-ChildItem` dodać polecenia cmdlet `CodeSigningCert` parametru w czasie wykonywania podczas `Path` parametru polecenia cmdlet ścieżka certyfikatu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed002-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="ed002-110">Jeśli `Path` parametru polecenia cmdlet Określa ścieżkę do innego dostawcy `CodeSigningCert` parametr nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="ed002-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="ed002-111">W poniższych przykładach pokazano sposób, w jaki `CodeSigningCert` w czasie wykonywania zostanie dodany parametr podczas `Get-Item` polecenie cmdlet jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="ed002-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="ed002-112">W pierwszym przykładzie środowiska uruchomieniowego programu Windows PowerShell został dodany parametr, a polecenie cmdlet zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ed002-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="ed002-113">W drugim przykładzie określono dysku systemu plików, i zostanie zwrócony błąd.</span><span class="sxs-lookup"><span data-stu-id="ed002-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="ed002-114">Komunikat o błędzie oznacza, że `CodeSigningCert` nie można odnaleźć parametru.</span><span class="sxs-lookup"><span data-stu-id="ed002-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="ed002-115">Obsługa parametrów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="ed002-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="ed002-116">Aby umożliwić obsługę parametrów dynamicznych, kodu polecenie cmdlet musi zawierać następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="ed002-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="ed002-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) ten interfejs zapewnia metody, która pobiera parametry dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="ed002-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="ed002-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ed002-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="ed002-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) ta metoda pobiera obiekt, który zawiera definicje parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="ed002-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="ed002-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ed002-120">Example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

<span data-ttu-id="ed002-121">Klasa dynamicznych parametrów ta klasa definiuje parametry, które mają zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="ed002-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="ed002-122">Ta klasa musi zawierać atrybut parametr, dla każdego parametru i opcjonalnych atrybutów Alias i sprawdzania poprawności, które są wymagane przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed002-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="ed002-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ed002-123">Example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="ed002-124">Aby uzyskać pełny przykład polecenia cmdlet, które obsługuje parametry dynamiczne, zobacz [jak deklarować parametrów dynamicznych](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed002-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed002-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed002-125">See Also</span></span>

[<span data-ttu-id="ed002-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="ed002-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="ed002-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="ed002-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="ed002-128">Jak deklarować parametrów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="ed002-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="ed002-129">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed002-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
