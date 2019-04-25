---
title: Tworzenie dostawcy programu PowerShell elementu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081873"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Tworzenie dostawcy elementów programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy środowiska Windows PowerShell, który można manipulować danymi w magazynie danych. W tym temacie są określane jako "elementy" dane magazyn elementów danych w magazynie. W konsekwencji dostawcę, który można manipulować danymi w magazynie jest określany jako dostawca elementu programu Windows PowerShell.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider03.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

Dostawcy elementu programu Windows PowerShell, które są opisane w tym temacie pobiera elementy danych z bazy danych programu Access. W tym przypadku "item" jest tabeli w bazie danych programu Access albo wiersz w tabeli.

Poniższa lista zawiera sekcje, w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem dostawcy elementu programu Windows PowerShell, należy przeczytać następujące sekcje w kolejności, w jakiej się pojawiają. Jednak jeśli znasz pisanie dostawcy elementu programu Windows PowerShell, przejść bezpośrednio do potrzebnych informacji:

- [Definiowanie klasy dostawcy programu PowerShell elementu Windows](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definiowanie podstawowe funkcje](#Defining-Base-Functionality)

- [Sprawdzanie poprawności ścieżki](#Checking-for-Path-Validity)

- [Określanie, czy element istnieje](#Determining-if-an-Item-Exists)

- [Dołączanie parametrów dynamicznych do `Test-Path` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Trwa pobieranie elementu](#Retrieving-an-Item)

- [Dołączanie parametrów dynamicznych do `Get-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Ustawienie elementu](#Setting-an-Item)

- [Dołączanie parametrów dynamicznych do `Set-Item` polecenia Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Zaznaczenie elementu](#Clearing-an-Item)

- [Dołączanie parametrów dynamicznych do polecenia cmdlet wyczyść element](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Wykonując akcję domyślną dla elementu](#Performing-a-Default-Action-for-an-Item)

- [Trwa pobieranie parametrów dynamicznych do InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementacja klasy i metody pomocnicze](#Implementing-Helper-Methods-and-Classes)

- [Przykładowy kod](#Code-Sample)

- [Definiowanie typów obiektów i formatowanie](#Defining-Object-Types-and-Formatting)

- [Tworzenie dostawcy programu Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Testowanie dostawcy programu Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definiowanie klasy dostawcy programu PowerShell elementu Windows

Dostawca elementu programu Windows PowerShell, należy zdefiniować klasy .NET, która pochodzi od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy bazowej. Poniżej znajduje się w definicji klasy dla dostawcy elementu opisane w tej sekcji.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Należy zauważyć, że w tej definicji klasy [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut zawiera dwa parametry. Pierwszy parametr określa przyjazną dla użytkownika nazwę dostawcy, który jest używany przez program Windows PowerShell. Drugi parametr określa specyficzne możliwości programu Windows PowerShell, które dostawca udostępnia do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Dla tego dostawcy istnieją nie dodano programu Windows PowerShell konkretne funkcje.

## <a name="defining-base-functionality"></a>Definiowanie podstawowe funkcje

Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa pochodzi od innych klas, które podano różne funkcje dostawcy. Element dostawcy środowiska Windows PowerShell, w związku z tym, należy zdefiniować wszystkie funkcje udostępniane przez te klasy.

Aby uzyskać więcej informacji o sposobie implementacji funkcji dodawania informacji specyficznych dla sesji inicjowania i zwalnianie zasobów używanych przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md). Jednak większość dostawców, w tym dostawcy opisane w tym miejscu, można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.

Zanim dostawcę elementów programu Windows PowerShell można manipulować elementów w magazynie, musi on implementować metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej na dostęp do magazynu danych. Aby uzyskać więcej informacji na temat implementowania tej klasy, zobacz [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Sprawdzanie poprawności ścieżki

Podczas wyszukiwania elementu danych, środowisko wykonawcze programu Windows PowerShell przedstawia ścieżki programu Windows PowerShell do dostawcy, zgodnie z definicją w sekcji "PSPath pojęcia" [sposób działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Dostawcy elementu programu Windows PowerShell należy sprawdzić ważność syntaktyczna i semantyczna dowolną ścieżkę przekazany przez zaimplementowanie [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metody. Ta metoda zwraca `true` Jeśli ścieżka jest prawidłowa, i `false` inaczej. Należy pamiętać, że implementacja tej metody powinna nie sprawdzał, czy elementu w ścieżce, ale tylko wtedy, czy ścieżka jest składniowo i semantycznie prawidłowe.

Oto implementacja [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metody dla tego dostawcy. Należy pamiętać, że ta implementacja wywołuje metodę pomocnika NormalizePath można przekonwertować wszystkie separatorach w ścieżce jednolitego niż ten, który.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Określanie, czy element istnieje

Po zweryfikowaniu ścieżki, w czasie wykonywania programu Windows PowerShell należy określić, czy element danych istnieje w tej ścieżce. Aby zapewnić obsługę tego typu zapytania, implementuje dostawcę elementów programu Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metody. Ta metoda zwraca `true` element znajduje się w określonej ścieżce i `false` (opcja domyślna) w przeciwnym razie.

Oto implementacja [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metody dla tego dostawcy. Należy pamiętać, że ta metoda wywołuje metody pomocnika PathIsDrive ChunkPath i Metoda GetTable i używa dostawcy zdefiniowany obiekt DatabaseTableInfo.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Warto zapamiętać o implementowaniu ItemExists

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Podczas definiowania klasy dostawcy, dostawca elementu programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metody należy upewnić się, że ścieżka przekazywany do metody spełnia wymagania określony element capabilities. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Implementacja tej metody powinna obsługiwać dowolnej formie dostępu do elementu, że element jest widoczny dla użytkownika. Na przykład, jeśli użytkownik ma dostęp do zapisu do pliku za pośrednictwem dostawcy systemu plików (dostarczonych przez program Windows PowerShell), ale nie dostęp do odczytu, plik nadal istnieje i [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) zwraca `true`. Wdrożenie może wymagać sprawdzenia elementu nadrzędnego, podrzędnego elementu mogą być wyliczane.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Test-Path

Czasami `Test-Path` polecenia cmdlet, który wywołuje [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne programu Windows PowerShell, element dostawca musi implementować [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Test-Path` polecenia cmdlet.

Ten dostawca elementu programu Windows PowerShell nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Trwa pobieranie elementu

Aby pobrać element, musisz przesłonić dostawcę elementów programu Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metody w celu obsługi wywołania z `Get-Item` polecenia cmdlet. Ta metoda zapisuje przy użyciu elementu [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metody.

Oto implementacja [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metody dla tego dostawcy. Należy pamiętać, że ta metoda używa metody pomocnika Metoda GetTable i getrow — można pobrać elementów znajdujących się na kilka tabel w bazie danych programu Access albo wierszy w tabeli danych.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Warto zapamiętać o implementowaniu GetItem

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Podczas definiowania klasy dostawcy, dostawca elementu programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) należy upewnić się, że ścieżka przekazywany do metody spełnia te wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać obiekty, które zazwyczaj są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Na przykład [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodę sprawdzania dostawcy FileSystem [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwości przed próbuje wywołać [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) dla ukryte lub systemu plików.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Get-Item

Czasami `Get-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne programu Windows PowerShell, element dostawca musi implementować [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Get-Item` polecenia cmdlet.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Ustawienie elementu

Aby ustawić element, należy zastąpić dostawcę elementów programu Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody w celu obsługi wywołania z `Set-Item` polecenia cmdlet. Ta metoda ustawia wartość elementu w określonej ścieżce.

Ten dostawca nie udostępnia zastąpienie [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody. Jednakże Oto Domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Warto zapamiętać o implementowaniu SetItem

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Podczas definiowania klasy dostawcy, dostawca elementu programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) należy upewnić się, że ścieżka przekazywany do metody spełnia te wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody powinna nie ustawiaj lub zapisania obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być przesyłane do [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodę, jeśli ścieżka reprezentuje element ukryty i [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

- Implementacja [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana, aby potwierdzić wykonanie operacji w przypadku zmian magazynu danych, na przykład usuwania plików. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoda wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji w określaniu, co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła wiadomość do użytkownika o zezwolenie opinię, aby sprawdzić, jeśli operacja powinna być kontynuowana. Wywołanie [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) zezwala na dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Trwa pobieranie parametrów dynamicznych do SetItem

Czasami `Set-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne programu Windows PowerShell, element dostawca musi implementować [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Set-Item` polecenia cmdlet.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Zaznaczenie elementu

Aby usunąć element, implementuje dostawcę elementów programu Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) metody w celu obsługi wywołania z `Clear-Item` polecenia cmdlet. Ta metoda usuwa element danych w określonej ścieżce.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Warto zapamiętać o implementowaniu ClearItem

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Podczas definiowania klasy dostawcy, dostawca elementu programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) należy upewnić się, że ścieżka przekazywany do metody spełnia te wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody powinna nie ustawiaj lub zapisania obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być przesyłane do [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodę, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

- Implementacja [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana, aby potwierdzić wykonanie operacji w przypadku zmian magazynu danych, na przykład usuwania plików. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoda wysyła nazwę zasobu, można zmienić z użytkownikiem w środowisku uruchomieniowym programu Windows PowerShell i obsługiwać wszystkie ustawienia wiersza polecenia lub preferencji zmienne w określaniu, co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła wiadomość do użytkownika o zezwolenie opinię, aby sprawdzić, jeśli operacja powinna być kontynuowana. Wywołanie [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) zezwala na dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Pobieranie parametrów dynamicznych dla ClearItem

Czasami `Clear-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne programu Windows PowerShell, element dostawca musi implementować [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Clear-Item` polecenia cmdlet.

Ten element dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Wykonując akcję domyślną dla elementu

Dostawca elementów programu Windows PowerShell można zaimplementować [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metody w celu obsługi wywołania z `Invoke-Item` polecenia cmdlet, które umożliwia dostawcy programu do Wykonaj akcję domyślną dla elementu w określonej ścieżce. Na przykład dostawcy systemu plików może użyć tej metody do wywołania ShellExecute dla określonego elementu.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Warto zapamiętać o implementowaniu InvokeDefaultAction

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Podczas definiowania klasy dostawcy, dostawca elementu programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) należy upewnić się, że ścieżka przekazywany do metody spełnia te wymagania. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody powinna nie ustawiaj lub zapisania obiektów ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być przesyłane do [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodę, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Pobieranie parametrów dynamicznych dla InvokeDefaultAction

Czasami `Invoke-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne programu Windows PowerShell, element dostawca musi implementować [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell używa zwrócony obiekt do dodania parametrów dynamicznych do `Invoke-Item` polecenia cmdlet.

Ten element dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementacja klasy i metody pomocnicze

Ten dostawca elementu implementuje kilka metod pomocniczych i klas, które są używane przez publiczny zastępują metody zdefiniowane przez środowisko Windows PowerShell. Kod dla tych metod pomocniczych i klas są wyświetlane w [przykładowy kod](#Code-Sample) sekcji.

### <a name="normalizepath-method"></a>Metoda NormalizePath

Ten dostawca elementu implementuje NormalizePath metody pomocnika, aby upewnić się, że ścieżka ma spójny format. Format określony używa ukośnik odwrotny (\\) jako separatora.

### <a name="pathisdrive-method"></a>Metoda PathIsDrive

Ten dostawca elementu implementuje PathIsDrive metody pomocnika do ustalenia, czy podana ścieżka jest faktycznie nazwę dysku.

### <a name="chunkpath-method"></a>Metoda ChunkPath

Ten dostawca elementu implementuje ChunkPath metody pomocnika, która dzieli się określonej ścieżki, aby dostawca może zidentyfikować poszczególne elementy. Zwraca czy tablica składa się z elementów ścieżki.

### <a name="gettable-method"></a>GetTable — metoda

Ten dostawca elementu implementuje metodę pomocnika GetTables, która zwraca obiekt DatabaseTableInfo, który reprezentuje informacji o tabeli określonej w wywołaniu.

### <a name="getrow-method"></a>Getrow — metoda

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metoda tego dostawcy elementu wywołuje metodę pomocnika GetRows. Ta metoda pomocnika pobiera obiekt DatabaseRowInfo, który reprezentuje informacje o określony wiersz w tabeli.

### <a name="databasetableinfo-class"></a>Klasa DatabaseTableInfo

Ten dostawca element definiuje klasa DatabaseTableInfo, która reprezentuje zbiór informacji w tabeli danych w bazie danych. Ta klasa jest podobna do [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) klasy.

Dostawca elementu przykładowy definiuje metodę DatabaseTableInfo.GetTables, która zwraca kolekcję obiektów informacji tabeli Definiowanie tabel w bazie danych. Ta metoda obejmuje bloku try/catch, aby upewnić się, że wszelkie błędy bazy danych jest wyświetlany jako wiersz z wpisami, zerowego.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo Class

Ten dostawca element definiuje klasa pomocnika DatabaseRowInfo, która reprezentuje wiersz w tabeli bazy danych. Ta klasa jest podobna do [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) klasy.

Dostawca przykładowy definiuje metodę DatabaseRowInfo.GetRows zwraca kolekcję obiektów informacje wiersza dla określonej tabeli. Ta metoda obejmuje bloku try/catch do przechwytywania wyjątków. Brak informacji o wierszu spowoduje błędy.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Podczas zapisywania dostawcy, może być konieczne dodawać członków do istniejących obiektów lub zdefiniuj nowe obiekty. Po zakończeniu tworzenia pliku typów, można użyć programu Windows PowerShell, aby zidentyfikować członków obiektu i plik formatu, który definiuje sposób wyświetlania obiektu. Aby uzyskać więcej informacji na temat, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Tworzenie dostawcy środowiska Windows PowerShell

Zobacz [sposobu rejestrowania poleceń cmdlet, dostawców i hostowanie aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testowanie dostawcy środowiska Windows PowerShell

Gdy tego dostawcę elementów programu Windows PowerShell zostanie zarejestrowane przy użyciu programu Windows PowerShell, można tylko podstawowy test i dysków funkcji dostawcy. Aby przetestować manipulowania elementów, należy także zaimplementować kontenera funkcji opisanych w [implementowanie dostawcy programu PowerShell Windows Container](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Tworzenie programu Windows PowerShell dostawców](./how-to-create-a-windows-powershell-provider.md)

[Projektowanie dostawcy usługi Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak działa program Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Tworzenie dostawcy dysk programu Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)