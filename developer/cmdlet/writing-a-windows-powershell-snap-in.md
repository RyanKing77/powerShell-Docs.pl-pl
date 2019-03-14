---
title: Zapisywanie przystawki Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: d4f57c062fee09e85c290445082be745ab229985
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795037"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="eed50-102">Pisanie przystawki programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed50-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="eed50-103">Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania wszystkich poleceń cmdlet i dostawcy środowiska Windows PowerShell w zestawie.</span><span class="sxs-lookup"><span data-stu-id="eed50-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="eed50-104">Z tego typu w przystawce nie należy wybierać które poleceń cmdlet i dostawców, które chcesz zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="eed50-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="eed50-105">Aby napisać przystawki, który służy do wybierania, co jest zarejestrowany, zobacz [pisania niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="eed50-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="eed50-106">Pisanie przystawki programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed50-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="eed50-107">Dodaj atrybut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="eed50-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="eed50-108">Utwórz klasę publicznej, która pochodzi od klasy [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) klasy.</span><span class="sxs-lookup"><span data-stu-id="eed50-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="eed50-109">W tym przykładzie nazwa klasy jest "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="eed50-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="eed50-110">Dodaj właściwość publiczną nazwę przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="eed50-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="eed50-111">Podczas określania nazwy przystawki, nie używaj żadnego z następujących znaków: #.</span><span class="sxs-lookup"><span data-stu-id="eed50-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="eed50-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="eed50-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="eed50-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="eed50-113">@ \` \*</span></span>

    <span data-ttu-id="eed50-114">W tym przykładzie nazwa ta przystawka jest "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="eed50-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="eed50-115">Dodaj właściwość publiczna dla dostawcy przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="eed50-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="eed50-116">W tym przykładzie Dostawca to "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="eed50-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="eed50-117">Dodaj właściwość publiczna dla dostawcy zasobu (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="eed50-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="eed50-118">W tym przykładzie zasób dostawcą jest "GetProcPSSnapIn01 Microsoft".</span><span class="sxs-lookup"><span data-stu-id="eed50-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="eed50-119">Dodaj właściwość publiczna opis przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="eed50-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="eed50-120">W tym przykładzie opis jest "To jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="eed50-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="eed50-121">Dodaj właściwość publiczna dla zasobu opis (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="eed50-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="eed50-122">W tym przykładzie zasobów dostawcy brzmi "GetProcPSSnapIn01, to jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="eed50-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="eed50-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="eed50-123">Example</span></span>

<span data-ttu-id="eed50-124">Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania polecenia cmdlet Get-Proc w powłoce programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eed50-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="eed50-125">Należy pamiętać, że w tym przykładzie kompletny zestaw będzie zawierać tylko GetProcPSSnapIn01 przystawki klasa i klasy polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="eed50-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="eed50-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eed50-126">See Also</span></span>

[<span data-ttu-id="eed50-127">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="eed50-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="eed50-128">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="eed50-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
