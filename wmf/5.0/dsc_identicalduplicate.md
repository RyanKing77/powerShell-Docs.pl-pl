---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187544"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="71a74-102">Zezwala na taki sam zduplikowane zasoby w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71a74-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="71a74-103">DSC Zezwalaj lub nie obsługiwać definicje powodujące konflikt zasobów w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="71a74-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="71a74-104">Zamiast w trakcie Rozwiąż konflikt, po prostu niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="71a74-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="71a74-105">Jako ponownemu konfiguracji staje się bardziej wykorzystywany przy użyciu złożonego zasobów, konflikty itp. będzie przeprowadzana częściej.</span><span class="sxs-lookup"><span data-stu-id="71a74-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="71a74-106">Gdy definicje powodujące konflikt zasobów są identyczne, DSC należy smart i umożliwia.</span><span class="sxs-lookup"><span data-stu-id="71a74-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="71a74-107">W tej wersji firma Microsoft obsługuje posiadanie wielu wystąpień zasobów mających taki sam definicje:</span><span class="sxs-lookup"><span data-stu-id="71a74-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="71a74-108">W poprzednich wersjach wyniki mogą być zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwera sieci Web".</span><span class="sxs-lookup"><span data-stu-id="71a74-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="71a74-109">Zwróć uwagę, że *wszystkie* właściwości, które mają być skonfigurowane są jednakowe w tych dwóch konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="71a74-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="71a74-110">Ponieważ *wszystkie* właściwości w tych dwóch zasobów są identyczne, spowoduje to teraz pomyślnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="71a74-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="71a74-111">Jeśli dowolne z właściwości różnią się między dwa zasoby, ich nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="71a74-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="71a74-112">Ta konfiguracja bardzo podobne zakończy się niepowodzeniem, ponieważ WindowsFeature FE_IIS i zasoby WindowsFeature Worker_IIS nie są identyczne i w związku z tym w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="71a74-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
