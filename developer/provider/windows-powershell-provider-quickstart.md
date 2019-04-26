---
title: Przewodnik Szybki Start Windows dostawcy programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080887"
---
# <a name="windows-powershell-provider-quickstart"></a>Przewodnik Szybki start dotyczący dostawcy programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy środowiska Windows PowerShell, który ma podstawowe funkcje tworzenia nowego dysku. Aby uzyskać ogólne informacje o dostawcy, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md). Przykłady dostawców z funkcjami bardziej szczegółowy, zobacz [przykłady dostawcy](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Zapisywanie podstawowego dostawcy

Jest najbardziej podstawową funkcjonalność dostawcy środowiska Windows PowerShell do tworzenia i usuwania dysków. W tym przykładzie wdrożymy [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy. Zobaczysz również sposób deklarowania klasy dostawcy.

Podczas pisania dostawcę, można określić domyślnego stacje dysków, które są tworzone automatycznie, gdy dostawca jest dostępny. Możesz również zdefiniować metodę, aby utworzyć nowe dyski, które używają tego dostawcy.

Przykłady podane w tym temacie są oparte na [AccessDBProviderSample02](./accessdbprovidersample02.md) próbki, który jest częścią większego przykładu, który reprezentuje bazy danych programu Access jako dysk programu Windows PowerShell.

### <a name="setting-up-the-project"></a>Konfigurowanie projektu

W programie Visual Studio Utwórz projekt biblioteki klas o nazwie AccessDBProviderSample. Wykonaj poniższe kroki, aby skonfigurować projekt zostanie uruchomiony program Windows PowerShell, a dostawca zostaną załadowane do sesji, gdy kompilujesz i Rozpocznij swój projekt.

##### <a name="configure-the-provider-project"></a>Konfigurowanie projektu dostawcy

1. Dodaj zestaw System.Management.Automation jako odwołanie do projektu.

2. Kliknij przycisk **projektu > właściwości AccessDBProviderSample > debugowanie**. W **spustit projekt**, kliknij przycisk **uruchomienia programu zewnętrznego**, a następnie przejdź do pliku wykonywalnego programu Windows PowerShell (zazwyczaj c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. W obszarze **opcje uruchamiania**, wprowadź następujące informacje w **argumenty wiersza polecenia** pola: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Deklarowanie klasy dostawcy

U naszego dostawcy jest pochodną [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy. Większość dostawców, które zapewniają funkcjonalności rzeczywistego (Uzyskiwanie dostępu do i manipulowanie elementami, nawigacja magazynu danych i pobieranie i ustawianie zawartość elementów) pochodzi od [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.

Oprócz określenia, czy klasa jest pochodną [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), musi dekoracji, za pomocą [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) jak pokazano w przykładzie.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>Implementowanie NewDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metoda jest wywoływana przez aparatu programu Windows PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)polecenia cmdlet, określając nazwę dostawcy. Parametr PSDriveInfo jest przekazywany przez aparat programu Windows PowerShell, a metoda ta zwraca nowy dysk do aparatu programu Windows PowerShell. Ta metoda musi być zadeklarowana w klasie utworzonego powyżej.

Metoda najpierw sprawdza, upewnij się, obiekt dysku i katalogu głównego dysku, które zostały przekazane, zwracając `null` jeśli którąś z tych funkcji nie jest. Reprezentuje połączenie z bazą danych programu Access dysku i następnie używa konstruktora klasy wewnętrznej AccessDBPSDriveInfo do utworzenia nowego dysku.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

Poniżej przedstawiono AccessDBPSDriveInfo Klasa wewnętrzna, która zawiera konstruktora, który został użyty do utworzenia nowego dysku i zawiera informacje o stanie dla dysku.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>Implementowanie RemoveDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoda jest wywoływana przez aparatu programu Windows PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) polecenia cmdlet. Metoda tego dostawcy zamyka połączenie z bazą danych programu Access.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```