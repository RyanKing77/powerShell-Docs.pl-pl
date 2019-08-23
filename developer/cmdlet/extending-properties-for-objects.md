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
# <a name="extending-properties-for-objects"></a>Rozszerzanie właściwości dla obiektów

Rozszerzając .NET Framework obiektów, można dodawać do obiektów właściwości aliasu, właściwości kodu, właściwości notatki, właściwości skryptu i zestawy właściwości. KOD XML, który definiuje te właściwości, jest opisany w poniższych sekcjach.

> [!NOTE]
> Przykłady w poniższych sekcjach pochodzą z domyślnego `Types.ps1xml` pliku typów w katalogu instalacyjnym programu PowerShell (`$PSHOME`). Aby uzyskać więcej informacji, zobacz [Informacje o typach. PS1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Właściwości aliasu

Właściwość aliasu definiuje nową nazwę istniejącej właściwości.

W poniższym przykładzie właściwość **Count** jest dodawana do typu [System. Array](/dotnet/api/System.Array) . Element [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) definiuje Właściwość rozszerzoną jako właściwość aliasu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) elementu Określa nową nazwę. I element [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) określa istniejącą właściwość, do której odwołuje się alias. Można również dodać `AliasProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="code-properties"></a>Właściwości kodu

Właściwość Code odwołuje się do właściwości statycznej obiektu .NET Framework.

W poniższym przykładzie właściwość **mode** jest dodawana do typu [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . Element [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) definiuje Właściwość rozszerzoną jako właściwość code. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej. I element [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definiuje statyczną metodę, do której odwołuje się właściwość rozszerzona. Można również dodać `CodeProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="note-properties"></a>Właściwości notatki

Właściwość notatki definiuje właściwość, która ma wartość statyczną.

W poniższym przykładzie właściwość **status** , której wartość jest zawsze **sukces**, jest dodawana do typu [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . Element [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) definiuje Właściwość rozszerzoną jako właściwość uwagi. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej. Element [Value](/dotnet/api/system.management.automation.psnoteproperty.value) określa wartość statyczną właściwości rozszerzonej. Element może być również dodany do elementów członkowskich elementu MemberSet. [](/dotnet/api/system.management.automation.psmemberset) `NoteProperty`

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

## <a name="script-properties"></a>Właściwości skryptu

Właściwość skryptu definiuje właściwość, której wartość jest wynikiem skryptu.

W poniższym przykładzie właściwość **VERSIONINFO** jest dodawana do typu [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) . Element [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) definiuje Właściwość rozszerzoną jako właściwość skryptu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę właściwości rozszerzonej. I element [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) określa skrypt generujący wartość właściwości. Można również dodać `ScriptProperty` element do elementów członkowskich elementu [MemberSet](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="property-sets"></a>Zestawy właściwości

Zestaw właściwości definiuje grupę rozszerzonych właściwości, do których może odwoływać się nazwa zestawu.
Na przykład parametr**Właściwości** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
może określać konkretny zestaw właściwości do wyświetlenia. Po określeniu zestawu właściwości są wyświetlane tylko te właściwości, które należą do zestawu.

Nie ma ograniczeń dotyczących liczby zestawów właściwości, które można zdefiniować dla obiektu. Jednak zestawy właściwości używane do definiowania domyślnych właściwości wyświetlania obiektu muszą być określone w ramach zestawu elementów członkowskich **PSStandardMembers** . W plikutypów domyślna nazwa zestawu właściwości to DefaultDisplayProperty, DefaultDisplayPropertySet i DefaultKeyPropertySet. `Types.ps1xml` Wszystkie dodatkowe zestawy właściwości dodawane do zestawu elementów członkowskich **PSStandardMembers** są ignorowane.

W poniższym przykładzie zestaw właściwości **DefaultDisplayPropertySet** jest dodawany do zestawu elementów członkowskich **PSStandardMembers** typu [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . Element [PropertySet —](/dotnet/api/system.management.automation.pspropertyset) definiuje grupę właściwości. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name) element określa nazwę zestawu właściwości. I element [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) określa właściwości zestawu. Możesz również dodać `PropertySet` element do elementów członkowskich [typu](/dotnet/api/system.management.automation.pstypename) .

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

## <a name="see-also"></a>Zobacz też

[Informacje o typach. PS1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
