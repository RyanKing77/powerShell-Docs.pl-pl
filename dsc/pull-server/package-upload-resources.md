---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pakiet i przekazywanie zasobów do serwera ściągania
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079575"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Pakiet i przekazywanie zasobów do serwera ściągania

W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania. Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie. Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.

## <a name="package-resource-modules"></a>Pakiet zasobów modułów

Każdy zasób jest dostępny dla klienta pobrać muszą być przechowywane w pliku ".zip". W poniższym przykładzie opisano kroki wymagane przy użyciu [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) zasobów.

> [!NOTE]
> W przypadku wszystkich klientów przy użyciu programu PowerShell 4.0 będzie konieczne flaten strukturę folderów zasobów i Usuń wszystkie foldery wersji. Aby uzyskać więcej informacji, zobacz [wielu wersji zasobu](../configurations/import-dscresource.md#multiple-resource-versions).

Można kompresować katalog zasobów przy użyciu dowolnego narzędzia, skryptu lub metoda, którego chcesz używać. W Windows, możesz *kliknij prawym przyciskiem myszy* w katalogu "xPSDesiredStateConfiguration" i wybierz pozycję "Wyślij", a następnie "Skompresowany Folder".

![Kliknij prawym przyciskiem myszy](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Nazewnictwo archiwum zasobów

Archiwum zasobu musi mieć nazwę w następującym formacie:

```
{ModuleName}_{Version}.zip
```

W powyższym przykładzie "xPSDesiredStateConfiguration.zip" powinien być zmieniono nazwę "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Tworzenie sumy kontrolne

Gdy moduł zasobów zostanie skompresowany i zmieniono jego nazwę, należy utworzyć **sumy kontrolnej**.  **Sumy kontrolnej** jest używany przez LCM na kliencie, aby ustalić, czy zasób został zmieniony i muszą zostać pobrane ponownie. Możesz utworzyć **sumy kontrolnej** z [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) polecenia cmdlet, jak pokazano w poniższym przykładzie.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Żadne dane wyjściowe będą wyświetlane, ale powinien zostać wyświetlony "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". Można również uruchomić `New-DSCCheckSum` względem katalogu plików, używając `-Path` parametru. Jeśli istnieje już sumy kontrolnej, aby wymusić można ponownie utworzyć za pomocą `-Force` parametru.

### <a name="where-to-store-resource-archives"></a>Miejsce przechowywania zasobów archiwa

#### <a name="on-a-dsc-http-pull-server"></a>Na serwerze ściągania HTTP DSC

Po skonfigurowaniu serwera ściągania HTTP, jak wyjaśniono w [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md), określ katalogi dla **ModulePath** i **ConfigurationPath** kluczy. **ConfigurationPath** klucz wskazuje, gdzie powinny być przechowywane pliki "MOF". **ModulePath** wskazuje przechowywania wszystkich modułów zasobów DSC.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>W udziale SMB

Jeśli określono **ResourceRepositoryShare**, gdy Konfigurowanie klienta ściągania, przechowywane archiwa i sumy kontrolne w **Ścieżka_źródłowa** katalogu z **ResourceRepositoryShare** bloku.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Jeśli określono tylko **ConfigurationRepositoryShare**, gdy Konfigurowanie klienta ściągania, przechowywane archiwa i sumy kontrolne w **Ścieżka_źródłowa** katalogu z  **ConfigurationRepositoryShare** bloku.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Aktualizowanie zasobów

Można wymusić węzeł, aby zaktualizować swoje zasoby, zmieniając numer wersji w nazwie archiwum lub tworząc nowe sumy kontrolnej. Klienta ściągania będzie sprawdzać dostępność nowych wersji z wymaganych zasobów, a także zaktualizować sumy kontrolne, podczas jego LCM odświeżania.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)
