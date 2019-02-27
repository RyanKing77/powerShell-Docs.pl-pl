---
title: Tworzenie dostawcy dysku środowiska PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846669"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Tworzenie dostawcy dysku programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy dysk programu Windows PowerShell, który umożliwia dostęp do magazynu danych za pośrednictwem dysk programu Windows PowerShell. Ten typ dostawcy jest również nazywane dostawców dysk programu Windows PowerShell. Dyski programu Windows PowerShell, używany przez dostawcę oferują sposób połączyć się z magazynem danych.

Dostawcy dysk programu Windows PowerShell, które są opisane w tym miejscu zapewnia dostęp do bazy danych programu Microsoft Access. Dla tego dostawcy, dysk programu Windows PowerShell reprezentuje bazy danych (jest można dodać dowolną liczbę dysków do dostawcy dysku), kontenery najwyższego poziomu stacji reprezentują tabele w bazie danych, a elementy kontenery reprezentują wierszy w tabele.

Oto lista sekcje w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem dostawcy dysk programu Windows PowerShell, należy przeczytać następujące sekcje w kolejności, w jakiej się pojawiają. Jednak osoby zaznajomione z pisaniem dostawcy dysku przejdź bezpośrednio do potrzebnych informacji.

- [Definiowanie klasy dostawcy programu PowerShell Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definiowanie podstawowe funkcje](#Defining-Base-Functionality)

- [Tworzenie informacji o stanie dysku](#Creating-Drive-State-Information)

- [Tworzenie dysku](#Creating-a-Drive)

- [Dołączanie parametrów dynamicznych do NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Usuwanie dysku](#Removing-a-Drive)

- [Inicjowanie domyślne dyski](#Initializing-Default-Drives)

- [Przykładowy kod](#Code-Sample)

- [Testowanie dostawcy programu Windows PowerShell dysku](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definiowanie klasy dostawcy programu PowerShell Windows

Twój dostawca dysku musi definiować klasy .NET, która pochodzi od klasy [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej. Oto definicji klasy dla tego dostawcy dysku:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Należy zauważyć, że w tym przykładzie [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut określa przyjazny dla użytkownika nazwę dostawcy i konkretne funkcje programu Windows PowerShell, dostawcy Umożliwia uzyskanie dostępu do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Możliwe wartości dla funkcji dostawcy są definiowane przez [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. Ten dostawca dysku nie obsługuje tych możliwości.

## <a name="defining-base-functionality"></a>Definiowanie podstawowe funkcje

Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa pochodzi od [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) podstawowa klasa, która definiuje metody wymagane dla inicjowanie i cofanie inicjowania dostawcy. Aby zaimplementować funkcje dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md). Jednak większość dostawców (w tym dostawcy opisane w tym miejscu) można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.

## <a name="creating-drive-state-information"></a>Tworzenie informacji o stanie dysku

Wszyscy dostawcy środowiska Windows PowerShell są traktowane jako bezstanowe, oznacza to, czy Twój dostawca dysku musi utworzyć informacje o stanie, wymaganego przez środowisko uruchomieniowe programu Windows PowerShell, wywoływanych przez nią dostawcy.

Dla tego dostawcy dysku informacje o stanie obejmuje połączenie z bazą danych, która jest przechowywana jako część informacji o dysku. Oto kod, który pokazuje, jak te informacje są przechowywane w [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysku:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Tworzenie dysku

Aby zezwolić na środowisko uruchomieniowe programu Windows PowerShell utworzyć dysk, dostawca dysku musi implementować [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody. Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody dla tego dostawcy dysku:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Przesłonięcia tej metody należy wykonać następujące czynności:

- Upewnij się, że [System.Management.Automation.Psdriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) składowa istnieje i że można nawiązać połączenia z magazynem danych.

- Dysk utworzyć i wypełnić połączenia elementu członkowskiego, wspomagające `New-PSDrive` polecenia cmdlet.

- Sprawdź poprawność [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiektu proponowane dysku.

- Modyfikowanie [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysk z jakichkolwiek wymagane wydajność lub niezawodność informacji lub zapewnia dodatkowe dane dla obiektów wywołujących korzystać z tego dysku.

- Obsługa błędów przy użyciu [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metody, a następnie wróć `null`.

  Ta metoda zwraca albo informacje dysku, który został przekazany do metody lub wersja właściwe dla dostawcy.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Dołączanie parametrów dynamicznych do NewDrive

`New-PSDrive` Polecenia cmdlet, obsługiwane przez dostawcę dysku może wymagać dodatkowych parametrów. Aby dołączyć te parametry dynamiczne do polecenia cmdlet, implementuje dostawcę [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody. Ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu.

Ten dostawca dysku nie zastępuje tę metodę. Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Usuwanie dysku

Aby zamknąć okno połączenie z bazą danych, należy zaimplementować dostawcy dysku [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody. Ta metoda zamyka połączenie na dysku po czyszczenie wszelkie informacje specyficzne dla dostawcy.

Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody dla tego dostawcy dysku:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Jeśli można usunąć dysku, metoda powinna zwrócić informacje przekazane do metody za pomocą `drive` parametru. Jeśli nie można usunąć dysku, metoda powinna zapisać wyjątek, a następnie wróć `null`. Jeśli Twój dostawca nie zastępuje tę metodę, domyślna implementacja tej metody zwraca tylko informacji o dysku przekazany jako dane wejściowe.

## <a name="initializing-default-drives"></a>Inicjowanie domyślne dyski

Implementuje dostawcę usługi dysku [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodę, aby zainstalować dyski. Na przykład dysk na domyślnym kontekstem nazw, jeśli komputer jest przyłączony do domeny mogą zainstalować dostawcę usługi Active Directory.

Ta metoda zwraca kolekcję informacji o dysku o zainicjowany CD-ROM lub pusta kolekcja. Wywołanie tej metody jest przeprowadzany po środowisko uruchomieniowe wywołuje programu Windows PowerShell [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, aby zainicjować dostawcy.

Ten dostawca dysku nie zastępuje [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metody. Jednakże poniższy kod pokazuje implementacji domyślnej, która zwraca kolekcję pusty dysk:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Warto zapamiętać o implementowaniu InitializeDefaultDrives

Wszyscy dostawcy dysku należy zainstalować dysku głównym, aby ułatwić użytkownikowi przy użyciu odnajdywania. Dysku głównym może być lista lokalizacji, które służą jako katalogi główne dla innych dysków zainstalowanych. Na przykład dostawca usługi Active Directory może utworzyć dysku, który zawiera listę kontekstów nazewnictwa w `namingContext` atrybutów w folderze głównym w środowisku systemu rozproszonego (DSE). Pomaga to użytkownikom dostęp do punktów instalacji na innych dyskach.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testowanie dostawcy programu Windows PowerShell dysku

Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia, w tym żadnych poleceń cmdlet udostępnianych przez tworzenie wartości pochodnych. Teraz przetestuj dostawcy dysku próbki.

1. Uruchom `Get-PSProvider` polecenie cmdlet do pobierania listy dostawców, aby upewnić się, że dostawcy dysku AccessDB znajduje się:

   **PS> `Get-PSProvider`**

   Zostaną wyświetlone następujące dane wyjściowe:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Sprawdź, czy nazwa serwera bazy danych (DSN) istnieje dla bazy danych, uzyskując dostęp do **źródeł danych** część **narzędzia administracyjne** systemu operacyjnego. W **DSN użytkownika** tabelę, kliknij dwukrotnie **bazy danych programu Access MS** i dodaj ścieżki dysku C:\ps\northwind.mdb.

3. Utwórz nowy dysk, przy użyciu dostawcy dysku próbki:

   **PS > nowe psdrive-mydb nazwa-root c:\ps\northwind.mdb - psprovider AccessDb**

   Zostaną wyświetlone następujące dane wyjściowe:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Sprawdzanie poprawności połączenia. Ponieważ połączenie jest zdefiniowany jako element członkowski w stacji, można sprawdzić za pomocą polecenia cmdlet Get-PDDrive.

   > [!NOTE]
   > Użytkownik jeszcze nie może korzystać z dostawcy jako stacja dysków, potrzeb dostawcy kontenera funkcji dla tej interakcji. Aby uzyskać więcej informacji, zobacz [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (get-psdrive mydb)**

   Zostaną wyświetlone następujące dane wyjściowe:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Usuń dysk i wyjdź z powłoki:

   **PS > remove-psdrive mydb**

   **PS > Zakończ**

## <a name="see-also"></a>Zobacz też

[Tworzenie programu Windows PowerShell dostawców](./how-to-create-a-windows-powershell-provider.md)

[Projektowanie dostawcą Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Tworzenie dostawcy podstawowy Windows PowerShell](./creating-a-basic-windows-powershell-provider.md)