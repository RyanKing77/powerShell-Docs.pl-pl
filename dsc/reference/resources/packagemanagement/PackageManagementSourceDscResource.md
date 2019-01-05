---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób PackageManagementSource DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048373"
---
# <a name="dsc-packagemanagementsource-resource"></a>Zasób PackageManagementSource DSC

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0, programu Windows PowerShell 5.1

**PackageManagementSource** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zarejestrować lub wyrejestrować źródła zarządzania pakietami na węzeł docelowy. **Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać konta systemowego lub aparatu DSC.** Ten zasób wymaga **PackageManagement** modułu dostępnym http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** moduł powinien wynosić co najmniej wersji 1.1.7.0 podanie następujących informacji właściwość prawdopodobnie jest niepoprawny.

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
| Nazwa| Określa nazwę źródła pakietu do zarejestrowania lub niezarejestrowanych w Twoim systemie.|
| ProviderName| Określa nazwę dostawca funkcji OneGet za pomocą którego można współdziałania ze źródłem pakietu.|
| SourceLocation| Określa identyfikator URI źródła pakietu.|
| Upewnij się| Określa, czy ma być rejestrowany i wyrejestrowywany źródła pakietu.|
| InstallationPolicy| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa, czy ufasz źródłu pakietu. Jeden z: "Niezaufanych", "zaufany".|
| SourceCredential| Umożliwia dostęp do pakietu zdalnego źródła.|

## <a name="example"></a>Przykład

W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów DSC.

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