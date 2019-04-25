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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068219"
---
# <a name="defining-default-methods-for-objects"></a>Definiowanie metod domyślnych dla obiektów

Rozszerzając obiektów .NET Framework, możesz dodać kod metody i metody skryptu do obiektów. Plik XML, który jest używany do definiowania tych metod jest opisane w poniższych sekcjach.

> [!NOTE]
> Przykłady podane w poniższych sekcjach pochodzą z pliku typy Types.ps1xml w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Kod metody

Metoda kod odwołuje się do statycznej metody obiektu .NET Framework.

W poniższym przykładzie **ConvertLargeIntegerToInt64** metoda jest dodawana do [System.Xml.Xmlnode? Displayproperty = imię i nazwisko](/dotnet/api/System.Xml.XmlNode) typu. [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element definiuje rozszerzone metody jako metodę kodu. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę metody rozszerzonej. Ponadto [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element określa metody statycznej. (Można również dodać [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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

Metoda skryptu definiuje metodę, której wartość znajduje się dane wyjściowe skryptu. W poniższym przykładzie **ConvertToDateTime** metoda jest dodawana do [System.Management.Managementobject? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.ManagementObject) typu. [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element definiuje rozszerzone metody jako metodę skryptu. [Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę metody rozszerzonej. Ponadto [skryptu](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element określa skrypt, który generuje wartość metody. (Można również dodać [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)

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