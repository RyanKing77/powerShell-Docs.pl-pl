---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Aktualizowanie węzłów z serwera ściągania
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079102"
---
# <a name="update-nodes-from-a-pull-server"></a>Aktualizowanie węzłów z serwera ściągania

W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania. Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie. Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Za pomocą polecenia cmdlet Update-DSCConfiguration

Począwszy od programu PowerShell w wersji 5.0 [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) polecenia cmdlet wymusza węzła do zaktualizowania jego konfiguracji z serwera ściągania skonfigurowany w LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Za pomocą Invoke-CIMMethod

W programie PowerShell 4.0, można nadal ręcznie wymusić na kliencie ściągania aktualizacji, jego konfigurację za pomocą polecenia [polecenia Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). Poniższy przykład tworzy sesję modelu wspólnych informacji przy użyciu podanych poświadczeń, wywołuje odpowiednią metodę modelu wspólnych informacji i usuwa sesji.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Zobacz też

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
