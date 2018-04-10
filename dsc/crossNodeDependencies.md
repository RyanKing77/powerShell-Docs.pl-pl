---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Określanie zależności między węzłami
ms.openlocfilehash: c563563118c4df8aeee442d3b30b79f7b7700fc7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="specifying-cross-node-dependencies"></a>Określanie zależności między węzłami

> Dotyczy: Środowiska Windows PowerShell 5.0

DSC zawiera specjalne zasoby **WaitForAll**, **WaitForAny**, i **WaitForSome** który można określić zależności na konfiguracji na innych w konfiguracji węzły. Zachowanie tych zasobów jest następujący:

* **WaitForAll**: zakończy się pomyślnie, jeśli określony zasób jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.
* **WaitForAny**: zakończy się pomyślnie, jeśli określony zasób jest w żądanym stanie na co najmniej jednym z węzłów docelowych określonych w **NodeName** właściwości.
* **WaitForSome**: Określa **NodeCount** właściwość oprócz **NodeName** właściwości. Zasób zakończy się pomyślnie, jeśli zasób jest w żądanym stanie na minimalna liczba węzłów (określonego przez **NodeCount**) określone przez **NodeName** właściwości.

## <a name="using-waitforxxxx-resources"></a>Korzystanie z zasobów WaitForXXXX

Aby użyć **WaitForXXXX** zasoby, utworzyć bloku zasobu tego typu zasobu, które określa DSC zasobów i węzłów oczekiwania. Następnie należy użyć **DependsOn** blokuje właściwość w innych zasobów w konfiguracji, aby czekać na warunki określone w **WaitForXXXX** węzła powiodło się.

Na przykład, w następującej konfiguracji węzła docelowego oczekuje na **xADDomain** zasobów do zakończenia **Kontroler_domeny** węzeł z maksymalnie 30 ponownych prób, na 15 sekund, zanim węzeł docelowy można przyłączyć do domeny.

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**Uwaga:** domyślnie WaitForXXX zasobów spróbuj jeden raz, a następnie kończą się niepowodzeniem. Chociaż nie jest wymagana, zwykle można określić interwał ponawiania prób i liczba.

## <a name="see-also"></a>Zobacz też
* [Konfiguracji DSC](configurations.md)
* [Zasoby usługi Konfiguracja DSC](resources.md)
* [Konfigurowanie lokalny program Configuration Manager](metaConfig.md)