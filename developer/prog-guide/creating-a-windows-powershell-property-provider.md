---
title: Tworzenie dostawcy właściwości programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055159"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Tworzenie dostawcy właściwości programu Windows PowerShell

W tym temacie opisano, jak utworzyć dostawcę, który umożliwia użytkownikowi do manipulowania właściwości elementów w magazynie danych. W konsekwencji ten typ dostawcy jest określone jako dostawca właściwości programu Windows PowerShell. Na przykład dostawca rejestru udostępniane przez wartości klucza rejestru programu Windows PowerShell obsługuje jako właściwości elementu klucza rejestru. Należy dodać ten typ dostawcy [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfejs do implementacji klasy .NET.

> [!NOTE]
> Program Windows PowerShell zawiera plik szablonu używanego do tworzenia dostawcy środowiska Windows PowerShell. Plik TemplateProvider.cs jest dostępny na Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Szablon pobrany jest dostępna w  **\<przykłady programu PowerShell >** katalogu. Należy utworzyć kopię tego pliku i kopia jest używana do tworzenia nowego dostawcę programu Windows PowerShell żadnej funkcji, która nie ma potrzeby usuwania.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Metody właściwości dostawcy należy zapisać wszystkie obiekty za pomocą [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) metody.

Poniższa lista zawiera sekcje, w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem Dostawca właściwości programu Windows PowerShell, przeczytaj te informacje w kolejności, która wygląda na to. Jednak jeśli i dopiero zaczynasz pisanie dostawcy właściwości programu Windows PowerShell, przejdź bezpośrednio do potrzebnych informacji.

- [Definiowanie dostawcy programu Windows PowerShell](#Defining-the-Windows-PowerShell-provider)

- [Definiowanie podstawowe funkcje](#Defining-Base-Functionality)

- [Pobieranie właściwości](#Retrieving-Properties)

- [Dołączanie parametrów dynamicznych do `Get-ItemProperty` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Ustawianie właściwości](#Setting-Properties)

- [Dołączanie parametrów dynamicznych do `Set-ItemProperty` polecenia Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Czyszczenie właściwości](#Clearing-Properties)

- [Dołączanie parametrów dynamicznych do `Clear-ItemProperty` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Tworzenie dostawcy programu Windows PowerShell](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Definiowanie dostawcy programu Windows PowerShell

Dostawca właściwości, należy utworzyć klasę .NET, która obsługuje [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfejsu. Oto domyślne deklarację klasy z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definiowanie podstawowe funkcje

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfejs może zostać dołączony do dowolnego dostawcy klas bazowych, z wyjątkiem produktów [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy. Dodaj podstawowe funkcje, która jest wymagana przez klasę bazową, którego używasz. Aby uzyskać więcej informacji na temat klas bazowych, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Pobieranie właściwości

Można pobrać właściwości, należy zaimplementować dostawcę [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metody w celu obsługi wywołania z `Get-ItemProperty` polecenia cmdlet. Ta metoda pobiera właściwości elementu znajduje się w określonej ścieżce wewnętrzna dostawcy (w pełni kwalifikowana).

`providerSpecificPickList` Parametr wskazuje właściwości, które można pobrać. Jeśli ten parametr jest `null` lub jest pusta, metoda powinna pobrać wszystkich właściwości. Ponadto [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) zapisuje wystąpienie [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiekt, który reprezentuje zbiór właściwości pobrane właściwości. Metoda powinna zwrócić nothing.

Zalecane jest wykonanie [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) obsługuje rozszerzenia symboli wieloznacznych w nazwach właściwości dla każdego elementu na liście wyboru. Aby to zrobić, należy użyć [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) klasy do realizacji dopasowania do wzorca symboli wieloznacznych.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Warto zapamiętać o implementowaniu GetProperty

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Podczas definiowania klasy dostawcy, Dostawca właściwości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać czytnika obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Get-zmieniona właściwość elementu

`Get-ItemProperty` Polecenia cmdlet mogą wymagać dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, Dostawca właściwości programu Windows PowerShell musi implementować [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metody. `path` Parametr wskazuje, w pełni kwalifikowana ścieżka wewnętrzna dostawcy, podczas gdy `providerSpecificPickList` parametr określa właściwości specyficzne dla dostawcy, wprowadzona w wierszu polecenia. Ten parametr może być `null` lub jest pusty, jeśli właściwości są przekazywane w potoku do polecenia cmdlet. W takim przypadku ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell używa zwracany obiekt, aby dodać parametry do polecenia cmdlet.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Ustawianie właściwości

Aby ustawić właściwości, musi implementować właściwość dostawcy środowiska Windows PowerShell [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metody w celu obsługi wywołania z `Set-ItemProperty` polecenia cmdlet. Ta metoda określa jedną lub więcej właściwości elementu w określonej ścieżce i zastępuje podanej właściwości zgodnie z potrzebami. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) zapisuje również dane wystąpienia [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiekt, który reprezentuje pakiet właściwości zaktualizowane właściwości.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Warto zapamiętać o implementowaniu Set-zmieniona właściwość elementu

Następujące warunki mogą dotyczyć wykonania [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Podczas definiowania klasy dostawcy, Dostawca właściwości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metody należy upewnić się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać czytnika obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

- Implementacja [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana, aby potwierdzić wykonanie operacji, podczas wprowadzania zmian do stanu systemu, na przykład zmiana nazw plików. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, za pomocą środowiska uruchomieniowego programu Windows PowerShell i obsługa wszelkie ustawienia wiersza polecenia lub zmienne preferencji przy określaniu co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, jeśli można wprowadzić modyfikacje potencjalnie niebezpiecznych systemu, [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła komunikat z potwierdzeniem dla użytkownika, aby zezwolić na dodatkową opinię wskazać, czy operacja powinna być kontynuowana.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Trwa dołączanie dynamicznych parametrów polecenia cmdlet Set-zmieniona właściwość elementu

`Set-ItemProperty` Polecenia cmdlet mogą wymagać dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, Dostawca właściwości programu Windows PowerShell musi implementować [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metody. Ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. `null` Wartości mogą być zwracane w przypadku nie parametrów dynamicznych do dodania.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Czyszczenie właściwości

Aby wyczyścić właściwości, musi implementować właściwość dostawcy środowiska Windows PowerShell [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metody w celu obsługi wywołania z `Clear-ItemProperty` polecenia cmdlet. Ta metoda określa jedną lub więcej właściwości dla elementu znajduje się w określonej ścieżce.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Jest, aby pamiętać o implementowaniu ClearProperty

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Podczas definiowania klasy dostawcy, Dostawca właściwości programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać czytnika obiektów, które są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Błąd powinny być zapisywane, jeśli ścieżka reprezentuje element, który jest ukryty przez użytkownika i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ustawiono `false`.

- Implementacja [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana do wykonywania operacji upewnij się, zanim zmian stanu systemu, takich jak czyszczenie zawartości. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji w Określanie, co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, jeśli można wprowadzić modyfikacje potencjalnie niebezpiecznych systemu, [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła komunikat z potwierdzeniem dla użytkownika, aby zezwolić na dodatkową opinię wskazać, potencjalnie niebezpiecznych operacji powinno być kontynuowane.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Clear-zmieniona właściwość elementu

`Clear-ItemProperty` Polecenia cmdlet mogą wymagać dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, Dostawca właściwości programu Windows PowerShell musi implementować [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metody. Ta metoda zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. `null` Wartości mogą być zwracane w przypadku nie parametrów dynamicznych do dodania.

W tym miejscu jest domyślna Implementacja klasy [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) z pliku TemplateProvider.cs dostarczane przez środowisko Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Tworzenie dostawcy środowiska Windows PowerShell

Zobacz [sposobu rejestrowania poleceń cmdlet, dostawców i hostowanie aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Zobacz też

[Dostawca programu Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Dostawca usługi Windows PowerShell projektu](./designing-your-windows-powershell-provider.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)