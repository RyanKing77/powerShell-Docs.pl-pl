---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079510"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (v4/v5)

W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania. Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie. Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.

## <a name="compile-configurations"></a>Konfiguracje kompilacji

Pierwszym krokiem do przechowywania [konfiguracje](../configurations/configurations.md) na serwerze ściągania, to aby skompilować je do plików "MOF". Aby konfiguracja ogólny i mające zastosowanie do większej liczby klientów, należy użyć `localhost` w bloku Twojej węzła. W poniższym przykładzie pokazano powłoki konfiguracji, który używa `localhost` zamiast nazwy określonego klienta.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Po skompilowałeś konfiguracji ogólnych powinny mieć plik "localhost.mof".

## <a name="renaming-the-mof-file"></a>Zmiana nazwy pliku MOF

Można przechowywać pliki "MOF" konfiguracji na serwerze ściągania przez **ConfigurationName** lub **ConfigurationID**. W zależności od tego, jak zamierzasz skonfigurować klientów ściągania możesz wybrać sekcję poniżej, aby odpowiednio zmienić nazwy plików skompilowanych "MOF".

### <a name="configuration-ids-guid"></a>Konfiguracja identyfikatory (GUID)

Musisz zmienić nazwę pliku "localhost.mof" do "<GUID>MOF" pliku. Można utworzyć losowej **Guid** w przykładzie poniżej lub za pomocą [nowy Guid](/powershell/module/microsoft.powershell.utility/new-guid) polecenia cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Przykładowe dane wyjściowe

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Następnie można zmienić nazwę pliku "MOF" przy użyciu dowolnej metody dopuszczalne. W poniższym przykładzie użyto [Zmień nazwę elementu](/powershell/module/microsoft.powershell.management/rename-item) polecenia cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Aby uzyskać więcej informacji o korzystaniu z **identyfikatorów GUID** w danym środowisku, zobacz [planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nazwy konfiguracji

Musisz zmienić nazwę pliku "localhost.mof" do "<Configuration Name>MOF" pliku. W poniższym przykładzie jest używana nazwa konfiguracji z poprzedniej sekcji. Następnie można zmienić nazwę pliku "MOF" przy użyciu dowolnej metody dopuszczalne. W poniższym przykładzie użyto [Zmień nazwę elementu](/powershell/module/microsoft.powershell.management/rename-item) polecenia cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Utwórz sumę kontrolną

Każdy plik "MOF" w udziale serwera ściągania lub udział SMB musi mieć plik skojarzony ".checksum". Ten plik umożliwia klientom, o których wiadomo, kiedy plik skojarzony "MOF" został zmieniony i powinny być pobierane ponownie.

Możesz utworzyć **sumy kontrolnej** z [New DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) polecenia cmdlet. Można również uruchomić `New-DSCCheckSum` względem katalogu plików, używając `-Path` parametru. Jeśli istnieje już sumy kontrolnej, aby wymusić można ponownie utworzyć za pomocą `-Force` parametru. W poniższym przykładzie określono katalogu zawierającego plik "MOF" w poprzedniej sekcji i używa `-Force` parametru.

```powershell
New-DscChecksum -Path '.\' -Force
```

Żadne dane wyjściowe będą wyświetlane, ale powinien zostać wyświetlony "<GUID or Configuration Name>. mof.checksum" pliku.

## <a name="where-to-store-mof-files-and-checksums"></a>Gdzie można przechowywać pliki MOF i sumy kontrolne

### <a name="on-a-dsc-http-pull-server"></a>Na serwerze ściągania HTTP DSC

Po skonfigurowaniu serwera ściągania HTTP, jak wyjaśniono w [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md), określ katalogi dla **ModulePath** i **ConfigurationPath** kluczy. **ConfigurationPath** klucz wskazuje, gdzie powinny być przechowywane pliki "MOF". **ConfigurationPath** wskazuje, gdzie wszystkie pliki "MOF" i ".checksum" pliki powinny być przechowywane.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>W udziale SMB

Po skonfigurowaniu używać udziału SMB klienta ściągania należy określić **ConfigurationRepositoryShare**. Wszystkie pliki "MOF" i ".checksum" pliki następnie powinny być przechowywane w **Ścieżka_źródłowa** katalogu z **ConfigurationRepositoryShare** bloku.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Następne kroki

Następnie należy skonfigurować klientów ściągnięcia w celu ściągnięcia określonej konfiguracji. Aby uzyskać więcej informacji zobacz jeden z następujących przewodników:

- [Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v4)](pullClientConfigId4.md)
- [Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v5)](pullClientConfigId.md)
- [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)
- [Pakiet i przekazywanie zasobów do serwera ściągania](package-upload-resources.md)
