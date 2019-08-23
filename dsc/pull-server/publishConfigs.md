---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (V4/V5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986571"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (V4/V5)

W poniższych sekcjach przyjęto założenie, że skonfigurowano już serwer ściągania. Jeśli nie skonfigurowano serwera ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB protokołu DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować w taki sposób, aby pobierał konfiguracje, zasoby, a nawet raportuje jego stan. W tym artykule pokazano, jak przekazywać zasoby, aby były dostępne do pobrania, i skonfigurować klientów do automatycznego pobierania zasobów. Gdy węzeł otrzyma przypisaną konfigurację za pośrednictwem **ściągania** lub **wypychania** (V5), automatycznie pobiera wszystkie zasoby wymagane przez konfigurację z lokalizacji określonej w lokalnej Configuration Manager (LCM).

## <a name="compile-configurations"></a>Kompiluj konfiguracje

Pierwszym krokiem do przechowywania [konfiguracji](../configurations/configurations.md) na serwerze ściągania jest skompilowanie ich do `.mof` plików. Aby skonfigurować konfigurację ogólną i zastosować ją do większej liczby klientów, użyj `localhost` w bloku węzła. W poniższym przykładzie przedstawiono powłokę konfiguracji używaną `localhost` zamiast określonej nazwy klienta.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Po skompilowaniu konfiguracji ogólnej należy mieć `localhost.mof` plik.

## <a name="renaming-the-mof-file"></a>Zmiana nazwy pliku MOF

Pliki konfiguracji `.mof` można przechowywać na serwerze ściągania za pomocą elementu **ConfigurationName** lub **ConfigurationID**. W zależności od sposobu konfigurowania klientów ściągania można wybrać sekcję poniżej, aby poprawnie zmienić nazwy skompilowanych `.mof` plików.

### <a name="configuration-ids-guid"></a>Identyfikatory konfiguracji (GUID)

Musisz zmienić nazwę `localhost.mof` pliku na `<GUID>.mof` plik. Można utworzyć losowy **Identyfikator GUID** przy użyciu poniższego przykładu lub przy użyciu polecenia cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Przykładowe dane wyjściowe

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Następnie można zmienić nazwę `.mof` pliku przy użyciu dowolnej akceptowalnej metody. Poniższy przykład używa polecenia cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Aby uzyskać więcej informacji na temat używania **identyfikatorów GUID** w środowisku, zobacz temat [Planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nazwy konfiguracji

Musisz zmienić nazwę `localhost.mof` pliku na `<Configuration Name>.mof` plik. W poniższym przykładzie użyto nazwy konfiguracji z poprzedniej sekcji. Następnie można zmienić nazwę `.mof` pliku przy użyciu dowolnej akceptowalnej metody. Poniższy przykład używa polecenia cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Utwórz sumę kontrolną

Każdy `.mof` plik przechowywany na serwerze ściągania lub udział SMB musi mieć skojarzony `.checksum` plik.
Ten plik umożliwia klientom znać, kiedy skojarzony `.mof` plik został zmieniony i powinien zostać pobrany ponownie.

Można utworzyć **sumę kontrolną** za pomocą polecenia cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) . Można również uruchomić `New-DSCCheckSum` dla katalogu plików `-Path` przy użyciu parametru.
Jeśli suma kontrolna już istnieje, można wymusić jej ponowne utworzenie za pomocą `-Force` parametru. Poniższy przykład określa katalog zawierający `.mof` plik z poprzedniej sekcji i `-Force` używa parametru.

```powershell
New-DscChecksum -Path '.\' -Force
```

Nie będą wyświetlane żadne dane wyjściowe, ale powinien `<GUID or Configuration Name>.mof.checksum` pojawić się plik.

## <a name="where-to-store-mof-files-and-checksums"></a>Miejsce przechowywania plików MOF i sum kontrolnych

### <a name="on-a-dsc-http-pull-server"></a>Na serwerze ściągania HTTP DSC

Podczas konfigurowania serwera ściągania HTTP, zgodnie z opisem w temacie [Konfigurowanie serwera ściągania http DSC](pullServer.md), należy określić katalogi dla kluczy **ModulePath** i **ConfigurationPath** . Klucz **ModulePath** wskazuje, gdzie mają być przechowywane spakowane `.zip` pliki modułu. **ConfigurationPath** wskazuje, gdzie mają `.mof` być przechowywane `.checksum` wszystkie pliki i pliki.

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

Po skonfigurowaniu klienta ściągania do korzystania z udziału SMB należy określić **ConfigurationRepositoryShare**.
Wszystkie `.mof` pliki i `.checksum` pliki powinny być przechowywane w katalogu **SourcePath** z bloku **ConfigurationRepositoryShare** .

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Następne kroki

Następnie należy skonfigurować klientów ściągania w celu ściągnięcia określonej konfiguracji. Aby uzyskać więcej informacji, zobacz jedną z następujących przewodników:

- [Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v4)](pullClientConfigId4.md)
- [Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (V5)](pullClientConfigId.md)
- [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji (V5)](pullClientConfigNames.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie serwera ściągania SMB protokołu DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)
- [Pakowanie i przekazywanie zasobów do serwera ściągania](package-upload-resources.md)
