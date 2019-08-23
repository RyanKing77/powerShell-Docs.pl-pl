---
title: Parametry dynamiczne polecenia cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986251"
---
# <a name="cmdlet-dynamic-parameters"></a>Parametry dynamiczne polecenia cmdlet

Polecenia cmdlet programu mogą definiować parametry, które są dostępne dla użytkownika w warunkach specjalnych, na przykład gdy argument innego parametru jest określoną wartością. Te parametry są dodawane w czasie wykonywania i są określane jako parametry dynamiczne, ponieważ są dodawane tylko w razie potrzeby. Na przykład można zaprojektować polecenie cmdlet, które dodaje kilka parametrów tylko w przypadku określenia określonego parametru przełącznika.

> [!NOTE]
> Dostawcy i funkcje programu PowerShell mogą również definiować parametry dynamiczne.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Parametry dynamiczne w poleceniach cmdlet programu PowerShell

Program PowerShell używa parametrów dynamicznych w kilku poleceniach cmdlet dostawcy. Na `Get-Item` przykład polecenia cmdlet i `Get-ChildItem` dodają parametr **CodeSigningCert** w czasie wykonywania, gdy parametr **Path** określa ścieżkę dostawcy **certyfikatów** . Jeśli parametr **Path** określa ścieżkę dla innego dostawcy, parametr **CodeSigningCert** jest niedostępny.

W poniższych przykładach pokazano, jak parametr **CodeSigningCert** jest dodawany w czasie `Get-Item` wykonywania, gdy jest uruchamiany.

W tym przykładzie środowisko uruchomieniowe programu PowerShell dodało parametr, a polecenie cmdlet zakończyło się pomyślnie.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

W tym przykładzie jest określony dysk systemu **plików** i zwracany jest błąd. Komunikat o błędzie wskazuje, że nie można znaleźć parametru **CodeSigningCert** .

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Obsługa parametrów dynamicznych

Aby można było obsługiwać parametry dynamiczne, należy uwzględnić następujące elementy w kodzie poleceń cmdlet.

### <a name="interface"></a>Interfejs

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Ten interfejs zapewnia metodę, która pobiera parametry dynamiczne.

Przykład:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Metoda

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Ta metoda pobiera obiekt, który zawiera definicje parametrów dynamicznych.

Przykład:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a>Klasa

Klasa, która definiuje parametry dynamiczne do dodania. Ta klasa musi zawierać atrybut **parametrów** dla każdego parametru oraz wszelkie opcjonalne **aliasy** i atrybuty **walidacji** , które są wymagane przez polecenie cmdlet.

Przykład:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Pełny przykład polecenia cmdlet, które obsługuje parametry dynamiczne, można znaleźć w temacie [How to DECLARE Dynamic Parameters](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Zobacz też

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Jak zadeklarować parametry dynamiczne](./how-to-declare-dynamic-parameters.md)

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
