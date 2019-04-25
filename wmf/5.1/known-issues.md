---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Znane problemy w programie WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084967"
---
# <a name="known-issues-in-wmf-51"></a>Znane problemy w programie WMF 5.1

> [!Note]
> Te informacje mogą się zmieniać.

## <a name="starting-powershell-shortcut-as-administrator"></a>Począwszy od skrótu programu PowerShell jako Administrator

Po zainstalowaniu programu WMF, jeśli zostanie podjęta próba Uruchom program PowerShell jako administrator za pomocą skrótu, może być wyświetlony komunikat "Z powodu nieokreślonego błędu".
Ponownie otwórz skrót jako użytkowników niebędących administratorami i działa teraz skrótów, nawet administrator.

## <a name="pester"></a>Pester

W tej wersji istnieją dwa problemy, których należy wiedzieć podczas na serwerze Nano Server przy użyciu usług Pester:

- Uruchamianie testów przeciwko usług Pester sam może spowodować niektóre błędy z powodu różnic między CLR pełnej i CORE CLR. W szczególności metoda sprawdzania poprawności jest niedostępna dla typu obiektu XmlDocument. Wiadomo, że sześciu testy, które próbuje sprawdzić schematu NUnit dzienniki wyjściowe powinny się nie powieść.
- Jeden test pokrycia kodu nie działa obecnie, ponieważ *WindowsFeature* zasób DSC nie istnieje na serwerze Nano Server. Jednak te błędy są zazwyczaj niegroźne i można bezpiecznie zignorować.

## <a name="operation-validation"></a>Sprawdzenie poprawności operacji

- `Update-Help` nie powiodło się dla modułu Microsoft.PowerShell.Operation.Validation ze względu na wolne od pracy Pomoc identyfikatora URI

## <a name="dsc-after-uninstall-wmf"></a>DSC po Odinstaluj program WMF

- Odinstalowywanie programu WMF nie powoduje usunięcia dokumentów DSC MOF z folderu konfiguracji. DSC nie będzie działać prawidłowo, jeśli dokumenty MOF zawiera nowszą właściwości, które nie są dostępne w starszych systemach. W takim przypadku uruchom następujący skrypt z podwyższonym poziomem uprawnień konsoli PowerShell, aby wyczyścić stany DSC.

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Kont wirtualnych JEA

Punktów końcowych JEA i konfiguracjami sesji skonfigurowany do używania kont wirtualnych w programie WMF 5.0 nie zostanie skonfigurowany do używania konta wirtualnego po uaktualnieniu do wersji programu WMF 5.1.
Oznacza to, że polecenia uruchamiane w sesjach JEA będzie uruchamiana tożsamości użytkownik nawiązujący połączenie, a nie tymczasowego konta administratora, potencjalnie uniemożliwianie uruchamiania poleceń, które wymagają podniesionych uprawnień.
Aby przywrócić kont wirtualnych, musisz wyrejestrować i ponownie zarejestrować konfiguracji sesji, które używać kont wirtualnych.

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