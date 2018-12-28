---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404711"
---
><span data-ttu-id="069c8-103">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="069c8-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="069c8-104">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="069c8-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="069c8-105">Zastosowań DSC **DSCAutomationHostEnabled** klucza rejestru w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** umożliwiające konfigurację maszyny podczas początkowego rozruchu.</span><span class="sxs-lookup"><span data-stu-id="069c8-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="069c8-106">DSCAutomationHostEnabled obsługuje trzy tryby:</span><span class="sxs-lookup"><span data-stu-id="069c8-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="069c8-107">Wartość DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="069c8-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="069c8-108">Opis</span><span class="sxs-lookup"><span data-stu-id="069c8-108">Description</span></span>   |
|---|---|
<span data-ttu-id="069c8-109">0</span><span class="sxs-lookup"><span data-stu-id="069c8-109">0</span></span> | <span data-ttu-id="069c8-110">Wyłącz Konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="069c8-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="069c8-111">1</span><span class="sxs-lookup"><span data-stu-id="069c8-111">1</span></span> | <span data-ttu-id="069c8-112">Włączanie, konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="069c8-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="069c8-113">2</span><span class="sxs-lookup"><span data-stu-id="069c8-113">2</span></span> | <span data-ttu-id="069c8-114">Włączanie, konfigurowanie maszyny, tylko wtedy, gdy trwa DSC oczekujące na zatwierdzenie lub bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="069c8-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="069c8-115">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="069c8-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="069c8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="069c8-116">See Also</span></span>

<span data-ttu-id="069c8-117">Na przykład jak ta funkcja służy do konfiguracji uruchamiania podczas początkowego rozruchu zobacz [skonfigurować maszyny wirtualnej podczas początkowego rozruchu przy użyciu DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="069c8-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>