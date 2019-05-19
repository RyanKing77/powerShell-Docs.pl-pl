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
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855202"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="5605c-102">Tworzenie dostawcy dysku programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5605c-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="5605c-103">W tym temacie opisano sposób tworzenia dostawcy dysk programu Windows PowerShell, który umożliwia dostęp do magazynu danych za pośrednictwem dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5605c-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="5605c-104">Ten typ dostawcy jest również nazywane dostawców dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5605c-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="5605c-105">Dyski programu Windows PowerShell, używany przez dostawcę oferują sposób połączyć się z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="5605c-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="5605c-106">Dostawcy dysk programu Windows PowerShell, które są opisane w tym miejscu zapewnia dostęp do bazy danych programu Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="5605c-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="5605c-107">Dla tego dostawcy, dysk programu Windows PowerShell reprezentuje bazy danych (jest można dodać dowolną liczbę dysków do dostawcy dysku), kontenery najwyższego poziomu stacji reprezentują tabele w bazie danych, a elementy kontenery reprezentują wierszy w tabele.</span><span class="sxs-lookup"><span data-stu-id="5605c-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="5605c-108">Definiowanie klasy dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="5605c-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="5605c-109">Twój dostawca dysku musi definiować klasy .NET, która pochodzi od klasy [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5605c-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="5605c-110">Oto definicji klasy dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="5605c-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5605c-111">Należy zauważyć, że w tym przykładzie [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut określa przyjazny dla użytkownika nazwę dostawcy i konkretne funkcje programu Windows PowerShell, dostawcy Umożliwia uzyskanie dostępu do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia.</span><span class="sxs-lookup"><span data-stu-id="5605c-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="5605c-112">Możliwe wartości dla funkcji dostawcy są definiowane przez [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5605c-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="5605c-113">Ten dostawca dysku nie obsługuje tych możliwości.</span><span class="sxs-lookup"><span data-stu-id="5605c-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="5605c-114">Definiowanie podstawowe funkcje</span><span class="sxs-lookup"><span data-stu-id="5605c-114">Defining Base Functionality</span></span>

<span data-ttu-id="5605c-115">Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa pochodzi od [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) podstawowa klasa, która definiuje metody wymagane dla inicjowanie i cofanie inicjowania dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5605c-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="5605c-116">Aby zaimplementować funkcje dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5605c-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="5605c-117">Jednak większość dostawców (w tym dostawcy opisane w tym miejscu) można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5605c-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="5605c-118">Tworzenie informacji o stanie dysku</span><span class="sxs-lookup"><span data-stu-id="5605c-118">Creating Drive State Information</span></span>

<span data-ttu-id="5605c-119">Wszyscy dostawcy środowiska Windows PowerShell są traktowane jako bezstanowe, oznacza to, czy Twój dostawca dysku musi utworzyć informacje o stanie, wymaganego przez środowisko uruchomieniowe programu Windows PowerShell, wywoływanych przez nią dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5605c-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="5605c-120">Dla tego dostawcy dysku informacje o stanie obejmuje połączenie z bazą danych, która jest przechowywana jako część informacji o dysku.</span><span class="sxs-lookup"><span data-stu-id="5605c-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="5605c-121">Oto kod, który pokazuje, jak te informacje są przechowywane w [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysku:</span><span class="sxs-lookup"><span data-stu-id="5605c-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="5605c-122">Tworzenie dysku</span><span class="sxs-lookup"><span data-stu-id="5605c-122">Creating a Drive</span></span>

<span data-ttu-id="5605c-123">Aby zezwolić na środowisko uruchomieniowe programu Windows PowerShell utworzyć dysk, dostawca dysku musi implementować [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody.</span><span class="sxs-lookup"><span data-stu-id="5605c-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="5605c-124">Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="5605c-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5605c-125">Przesłonięcia tej metody należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5605c-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="5605c-126">Upewnij się, że [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) składowa istnieje i że można nawiązać połączenia z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="5605c-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="5605c-127">Dysk utworzyć i wypełnić połączenia elementu członkowskiego, wspomagające `New-PSDrive` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5605c-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="5605c-128">Sprawdź poprawność [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiektu proponowane dysku.</span><span class="sxs-lookup"><span data-stu-id="5605c-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="5605c-129">Modyfikowanie [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysk z jakichkolwiek wymagane wydajność lub niezawodność informacji lub zapewnia dodatkowe dane dla obiektów wywołujących korzystać z tego dysku.</span><span class="sxs-lookup"><span data-stu-id="5605c-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="5605c-130">Obsługa błędów przy użyciu [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metody, a następnie wróć `null`.</span><span class="sxs-lookup"><span data-stu-id="5605c-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="5605c-131">Ta metoda zwraca albo informacje dysku, który został przekazany do metody lub wersja właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5605c-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="5605c-132">Dołączanie parametrów dynamicznych do NewDrive</span><span class="sxs-lookup"><span data-stu-id="5605c-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="5605c-133">`New-PSDrive` Polecenia cmdlet, obsługiwane przez dostawcę dysku może wymagać dodatkowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5605c-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="5605c-134">Aby dołączyć te parametry dynamiczne do polecenia cmdlet, implementuje dostawcę [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody.</span><span class="sxs-lookup"><span data-stu-id="5605c-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="5605c-135">Ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5605c-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="5605c-136">Ten dostawca dysku nie zastępuje tę metodę.</span><span class="sxs-lookup"><span data-stu-id="5605c-136">This drive provider does not override this method.</span></span> <span data-ttu-id="5605c-137">Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="5605c-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="5605c-138">Usuwanie dysku</span><span class="sxs-lookup"><span data-stu-id="5605c-138">Removing a Drive</span></span>

<span data-ttu-id="5605c-139">Aby zamknąć okno połączenie z bazą danych, należy zaimplementować dostawcy dysku [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody.</span><span class="sxs-lookup"><span data-stu-id="5605c-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="5605c-140">Ta metoda zamyka połączenie na dysku po czyszczenie wszelkie informacje specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5605c-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="5605c-141">Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="5605c-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5605c-142">Jeśli można usunąć dysku, metoda powinna zwrócić informacje przekazane do metody za pomocą `drive` parametru.</span><span class="sxs-lookup"><span data-stu-id="5605c-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="5605c-143">Jeśli nie można usunąć dysku, metoda powinna zapisać wyjątek, a następnie wróć `null`.</span><span class="sxs-lookup"><span data-stu-id="5605c-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="5605c-144">Jeśli Twój dostawca nie zastępuje tę metodę, domyślna implementacja tej metody zwraca tylko informacji o dysku przekazany jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5605c-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="5605c-145">Inicjowanie domyślne dyski</span><span class="sxs-lookup"><span data-stu-id="5605c-145">Initializing Default Drives</span></span>

<span data-ttu-id="5605c-146">Implementuje dostawcę usługi dysku [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodę, aby zainstalować dyski.</span><span class="sxs-lookup"><span data-stu-id="5605c-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="5605c-147">Na przykład dysk na domyślnym kontekstem nazw, jeśli komputer jest przyłączony do domeny mogą zainstalować dostawcę usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5605c-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="5605c-148">Ta metoda zwraca kolekcję informacji o dysku o zainicjowany CD-ROM lub pusta kolekcja.</span><span class="sxs-lookup"><span data-stu-id="5605c-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="5605c-149">Wywołanie tej metody jest przeprowadzany po środowisko uruchomieniowe wywołuje programu Windows PowerShell [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, aby zainicjować dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5605c-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="5605c-150">Ten dostawca dysku nie zastępuje [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metody.</span><span class="sxs-lookup"><span data-stu-id="5605c-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="5605c-151">Jednakże poniższy kod pokazuje implementacji domyślnej, która zwraca kolekcję pusty dysk:</span><span class="sxs-lookup"><span data-stu-id="5605c-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="5605c-152">Warto zapamiętać o implementowaniu InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="5605c-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="5605c-153">Wszyscy dostawcy dysku należy zainstalować dysku głównym, aby ułatwić użytkownikowi przy użyciu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="5605c-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="5605c-154">Dysku głównym może być lista lokalizacji, które służą jako katalogi główne dla innych dysków zainstalowanych.</span><span class="sxs-lookup"><span data-stu-id="5605c-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="5605c-155">Na przykład dostawca usługi Active Directory może utworzyć dysku, który zawiera listę kontekstów nazewnictwa w `namingContext` atrybutów w folderze głównym w środowisku systemu rozproszonego (DSE).</span><span class="sxs-lookup"><span data-stu-id="5605c-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="5605c-156">Pomaga to użytkownikom dostęp do punktów instalacji na innych dyskach.</span><span class="sxs-lookup"><span data-stu-id="5605c-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5605c-157">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="5605c-157">Code Sample</span></span>

<span data-ttu-id="5605c-158">Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5605c-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="5605c-159">Testowanie dostawcy programu Windows PowerShell dysku</span><span class="sxs-lookup"><span data-stu-id="5605c-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="5605c-160">Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia, w tym żadnych poleceń cmdlet udostępnianych przez tworzenie wartości pochodnych.</span><span class="sxs-lookup"><span data-stu-id="5605c-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="5605c-161">Teraz przetestuj dostawcy dysku próbki.</span><span class="sxs-lookup"><span data-stu-id="5605c-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="5605c-162">Uruchom `Get-PSProvider` polecenie cmdlet do pobierania listy dostawców, aby upewnić się, że dostawcy dysku AccessDB znajduje się:</span><span class="sxs-lookup"><span data-stu-id="5605c-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="5605c-163">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="5605c-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="5605c-164">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5605c-164">The following output appears:</span></span>

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

2. <span data-ttu-id="5605c-165">Sprawdź, czy nazwa serwera bazy danych (DSN) istnieje dla bazy danych, uzyskując dostęp do **źródeł danych** część **narzędzia administracyjne** systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5605c-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="5605c-166">W **DSN użytkownika** tabelę, kliknij dwukrotnie **bazy danych programu Access MS** i dodaj ścieżki dysku C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="5605c-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="5605c-167">Utwórz nowy dysk, przy użyciu dostawcy dysku próbki:</span><span class="sxs-lookup"><span data-stu-id="5605c-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="5605c-168">**PS > nowe psdrive-mydb nazwa-root c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="5605c-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="5605c-169">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5605c-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="5605c-170">Sprawdzanie poprawności połączenia.</span><span class="sxs-lookup"><span data-stu-id="5605c-170">Validate the connection.</span></span> <span data-ttu-id="5605c-171">Ponieważ połączenie jest zdefiniowany jako element członkowski w stacji, można sprawdzić za pomocą polecenia cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="5605c-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5605c-172">Użytkownik jeszcze nie może korzystać z dostawcy jako stacja dysków, potrzeb dostawcy kontenera funkcji dla tej interakcji.</span><span class="sxs-lookup"><span data-stu-id="5605c-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="5605c-173">Aby uzyskać więcej informacji, zobacz [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5605c-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="5605c-174">**PS > .connection (get-psdrive mydb)**</span><span class="sxs-lookup"><span data-stu-id="5605c-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="5605c-175">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5605c-175">The following output appears:</span></span>

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

5. <span data-ttu-id="5605c-176">Usuń dysk i wyjdź z powłoki:</span><span class="sxs-lookup"><span data-stu-id="5605c-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="5605c-177">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="5605c-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="5605c-178">**PS > Zakończ**</span><span class="sxs-lookup"><span data-stu-id="5605c-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="5605c-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5605c-179">See Also</span></span>

[<span data-ttu-id="5605c-180">Tworzenie programu Windows PowerShell dostawców</span><span class="sxs-lookup"><span data-stu-id="5605c-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="5605c-181">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5605c-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="5605c-182">Tworzenie dostawcy podstawowy Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5605c-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)