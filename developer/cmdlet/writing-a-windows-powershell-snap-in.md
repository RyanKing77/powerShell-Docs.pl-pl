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
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057794"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Pisanie przystawki programu Windows PowerShell

Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania wszystkich poleceń cmdlet i dostawcy środowiska Windows PowerShell w zestawie.

Z tego typu w przystawce nie należy wybierać które poleceń cmdlet i dostawców, które chcesz zarejestrować. Aby napisać przystawki, który służy do wybierania, co jest zarejestrowany, zobacz [pisania niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Pisanie przystawki programu Windows PowerShell

1. Dodaj atrybut RunInstallerAttribute.

2. Utwórz klasę publicznej, która pochodzi od klasy [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) klasy.

    W tym przykładzie nazwa klasy jest "GetProcPSSnapIn01".

3. Dodaj właściwość publiczną nazwę przystawki (wymagane). Podczas określania nazwy przystawki, nie używaj żadnego z następujących znaków: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    W tym przykładzie nazwa ta przystawka jest "GetProcPSSnapIn01".

4. Dodaj właściwość publiczna dla dostawcy przystawki (wymagane).

    W tym przykładzie Dostawca to "Microsoft".

5. Dodaj właściwość publiczna dla dostawcy zasobu (opcjonalnie) przystawki.

    W tym przykładzie zasób dostawcą jest "GetProcPSSnapIn01 Microsoft".

6. Dodaj właściwość publiczna opis przystawki (wymagane).

    W tym przykładzie opis jest "To jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".

7. Dodaj właściwość publiczna dla zasobu opis (opcjonalnie) przystawki.

    W tym przykładzie zasobów dostawcy brzmi "GetProcPSSnapIn01, to jest przystawka programu Windows PowerShell, która rejestruje polecenia cmdlet get-proc".

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób zapisania przystawkę programu Windows PowerShell, który może służyć do rejestrowania polecenia cmdlet Get-Proc w powłoce programu Windows PowerShell. Należy pamiętać, że w tym przykładzie kompletny zestaw będzie zawierać tylko GetProcPSSnapIn01 przystawki klasa i klasy polecenia cmdlet Get-Proc.

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

## <a name="see-also"></a>Zobacz też

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
