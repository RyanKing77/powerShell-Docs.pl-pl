---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: Znane problemy w WMF 5.1
ms.openlocfilehash: bb8967a55ec32f0ce21812e065725985010bfc8e
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="known-issues-in-wmf-51"></a>Znane problemy w WMF 5.1 #

> Uwaga: Jest te informacje mogą ulec zmianie.

## <a name="starting-powershell-shortcut-as-administrator"></a>Uruchamianie skrótów programu PowerShell jako Administrator
Po zainstalowaniu pakietu WMF, Jeśli spróbujesz Uruchom program PowerShell jako administrator z skrótu, może wystąpić komunikat "Nieokreślony błąd".
Otwórz ponownie skrót jako bez uprawnień administratora i działa teraz skrót nawet jako administrator.

## <a name="pester"></a>Pester
W tej wersji istnieją dwie kwestie, które należy zwrócić uwagę przy użyciu Pester na serwerze Nano:

* Uruchamianie testów przed Pester się może spowodować niektóre błędy z powodu różnic między PEŁNĄ CLR i CORE CLR. W szczególności metodę sprawdzania poprawności nie jest dostępna w typie XmlDocument. Sześć testów, które będzie przeprowadzane sprawdzanie poprawności schematu dzienniki wyjściowe NUnit są znane się niepowodzeniem. 
* Jeden test pokrycie kodu nie działa obecnie, ponieważ *WindowsFeature* DSC zasób nie istnieje na serwerze Nano Server. Jednak te błędy są zwykle niegroźne i można bezpiecznie zignorować.

## <a name="operation-validation"></a>Sprawdzenie poprawności operacji 

* Update-Help Microsoft.PowerShell.Operation.Validation modułu z powodu wolnego pomocy identyfikator URI kończy się niepowodzeniem

## <a name="dsc-after-uninstall-wmf"></a>DSC po odinstalować WMF 
* Odinstalowywanie WMF nie powoduje usunięcia DSC MOF dokumentów z folderu konfiguracji. DSC nie będą działać prawidłowo, jeśli dokumenty MOF zawiera nowszą właściwości, które nie są dostępne w starszych systemach. W takim przypadku uruchom następujący skrypt konsoli programu PowerShell z podwyższonym poziomem uprawnień, aby wyczyścić stanów DSC.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  

## <a name="jea-virtual-accounts"></a>JEA kont wirtualnych
Punkty końcowe JEA i konfiguracjami sesji skonfigurowane do używania kont wirtualnych w programie WMF 5.0 nie zostanie skonfigurowany do używania konta wirtualnego po uaktualnieniu do wersji WMF 5.1.
Oznacza to, polecenia uruchamiane w sesji JEA będzie uruchamiana tożsamości łączącego się użytkownika zamiast tymczasowego konta administratora, potencjalnie uniemożliwia użytkownikowi uruchamianie poleceń, które wymagają podniesionych uprawnień.
Aby przywrócić kont wirtualnych, należy wyrejestrować i Zarejestruj ponownie wszystkie konfiguracje sesji, które używają kont wirtualnych.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```

