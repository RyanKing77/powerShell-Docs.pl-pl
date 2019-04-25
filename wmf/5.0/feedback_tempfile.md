---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057859"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="104a4-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="104a4-102">New-TemporaryFile</span></span>
<span data-ttu-id="104a4-103">Czasami w skryptach, można utworzyć pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="104a4-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="104a4-104">Łatwo to zrobić za pomocą **New TemporaryFile** polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="104a4-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="104a4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="104a4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="104a4-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="104a4-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="104a4-107">C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="104a4-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
