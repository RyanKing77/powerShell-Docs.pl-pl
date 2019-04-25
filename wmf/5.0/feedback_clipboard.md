---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057302"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="8e336-102">Polecenia cmdlet schowka</span><span class="sxs-lookup"><span data-stu-id="8e336-102">Clipboard cmdlets</span></span>
<span data-ttu-id="8e336-103">**Get-Schowka** i **Schowka zestaw** ułatwić transferu zawartości do i z sesji środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e336-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="8e336-104">Na przykład, jeśli korzystasz z Eksploratora Windows do skopiowania trzy pliki do Schowka (wybierając je i naciskając klawisz `ctrl-c`, na przykład), następnie łatwo dostępnej zawartość Schowka jako lista plików:</span><span class="sxs-lookup"><span data-stu-id="8e336-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="8e336-105">Polecenia cmdlet Schowka obsługuje obrazy, pliki audio, listy plików i tekst.</span><span class="sxs-lookup"><span data-stu-id="8e336-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
