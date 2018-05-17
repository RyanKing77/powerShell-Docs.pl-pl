---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Zezwala na taki sam zduplikowane zasoby w konfiguracji

DSC Zezwalaj lub nie obsługiwać definicje powodujące konflikt zasobów w ramach konfiguracji. Zamiast w trakcie Rozwiąż konflikt, po prostu niepowodzenia. Jako ponownemu konfiguracji staje się bardziej wykorzystywany przy użyciu złożonego zasobów, konflikty itp. będzie przeprowadzana częściej. Gdy definicje powodujące konflikt zasobów są identyczne, DSC należy smart i umożliwia. W tej wersji firma Microsoft obsługuje posiadanie wielu wystąpień zasobów mających taki sam definicje:

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

W poprzednich wersjach wyniki mogą być zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwera sieci Web". Zwróć uwagę, że *wszystkie* właściwości, które mają być skonfigurowane są jednakowe w tych dwóch konfiguracjach. Ponieważ *wszystkie* właściwości w tych dwóch zasobów są identyczne, spowoduje to teraz pomyślnie kompilacji.

Jeśli dowolne z właściwości różnią się między dwa zasoby, ich nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem:

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

Ta konfiguracja bardzo podobne zakończy się niepowodzeniem, ponieważ WindowsFeature FE_IIS i zasoby WindowsFeature Worker_IIS nie są identyczne i w związku z tym w konflikcie.
