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
# <a name="defining-default-methods-for-objects"></a>Definiowanie metod domyślnych dla obiektów

Rozszerzając obiektów .NET Framework, możesz dodać kod metody i metody skryptu do obiektów. Plik XML, który jest używany do definiowania tych metod jest opisane w poniższych sekcjach.

> [!NOTE]
> Przykłady podane w poniższych sekcjach pochodzą z pliku typy Types.ps1xml w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Kod metody

Metoda kod odwołuje się do statycznej metody obiektu .NET Framework.

W poniższym przykładzie **ConvertLargeIntegerToInt64** metoda jest dodawana do [System.Xml.Xmlnode? Displayproperty = imię i nazwisko](/dotnet/api/System.Xml.XmlNode) typu. [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element definiuje rozszerzone metody jako metodę kodu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Określa nazwę metody rozszerzonej. Ponadto [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element określa metody statycznej. (Można również dodać [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element do elementów członkowskich [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elementu.)

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

## <a name="script-methods"></a>Metody skryptu

Metoda skryptu definiuje metodę, której wartość znajduje się dane wyjściowe skryptu. W poniższym przykładzie **ConvertToDateTime** metoda jest dodawana do [System.Management.Managementobject? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.ManagementObject) typu. [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element definiuje rozszerzone metody jako metodę skryptu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Określa nazwę metody rozszerzonej. Ponadto [skryptu](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element określa skrypt, który generuje wartość metody. (Można również dodać [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element do elementów członkowskich [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elementu.)

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

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
