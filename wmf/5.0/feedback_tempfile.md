---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a><span data-ttu-id="df760-102">Nowe TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="df760-102">New-TemporaryFile</span></span>
<span data-ttu-id="df760-103">Czasami w skryptach, można utworzyć pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="df760-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="df760-104">Można łatwo to zrobić z **TemporaryFile nowy** polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="df760-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="df760-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="df760-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="df760-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="df760-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="df760-107">C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="df760-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

