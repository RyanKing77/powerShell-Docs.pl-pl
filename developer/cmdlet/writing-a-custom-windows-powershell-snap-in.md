---
title: Pisanie niestandardowych Windows PowerShell przystawką | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795593"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="42446-102">Pisanie niestandardowej przystawki programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42446-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="42446-103">Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który rejestruje konkretne polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42446-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="42446-104">Z tego typu w przystawce określasz, które poleceń cmdlet, dostawców, typy lub formaty można zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="42446-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="42446-105">Aby uzyskać więcej informacji na temat sposobu pisania przystawki, który rejestruje wszystkie polecenia cmdlet i dostawców w zestawie, zobacz [pisania przystawki programu PowerShell Windows](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="42446-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="42446-106">Aby zapisać Windows PowerShell przystawki rejestrowanej konkretne polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42446-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="42446-107">Dodaj atrybut RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="42446-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="42446-108">Utwórz klasę publicznej, która pochodzi od klasy [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasy.</span><span class="sxs-lookup"><span data-stu-id="42446-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="42446-109">W tym przykładzie nazwa klasy jest "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="42446-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="42446-110">Dodaj właściwość publiczną nazwę przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="42446-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="42446-111">Podczas określania nazwy przystawki, nie używaj żadnego z następujących znaków: #.</span><span class="sxs-lookup"><span data-stu-id="42446-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="42446-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="42446-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="42446-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="42446-113">@ \` \*</span></span>

   <span data-ttu-id="42446-114">W tym przykładzie nazwa ta przystawka jest "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="42446-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="42446-115">Dodaj właściwość publiczna dla dostawcy przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="42446-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="42446-116">W tym przykładzie Dostawca to "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="42446-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="42446-117">Dodaj właściwość publiczna dla dostawcy zasobu (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="42446-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="42446-118">W tym przykładzie zasób dostawcą jest "CustomPSSnapInTest Microsoft".</span><span class="sxs-lookup"><span data-stu-id="42446-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="42446-119">Dodaj właściwość publiczna opis przystawki (wymagane).</span><span class="sxs-lookup"><span data-stu-id="42446-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="42446-120">W tym przykładzie opis jest: "To jest niestandardowe środowiska Windows PowerShell przystawki zawierający Test-HelloWorld i polecenia cmdlet Test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="42446-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="42446-121">Dodaj właściwość publiczna dla zasobu opis (opcjonalnie) przystawki.</span><span class="sxs-lookup"><span data-stu-id="42446-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="42446-122">W tym przykładzie zasobów dostawcy brzmi "CustomPSSnapInTest, to jest niestandardowe środowiska Windows PowerShell przystawki obejmujący polecenia cmdlet Test-HelloWorld i CustomSnapinTest testów".</span><span class="sxs-lookup"><span data-stu-id="42446-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="42446-123">Określ poleceń cmdlet, które należą do niestandardowych w przystawce (opcjonalnie) przy użyciu [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klasy.</span><span class="sxs-lookup"><span data-stu-id="42446-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="42446-124">Dodanych w tym miejscu informacje: nazwa polecenia cmdlet, jego typ architektury .NET i nazwa pliku pomocy polecenia cmdlet (nazwa pliku pomocy polecenia cmdlet powinny być w formacie name.dll help.xml).</span><span class="sxs-lookup"><span data-stu-id="42446-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="42446-125">Ten przykład dodaje polecenia cmdlet Test-HelloWorld i TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="42446-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="42446-126">Określ dostawców, które należą do przystawki niestandardowej (opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="42446-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="42446-127">W tym przykładzie nie określono żadnych dostawców.</span><span class="sxs-lookup"><span data-stu-id="42446-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="42446-128">Określić typy, które należą do przystawki niestandardowej (opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="42446-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="42446-129">W tym przykładzie nie określono żadnych typów.</span><span class="sxs-lookup"><span data-stu-id="42446-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="42446-130">Określanie formatów, które należą do przystawki niestandardowej (opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="42446-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="42446-131">W tym przykładzie nie określono żadnych formatów.</span><span class="sxs-lookup"><span data-stu-id="42446-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="42446-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="42446-132">Example</span></span>

<span data-ttu-id="42446-133">Ten przykład przedstawia sposób zapisania przystawki Niestandardowa Windows PowerShell, który może służyć do rejestrowania testów-HelloWorld i polecenia cmdlet Test-CustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="42446-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="42446-134">Należy pamiętać, że w tym przykładzie kompletny zestaw może zawierać innych poleceń cmdlet i dostawców, którzy nie będzie można zarejestrować przy tej przystawki.</span><span class="sxs-lookup"><span data-stu-id="42446-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="42446-135">Aby uzyskać więcej informacji na temat rejestrowania przystawki, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) w [Windows PowerShell przewodnik](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="42446-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42446-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42446-136">See Also</span></span>

[<span data-ttu-id="42446-137">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="42446-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="42446-138">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="42446-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
