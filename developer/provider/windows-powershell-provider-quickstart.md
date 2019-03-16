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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054921"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="d6906-102">Przewodnik Szybki start dotyczący dostawcy programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6906-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="d6906-103">W tym temacie opisano sposób tworzenia dostawcy środowiska Windows PowerShell, który ma podstawowe funkcje tworzenia nowego dysku.</span><span class="sxs-lookup"><span data-stu-id="d6906-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="d6906-104">Aby uzyskać ogólne informacje o dostawcy, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d6906-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="d6906-105">Przykłady dostawców z funkcjami bardziej szczegółowy, zobacz [przykłady dostawcy](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6906-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="d6906-106">Zapisywanie podstawowego dostawcy</span><span class="sxs-lookup"><span data-stu-id="d6906-106">Writing a basic provider</span></span>

<span data-ttu-id="d6906-107">Jest najbardziej podstawową funkcjonalność dostawcy środowiska Windows PowerShell do tworzenia i usuwania dysków.</span><span class="sxs-lookup"><span data-stu-id="d6906-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="d6906-108">W tym przykładzie wdrożymy [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="d6906-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="d6906-109">Zobaczysz również sposób deklarowania klasy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d6906-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="d6906-110">Podczas pisania dostawcę, można określić domyślnego stacje dysków, które są tworzone automatycznie, gdy dostawca jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="d6906-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="d6906-111">Możesz również zdefiniować metodę, aby utworzyć nowe dyski, które używają tego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d6906-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="d6906-112">Przykłady podane w tym temacie są oparte na [AccessDBProviderSample02](./accessdbprovidersample02.md) próbki, który jest częścią większego przykładu, który reprezentuje bazy danych programu Access jako dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6906-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="d6906-113">Konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="d6906-113">Setting up the project</span></span>

<span data-ttu-id="d6906-114">W programie Visual Studio Utwórz projekt biblioteki klas o nazwie AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="d6906-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="d6906-115">Wykonaj poniższe kroki, aby skonfigurować projekt zostanie uruchomiony program Windows PowerShell, a dostawca zostaną załadowane do sesji, gdy kompilujesz i Rozpocznij swój projekt.</span><span class="sxs-lookup"><span data-stu-id="d6906-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="d6906-116">Konfigurowanie projektu dostawcy</span><span class="sxs-lookup"><span data-stu-id="d6906-116">Configure the provider project</span></span>

1. <span data-ttu-id="d6906-117">Dodaj zestaw System.Management.Automation jako odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="d6906-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="d6906-118">Kliknij przycisk **projektu > właściwości AccessDBProviderSample > debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="d6906-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="d6906-119">W **spustit projekt**, kliknij przycisk **uruchomienia programu zewnętrznego**, a następnie przejdź do pliku wykonywalnego programu Windows PowerShell (zazwyczaj c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="d6906-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="d6906-120">W obszarze **opcje uruchamiania**, wprowadź następujące informacje w **argumenty wiersza polecenia** pola: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="d6906-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="d6906-121">Deklarowanie klasy dostawcy</span><span class="sxs-lookup"><span data-stu-id="d6906-121">Declaring the provider class</span></span>

<span data-ttu-id="d6906-122">U naszego dostawcy jest pochodną [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="d6906-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="d6906-123">Większość dostawców, które zapewniają funkcjonalności rzeczywistego (Uzyskiwanie dostępu do i manipulowanie elementami, nawigacja magazynu danych i pobieranie i ustawianie zawartość elementów) pochodzi od [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="d6906-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="d6906-124">Oprócz określenia, czy klasa jest pochodną [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), musi dekoracji, za pomocą [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d6906-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="d6906-125">Implementowanie NewDrive</span><span class="sxs-lookup"><span data-stu-id="d6906-125">Implementing NewDrive</span></span>

<span data-ttu-id="d6906-126">[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metoda jest wywoływana przez aparatu programu Windows PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)polecenia cmdlet, określając nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d6906-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="d6906-127">Parametr PSDriveInfo jest przekazywany przez aparat programu Windows PowerShell, a metoda ta zwraca nowy dysk do aparatu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6906-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="d6906-128">Ta metoda musi być zadeklarowana w klasie utworzonego powyżej.</span><span class="sxs-lookup"><span data-stu-id="d6906-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="d6906-129">Metoda najpierw sprawdza, upewnij się, obiekt dysku i katalogu głównego dysku, które zostały przekazane, zwracając `null` jeśli którąś z tych funkcji nie jest.</span><span class="sxs-lookup"><span data-stu-id="d6906-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="d6906-130">Reprezentuje połączenie z bazą danych programu Access dysku i następnie używa konstruktora klasy wewnętrznej AccessDBPSDriveInfo do utworzenia nowego dysku.</span><span class="sxs-lookup"><span data-stu-id="d6906-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="d6906-131">Poniżej przedstawiono AccessDBPSDriveInfo Klasa wewnętrzna, która zawiera konstruktora, który został użyty do utworzenia nowego dysku i zawiera informacje o stanie dla dysku.</span><span class="sxs-lookup"><span data-stu-id="d6906-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="d6906-132">Implementowanie RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="d6906-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="d6906-133">[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoda jest wywoływana przez aparatu programu Windows PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6906-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="d6906-134">Metoda tego dostawcy zamyka połączenie z bazą danych programu Access.</span><span class="sxs-lookup"><span data-stu-id="d6906-134">The method in this provider closes the connection to the Access database.</span></span>

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