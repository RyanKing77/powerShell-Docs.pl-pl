---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Importowanie określonej wersji instalowanego zasobu
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080004"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importowanie określonej wersji instalowanego zasobu

> Dotyczy: Windows PowerShell 5.0

W programie PowerShell w wersji 5.0 oddzielnych wersji zasobów DSC można zainstalować na komputerze obok siebie. Moduł zasobów można przechowywać różne wersje zasobu w wersji o nazwie folderów.

## <a name="installing-separate-resource-versions-side-by-side"></a>Instalowanie wersji osobny zasób obok siebie

Możesz użyć **MinimumVersion**, **MaximumVersion**, i **RequiredVersion** parametry [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby określić która wersja modułu do zainstalowania. Wywoływanie **Install-Module** bez określenia wersji instaluje najnowszą wersję.

Na przykład, istnieje wiele wersji **xFailOverCluster** modułu, z których każdy zawiera **xCluster** zasobów. Wywoływanie **Install-Module** bez określenia wersji numer instaluje najnowszą wersję modułu.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Aby zainstalować określoną wersję modułu, należy określić **RequiredVersion** z 1.1.0.0. Spowoduje to zainstalowanie określonej wersji równolegle z zainstalowaną wersją.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Teraz można zobaczyć zarówno wersji modułu liście przy użyciu `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Określanie wersji zasobu w konfiguracji

Jeśli masz osobnego zasobu wersje zainstalowane na komputerze, należy określić wersję tego zasobu, gdy używasz w konfiguracji. Można to zrobić, określając **ModuleVersion** parametru **Import-DscResource** — słowo kluczowe. Jeśli nie można określić wersję modułu zasobów, zasobów, które mają więcej niż jedna wersja zainstalowana, dana konfiguracja taką generuje błąd.

Następująca konfiguracja pokazuje, jak określać wersję zasobu do wywołania:

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

>Uwaga: Parametr ModuleVersion Import-DscResource nie jest dostępny w programie PowerShell 4.0. W programie PowerShell 4.0 można określić wersji modułu, przekazując obiekt specyfikacji modułu do parametru ModuleName Import-DscResource. Obiekt specyfikacji modułu jest tabeli wyznaczania wartości skrótu, która zawiera klucze ModuleName i RequiredVersion. Przykład:

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

Spowoduje to działa również w programie PowerShell 5.0, ale zaleca się, że używasz **ModuleVersion** parametru.

## <a name="see-also"></a>Zobacz też

- [Konfiguracje DSC](configurations.md)
- [Zasoby DSC](../resources/resources.md)
