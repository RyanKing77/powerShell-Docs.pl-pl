---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie tematów pomocy dotyczących konfiguracji DSC
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405203"
---
# <a name="writing-help-for-dsc-configurations"></a>Pisanie tematów pomocy dotyczących konfiguracji DSC

>Dotyczy: Windows PowerShell 5.0

Korzystanie z pomocy oparta na komentarzach, w konfiguracjach DSC. Użytkownicy mogą uzyskiwać dostęp do pomocy przez wywołanie metody **konfiguracji** z `-?`, lub za pomocą [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet. Umieść Twojego komentarza Pomoc oparta na bezpośrednio powyżej `Configuration` — słowo kluczowe.
Za pomocą usługi blok komentarza bezpośrednio powyżej deklaracji parametru i / lub tak jak w poniższym przykładzie, można umieścić parametr pomoc w wierszu.

Aby uzyskać więcej informacji na temat programu PowerShell oparta na komentarzach pomocy zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

> [!NOTE]
> PowerShell środowiskach programistycznych, takich jak VSCode i ISE, mają również fragmenty kodu, aby umożliwić automatyczne wstawianie komentarza szablony bloków.

Poniższy przykład pokazuje skrypt, który zawiera konfigurację i oparta na komentarzach pomoc dotyczącą go. W tym przykładzie pokazano konfigurację z parametrami. Aby dowiedzieć się więcej na temat użycia parametrów w konfiguracji, zobacz [Dodaj parametry konfiguracji](add-parameters-to-a-configuration.md).

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a>Wyświetlanie pomocy konfiguracji

Aby wyświetlić Pomoc dla konfiguracji, należy użyć `Get-Help` polecenia cmdlet, o nazwie funkcji lub wpisz nazwę funkcji następuje `-?`. Oto dane wyjściowe poprzedniej konfiguracji, które są przekazywane do `Get-Help`.

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> Składnia pola i atrybuty parametru są generowane automatycznie dla Ciebie programu PowerShell.

## <a name="see-also"></a>Zobacz też

- [Konfiguracje DSC](configurations.md)
- [Zapis, skompilowania i zastosowania konfiguracji](write-compile-apply-configuration.md)
- [Dodaj parametry konfiguracji](add-parameters-to-a-configuration.md)
