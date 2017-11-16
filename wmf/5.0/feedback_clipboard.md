---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="81c8e-102">Polecenia cmdlet schowka</span><span class="sxs-lookup"><span data-stu-id="81c8e-102">Clipboard cmdlets</span></span>
<span data-ttu-id="81c8e-103">**Get-Schowka** i **Schowka zestaw** ułatwić przesyłanie zawartości do i z sesji środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81c8e-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="81c8e-104">Na przykład skopiuj trzy pliki do Schowka za pomocą Eksploratora Windows (zaznaczając je i naciskając klawisz `ctrl-c`, na przykład), następnie móc zawartość Schowka jako lista plików:</span><span class="sxs-lookup"><span data-stu-id="81c8e-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="81c8e-105">Polecenia cmdlet Schowek obsługuje obrazów, plików audio listy plików i tekst.</span><span class="sxs-lookup"><span data-stu-id="81c8e-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

