---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058730"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="d3100-102">Zezwalanie na identycznych powielonych zasobów w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d3100-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="d3100-103">DSC Zezwalaj lub nie obsługiwać sprzeczne definicje zasobów w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d3100-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="d3100-104">Zamiast próbować rozwiązać konflikt, ją po prostu nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="d3100-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="d3100-105">Jak ponowne użycie konfiguracji staje się bardziej wykorzystywany przez zasoby złożone, konflikty itp. nastąpi częściej.</span><span class="sxs-lookup"><span data-stu-id="d3100-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="d3100-106">W przypadku identyczne sprzecznych definicji zasobu DSC należy inteligentne i zezwolić na to.</span><span class="sxs-lookup"><span data-stu-id="d3100-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="d3100-107">W tej wersji obsługiwane jest posiadanie wielu wystąpień zasobów, które mają identyczne definicje:</span><span class="sxs-lookup"><span data-stu-id="d3100-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="d3100-108">W poprzednich wersjach wynik będzie, że zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwer sieci Web".</span><span class="sxs-lookup"><span data-stu-id="d3100-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="d3100-109">Należy zauważyć, że *wszystkich* właściwości, które są konfigurowane są identyczne w dwóch konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="d3100-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="d3100-110">Ponieważ *wszystkich* właściwości w te dwa zasoby są identyczne, wynikiem będzie teraz pomyślnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d3100-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="d3100-111">Jeśli dowolne z właściwości różnią się między dwa zasoby, one nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="d3100-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

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

<span data-ttu-id="d3100-112">To bardzo podobnej konfiguracji nie powiedzie się, ponieważ WindowsFeature FE_IIS i zasoby WindowsFeature Worker_IIS nie są identyczne i w związku z tym w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="d3100-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
