---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
><span data-ttu-id="51d02-103">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="51d02-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="51d02-104">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="51d02-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="51d02-105">Używa DSC **DSCAutomationHostEnabled** klucza rejestru w kluczu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** umożliwiające konfigurację na komputerze pod adresem początkowego rozruchu w górę.</span><span class="sxs-lookup"><span data-stu-id="51d02-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="51d02-106">DSCAutomationHostEnabled obsługuje trzy tryby:</span><span class="sxs-lookup"><span data-stu-id="51d02-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="51d02-107">Wartość DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="51d02-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="51d02-108">Opis</span><span class="sxs-lookup"><span data-stu-id="51d02-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="51d02-109">0</span><span class="sxs-lookup"><span data-stu-id="51d02-109">0</span></span> | <span data-ttu-id="51d02-110">Wyłącz Konfigurowanie komputera na rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="51d02-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="51d02-111">1</span><span class="sxs-lookup"><span data-stu-id="51d02-111">1</span></span> | <span data-ttu-id="51d02-112">Włącz konfigurowanie komputera na rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="51d02-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="51d02-113">2</span><span class="sxs-lookup"><span data-stu-id="51d02-113">2</span></span> | <span data-ttu-id="51d02-114">Włącz konfigurowanie maszyny tylko wtedy, gdy trwa DSC oczekujące lub bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="51d02-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="51d02-115">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="51d02-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="51d02-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51d02-116">See Also</span></span>

<span data-ttu-id="51d02-117">Na przykład sposobu używania tej funkcji do jednocześnie konfiguracje początkowego rozruchu w górę zobacz [Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="51d02-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


