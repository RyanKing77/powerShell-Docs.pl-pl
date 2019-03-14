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
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Pisanie niestandardowej przystawki programu Windows PowerShell

Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który rejestruje konkretne polecenia cmdlet.

Z tego typu w przystawce określasz, które poleceń cmdlet, dostawców, typy lub formaty można zarejestrować. Aby uzyskać więcej informacji na temat sposobu pisania przystawki, który rejestruje wszystkie polecenia cmdlet i dostawców w zestawie, zobacz [pisania przystawki programu PowerShell Windows](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Aby zapisać Windows PowerShell przystawki rejestrowanej konkretne polecenia cmdlet.

1. Dodaj atrybut RunInstallerAttribute.

2. Utwórz klasę publicznej, która pochodzi od klasy [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasy.

   W tym przykładzie nazwa klasy jest "CustomPSSnapinTest".

3. Dodaj właściwość publiczną nazwę przystawki (wymagane). Podczas określania nazwy przystawki, nie używaj żadnego z następujących znaków: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   W tym przykładzie nazwa ta przystawka jest "CustomPSSnapInTest".

4. Dodaj właściwość publiczna dla dostawcy przystawki (wymagane).

   W tym przykładzie Dostawca to "Microsoft".

5. Dodaj właściwość publiczna dla dostawcy zasobu (opcjonalnie) przystawki.

   W tym przykładzie zasób dostawcą jest "CustomPSSnapInTest Microsoft".

6. Dodaj właściwość publiczna opis przystawki (wymagane).

   W tym przykładzie opis jest: "To jest niestandardowe środowiska Windows PowerShell przystawki zawierający Test-HelloWorld i polecenia cmdlet Test-CustomSnapinTest".

7. Dodaj właściwość publiczna dla zasobu opis (opcjonalnie) przystawki.

   W tym przykładzie zasobów dostawcy brzmi "CustomPSSnapInTest, to jest niestandardowe środowiska Windows PowerShell przystawki obejmujący polecenia cmdlet Test-HelloWorld i CustomSnapinTest testów".

8. Określ poleceń cmdlet, które należą do niestandardowych w przystawce (opcjonalnie) przy użyciu [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klasy. Dodanych w tym miejscu informacje: nazwa polecenia cmdlet, jego typ architektury .NET i nazwa pliku pomocy polecenia cmdlet (nazwa pliku pomocy polecenia cmdlet powinny być w formacie name.dll help.xml).

   Ten przykład dodaje polecenia cmdlet Test-HelloWorld i TestCustomSnapinTest.

9. Określ dostawców, które należą do przystawki niestandardowej (opcjonalnie).

   W tym przykładzie nie określono żadnych dostawców.

10. Określić typy, które należą do przystawki niestandardowej (opcjonalnie).

    W tym przykładzie nie określono żadnych typów.

11. Określanie formatów, które należą do przystawki niestandardowej (opcjonalnie).

    W tym przykładzie nie określono żadnych formatów.

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób zapisania przystawki Niestandardowa Windows PowerShell, który może służyć do rejestrowania testów-HelloWorld i polecenia cmdlet Test-CustomSnapinTest. Należy pamiętać, że w tym przykładzie kompletny zestaw może zawierać innych poleceń cmdlet i dostawców, którzy nie będzie można zarejestrować przy tej przystawki.

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

Aby uzyskać więcej informacji na temat rejestrowania przystawki, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) w [Windows PowerShell przewodnik](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Zobacz też

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
