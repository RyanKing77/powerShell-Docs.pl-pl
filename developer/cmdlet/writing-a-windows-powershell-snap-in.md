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
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845248"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="e039d-102">Pisanie przystawki programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e039d-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="e039d-103">Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania wszystkich poleceń cmdlet i dostawcy środowiska Windows PowerShell w zestawie.</span><span class="sxs-lookup"><span data-stu-id="e039d-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="e039d-104">Z tego typu w przystawce nie należy wybierać które poleceń cmdlet i dostawców, które chcesz zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="e039d-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="e039d-105">Aby napisać przystawki, który służy do wybierania, co jest zarejestrowany, zobacz [pisania niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="e039d-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="e039d-106">Pisanie przystawki programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e039d-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="e039d-107">Dodaj atrybut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="e039d-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="e039d-108">Utwórz klasę publicznej, która pochodzi od klasy [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) klasy.</span><span class="sxs-lookup"><span data-stu-id="e039d-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="e039d-109">W tym przykładzie nazwa klasy jest "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="e039d-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="e039d-110">Dodaj właściwość publiczną nazwę przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="e039d-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="e039d-111">Podczas określania nazwy przystawki, nie używaj żadnego z następujących znaków: #.</span><span class="sxs-lookup"><span data-stu-id="e039d-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="e039d-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="e039d-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="e039d-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="e039d-113">@ \` \*</span></span>

    <span data-ttu-id="e039d-114">W tym przykładzie nazwa ta przystawka jest "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="e039d-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="e039d-115">Dodaj właściwość publiczna dla dostawcy przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="e039d-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="e039d-116">W tym przykładzie Dostawca to "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="e039d-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="e039d-117">Dodaj właściwość publiczna dla dostawcy zasobu (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="e039d-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="e039d-118">W tym przykładzie zasób dostawcą jest "GetProcPSSnapIn01 Microsoft".</span><span class="sxs-lookup"><span data-stu-id="e039d-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="e039d-119">Dodaj właściwość publiczna opis przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="e039d-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="e039d-120">W tym przykładzie opis jest "To jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="e039d-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="e039d-121">Dodaj właściwość publiczna dla zasobu opis (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="e039d-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="e039d-122">W tym przykładzie zasobów dostawcy brzmi "GetProcPSSnapIn01, to jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="e039d-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="e039d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e039d-123">Example</span></span>

<span data-ttu-id="e039d-124">Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania polecenia cmdlet Get-Proc w powłoce programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e039d-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="e039d-125">Należy pamiętać, że w tym przykładzie kompletny zestaw będzie zawierać tylko GetProcPSSnapIn01 przystawki klasa i klasy polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="e039d-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e039d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e039d-126">See Also</span></span>

[<span data-ttu-id="e039d-127">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="e039d-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e039d-128">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="e039d-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e039d-129">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="e039d-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
