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
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="6186d-103">Pisanie tematów pomocy dotyczących konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="6186d-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="6186d-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6186d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6186d-105">Korzystanie z pomocy oparta na komentarzach, w konfiguracjach DSC.</span><span class="sxs-lookup"><span data-stu-id="6186d-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="6186d-106">Użytkownicy mogą uzyskiwać dostęp do pomocy przez wywołanie metody **konfiguracji** z `-?`, lub za pomocą [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6186d-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="6186d-107">Umieść Twojego komentarza Pomoc oparta na bezpośrednio powyżej `Configuration` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6186d-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="6186d-108">Za pomocą usługi blok komentarza bezpośrednio powyżej deklaracji parametru i / lub tak jak w poniższym przykładzie, można umieścić parametr pomoc w wierszu.</span><span class="sxs-lookup"><span data-stu-id="6186d-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="6186d-109">Aby uzyskać więcej informacji na temat programu PowerShell oparta na komentarzach pomocy zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="6186d-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="6186d-110">PowerShell środowiskach programistycznych, takich jak VSCode i ISE, mają również fragmenty kodu, aby umożliwić automatyczne wstawianie komentarza szablony bloków.</span><span class="sxs-lookup"><span data-stu-id="6186d-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="6186d-111">Poniższy przykład pokazuje skrypt, który zawiera konfigurację i oparta na komentarzach pomoc dotyczącą go.</span><span class="sxs-lookup"><span data-stu-id="6186d-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="6186d-112">W tym przykładzie pokazano konfigurację z parametrami.</span><span class="sxs-lookup"><span data-stu-id="6186d-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="6186d-113">Aby dowiedzieć się więcej na temat użycia parametrów w konfiguracji, zobacz [Dodaj parametry konfiguracji](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6186d-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="6186d-114">Wyświetlanie pomocy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6186d-114">Viewing configuration help</span></span>

<span data-ttu-id="6186d-115">Aby wyświetlić Pomoc dla konfiguracji, należy użyć `Get-Help` polecenia cmdlet, o nazwie funkcji lub wpisz nazwę funkcji następuje `-?`.</span><span class="sxs-lookup"><span data-stu-id="6186d-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="6186d-116">Oto dane wyjściowe poprzedniej konfiguracji, które są przekazywane do `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6186d-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

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
> <span data-ttu-id="6186d-117">Składnia pola i atrybuty parametru są generowane automatycznie dla Ciebie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6186d-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="6186d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6186d-118">See Also</span></span>

- [<span data-ttu-id="6186d-119">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="6186d-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="6186d-120">Zapis, skompilowania i zastosowania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6186d-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="6186d-121">Dodaj parametry konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6186d-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
