---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Tworzenie tematów Pomocy dotyczących konfiguracji DSC"
ms.openlocfilehash: c5d499ec887829c864c0f63f64af2d0a7738220b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="writing-help-for-dsc-configurations"></a>Tworzenie tematów Pomocy dotyczących konfiguracji DSC

>Dotyczy: Windows środowiska Windows PowerShell 5.0

Korzystanie z pomocy na podstawie komentarza, w konfiguracji DSC. Użytkownicy mają dostęp do pomocy przez wywołanie funkcji z konfiguracji `-?`, lub za pomocą [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) polecenia cmdlet. Aby uzyskać więcej informacji o pomoc oparta na komentarzach programu PowerShell, zobacz [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).

W poniższym przykładzie przedstawiono skrypt, który zawiera konfigurację i oparta na komentarzach pomocy dla niej:

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

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a>Wyświetlanie pomocy konfiguracji

Aby wyświetlić Pomoc dla konfiguracji, użyj **Get-Help** polecenia cmdlet z nazwą funkcji lub typu następuje nazwa funkcji `-?`. Poniżej przedstawiono dane wyjściowe poprzedniego funkcji przekazany do **Get-Help**:

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1
    
SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.
    
    
SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] 
    <String>] [[-FilePath] <String>] [<CommonParameters>]
    
    
DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.
    

RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a>Zobacz też
* [Konfiguracji DSC](configurations.md)

