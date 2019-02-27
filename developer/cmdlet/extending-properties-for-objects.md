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
# <a name="extending-properties-for-objects"></a>Rozszerzanie właściwości dla obiektów

Rozszerzając obiektów .NET Framework, możesz dodać aliasu właściwości, właściwości kodu, właściwości notatek, właściwości skryptu i zestawy właściwości do obiektów. Plik XML, który jest używany do definiowania tych właściwości jest opisane w poniższych sekcjach.

> [!NOTE]
> W poniższych sekcjach należą do nich z typów Types.ps1xml domyślnego pliku w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Właściwości aliasu

Właściwość alias definiuje nazwę istniejącej właściwości.

W poniższym przykładzie `Count` właściwość została dodana do [System.Array? Displayproperty = imię i nazwisko](/dotnet/api/System.Array) typu. [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element definiuje właściwość rozszerzona jako właściwość aliasu. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nową nazwę. Ponadto [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element Określa istniejącą właściwość, która odwołuje się do aliasu. (Można również dodać [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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

Właściwość kod odwołuje się właściwość statyczna obiektu .NET Framework.

W poniższym przykładzie `Node` właściwość została dodana do [System.IO.Directoryinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.DirectoryInfo) typu. [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element definiuje właściwość rozszerzona jako właściwość kodu. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej. Ponadto [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element definiuje statyczna metoda, która odwołuje się do właściwości rozszerzonej. (Można również dodać [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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

## <a name="note-properties"></a>Właściwości notatek

Właściwość Uwaga definiuje właściwość, która ma wartość statyczną.

W poniższym przykładzie `Status` właściwości (zawsze ma wartość "Powodzenie") jest dodawany do [System.IO.Directoryinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.DirectoryInfo) typu. [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element definiuje właściwość rozszerzona jako właściwość Uwaga; [nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej; i [wartość](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) — element Określa statyczne wartość właściwości rozszerzonej. ( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elementu mogą być również dodawane do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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

Właściwości script definiuje właściwość, której wartość znajduje się dane wyjściowe skryptu.

W poniższym przykładzie `VersionInfo` właściwość została dodana do [System.IO.Fileinfo? Displayproperty = imię i nazwisko](/dotnet/api/System.IO.FileInfo) typu. [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element definiuje właściwość rozszerzona jako właściwość skryptu. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę właściwości rozszerzonej. Ponadto [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element określa skrypt, który generuje wartość właściwości. (Można również dodać [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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

Zestaw właściwości definiuje grupę rozszerzone właściwości, które mogą być przywoływane przez nazwę zestawu. Na przykład `Property` parametru [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) polecenia cmdlet można określić określoną właściwość, aby były wyświetlane. Jeśli jest określony zestaw właściwości, są wyświetlane tylko te właściwości, które należą do zestawu.
Zestaw właściwości definiuje grupę rozszerzone właściwości, które mogą być przywoływane przez nazwę zestawu. Na przykład `Property` parametru [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) polecenia cmdlet można określić określoną właściwość, aby były wyświetlane. Jeśli jest określony zestaw właściwości, są wyświetlane tylko te właściwości, które należą do zestawu.

Nie ma żadnych ograniczeń liczby zestawów właściwości, które mogą być definiowane dla obiektu. Jednak zestawy właściwości, używany do definiowania właściwości wyświetlania domyślnego obiektu muszą być określone w PSStandardMembers zestaw elementów członkowskich. W pliku typy Types.ps1xml domyślne nazwy zestawu właściwości obejmują DefaultDisplayProperty DefaultDisplayPropertySet i DefaultKeyPropertySet. Wszystkie zestawy dodatkowe właściwości, dodawane do zestawu elementów członkowskich PSStandardMembers są ignorowane.

W poniższym przykładzie zestaw właściwości DefaultDisplayPropertySet zostanie dodany do elementu członkowskiego PSStandardMembers zbiór [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) typu. [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element definiuje grupę właściwości. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę zestawu właściwości. Ponadto [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element określa właściwości zestawu. (Można również dodać [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element do elementów członkowskich [typu](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elementu.)

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

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
