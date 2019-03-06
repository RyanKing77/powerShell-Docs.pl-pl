---
title: Tworzenie dostawcy nawigacji Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: cbc8ce0600553f9e9ab973d6f92ea5eafde310e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430040"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Tworzenie dostawcy nawigacji programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy nawigacji programu Windows PowerShell, który można przejść do magazynu danych. Ten typ dostawcy obsługuje cykliczne poleceń, zagnieżdżone kontenery i ścieżek względnych.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider05.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

Dostawca opisane w tym miejscu umożliwia dojście użytkownika bazy danych programu Access jako dysk, dzięki czemu użytkownik może przejść do tabel danych w bazie danych. Podczas tworzenia własnego dostawcę nawigacji, można zaimplementować metody, które można wprowadzić kwalifikowana dysku ścieżek, wymagane do nawigacji, normalizacji ścieżek względnych, przenoszenie elementów w magazynie danych, a także metody, które pobrać nazw podrzędnych, uzyskać ścieżki nadrzędnej elementu i testowanie Aby sprawdzić, czy element jest kontenerem.

> [!CAUTION]
> Należy pamiętać, zakłada, że ten projekt bazy danych, które zawiera pole o identyfikatorze nazwa i typ pola to LongInteger.

Poniższa lista zawiera sekcje, w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem dostawcy nawigacji programu Windows PowerShell, przeczytaj te informacje w kolejności, która wygląda na to. Jednak jeśli i dopiero zaczynasz pisanie dostawcy nawigacji programu Windows PowerShell, przejdź bezpośrednio do potrzebnych informacji.

