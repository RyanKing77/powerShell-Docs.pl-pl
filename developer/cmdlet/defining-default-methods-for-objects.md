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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850596"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="0b866-102">Definiowanie metod domyślnych dla obiektów</span><span class="sxs-lookup"><span data-stu-id="0b866-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="0b866-103">Rozszerzając obiektów .NET Framework, możesz dodać kod metody i metody skryptu do obiektów.</span><span class="sxs-lookup"><span data-stu-id="0b866-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="0b866-104">Plik XML, który jest używany do definiowania tych metod jest opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="0b866-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="0b866-105">Przykłady podane w poniższych sekcjach pochodzą z pliku typy Types.ps1xml w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="0b866-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="0b866-106">Kod metody</span><span class="sxs-lookup"><span data-stu-id="0b866-106">Code Methods</span></span>

<span data-ttu-id="0b866-107">Metoda kod odwołuje się do statycznej metody obiektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b866-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="0b866-108">W poniższym przykładzie **ConvertLargeIntegerToInt64** metoda jest dodawana do [System.Xml.Xmlnode? Displayproperty = imię i nazwisko](/dotnet/api/System.Xml.XmlNode) typu.</span><span class="sxs-lookup"><span data-stu-id="0b866-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="0b866-109">[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element definiuje rozszerzone metody jako metodę kodu.</span><span class="sxs-lookup"><span data-stu-id="0b866-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="0b866-110">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="0b866-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="0b866-111">Ponadto [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element określa metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="0b866-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="0b866-112">(Można również dodać [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="0b866-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="0b866-113">Metody skryptu</span><span class="sxs-lookup"><span data-stu-id="0b866-113">Script Methods</span></span>

<span data-ttu-id="0b866-114">Metoda skryptu definiuje metodę, której wartość znajduje się dane wyjściowe skryptu.</span><span class="sxs-lookup"><span data-stu-id="0b866-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="0b866-115">W poniższym przykładzie **ConvertToDateTime** metoda jest dodawana do [System.Management.Managementobject? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.ManagementObject) typu.</span><span class="sxs-lookup"><span data-stu-id="0b866-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="0b866-116">[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element definiuje rozszerzone metody jako metodę skryptu.</span><span class="sxs-lookup"><span data-stu-id="0b866-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="0b866-117">[Nazwa](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Określa nazwę metody rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="0b866-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="0b866-118">Ponadto [skryptu](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element określa skrypt, który generuje wartość metody.</span><span class="sxs-lookup"><span data-stu-id="0b866-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="0b866-119">(Można również dodać [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element do elementów członkowskich [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elementu.)</span><span class="sxs-lookup"><span data-stu-id="0b866-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b866-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b866-120">See Also</span></span>

[<span data-ttu-id="0b866-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b866-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)