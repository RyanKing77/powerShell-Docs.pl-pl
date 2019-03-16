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
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055653"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="d5940-102">Tworzenie dostawcy dysku programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5940-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="d5940-103">W tym temacie opisano sposób tworzenia dostawcy dysk programu Windows PowerShell, który umożliwia dostęp do magazynu danych za pośrednictwem dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5940-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="d5940-104">Ten typ dostawcy jest również nazywane dostawców dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5940-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="d5940-105">Dyski programu Windows PowerShell, używany przez dostawcę oferują sposób połączyć się z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="d5940-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="d5940-106">Dostawcy dysk programu Windows PowerShell, które są opisane w tym miejscu zapewnia dostęp do bazy danych programu Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="d5940-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="d5940-107">Dla tego dostawcy, dysk programu Windows PowerShell reprezentuje bazy danych (jest można dodać dowolną liczbę dysków do dostawcy dysku), kontenery najwyższego poziomu stacji reprezentują tabele w bazie danych, a elementy kontenery reprezentują wierszy w tabele.</span><span class="sxs-lookup"><span data-stu-id="d5940-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="d5940-108">Oto lista sekcje w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d5940-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="d5940-109">Jeśli nie jesteś zaznajomiony z pisaniem dostawcy dysk programu Windows PowerShell, należy przeczytać następujące sekcje w kolejności, w jakiej się pojawiają.</span><span class="sxs-lookup"><span data-stu-id="d5940-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="d5940-110">Jednak osoby zaznajomione z pisaniem dostawcy dysku przejdź bezpośrednio do potrzebnych informacji.</span><span class="sxs-lookup"><span data-stu-id="d5940-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="d5940-111">Definiowanie klasy dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="d5940-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="d5940-112">Definiowanie podstawowe funkcje</span><span class="sxs-lookup"><span data-stu-id="d5940-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="d5940-113">Tworzenie informacji o stanie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="d5940-114">Tworzenie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="d5940-115">Dołączanie parametrów dynamicznych do NewDrive</span><span class="sxs-lookup"><span data-stu-id="d5940-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="d5940-116">Usuwanie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="d5940-117">Inicjowanie domyślne dyski</span><span class="sxs-lookup"><span data-stu-id="d5940-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="d5940-118">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="d5940-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="d5940-119">Testowanie dostawcy programu Windows PowerShell dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="d5940-120">Definiowanie klasy dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="d5940-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="d5940-121">Twój dostawca dysku musi definiować klasy .NET, która pochodzi od klasy [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d5940-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="d5940-122">Oto definicji klasy dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="d5940-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="d5940-123">Należy zauważyć, że w tym przykładzie [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut określa przyjazny dla użytkownika nazwę dostawcy i konkretne funkcje programu Windows PowerShell, dostawcy Umożliwia uzyskanie dostępu do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia.</span><span class="sxs-lookup"><span data-stu-id="d5940-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="d5940-124">Możliwe wartości dla funkcji dostawcy są definiowane przez [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d5940-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="d5940-125">Ten dostawca dysku nie obsługuje tych możliwości.</span><span class="sxs-lookup"><span data-stu-id="d5940-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="d5940-126">Definiowanie podstawowe funkcje</span><span class="sxs-lookup"><span data-stu-id="d5940-126">Defining Base Functionality</span></span>

<span data-ttu-id="d5940-127">Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa pochodzi od [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) podstawowa klasa, która definiuje metody wymagane dla inicjowanie i cofanie inicjowania dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d5940-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="d5940-128">Aby zaimplementować funkcje dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d5940-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="d5940-129">Jednak większość dostawców (w tym dostawcy opisane w tym miejscu) można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5940-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="d5940-130">Tworzenie informacji o stanie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-130">Creating Drive State Information</span></span>

<span data-ttu-id="d5940-131">Wszyscy dostawcy środowiska Windows PowerShell są traktowane jako bezstanowe, oznacza to, czy Twój dostawca dysku musi utworzyć informacje o stanie, wymaganego przez środowisko uruchomieniowe programu Windows PowerShell, wywoływanych przez nią dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d5940-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="d5940-132">Dla tego dostawcy dysku informacje o stanie obejmuje połączenie z bazą danych, która jest przechowywana jako część informacji o dysku.</span><span class="sxs-lookup"><span data-stu-id="d5940-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="d5940-133">Oto kod, który pokazuje, jak te informacje są przechowywane w [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysku:</span><span class="sxs-lookup"><span data-stu-id="d5940-133">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="d5940-134">Tworzenie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-134">Creating a Drive</span></span>

<span data-ttu-id="d5940-135">Aby zezwolić na środowisko uruchomieniowe programu Windows PowerShell utworzyć dysk, dostawca dysku musi implementować [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody.</span><span class="sxs-lookup"><span data-stu-id="d5940-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="d5940-136">Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metody dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="d5940-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="d5940-137">Przesłonięcia tej metody należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d5940-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="d5940-138">Upewnij się, że [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) składowa istnieje i że można nawiązać połączenia z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="d5940-138">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="d5940-139">Dysk utworzyć i wypełnić połączenia elementu członkowskiego, wspomagające `New-PSDrive` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5940-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="d5940-140">Sprawdź poprawność [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiektu proponowane dysku.</span><span class="sxs-lookup"><span data-stu-id="d5940-140">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="d5940-141">Modyfikowanie [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiekt, który opisuje dysk z jakichkolwiek wymagane wydajność lub niezawodność informacji lub zapewnia dodatkowe dane dla obiektów wywołujących korzystać z tego dysku.</span><span class="sxs-lookup"><span data-stu-id="d5940-141">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="d5940-142">Obsługa błędów przy użyciu [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metody, a następnie wróć `null`.</span><span class="sxs-lookup"><span data-stu-id="d5940-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="d5940-143">Ta metoda zwraca albo informacje dysku, który został przekazany do metody lub wersja właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d5940-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="d5940-144">Dołączanie parametrów dynamicznych do NewDrive</span><span class="sxs-lookup"><span data-stu-id="d5940-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="d5940-145">`New-PSDrive` Polecenia cmdlet, obsługiwane przez dostawcę dysku może wymagać dodatkowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d5940-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="d5940-146">Aby dołączyć te parametry dynamiczne do polecenia cmdlet, implementuje dostawcę [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody.</span><span class="sxs-lookup"><span data-stu-id="d5940-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="d5940-147">Ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5940-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="d5940-148">Ten dostawca dysku nie zastępuje tę metodę.</span><span class="sxs-lookup"><span data-stu-id="d5940-148">This drive provider does not override this method.</span></span> <span data-ttu-id="d5940-149">Jednakże poniższy kod przedstawia Domyślna implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="d5940-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="d5940-150">Usuwanie dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-150">Removing a Drive</span></span>

<span data-ttu-id="d5940-151">Aby zamknąć okno połączenie z bazą danych, należy zaimplementować dostawcy dysku [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody.</span><span class="sxs-lookup"><span data-stu-id="d5940-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="d5940-152">Ta metoda zamyka połączenie na dysku po czyszczenie wszelkie informacje specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d5940-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="d5940-153">Poniższy kod przedstawia implementację [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody dla tego dostawcy dysku:</span><span class="sxs-lookup"><span data-stu-id="d5940-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="d5940-154">Jeśli można usunąć dysku, metoda powinna zwrócić informacje przekazane do metody za pomocą `drive` parametru.</span><span class="sxs-lookup"><span data-stu-id="d5940-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="d5940-155">Jeśli nie można usunąć dysku, metoda powinna zapisać wyjątek, a następnie wróć `null`.</span><span class="sxs-lookup"><span data-stu-id="d5940-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="d5940-156">Jeśli Twój dostawca nie zastępuje tę metodę, domyślna implementacja tej metody zwraca tylko informacji o dysku przekazany jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d5940-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="d5940-157">Inicjowanie domyślne dyski</span><span class="sxs-lookup"><span data-stu-id="d5940-157">Initializing Default Drives</span></span>

<span data-ttu-id="d5940-158">Implementuje dostawcę usługi dysku [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodę, aby zainstalować dyski.</span><span class="sxs-lookup"><span data-stu-id="d5940-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="d5940-159">Na przykład dysk na domyślnym kontekstem nazw, jeśli komputer jest przyłączony do domeny mogą zainstalować dostawcę usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d5940-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="d5940-160">Ta metoda zwraca kolekcję informacji o dysku o zainicjowany CD-ROM lub pusta kolekcja.</span><span class="sxs-lookup"><span data-stu-id="d5940-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="d5940-161">Wywołanie tej metody jest przeprowadzany po środowisko uruchomieniowe wywołuje programu Windows PowerShell [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodę, aby zainicjować dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d5940-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="d5940-162">Ten dostawca dysku nie zastępuje [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metody.</span><span class="sxs-lookup"><span data-stu-id="d5940-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="d5940-163">Jednakże poniższy kod pokazuje implementacji domyślnej, która zwraca kolekcję pusty dysk:</span><span class="sxs-lookup"><span data-stu-id="d5940-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="d5940-164">Warto zapamiętać o implementowaniu InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="d5940-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="d5940-165">Wszyscy dostawcy dysku należy zainstalować dysku głównym, aby ułatwić użytkownikowi przy użyciu odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="d5940-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="d5940-166">Dysku głównym może być lista lokalizacji, które służą jako katalogi główne dla innych dysków zainstalowanych.</span><span class="sxs-lookup"><span data-stu-id="d5940-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="d5940-167">Na przykład dostawca usługi Active Directory może utworzyć dysku, który zawiera listę kontekstów nazewnictwa w `namingContext` atrybutów w folderze głównym w środowisku systemu rozproszonego (DSE).</span><span class="sxs-lookup"><span data-stu-id="d5940-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="d5940-168">Pomaga to użytkownikom dostęp do punktów instalacji na innych dyskach.</span><span class="sxs-lookup"><span data-stu-id="d5940-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d5940-169">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="d5940-169">Code Sample</span></span>

<span data-ttu-id="d5940-170">Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d5940-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="d5940-171">Testowanie dostawcy programu Windows PowerShell dysku</span><span class="sxs-lookup"><span data-stu-id="d5940-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="d5940-172">Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia, w tym żadnych poleceń cmdlet udostępnianych przez tworzenie wartości pochodnych.</span><span class="sxs-lookup"><span data-stu-id="d5940-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="d5940-173">Teraz przetestuj dostawcy dysku próbki.</span><span class="sxs-lookup"><span data-stu-id="d5940-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="d5940-174">Uruchom `Get-PSProvider` polecenie cmdlet do pobierania listy dostawców, aby upewnić się, że dostawcy dysku AccessDB znajduje się:</span><span class="sxs-lookup"><span data-stu-id="d5940-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="d5940-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="d5940-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="d5940-176">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d5940-176">The following output appears:</span></span>

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

2. <span data-ttu-id="d5940-177">Sprawdź, czy nazwa serwera bazy danych (DSN) istnieje dla bazy danych, uzyskując dostęp do **źródeł danych** część **narzędzia administracyjne** systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d5940-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="d5940-178">W **DSN użytkownika** tabelę, kliknij dwukrotnie **bazy danych programu Access MS** i dodaj ścieżki dysku C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="d5940-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="d5940-179">Utwórz nowy dysk, przy użyciu dostawcy dysku próbki:</span><span class="sxs-lookup"><span data-stu-id="d5940-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="d5940-180">**PS > nowe psdrive-mydb nazwa-root c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="d5940-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="d5940-181">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d5940-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="d5940-182">Sprawdzanie poprawności połączenia.</span><span class="sxs-lookup"><span data-stu-id="d5940-182">Validate the connection.</span></span> <span data-ttu-id="d5940-183">Ponieważ połączenie jest zdefiniowany jako element członkowski w stacji, można sprawdzić za pomocą polecenia cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="d5940-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d5940-184">Użytkownik jeszcze nie może korzystać z dostawcy jako stacja dysków, potrzeb dostawcy kontenera funkcji dla tej interakcji.</span><span class="sxs-lookup"><span data-stu-id="d5940-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="d5940-185">Aby uzyskać więcej informacji, zobacz [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d5940-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="d5940-186">**PS > .connection (get-psdrive mydb)**</span><span class="sxs-lookup"><span data-stu-id="d5940-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="d5940-187">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d5940-187">The following output appears:</span></span>

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

5. <span data-ttu-id="d5940-188">Usuń dysk i wyjdź z powłoki:</span><span class="sxs-lookup"><span data-stu-id="d5940-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="d5940-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="d5940-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="d5940-190">**PS > Zakończ**</span><span class="sxs-lookup"><span data-stu-id="d5940-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="d5940-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5940-191">See Also</span></span>

[<span data-ttu-id="d5940-192">Tworzenie programu Windows PowerShell dostawców</span><span class="sxs-lookup"><span data-stu-id="d5940-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="d5940-193">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5940-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="d5940-194">Tworzenie dostawcy podstawowy Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5940-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)