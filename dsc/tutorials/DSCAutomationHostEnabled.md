---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076496"
---
><span data-ttu-id="c3258-103">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c3258-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="c3258-104">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="c3258-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="c3258-105">Zastosowań DSC **DSCAutomationHostEnabled** klucza rejestru w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** umożliwiające konfigurację na komputerze pod adresem początkowym rozruchu.</span><span class="sxs-lookup"><span data-stu-id="c3258-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="c3258-106">**DSCAutomationHostEnabled** obsługuje trzy tryby:</span><span class="sxs-lookup"><span data-stu-id="c3258-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="c3258-107">Wartość DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="c3258-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="c3258-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c3258-108">Description</span></span>   |
|---|---|
<span data-ttu-id="c3258-109">0</span><span class="sxs-lookup"><span data-stu-id="c3258-109">0</span></span> | <span data-ttu-id="c3258-110">Wyłącz Konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="c3258-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="c3258-111">1</span><span class="sxs-lookup"><span data-stu-id="c3258-111">1</span></span> | <span data-ttu-id="c3258-112">Włączanie, konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="c3258-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="c3258-113">2</span><span class="sxs-lookup"><span data-stu-id="c3258-113">2</span></span> | <span data-ttu-id="c3258-114">Włączanie, konfigurowanie maszyny, tylko wtedy, gdy trwa DSC oczekujące na zatwierdzenie lub bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="c3258-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="c3258-115">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="c3258-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3258-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3258-116">See Also</span></span>

<span data-ttu-id="c3258-117">Na przykład jak ta funkcja służy do konfiguracji uruchamiania podczas początkowego rozruchu zobacz [skonfigurować maszyny wirtualnej podczas początkowego rozruchu przy użyciu DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="c3258-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
