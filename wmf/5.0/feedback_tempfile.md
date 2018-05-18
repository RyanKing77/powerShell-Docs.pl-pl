---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="9103a-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="9103a-102">New-TemporaryFile</span></span>
<span data-ttu-id="9103a-103">Czasami w skryptach, można utworzyć pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="9103a-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="9103a-104">Można łatwo to zrobić z **TemporaryFile nowy** polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="9103a-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="9103a-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="9103a-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="9103a-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="9103a-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="9103a-107">C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="9103a-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
