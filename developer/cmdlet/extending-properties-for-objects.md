---
title: Rozszerzanie właściwości obiektów | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986487"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="2ad57-102">Rozszerzanie właściwości dla obiektów</span><span class="sxs-lookup"><span data-stu-id="2ad57-102">Extending Properties for Objects</span></span>

<span data-ttu-id="2ad57-103">Rozszerzając .NET Framework obiektów, można dodawać do obiektów właściwości aliasu, właściwości kodu, właściwości notatki, właściwości skryptu i zestawy właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ad57-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="2ad57-104">KOD XML, który definiuje te właściwości, jest opisany w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="2ad57-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="2ad57-105">Przykłady w poniższych sekcjach pochodzą z domyślnego `Types.ps1xml` pliku typów w katalogu instalacyjnym programu PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="2ad57-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="2ad57-106">Aby uzyskać więcej informacji, zobacz [Informacje o typach. PS1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="2ad57-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="2ad57-107">Właściwości aliasu</span><span class="sxs-lookup"><span data-stu-id="2ad57-107">Alias properties</span></span>

<span data-ttu-id="2ad57-108">Właściwość aliasu definiuje nową nazwę istniejącej właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ad57-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="2ad57-109">W poniższym przykładzie właściwość **Count** jest dodawana do typu [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="2ad57-110">Element [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) definiuje Właściwość rozszerzoną jako właściwość aliasu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="2ad57-111">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) elementu Określa nową nazwę.</span><span class="sxs-lookup"><span data-stu-id="2ad57-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="2ad57-112">I element [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) określa istniejącą właściwość, do której odwołuje się alias.</span><span class="sxs-lookup"><span data-stu-id="2ad57-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="2ad57-113">Można również dodać `AliasProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a><span data-ttu-id="2ad57-114">Właściwości kodu</span><span class="sxs-lookup"><span data-stu-id="2ad57-114">Code properties</span></span>

<span data-ttu-id="2ad57-115">Właściwość Code odwołuje się do właściwości statycznej obiektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ad57-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="2ad57-116">W poniższym przykładzie właściwość **mode** jest dodawana do typu [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="2ad57-117">Element [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) definiuje Właściwość rozszerzoną jako właściwość code.</span><span class="sxs-lookup"><span data-stu-id="2ad57-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="2ad57-118">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="2ad57-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="2ad57-119">I element [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definiuje statyczną metodę, do której odwołuje się właściwość rozszerzona.</span><span class="sxs-lookup"><span data-stu-id="2ad57-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="2ad57-120">Można również dodać `CodeProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="2ad57-121">Właściwości notatki</span><span class="sxs-lookup"><span data-stu-id="2ad57-121">Note properties</span></span>

<span data-ttu-id="2ad57-122">Właściwość notatki definiuje właściwość, która ma wartość statyczną.</span><span class="sxs-lookup"><span data-stu-id="2ad57-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="2ad57-123">W poniższym przykładzie właściwość **status** , której wartość jest zawsze **sukces**, jest dodawana do typu [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="2ad57-124">Element [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) definiuje Właściwość rozszerzoną jako właściwość uwagi.</span><span class="sxs-lookup"><span data-stu-id="2ad57-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="2ad57-125">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="2ad57-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="2ad57-126">Element [Value](/dotnet/api/system.management.automation.psnoteproperty.value) określa wartość statyczną właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="2ad57-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="2ad57-127">Element może być również dodany do elementów członkowskich elementu MemberSet. [](/dotnet/api/system.management.automation.psmemberset) `NoteProperty`</span><span class="sxs-lookup"><span data-stu-id="2ad57-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="2ad57-128">Właściwości skryptu</span><span class="sxs-lookup"><span data-stu-id="2ad57-128">Script properties</span></span>

<span data-ttu-id="2ad57-129">Właściwość skryptu definiuje właściwość, której wartość jest wynikiem skryptu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="2ad57-130">W poniższym przykładzie właściwość **VERSIONINFO** jest dodawana do typu [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="2ad57-131">Element [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) definiuje Właściwość rozszerzoną jako właściwość skryptu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="2ad57-132">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="2ad57-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="2ad57-133">I element [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) określa skrypt generujący wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ad57-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="2ad57-134">Można również dodać `ScriptProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="2ad57-135">Zestawy właściwości</span><span class="sxs-lookup"><span data-stu-id="2ad57-135">Property sets</span></span>

<span data-ttu-id="2ad57-136">Zestaw właściwości definiuje grupę rozszerzonych właściwości, do których może odwoływać się nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="2ad57-137">Na przykład parametr**Właściwości** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
może określać konkretny zestaw właściwości do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="2ad57-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="2ad57-138">Po określeniu zestawu właściwości są wyświetlane tylko te właściwości, które należą do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="2ad57-139">Nie ma ograniczeń dotyczących liczby zestawów właściwości, które można zdefiniować dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="2ad57-140">Jednak zestawy właściwości używane do definiowania domyślnych właściwości wyświetlania obiektu muszą być określone w ramach zestawu elementów członkowskich **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="2ad57-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="2ad57-141">W plikutypów domyślna nazwa zestawu właściwości to DefaultDisplayProperty, DefaultDisplayPropertySet i DefaultKeyPropertySet. `Types.ps1xml`</span><span class="sxs-lookup"><span data-stu-id="2ad57-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="2ad57-142">Wszystkie dodatkowe zestawy właściwości dodawane do zestawu elementów członkowskich **PSStandardMembers** są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2ad57-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="2ad57-143">W poniższym przykładzie zestaw właściwości **DefaultDisplayPropertySet** jest dodawany do zestawu elementów członkowskich **PSStandardMembers** typu [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="2ad57-144">Element [PropertySet —](/dotnet/api/system.management.automation.pspropertyset) definiuje grupę właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ad57-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="2ad57-145">[Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ad57-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="2ad57-146">I element [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) określa właściwości zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ad57-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="2ad57-147">Możesz również dodać `PropertySet` element do elementów członkowskich [typu](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="2ad57-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="2ad57-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ad57-148">See also</span></span>

[<span data-ttu-id="2ad57-149">Informacje o typach. PS1XML</span><span class="sxs-lookup"><span data-stu-id="2ad57-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="2ad57-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="2ad57-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="2ad57-151">Pisanie polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ad57-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
