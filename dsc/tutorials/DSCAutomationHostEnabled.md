---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684801"
---
><span data-ttu-id="f6363-103">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6363-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="f6363-104">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="f6363-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="f6363-105">Zastosowań DSC **DSCAutomationHostEnabled** klucza rejestru w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** umożliwiające konfigurację na komputerze pod adresem początkowym rozruchu.</span><span class="sxs-lookup"><span data-stu-id="f6363-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="f6363-106">**DSCAutomationHostEnabled** obsługuje trzy tryby:</span><span class="sxs-lookup"><span data-stu-id="f6363-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="f6363-107">Wartość DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="f6363-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="f6363-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f6363-108">Description</span></span>   |
|---|---|
<span data-ttu-id="f6363-109">0</span><span class="sxs-lookup"><span data-stu-id="f6363-109">0</span></span> | <span data-ttu-id="f6363-110">Wyłącz Konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="f6363-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f6363-111">1</span><span class="sxs-lookup"><span data-stu-id="f6363-111">1</span></span> | <span data-ttu-id="f6363-112">Włączanie, konfigurowanie maszyny podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="f6363-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f6363-113">2</span><span class="sxs-lookup"><span data-stu-id="f6363-113">2</span></span> | <span data-ttu-id="f6363-114">Włączanie, konfigurowanie maszyny, tylko wtedy, gdy trwa DSC oczekujące na zatwierdzenie lub bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="f6363-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="f6363-115">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="f6363-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f6363-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6363-116">See Also</span></span>

<span data-ttu-id="f6363-117">Na przykład jak ta funkcja służy do konfiguracji uruchamiania podczas początkowego rozruchu zobacz [skonfigurować maszyny wirtualnej podczas początkowego rozruchu przy użyciu DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="f6363-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
