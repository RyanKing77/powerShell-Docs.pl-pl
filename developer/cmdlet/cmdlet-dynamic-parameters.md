---
title: Parametry dynamiczne polecenia cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986251"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="41490-102">Parametry dynamiczne polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="41490-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="41490-103">Polecenia cmdlet programu mogą definiować parametry, które są dostępne dla użytkownika w warunkach specjalnych, na przykład gdy argument innego parametru jest określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="41490-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="41490-104">Te parametry są dodawane w czasie wykonywania i są określane jako parametry dynamiczne, ponieważ są dodawane tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="41490-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="41490-105">Na przykład można zaprojektować polecenie cmdlet, które dodaje kilka parametrów tylko w przypadku określenia określonego parametru przełącznika.</span><span class="sxs-lookup"><span data-stu-id="41490-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="41490-106">Dostawcy i funkcje programu PowerShell mogą również definiować parametry dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="41490-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="41490-107">Parametry dynamiczne w poleceniach cmdlet programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="41490-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="41490-108">Program PowerShell używa parametrów dynamicznych w kilku poleceniach cmdlet dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41490-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="41490-109">Na `Get-Item` przykład polecenia cmdlet i `Get-ChildItem` dodają parametr **CodeSigningCert** w czasie wykonywania, gdy parametr **Path** określa ścieżkę dostawcy **certyfikatów** .</span><span class="sxs-lookup"><span data-stu-id="41490-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="41490-110">Jeśli parametr **Path** określa ścieżkę dla innego dostawcy, parametr **CodeSigningCert** jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="41490-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="41490-111">W poniższych przykładach pokazano, jak parametr **CodeSigningCert** jest dodawany w czasie `Get-Item` wykonywania, gdy jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="41490-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="41490-112">W tym przykładzie środowisko uruchomieniowe programu PowerShell dodało parametr, a polecenie cmdlet zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="41490-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="41490-113">W tym przykładzie jest określony dysk systemu **plików** i zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="41490-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="41490-114">Komunikat o błędzie wskazuje, że nie można znaleźć parametru **CodeSigningCert** .</span><span class="sxs-lookup"><span data-stu-id="41490-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="41490-115">Obsługa parametrów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="41490-115">Support for dynamic parameters</span></span>

<span data-ttu-id="41490-116">Aby można było obsługiwać parametry dynamiczne, należy uwzględnić następujące elementy w kodzie poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41490-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="41490-117">Interfejs</span><span class="sxs-lookup"><span data-stu-id="41490-117">Interface</span></span>

<span data-ttu-id="41490-118">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="41490-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="41490-119">Ten interfejs zapewnia metodę, która pobiera parametry dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="41490-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="41490-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="41490-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="41490-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="41490-121">Method</span></span>

<span data-ttu-id="41490-122">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="41490-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="41490-123">Ta metoda pobiera obiekt, który zawiera definicje parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="41490-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="41490-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="41490-124">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="41490-125">Klasa</span><span class="sxs-lookup"><span data-stu-id="41490-125">Class</span></span>

<span data-ttu-id="41490-126">Klasa, która definiuje parametry dynamiczne do dodania.</span><span class="sxs-lookup"><span data-stu-id="41490-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="41490-127">Ta klasa musi zawierać atrybut **parametrów** dla każdego parametru oraz wszelkie opcjonalne **aliasy** i atrybuty **walidacji** , które są wymagane przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41490-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="41490-128">Przykład:</span><span class="sxs-lookup"><span data-stu-id="41490-128">For example:</span></span>

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

<span data-ttu-id="41490-129">Pełny przykład polecenia cmdlet, które obsługuje parametry dynamiczne, można znaleźć w temacie [How to DECLARE Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="41490-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41490-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41490-130">See also</span></span>

[<span data-ttu-id="41490-131">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="41490-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="41490-132">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="41490-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="41490-133">Jak zadeklarować parametry dynamiczne</span><span class="sxs-lookup"><span data-stu-id="41490-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="41490-134">Pisanie polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41490-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
