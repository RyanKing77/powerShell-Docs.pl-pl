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
# <a name="defining-default-methods-for-objects"></a>Definiowanie metod domyślnych dla obiektów

Rozszerzając .NET Framework obiektów, można dodać metody kodu i metody skryptu do obiektów.
KOD XML, który jest używany do definiowania tych metod, jest opisany w poniższych sekcjach.

> [!NOTE]
> Przykłady w poniższych sekcjach pochodzą z `Types.ps1xml` pliku typów w katalogu instalacyjnym programu Windows PowerShell (`$PSHOME`). Aby uzyskać więcej informacji, zobacz [Informacje o typach. PS1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Metody kodu

Metoda Code odwołuje się do statycznej metody obiektu .NET Framework.

W poniższym przykładzie metoda **ToString** jest dodawana do typu [System. XML. XmlNode](/dotnet/api/System.Xml.XmlNode) . Element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) definiuje metodę rozszerzoną jako metodę kodu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element określa nazwę metody rozszerzonej. I element [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) określa metodę statyczną. Można również dodać element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) do elementów członkowskich elementu [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

## <a name="script-methods"></a>Metody skryptu

Metoda skryptu definiuje metodę, której wartość jest wynikiem skryptu. W poniższym przykładzie metoda **ConvertToDateTime** jest dodawana do typu [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . Element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) definiuje metodę rozszerzoną jako metodę skryptu. [Nazwa](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element określa nazwę metody rozszerzonej. I, element [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) określa skrypt, który generuje wartość metody. Można również dodać element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) do elementów członkowskich elementu [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
