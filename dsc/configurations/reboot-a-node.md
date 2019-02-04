---
ms.date: 1/17/2019
keywords: DSC, powershell, konfiguracja, ustawienia
title: Ponowny rozruch węzła
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685690"
---
# <a name="reboot-a-node"></a>Ponowny rozruch węzła

> [!NOTE]
> W tym temacie opowiada, jak wykonać ponowny rozruch węzła. Aby ponowne uruchomienie w celu pomyślnego **ActionAfterReboot** i **RebootNodeIfNeeded** LCM ustawienia muszą być prawidłowo skonfigurowane.
> Aby uzyskać informacje o ustawieniach Local Configuration Manager, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md), lub [Konfigurowanie programu Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).

Węzły mogą być uruchamiane z w ramach zasobu, używając `$global:DSCMachineStatus` flagi. Ustawienie tej flagi `1` w `Set-TargetResource` funkcja wymusza LCM wykonać ponowny rozruch węzła, bezpośrednio po **ustaw** metoda bieżącego zasobu. Przy użyciu tej flagi **xPendingReboot** zasobów wykrywa, jeśli trwa oczekiwanie na ponowne poza DSC.

Twoje [konfiguracje](configurations.md) może wykonywać czynności, które wymagają węzłów o ponownym uruchomieniu. Może to obejmować rzeczy, takich jak:

- Aktualizacje Windows
- Instalacja oprogramowania
- Zmienia nazwę pliku
- Zmiana nazwy komputera

**XPendingReboot** zasobów sprawdza, czy określony komputer lokalizacje, aby określić, jeśli trwa oczekiwanie na ponowne. Jeśli węzeł wymaga ponownego uruchomienia systemu poza DSC, **xPendingReboot** zestawów zasobów `$global:DSCMachineStatus` flaga `1` wymuszenie ponownego uruchomienia systemu i rozwiązywania oczekujące warunku.

> [!NOTE]
> Dowolny zasób DSC można nakazać LCM wykonać ponowny rozruch węzła przez ustawienie tej flagi `Set-TargetResource` funkcji. Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych z pliku MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Składnia

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Właściwości

| Właściwość | Opis |
| --- | --- |
| Nazwa| Wymagany parametr, który musi być unikatowy dla każdego wystąpienia zasobów w ramach konfiguracji.|
| SkipComponentBasedServicing | Pomiń ponowne uruchamianie wyzwalane przez składnik oparty na komponentach obsługi. |
| SkipWindowsUpdate | Pomiń ponowne uruchamianie wyzwalane przez usługę Windows Update.|
| SkipPendingFileRename | Pomiń plik oczekujące zmiany nazwy jest uruchamiany ponownie. |
| SkipCcmClientSDK | Pomiń ponowne uruchamianie wyzwalane przez klienta programu ConfigMgr. |
| SkipComputerRename | Pomiń ponowny rozruch wyzwolone przez zmienia nazwę komputera. |
| PSDSCRunAsCredential | Obsługiwane w wersji 5. Wykonuje zasobu jako określony użytkownik. |
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`. Aby uzyskać więcej informacji, zobacz [DependsOn przy użyciu](resource-depends-on.md)|

## <a name="example"></a>Przykład

W poniższym przykładzie instalowana za pomocą programu Microsoft Exchange [xExchange](https://github.com/PowerShell/xExchange) zasobów.
W całej instalacji **xPendingReboot** zasób służy do ponownego rozruchu węzła.

> [!NOTE]
> W tym przykładzie wymaga poświadczeń konta które ma prawa do dodawania serwera Exchange w lesie. Aby uzyskać więcej informacji na temat korzystania z poświadczeń w DSC, zobacz [obsługi poświadczeń w DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> W przykładzie założono, że skonfigurowano usługi Local Configuration Manager, aby zezwolić na ponowne uruchamianie i kontynuować konfigurację po ponownym uruchomieniu.

## <a name="where-to-download"></a>Gdzie można pobrać

Możesz pobrać zasoby używane w tym temacie w następujących lokalizacjach lub za pomocą galerii programu PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
