---
title: Definiowanie domyślnych metod dla obiektów | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215290"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="1caa3-102">Definiowanie metod domyślnych dla obiektów</span><span class="sxs-lookup"><span data-stu-id="1caa3-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="1caa3-103">Rozszerzając .NET Framework obiektów, można dodać metody kodu i metody skryptu do obiektów.</span><span class="sxs-lookup"><span data-stu-id="1caa3-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="1caa3-104">KOD XML, który jest używany do definiowania tych metod, jest opisany w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="1caa3-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="1caa3-105">Przykłady w poniższych sekcjach pochodzą z `Types.ps1xml` pliku typów w katalogu instalacyjnym programu Windows PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="1caa3-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="1caa3-106">Aby uzyskać więcej informacji, zobacz [Informacje o typach. PS1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="1caa3-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="1caa3-107">Metody kodu</span><span class="sxs-lookup"><span data-stu-id="1caa3-107">Code methods</span></span>

<span data-ttu-id="1caa3-108">Metoda Code odwołuje się do statycznej metody obiektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1caa3-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="1caa3-109">W poniższym przykładzie metoda **ToString** jest dodawana do typu [System. XML. XmlNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="1caa3-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="1caa3-110">Element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) definiuje metodę rozszerzoną jako metodę kodu.</span><span class="sxs-lookup"><span data-stu-id="1caa3-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="1caa3-111">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="1caa3-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="1caa3-112">I element [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) określa metodę statyczną.</span><span class="sxs-lookup"><span data-stu-id="1caa3-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="1caa3-113">Można również dodać element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) do elementów członkowskich elementu [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="1caa3-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="1caa3-114">Metody skryptu</span><span class="sxs-lookup"><span data-stu-id="1caa3-114">Script methods</span></span>

<span data-ttu-id="1caa3-115">Metoda skryptu definiuje metodę, której wartość jest wynikiem skryptu.</span><span class="sxs-lookup"><span data-stu-id="1caa3-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="1caa3-116">W poniższym przykładzie metoda **ConvertToDateTime** jest dodawana do typu [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="1caa3-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="1caa3-117">Element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) definiuje metodę rozszerzoną jako metodę skryptu.</span><span class="sxs-lookup"><span data-stu-id="1caa3-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="1caa3-118">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="1caa3-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="1caa3-119">I, element [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) określa skrypt, który generuje wartość metody.</span><span class="sxs-lookup"><span data-stu-id="1caa3-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="1caa3-120">Można również dodać element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) do elementów członkowskich elementu [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="1caa3-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="1caa3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1caa3-121">See also</span></span>

[<span data-ttu-id="1caa3-122">Pisanie polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1caa3-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
