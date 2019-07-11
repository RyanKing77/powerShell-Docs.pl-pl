---
title: Definiowanie domyślnych metod dla obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733978"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="9724e-102">Definiowanie metod domyślnych dla obiektów</span><span class="sxs-lookup"><span data-stu-id="9724e-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="9724e-103">Rozszerzając obiektów .NET Framework, możesz dodać kod metody i metody skryptu do obiektów.</span><span class="sxs-lookup"><span data-stu-id="9724e-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="9724e-104">Plik XML, który jest używany do definiowania tych metod jest opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="9724e-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="9724e-105">Przykłady podane w poniższych sekcjach pochodzą z pliku typy Types.ps1xml w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="9724e-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="9724e-106">Kod metody</span><span class="sxs-lookup"><span data-stu-id="9724e-106">Code Methods</span></span>

<span data-ttu-id="9724e-107">Metoda kod odwołuje się do statycznej metody obiektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9724e-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="9724e-108">W poniższym przykładzie **ConvertLargeIntegerToInt64** metoda jest dodawana do [System.Xml.Xmlnode? Displayproperty = imię i nazwisko](/dotnet/api/System.Xml.XmlNode) typu.</span><span class="sxs-lookup"><span data-stu-id="9724e-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="9724e-109">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element definiuje rozszerzone metody jako metodę kodu.</span><span class="sxs-lookup"><span data-stu-id="9724e-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="9724e-110">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="9724e-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="9724e-111">Ponadto [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element określa metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="9724e-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="9724e-112">(Można również dodać [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element do elementów członkowskich [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elementu.)</span><span class="sxs-lookup"><span data-stu-id="9724e-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="9724e-113">Metody skryptu</span><span class="sxs-lookup"><span data-stu-id="9724e-113">Script Methods</span></span>

<span data-ttu-id="9724e-114">Metoda skryptu definiuje metodę, której wartość znajduje się dane wyjściowe skryptu.</span><span class="sxs-lookup"><span data-stu-id="9724e-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="9724e-115">W poniższym przykładzie **ConvertToDateTime** metoda jest dodawana do [System.Management.Managementobject? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.ManagementObject) typu.</span><span class="sxs-lookup"><span data-stu-id="9724e-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="9724e-116">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element definiuje rozszerzone metody jako metodę skryptu.</span><span class="sxs-lookup"><span data-stu-id="9724e-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="9724e-117">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="9724e-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="9724e-118">Ponadto [skryptu](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element określa skrypt, który generuje wartość metody.</span><span class="sxs-lookup"><span data-stu-id="9724e-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="9724e-119">(Można również dodać [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element do elementów członkowskich [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elementu.)</span><span class="sxs-lookup"><span data-stu-id="9724e-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9724e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9724e-120">See Also</span></span>

[<span data-ttu-id="9724e-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9724e-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
