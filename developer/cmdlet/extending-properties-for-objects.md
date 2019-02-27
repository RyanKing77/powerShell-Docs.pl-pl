---
title: Rozszerzanie właściwości dla obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845780"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="d7d5a-102">Rozszerzanie właściwości dla obiektów</span><span class="sxs-lookup"><span data-stu-id="d7d5a-102">Extending Properties for Objects</span></span>

<span data-ttu-id="d7d5a-103">Rozszerzając obiektów .NET Framework, możesz dodać aliasu właściwości, właściwości kodu, właściwości notatek, właściwości skryptu i zestawy właściwości do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="d7d5a-104">Plik XML, który jest używany do definiowania tych właściwości jest opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="d7d5a-105">W poniższych sekcjach należą do nich z typów Types.ps1xml domyślnego pliku w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="d7d5a-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="d7d5a-106">Właściwości aliasu</span><span class="sxs-lookup"><span data-stu-id="d7d5a-106">Alias Properties</span></span>

<span data-ttu-id="d7d5a-107">Właściwość alias definiuje nazwę istniejącej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="d7d5a-108">W poniższym przykładzie `Count` właściwość została dodana do [System.Array? Displayproperty = imię i nazwisko](/dotnet/api/System.Array) typu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="d7d5a-109">[AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element definiuje właściwość rozszerzona jako właściwość aliasu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="d7d5a-110">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nową nazwę.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="d7d5a-111">Ponadto [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element Określa istniejącą właściwość, która odwołuje się do aliasu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="d7d5a-112">(Można również dodać [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="d7d5a-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="d7d5a-113">Właściwości kodu</span><span class="sxs-lookup"><span data-stu-id="d7d5a-113">Code Properties</span></span>

<span data-ttu-id="d7d5a-114">Właściwość kod odwołuje się właściwość statyczna obiektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="d7d5a-115">W poniższym przykładzie `Node` właściwość została dodana do [System.IO.Directoryinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.DirectoryInfo) typu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="d7d5a-116">[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element definiuje właściwość rozszerzona jako właściwość kodu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="d7d5a-117">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="d7d5a-118">Ponadto [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element definiuje statyczna metoda, która odwołuje się do właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="d7d5a-119">(Można również dodać [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="d7d5a-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="d7d5a-120">Właściwości notatek</span><span class="sxs-lookup"><span data-stu-id="d7d5a-120">Note Properties</span></span>

<span data-ttu-id="d7d5a-121">Właściwość Uwaga definiuje właściwość, która ma wartość statyczną.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="d7d5a-122">W poniższym przykładzie `Status` właściwości (zawsze ma wartość "Powodzenie") jest dodawany do [System.IO.Directoryinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.DirectoryInfo) typu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="d7d5a-123">[NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element definiuje właściwość rozszerzona jako właściwość Uwaga; [nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej; i [wartość](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) — element Określa statyczne wartość właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="d7d5a-124">( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elementu mogą być również dodawane do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="d7d5a-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="d7d5a-125">Właściwości skryptu</span><span class="sxs-lookup"><span data-stu-id="d7d5a-125">Script Properties</span></span>

<span data-ttu-id="d7d5a-126">Właściwości script definiuje właściwość, której wartość znajduje się dane wyjściowe skryptu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="d7d5a-127">W poniższym przykładzie `VersionInfo` właściwość została dodana do [System.IO.Fileinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.FileInfo) typu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="d7d5a-128">[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element definiuje właściwość rozszerzona jako właściwość skryptu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="d7d5a-129">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="d7d5a-130">Ponadto [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element określa skrypt, który generuje wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="d7d5a-131">(Można również dodać [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="d7d5a-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="d7d5a-132">Zestawy właściwości</span><span class="sxs-lookup"><span data-stu-id="d7d5a-132">Property Sets</span></span>

<span data-ttu-id="d7d5a-133">Zestaw właściwości definiuje grupę rozszerzone właściwości, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="d7d5a-134">Na przykład `Property` parametru [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) polecenia cmdlet można określić określoną właściwość, aby były wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="d7d5a-135">Jeśli jest określony zestaw właściwości, są wyświetlane tylko te właściwości, które należą do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="d7d5a-136">Zestaw właściwości definiuje grupę rozszerzone właściwości, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="d7d5a-137">Na przykład `Property` parametru [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) polecenia cmdlet można określić określoną właściwość, aby były wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="d7d5a-138">Jeśli jest określony zestaw właściwości, są wyświetlane tylko te właściwości, które należą do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="d7d5a-139">Nie ma żadnych ograniczeń liczby zestawów właściwości, które mogą być definiowane dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="d7d5a-140">Jednak zestawy właściwości, używany do definiowania właściwości wyświetlania domyślnego obiektu muszą być określone w PSStandardMembers zestaw elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="d7d5a-141">W pliku typy Types.ps1xml domyślne nazwy zestawu właściwości obejmują DefaultDisplayProperty DefaultDisplayPropertySet i DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="d7d5a-142">Wszystkie zestawy dodatkowe właściwości, dodawane do zestawu elementów członkowskich PSStandardMembers są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="d7d5a-143">W poniższym przykładzie zestaw właściwości DefaultDisplayPropertySet zostanie dodany do elementu członkowskiego PSStandardMembers zbiór [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) typu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="d7d5a-144">[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element definiuje grupę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="d7d5a-145">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="d7d5a-146">Ponadto [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element określa właściwości zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7d5a-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="d7d5a-147">(Można również dodać [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element do elementów członkowskich [typu](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elementu.)</span><span class="sxs-lookup"><span data-stu-id="d7d5a-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d7d5a-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7d5a-148">See Also</span></span>

[<span data-ttu-id="d7d5a-149">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7d5a-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
