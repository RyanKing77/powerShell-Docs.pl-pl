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
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Zezwalanie na identycznych powielonych zasobów w konfiguracji

DSC Zezwalaj lub nie obsługiwać sprzeczne definicje zasobów w ramach konfiguracji. Zamiast próbować rozwiązać konflikt, ją po prostu nie powiedzie się. Jak ponowne użycie konfiguracji staje się bardziej wykorzystywany przez zasoby złożone, konflikty itp. nastąpi częściej. W przypadku identyczne sprzecznych definicji zasobu DSC należy inteligentne i zezwolić na to. W tej wersji obsługiwane jest posiadanie wielu wystąpień zasobów, które mają identyczne definicje:

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

W poprzednich wersjach wynik będzie, że zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwer sieci Web". Należy zauważyć, że *wszystkich* właściwości, które są konfigurowane są identyczne w dwóch konfiguracjach. Ponieważ *wszystkich* właściwości w te dwa zasoby są identyczne, wynikiem będzie teraz pomyślnej kompilacji.

Jeśli dowolne z właściwości różnią się między dwa zasoby, one nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem:

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

To bardzo podobnej konfiguracji nie powiedzie się, ponieważ WindowsFeature FE_IIS i zasoby WindowsFeature Worker_IIS nie są identyczne i w związku z tym w konflikcie.
