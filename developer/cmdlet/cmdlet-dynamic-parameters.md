---
title: Parametry polecenia cmdlet dynamiczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845276"
---
# <a name="cmdlet-dynamic-parameters"></a>Dynamiczne parametry poleceń cmdlet

Polecenia cmdlet można zdefiniować parametry, które są dostępne dla użytkownika w warunkach specjalne, np. gdy argument innego parametru jest określoną wartością. Te parametry są dodawane w czasie wykonywania i są określane jako *parametrów dynamicznych* ponieważ są one dodawane tylko wtedy, gdy są potrzebne. Na przykład można zaprojektować polecenia cmdlet, który dodaje kilka parametrów, tylko wtedy, gdy określono parametr określonego przełącznika.

> [!NOTE]
> Dostawcy i funkcje programu Windows PowerShell można również definiować parametry dynamiczne.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Parametry dynamiczne w poleceniach cmdlet programu Windows PowerShell

Program Windows PowerShell używa parametrów dynamicznych w kilka z jego poleceń cmdlet dostawcy. Na przykład `Get-Item` i `Get-ChildItem` dodać polecenia cmdlet `CodeSigningCert` parametru w czasie wykonywania podczas `Path` parametru polecenia cmdlet ścieżka certyfikatu dostawcy. Jeśli `Path` parametru polecenia cmdlet Określa ścieżkę do innego dostawcy `CodeSigningCert` parametr nie jest dostępny.

W poniższych przykładach pokazano sposób, w jaki `CodeSigningCert` w czasie wykonywania zostanie dodany parametr podczas `Get-Item` polecenie cmdlet jest uruchamiane.

W pierwszym przykładzie środowiska uruchomieniowego programu Windows PowerShell został dodany parametr, a polecenie cmdlet zakończy się pomyślnie.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

W drugim przykładzie określono dysku systemu plików, i zostanie zwrócony błąd. Komunikat o błędzie oznacza, że `CodeSigningCert` nie można odnaleźć parametru.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Obsługa parametrów dynamicznych

Aby umożliwić obsługę parametrów dynamicznych, kodu polecenie cmdlet musi zawierać następujące elementy.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) ten interfejs zapewnia metody, która pobiera parametry dynamiczne.

Przykład:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) ta metoda pobiera obiekt, który zawiera definicje parametrów dynamicznych.

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

Klasa dynamicznych parametrów ta klasa definiuje parametry, które mają zostać dodane. Ta klasa musi zawierać atrybut parametr, dla każdego parametru i opcjonalnych atrybutów Alias i sprawdzania poprawności, które są wymagane przez polecenie cmdlet.

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

Aby uzyskać pełny przykład polecenia cmdlet, które obsługuje parametry dynamiczne, zobacz [jak deklarować parametrów dynamicznych](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Jak deklarować parametrów dynamicznych](./how-to-declare-dynamic-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
