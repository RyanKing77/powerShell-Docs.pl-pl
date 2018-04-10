---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Korzystanie z zasobów z wieloma wersjami
ms.openlocfilehash: 9e5b989be3f33fb9151f76cecb6d5f700b1e36c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-resources-with-multiple-versions"></a>Korzystanie z zasobów z wieloma wersjami

> Dotyczy: Środowiska Windows PowerShell 5.0

W programie PowerShell 5.0 DSC zasobów może mieć wiele wersji, a wersji można zainstalować na komputerze side-by-side. Ten sposób jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Instalowanie wielu zasobów wersji side-by-side

Można użyć **MinimumVersion**, **MaximumVersion**, i **RequiredVersion** parametry [instalacji modułu](https://technet.microsoft.com/library/dn807162.aspx) polecenia cmdlet, aby określić która wersja modułu do zainstalowania. Wywoływanie **instalacji modułu** bez określania wersji instaluje najnowszą wersję.

Na przykład istnieje wiele wersji **xFailOverCluster** modułu, z których każdy zawiera **xCluster** zasobów. Wyniku wywołania metody **instalacji modułu** bez określania wersji numer wygląda następująco:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Teraz, jeśli wywołujesz **instalacji modułu** ponownie, ale określ **RequiredVersion** z 1.1.0.0, wyniki w następujących:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Określanie wersji zasobu w konfiguracji

Jeśli masz wiele zasobów zainstalowany na komputerze, gdy jest używany w konfiguracji należy określić wersji tego zasobu. Aby to zrobić, określając **ModuleVersion** parametr **DscResource importu** — słowo kluczowe. Jeśli nie można określić wersji modułu zasobów zasobu, na których zainstalowano więcej niż jedną wersję, konfiguracja powoduje błąd.

Następująca konfiguracja pokazano, jak można określić wersji zasobu, aby wywołać:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Uwaga: Parametr ModuleVersion DscResource importu nie jest dostępny w programie PowerShell 4.0. W programie PowerShell 4.0 można określić wersji modułu przez przekazanie obiektu specyfikacji modułu do parametru ModuleName DscResource importu. Obiekt specyfikacji modułu jest tablicy skrótów, która zawiera klucze ModuleName i RequiredVersion. Przykład:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

To również będą działać w programie PowerShell 5.0, ale zaleca się, że używasz **ModuleVersion** parametru.

## <a name="see-also"></a>Zobacz też
* [Konfiguracji DSC](configurations.md)
* [Zasoby usługi Konfiguracja DSC](resources.md)