- [Definiowanie klasy dostawcy nawigacji PS](#Define-the-Windows-PowerShell-provider)

- [Definiowanie podstawowe funkcje](#Defining-Base-Functionality)

- [Tworzenie ścieżki PS](#Creating-a-Windows-PowerShell-Path)

- [Pobieranie ścieżki nadrzędnej](#Retrieving-the-Parent-Path)

- [Pobieranie nazwy ścieżki podrzędne](#Retrieve-the-Child-Path-Name)

- [Określanie, czy element kontenera](#Determining-if-an-Item-is-a-Container)

- [Przenoszenie elementu](#Moving-an-Item)

- [Dołączanie parametrów dynamicznych do `Move-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Normalizowanie ścieżki względnej](#Normalizing-a-Relative-Path)

- [Przykładowy kod](#Code-Sample)

- [Definiowanie typów obiektów i formatowanie](#Defining-Object-Types-and-Formatting)

- [Tworzenie dostawcy programu Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Testowanie dostawcy programu Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Zdefiniuj dostawcy programu Windows PowerShell

Dostawca nawigacji programu Windows PowerShell należy utworzyć klasę .NET, która pochodzi od klasy [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy bazowej. Oto definicji klasy dla dostawcy nawigacji opisane w tej sekcji.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Należy pamiętać, że w tym dostawcy [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut zawiera dwa parametry. Pierwszy parametr określa przyjazną dla użytkownika nazwę dostawcy, który jest używany przez program Windows PowerShell. Drugi parametr określa specyficzne możliwości programu Windows PowerShell, które dostawca udostępnia do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Dla tego dostawcy istnieją nie konkretne funkcje programu Windows PowerShell, które są dodawane.

## <a name="defining-base-functionality"></a>Definiowanie podstawowe funkcje

Zgodnie z opisem w [projektowania Twój dostawca PS](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) podstawowa klasa pochodzi od innych klas, które podano innego dostawcy funkcje. Dostawca nawigacji programu Windows PowerShell, w związku z tym, należy zdefiniować wszystkie funkcje udostępniane przez te klasy.

Aby zaimplementować funkcje dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy PS](./creating-a-basic-windows-powershell-provider.md). Jednak większość dostawców (w tym dostawcy opisane w tym miejscu) można użyć Domyślna implementacja tej funkcji, dostarczonych przez program Windows PowerShell.

Aby uzyskać dostęp do magazynu danych za pośrednictwem dysk programu Windows PowerShell, należy zaimplementować metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Do modyfikowania elementów magazynu danych, takich jak wprowadzenie, ustawienia i czyszczenie elementów, dostawca musi implementować metod dostarczonych przez [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy usługi Windows PowerShell elementu](./creating-a-windows-powershell-item-provider.md).

Aby uzyskać dostęp do elementów podrzędnych lub ich nazwy w magazynie danych, a także metody, tworzenie, kopiowanie, zmiana nazwy i usuwanie elementów, które należy zaimplementować metod dostarczonych przez [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Tworzenie ścieżki Windows PowerShell

Dostawca nawigacji programu Windows PowerShell Użyj wewnętrzna dostawcy ścieżki programu Windows PowerShell, aby przejść elementów magazynu danych. Aby utworzyć ścieżkę wewnętrzna dostawcy dostawca musi implementować [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metody obsługuje wywołania z polecenia cmdlet ścieżkę łączenia. Ta metoda łączy ścieżki nadrzędnej i podrzędnej w ścieżką wewnętrzna dostawcy przy użyciu separatora ścieżki specyficznego dla dostawcy między ścieżek nadrzędnych i podrzędnych.

Domyślna implementacja pobiera ścieżki "/" lub "\\"jako separatora ścieżki normalizuje separatora ścieżki do"\\", łączy części ścieżki nadrzędnej i podrzędnej z separatorem między nimi, a następnie zwraca ciąg, który zawiera połączone ścieżki.

Ten dostawca nawigacji nie implementuje tej metody. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Warto zapamiętać o implementowaniu makepath —

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Implementacja [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoda nie może zweryfikować ścieżkę jako ścieżka w pełni kwalifikowanych w przestrzeni nazw dostawcy. Należy pamiętać, że każdego parametru może być reprezentowana przez części ścieżki i elementy połączone nie może wygenerować pełną ścieżkę. Na przykład [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metody dla dostawcy systemu plików może zostać wyświetlony "windows\system32" w `parent` parametr i "abc.dll" w `child` parametru. Metoda łączy te wartości przy użyciu "\\" separatora i zwraca "windows\system32\abc.dll", który nie jest ścieżka systemu plików w pełni kwalifikowana.

  > [!IMPORTANT]
  > Części ścieżki podany w wywołaniu [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) może zawierać znaki nie są dozwolone w przestrzeni nazw dostawcy. Te znaki prawdopodobnie są używane do rozszerzenia symboli wieloznacznych i implementacja tej metody nie należy usuwać je.

## <a name="retrieving-the-parent-path"></a>Pobieranie ścieżki nadrzędnej

Implementowanie dostawcy nawigacji programu Windows PowerShell [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metodę, która pobierze nadrzędnej części wskazany pełnej lub częściowej Ścieżka właściwe dla dostawcy. Metoda usuwa podrzędne części ścieżki i zwraca element nadrzędny część ścieżki. `root` Parametr określa pełną ścieżkę do katalogu głównego dysku. Ten parametr może być wartość null lub jest pusta, jeśli zainstalowany dysk nie jest używany dla operacji pobierania. Jeśli katalog główny jest określony, metoda musi zwracać ścieżka do kontenera w tym samym drzewie jako katalogu głównego.

Dostawca nawigacji przykładowych nie należy przesłonić tę metodę, ale używa implementacji domyślnej. Akceptuje ścieżki, które używają zarówno "/" i "\\" jako separatorami ścieżki. Najpierw normalizuje ścieżkę do mają tylko "\\" separatory, następnie dzieli Ścieżka nadrzędna poza ostatni "\\" i zwraca ścieżkę nadrzędną.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Należy pamiętać o implementowaniu GetParentPath

Implementacja [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoda podzielić ścieżka leksykalnie separatora ścieżki dla przestrzeni nazw dostawcy. Na przykład dostawcy filesystem używa tej metody do wyszukania w ciągu ostatnich "\\" i zwraca wszystkie elementy z lewej strony separatora.

## <a name="retrieve-the-child-path-name"></a>Pobieranie nazwy ścieżki podrzędne

Implementuje dostawcę usługi nawigacji [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metodę, aby pobrać nazwy (element liścia) podrzędny element znajdujący się w wskazany pełnej lub Ścieżka częściowa właściwe dla dostawcy.

Dostawcy nawigacji próbki nie zastępuje tę metodę. Domyślna implementacja znajdują się poniżej. Akceptuje ścieżki, które używają zarówno "/" i "\\" jako separatorami ścieżki. Najpierw normalizuje ścieżkę do mają tylko "\\" separatory, następnie dzieli Ścieżka nadrzędna poza ostatni "\\" i zwraca nazwę elementu podrzędnego część ścieżki.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Warto zapamiętać o implementowaniu GetChildName

Implementacja [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoda podzielić ścieżka leksykalnie separatora ścieżki. Jeśli podana ścieżka nie zawiera żadnych separatorów ścieżek, metoda powinna zwrócić ścieżki w niezmienionej postaci.

> [!IMPORTANT]
> Ścieżka jest podana w wywołaniu tej metody może zawierać znaków, które są niedozwolone w przestrzeni nazw dostawcy. Te znaki są najczęściej używane na potrzeby rozszerzenia symboli wieloznacznych ani Dopasowywanie wyrażeń regularnych, a implementacja tej metody nie należy usuwać je.

## <a name="determining-if-an-item-is-a-container"></a>Określanie, czy element kontenera

Dostawca nawigacji można zaimplementować [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metodę, aby określić, jeśli określona ścieżka wskazuje kontenera. Zwraca wartość true, jeśli ścieżka reprezentuje kontener, a wartość false w przeciwnym razie. Użytkownik musi tę metodę, aby móc używać `Test-Path` polecenia cmdlet dla podanej ścieżki.

Poniższy kod przedstawia [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementacji dostawcy nawigacji naszej próbki. Ta metoda sprawdza, czy podana ścieżka jest prawidłowa i czy tabela istnieje i zwraca wartość true, jeśli ścieżka wskazuje kontener.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Warto zapamiętać o implementowaniu IsItemContainer

Twój dostawca nawigacji klasę .NET może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W tym przypadku stosowania [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) musi zapewnić, że ścieżka przekazywane spełnia wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) właściwości.

## <a name="moving-an-item"></a>Przenoszenie elementu

Wspierających `Move-Item` polecenia cmdlet, Twój dostawca nawigacji implementuje [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metody. Ta metoda powoduje przeniesienie elementu określonego przez `path` parametr do kontenera w ścieżce podane w `destination` parametru.

Nie powoduje zastąpienia dostawcy nawigacji próbki [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metody. Poniżej znajduje się w implementacji domyślnej.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Warto zapamiętać o implementowaniu MoveItem

Twój dostawca nawigacji klasę .NET może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W tym przypadku stosowania [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) należy upewnić się, że ścieżka przekazywane spełnia wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, **CmdletProvider.Exclude** właściwości.

Domyślnie przesłonięcia tej metody nie należy przenosić obiekty za pośrednictwem istniejących obiektów chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Na przykład dostawcy filesystem nie skopiuje c:\temp\abc.txt przez istniejący plik c:\bar.txt chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Jeśli ścieżka określona w `destination` parametru istnieje i jest kontenerem, [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość nie jest wymagane. W tym przypadku [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) należy przenieść element wskazywany przez `path` parametru do kontenera wskazywanym przez `destination` parametr jako element podrzędny.

Implementacja [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana, aby potwierdzić wykonanie operacji, podczas wprowadzania zmian do stanu systemu, na przykład usuwania plików. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji w Określanie, co powinno być wyświetlane użytkownikowi.

Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła wiadomość do użytkownika o zezwolenie opinii powiedzieć, jeśli operacja powinna być kontynuowana. Twój dostawca powinien wywoływać [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) jako dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Move element

Czasami `Move-Item` polecenie cmdlet wymaga dodatkowych parametrów, które znajdują się dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, dostawca nawigacji musi implementować [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metodę, aby uzyskać wartości wymaganego parametru z elementu w wskazanej ścieżki i zwrócenie obiektu, który ma właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu.

Ten dostawca nawigacji nie implementuje tej metody. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalizowanie ścieżki względnej

Implementuje dostawcę usługi nawigacji [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metody do normalizacji w pełni kwalifikowaną ścieżkę czcionką `path` parametru jako względem ścieżka określona przez plik `basePath` parametru. Metoda zwraca reprezentację ciągu ścieżka znormalizowana. Zapisuje komunikat o błędzie, jeśli `path` parametr określa nieistniejącą ścieżkę.

Dostawcy nawigacji próbki nie zastępuje tę metodę. Poniżej znajduje się w implementacji domyślnej.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Warto zapamiętać o implementowaniu NormalizeRelativePath

Implementacja [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) powinny być analizowane `path` parametru, ale nie trzeba używać wyłącznie syntaktycznych analizy. Zachęcamy do projektowania, że tę metodę, aby użyć ścieżki do wyszukiwania informacji o ścieżce w magazynie danych i utworzyć ścieżkę, która odpowiada małych i wielkich liter, a standardowe składnia ścieżki.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Istnieje możliwość dla dostawcy dodać członków do istniejących obiektów lub zdefiniuj nowe obiekty. Aby uzyskać więcej informacji, zobacz[rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Tworzenie dostawcy środowiska Windows PowerShell

Aby uzyskać więcej informacji, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testowanie dostawcy środowiska Windows PowerShell

Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia, łącznie z poleceniami cmdlet udostępnianych przez tworzenie wartości pochodnych. W tym przykładzie przetestuje dostawcy nawigacji próbki.

1. Uruchamianie nowej powłoki i użyj `Set-Location` polecenia cmdlet, aby ustawić ścieżkę, aby wskazać bazy danych programu Access.

   ```powershell
   Set-Location mydb:
   ```

2. Teraz uruchom `Get-Childitem` polecenie cmdlet do pobierania listy elementów bazy danych, które są dostępne tabele bazy danych. Dla każdej tabeli to polecenie cmdlet pobiera liczbę wierszy tabeli.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Użyj `Set-Location` polecenie cmdlet ponownie, aby ustawić lokalizację tabeli danych pracowników.

   ```powershell
   Set-Location Employees
   ```

4. Teraz Użyjmy `Get-Location` polecenia cmdlet, aby pobrać ścieżkę do tabel pracownikami.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Teraz za pomocą `Get-Childitem` w potoku do polecenia cmdlet `Format-Table` polecenia cmdlet. Ten zbiór poleceń cmdlet umożliwia pobranie elementów dla tabeli danych pracowników, które są wiersze tabeli. Są one formatowane zgodnie z określonym `Format-Table` polecenia cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Możesz teraz uruchomić `Get-Item` polecenie cmdlet do pobierania elementów dla wiersza 0 z tabelą danych pracowników.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Użyj `Get-Item` polecenie cmdlet ponownie, aby pobrać dane pracowników dla elementów w wierszu 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy środowiska Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Dostawca usługi Windows PowerShell projektu](./designing-your-windows-powershell-provider.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementowanie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)