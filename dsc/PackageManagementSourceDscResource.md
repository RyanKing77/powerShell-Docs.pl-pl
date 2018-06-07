---
ms.date: 06/20/2018
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób PackageManagementSource DSC
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753774"
---
# <a name="dsc-packagemanagementsource-resource"></a>Zasób PackageManagementSource DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1

**PackageManagementSource** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm do zarejestrowania lub wyrejestrowania źródła zarządzania pakietami w docelowym węźle. **Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać z konta System lub przez aparat DSC.** Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** modułu powinna wynosić co najmniej wersji 1.1.7.0 następujących informacji właściwości są prawidłowe.

## <a name="syntax"></a>Składnia

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Określa nazwę źródła pakietu jest zarejestrowany lub wyrejestrowany w systemie.|
| ProviderName| Określa nazwę dostawcy OneGet za pośrednictwem której można współdziałanie ze źródłem pakietu.|
| SourceLocation| Określa identyfikator URI źródła pakietu.|
| Upewnij się| Określa, czy źródło pakietu ma zostać zarejestrowany lub wyrejestrowany.|
| InstallationPolicy| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa, czy ufasz źródłu tego pakietu. Jeden z: "Niezaufanych", "Zaufanym".|
| SourceCredential| Umożliwia dostęp do pakietu zdalnego źródła.|

## <a name="example"></a>Przykład

W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów usługi Konfiguracja DSC.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```