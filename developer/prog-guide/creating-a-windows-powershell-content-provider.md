---
title: Tworzenie dostawcy zawartość programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 5e35d2fdfa4c6bd70c1b69ca1f357ee8d8ebcdc4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429979"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Tworzenie dostawcy zawartości programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi manipulować zawartością elementów w magazynie danych. W konsekwencji dostawcę, który będzie obsługiwał zawartość elementów jest określane jako dostawcy zawartości programu Windows PowerShell.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider06.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

Poniższa lista zawiera sekcje, w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem dostawcy zawartości programu Windows PowerShell, należy przeczytać następujące sekcje w kolejności, w jakiej się pojawiają. Jednak jeśli znasz pisanie dostawcy zawartości programu Windows PowerShell, przejdź bezpośrednio do potrzebnych informacji.

- [Definiowanie klasy dostawcy Windows zawartość programu PowerShell](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definiowanie podstawowe funkcje](#Define-Functionality-of-Base-Class)

- [Implementowanie czytnik zawartości](#Implementing-a-Content-Reader)

- [Wdrażanie zapisywania zawartości](#Implementing-a-Content-Writer)

- [Trwa pobieranie czytnika zawartości](#Retrieving-the-Content-Reader)

- [Dołączanie parametrów dynamicznych do `Get-Content` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Trwa pobieranie zawartości składnika zapisywania](#Retrieving-the-Content-Writer)

- [Dołączanie parametrów dynamicznych do Add_Content i `Set-Content` poleceń cmdlet](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Czyszczenie zawartości](#Clearing-Content)

- [Dołączanie parametrów dynamicznych do `Clear-Content` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Przykładowy kod](#Code-Sample)

- [Definiowanie typów obiektów i formatowanie]()

- [Tworzenie dostawcy środowiska Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Testowanie dostawcy środowiska Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definiowanie klasy dostawcy Windows zawartość programu PowerShell

Dostawcy zawartości programu Windows PowerShell, należy utworzyć klasę .NET, która obsługuje [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu. Oto definicji klasy dla dostawcy elementu opisane w tej sekcji.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Należy zauważyć, że w tej definicji klasy [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut zawiera dwa parametry. Pierwszy parametr określa przyjazną dla użytkownika nazwę dostawcy, który jest używany przez program Windows PowerShell. Drugi parametr określa specyficzne możliwości programu Windows PowerShell, które dostawca udostępnia do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Dla tego dostawcy istnieją nie dodano programu Windows PowerShell konkretne funkcje.

## <a name="define-functionality-of-base-class"></a>Definiowanie funkcji klasy podstawowej

Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasa pochodzi od innych klas, które podano funkcje innego dostawcy. Dostawcy zawartości programu Windows PowerShell, dlatego zwykle definiuje wszystkie funkcje udostępniane przez te klasy.

Aby uzyskać więcej informacji o sposobie implementacji funkcji dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md). Jednak większość dostawców, w tym dostawcy opisane w tym miejscu, można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.

Aby uzyskać dostęp do magazynu danych, dostawca musi implementować metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Do modyfikowania elementów magazynu danych, takich jak wprowadzenie, ustawienia i czyszczenie elementów, dostawca musi implementować metod dostarczonych przez [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [tworzenia dostawcy usługi Windows PowerShell elementu](./creating-a-windows-powershell-item-provider.md).

Aby pracować w magazynach danych wielowarstwową, dostawca musi implementować metod dostarczonych przez [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Aby zapewnić obsługę poleceń cykliczne, zagnieżdżone kontenery i ścieżki względne, dostawca musi implementować [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy bazowej. Oprócz tego dostawcy zawartości programu Windows PowerShell można dołącza [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) współpracować w celu [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy bazowej, a w związku z tym musi implementować metod dostarczonych przez tę klasę. Aby uzyskać więcej informacji, zobacz temat implementowania tych metod, zobacz [implementowanie dostawcy programu PowerShell Windows nawigacji](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementowanie czytnik zawartości

Na odczyt zawartości z elementu, dostawca musi implementuje klasy czytnika zawartości, która pochodzi od klasy [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). Czytnik zawartości dla tego dostawcy umożliwia dostęp do zawartości wiersza w tabeli danych. Definiuje klasy czytnika zawartości **odczytu** metodę, która pobiera dane z wskazanego wiersza i zwraca listę reprezentujący reprezentatywną próbę danych, **Seek** metodę, która przenosi czytnik zawartości  **Zamknij** metodę, która powoduje zamknięcie czytnik zawartości i **Dispose** metody.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Wdrażanie zapisywania zawartości

Można zapisać zawartości dla elementu, dostawca musi implementować zawartości pochodną klasę edytora [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Definiuje klasę edytora zawartości **zapisu** metodę, która zapisuje zawartość określony wiersz **Seek** metodę, która przenosi składnika zapisywania programu zawartości **Zamknij** metodę, która zostanie zamknięty Składnik zapisywania zawartości, a **Dispose** metody.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Trwa pobieranie czytnika zawartości

Można pobrać zawartości z elementu, dostawca musi implementować [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) do obsługi `Get-Content` polecenia cmdlet. Ta metoda zwraca czytnik zawartości dla elementu znajduje się w określonej ścieżce. Obiekt czytnika można następnie otworzyć do odczytu zawartości.

Oto implementacja [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) dla tej metody dla tego dostawcy.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Warto zapamiętać o implementowaniu GetContentReader

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Podczas definiowania klasy dostawcy, dostawcy zawartości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metody należy upewnić się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać czytnika obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Get zawartość

`Get-Content` Polecenia cmdlet mogą wymagać dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy zawartości w programie Windows PowerShell [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell używa zwracany obiekt, aby dodać parametry do polecenia cmdlet.

Ten dostawca kontenera programu Windows PowerShell nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Trwa pobieranie zawartości składnika zapisywania

Aby zapisać zawartości dla elementu, dostawca musi implementować [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) do obsługi `Set-Content` i `Add-Content` polecenia cmdlet. Ta metoda zwraca zawartości modułu zapisującego dla elementu znajduje się w określonej ścieżce.

Oto implementacja [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) dla tej metody.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Warto zapamiętać o implementowaniu GetContentWriter

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Podczas definiowania klasy dostawcy, dostawcy zawartości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metody należy upewnić się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać Edytor obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Dołączanie parametrów dynamicznych do dodawania zawartości i zawartości zestawu poleceń cmdlet

`Add-Content` i `Set-Content` polecenia cmdlet mogą wymagać dodatkowych parametrów dynamicznych, które są dodawane do środowiska uruchomieniowego. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy zawartości w programie Windows PowerShell [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metody, aby obsłużyć te Parametry. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell używa zwrócony obiekt można dodać parametry do polecenia cmdlet.

Ten dostawca kontenera programu Windows PowerShell nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Czyszczenie zawartości

Twoja implementacja dostawcy zawartości [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metoda wspierających `Clear-Content` polecenia cmdlet. Ta metoda usuwa zawartość elementu w określonej ścieżce, ale pozostawia element bez zmian.

Oto implementacja [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metody dla tego dostawcy.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Warto zapamiętać o implementowaniu ClearContent

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Podczas definiowania klasy dostawcy, dostawcy zawartości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metody należy upewnić się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie należy wyczyścić zawartość obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

- Implementacja [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana do wykonywania operacji upewnij się, gdy dokonywane są zmiany w magazynie danych, takich jak czyszczenie zawartości. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoda wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, obsługa wszelkie ustawienia wiersza polecenia lub preferencji zmienne w określaniu, co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła wiadomość do użytkownika o zezwolenie opinię, aby sprawdzić, jeśli operacja powinna być kontynuowana. Wywołanie [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) zezwala na dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Wyczyść zawartość

`Clear-Content` Polecenia cmdlet mogą wymagać dodatkowych parametrów dynamicznych, które są dodawane w czasie wykonywania. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy zawartości w programie Windows PowerShell [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metody, aby obsłużyć te Parametry. Ta metoda pobiera parametry dla elementu w wskazanej ścieżce. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell używa zwracany obiekt, aby dodać parametry do polecenia cmdlet.

Ten dostawca kontenera programu Windows PowerShell nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Podczas zapisywania dostawcy, może być konieczne dodawać członków do istniejących obiektów lub zdefiniuj nowe obiekty. Po zakończeniu tej operacji należy utworzyć plik typów, można użyć programu Windows PowerShell, aby zidentyfikować członków obiektu i plik formatu, który definiuje sposób wyświetlania obiektu. Aby uzyskać więcej informacji, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Tworzenie dostawcy programu Windows PowerShell

Zobacz [sposobu rejestrowania poleceń cmdlet, dostawców i hostowanie aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testowanie dostawcy programu Windows PowerShell

Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia. Na przykład przetestować dostawcy zawartości w próbce.

Użyj `Get-Content` polecenie cmdlet do pobierania zawartości określonego elementu w tabeli bazy danych w ścieżce określonej przez `Path` parametru. `ReadCount` Parametr określa liczbę elementów do zdefiniowanych czytnik zawartości do odczytu (wartość domyślna: 1). Za pomocą następującego polecenia polecenie cmdlet pobiera dwa wiersze (elementy) z tabeli i wyświetla jego zawartość. Należy zauważyć, że następujące przykładowe dane wyjściowe korzysta z fikcyjnych dostępu do bazy danych.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy środowiska Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Dostawca usługi Windows PowerShell projektu](./designing-your-windows-powershell-provider.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementowanie dostawcy nawigacji Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)
