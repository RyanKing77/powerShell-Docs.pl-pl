---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: DSC PackageManagementSource Resource
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource Resource

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**PackageManagementSource** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm do zarejestrowania lub wyrejestrowania źródła zarządzania pakietami w docelowym węźle. **Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać z konta System lub przez aparat DSC.** Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.

## <a name="syntax"></a>Składnia

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Właściwości
|  Właściwość  |  Opis   | 
|---|---| 
| Nazwa| Określa nazwę źródła pakietu jest zarejestrowany lub wyrejestrowany w systemie.| 
| Upewnij się| Określa, czy źródło pakietu ma zostać zarejestrowany lub wyrejestrowany.| 
| InstallationPolicy| Określa, czy masz zaufanie źródła pakietu. One of: "Untrusted", "Trusted".| 
| ProviderName| Określa nazwę dostawcy OneGet za pośrednictwem której można współdziałanie ze źródłem pakietu.| 
| SourceUri| Określa identyfikator URI źródła pakietu.| 
| SourceCredential| Umożliwia dostęp do pakietu zdalnego źródła.| 

## <a name="example"></a>Przykład

W tym przykładzie rejestruje http://nuget.org pakiet źródłowy używa **PackageManagementSource** zasobów usługi Konfiguracja DSC.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

