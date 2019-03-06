---
title: Projektowanie dostawcy programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429945"
---
# <a name="designing-your-windows-powershell-provider"></a>Projektowanie dostawcy programu Windows PowerShell

Jeśli Twój produkt lub Konfiguracja udostępnia zestaw przechowywanych danych, takich jak bazy danych, który użytkownik będzie chciał Przejdź lub Przeglądaj, powinny implementować dostawcy środowiska Windows PowerShell. Ponadto jeśli produktu zawiera kontener, nawet jeśli nie jest wielopoziomowej kontenera, dobrym pomysłem do implementowania dostawcy środowiska Windows PowerShell. Na przykład można wdrożyć dostawcy kontenera programu Windows PowerShell, jeśli zlecenia polecenia cmdlet kopii, przenoszenie, zmiana nazwy, nowe lub usuń ma sens jako operacja na danych produktu lub konfiguracji.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell ścieżki identyfikacji dostawcy

Środowisko wykonawcze programu Windows PowerShell używa programu Windows PowerShell ścieżek dostępu do odpowiedniego dostawcy środowiska Windows PowerShell. Gdy polecenie cmdlet Określa jedno z tych ścieżek, środowisko uruchomieniowe wie, który dostawca za pomocą uzyskać dostępu do magazynu danych. Te ścieżki obejmują kwalifikowana dysku ścieżki, kwalifikowana dostawcy ścieżki, ścieżki dostawcy bezpośrednio i wewnętrzny dostawcę ścieżek. Każdy dostawca programu Windows PowerShell musi obsługiwać co najmniej jedną z tych ścieżek.

Aby uzyskać więcej informacji na temat ścieżek programu Windows PowerShell zobacz sposób działania programu Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definiowanie ścieżki kwalifikowana dysku

Aby zezwolić użytkownikowi na dostęp do danych znajdujących się na dysku fizycznego, Twój dostawca programu Windows PowerShell musi obsługiwać ścieżką kwalifikowana dysku. Ta ścieżka zaczyna się od nazwy dysku z dwukropkiem (:), na przykład mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definiowanie ścieżki kwalifikowana dostawcy

Aby zezwolić na inicjowanie i uninitialize dostawcy środowiska uruchomieniowego programu Windows PowerShell, Twój dostawca programu Windows PowerShell musi obsługiwać ścieżką kwalifikowana przez dostawcę. Na przykład system plików::\\\uncshare\abc\bar jest ścieżką kwalifikowana dostawcy dla dostawcy filesystem dostarczony przez środowisko Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definiowanie ścieżki bezpośrednio dostawcy

Aby zezwolić na zdalny dostęp do dostawcy programu Windows PowerShell, jego powinien obsługiwać ścieżki dostawcy bezpośrednio przekazać bezpośrednio do dostawcy programu Windows PowerShell dla bieżącej lokalizacji. Na przykład, można użyć dostawcy programu Windows PowerShell rejestru \\\server\regkeypath jako ścieżka dostawcy bezpośrednio.

### <a name="defining-a-provider-internal-path"></a>Definiowanie ścieżki wewnętrzna dostawcy

Aby zezwolić na dostęp do danych za pomocą interfejsów programowania aplikacji (API) — Windows PowerShell polecenia cmdlet dostawcy, Twój dostawca programu Windows PowerShell powinien obsługiwać wewnętrzna dostawcy ścieżki. Ta ścieżka jest oznaczany po "::" w ścieżce kwalifikowana przez dostawcę. Na przykład ścieżka wewnętrzna dostawcy dla dostawcy programu Windows PowerShell system plików jest \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Zmiana przechowywanych danych

Podczas nadpisywania metod, które modyfikują źródłowy magazyn danych, zawsze wywołuj [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metody z najbardziej aktualną wersję elementu zmienione przez to Metoda. Infrastruktury dostawcy określa, czy obiekt elementu ma być przekazywane do potoku, np. kiedy użytkownik określa parametru - PassThru. W przypadku pobierania elementu najbardziej aktualne kosztownych operacji (performance-wise), można sprawdzić właściwość Context.PassThru, aby określić, jeśli rzeczywiście należy napisać wynikowy element.

## <a name="choose-a-base-class-for-your-provider"></a>Wybierz klasę bazową dla dostawcy

Program Windows PowerShell udostępnia wiele klas bazowych, używanych do implementowania dostawcy środowiska Windows PowerShell. Podczas projektowania dostawcę, należy wybrać klasę bazową, opisane w tej sekcji, która najbardziej nadaje się do wymagań.

Każda klasa bazowa dostawcy środowiska Windows PowerShell udostępnia zestaw poleceń cmdlet. W tej sekcji opisano poleceń cmdlet, ale nie opisano ich parametrów.

Przy użyciu stanu sesji, środowisko wykonawcze programu Windows PowerShell udostępnia kilka poleceń cmdlet lokalizacji niektórych dostawców środowiska Windows PowerShell, takie jak `Get-Location`, `Set-Location`, `Pop-Location`, i `Push-Location` polecenia cmdlet. Możesz użyć `Get-Help` polecenia cmdlet, aby uzyskać informacje na temat tych poleceń cmdlet lokalizacji.

### <a name="cmdletprovider-base-class"></a>Klasa bazowa CmdletProvider

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasa definiuje podstawowego dostawcy środowiska Windows PowerShell. Ta klasa obsługuje deklaracji dostawcy i udostępnia wiele właściwości i metod, które są dostępne dla wszystkich dostawców środowiska Windows PowerShell. Klasa jest wywoływany przez `Get-PSProvider` polecenia cmdlet, aby wyświetlić listę wszystkich dostępnych dostawców dla sesji. Wykonanie tego polecenia cmdlet zostanie dostarczony przez stanu sesji.

> [!NOTE]
> Dostawcy programu Windows PowerShell są dostępne dla wszystkich zakresów języka programu Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Klasa bazowa DriveCmdletProvider

[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa definiuje dostawcę dysk programu Windows PowerShell, który obsługuje operacje Dodawanie nowych dysków, usuwając istniejące dyski i inicjowanie dysków domyślne. Na przykład dostawcy FileSystem dostarczane przez środowisko Windows PowerShell inicjuje dysków dla wszystkich woluminów, które są instalowane, takie jak dyski twarde dysków CD/DVD czy dyski urządzenia.

Ta klasa jest pochodną [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy bazowej. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez tę klasę. Oprócz tych wymienionych `Get-PSDrive` polecenia cmdlet (udostępniany przez sesję stanu) jest powiązane polecenia cmdlet, które służy do pobierania dostępnych dysków.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`New-PSDrive`|Tworzy nowy dysk dla sesji, a następnie przesyła strumieniowo informacji o dysku.|
|`Remove-PSDrive`|Usuwa dysk z sesji.|

### <a name="itemcmdletprovider-base-class"></a>Klasa bazowa ItemCmdletProvider

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy definiuje dostawcę elementu programu Windows PowerShell, który wykonuje operacje dla poszczególnych elementów w magazynie danych, a nie przyjmuje żadnych kontenerów lub możliwości nawigacji. Ta klasa jest pochodną [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez tę klasę.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Clear-Item`|Czyści bieżącą zawartość elementów w określonej lokalizacji i zastępuje go znakiem "clear" wartość określoną przez dostawcę. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Get-Item`|Pobiera elementy z określonej lokalizacji, a następnie przesyła strumieniowo obiekty wynikowe.|
|`Invoke-Item`|Wywołuje domyślną akcję dla elementu w określonej ścieżce.|
|`Set-Item`|Ustawia element w określonej lokalizacji z podaną wartość. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Resolve-Path`|Usuwa symbole wieloznaczne ścieżki programu Windows PowerShell i informacje o ścieżce strumieni.|
|`Test-Path`|Sprawdza, czy określona ścieżka, a następnie zwraca `true` jeśli taki istnieje i `false` inaczej. To polecenie cmdlet jest implementowane w celu obsługi `IsContainer` parametr [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metody.|

### <a name="containercmdletprovider-base-class"></a>Klasa bazowa ContainerCmdletProvider

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasa definiuje dostawcy kontenera programu Windows PowerShell, który udostępnia kontener dla elementów magazynu danych, dla użytkownika. Należy pamiętać, że dostawcy kontenera programu Windows PowerShell, mogą być używane tylko wtedy, gdy jeden kontener (nie zagnieżdżone kontenery) przy użyciu elementów. W przypadku zagnieżdżone kontenery należy zaimplementować dostawcę nawigacji programu Windows PowerShell.

Ta klasa jest pochodną [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy bazowej. W poniższej tabeli opisano poleceń cmdlet zaimplementowane przez tę klasę.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Copy-Item`|Kopiuje elementy z jednej lokalizacji do innej. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Get-Childitem`|Pobiera elementy podrzędne w określonej lokalizacji i przesyła je strumieniowo jako obiekty.|
|`New-Item`|Tworzy nowe elementy w określonej lokalizacji, a wynikowy obiekt strumieni.|
|`Remove-Item`|Usuwa elementy z określonej lokalizacji.|
|`Rename-Item`|Zmienia nazwę elementu w określonej lokalizacji. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|

### <a name="navigationcmdletprovider-base-class"></a>Klasa bazowa NavigationCmdletProvider

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasa definiuje dostawcę nawigacji programu Windows PowerShell, który wykonuje operacje dla elementów, które używają więcej niż jednego kontenera. Ta klasa jest pochodną [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy bazowej. Następująca tabela zawiera listę poleceń cmdlet udostępnianych przez tę klasę.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|Combine-Path|Łączy dwie ścieżki w pojedynczą ścieżkę przy użyciu ogranicznika właściwe dla dostawcy między ścieżki. To polecenie cmdlet strumieni ciągów.|
|`Move-Item`|Przenosi elementy do określonej lokalizacji. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|

Powiązane polecenia cmdlet to podstawowe polecenie cmdlet ścieżki analizy dostarczony przez środowisko Windows PowerShell. To polecenie cmdlet może służyć do analizowania ścieżki programu Windows PowerShell do obsługi `Parent` parametru. Ciąg ścieżki nadrzędnej strumieniowo.

## <a name="select-provider-interfaces-to-support"></a>Wybierz interfejsy dostawcy do działu pomocy technicznej

Oprócz pochodząca z jednej z klas podstawowych programu Windows PowerShell, Twój dostawca programu Windows PowerShell można obsługiwać inne funkcje wynikających z co najmniej jeden z następujących interfejsów dostawcy. Ta sekcja definiuje tych interfejsów i obsługiwane przez każdego polecenia cmdlet. Nie opisano parametry polecenia cmdlet obsługiwane przez interfejs. Informacje o parametrach z polecenia cmdlet jest dostępna online za pomocą `Get-Command` i `Get-Help` polecenia cmdlet.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejs definiuje dostawcy zawartości, który wykonuje operacje na zawartość elementu danych. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez ten interfejs.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Add-Content`|Dołącza podaną wartość długości zawartości określonego elementu. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Clear-Content`|Ustawienie zawartości określonego elementu na wartość "clear". To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Get-Content`|Pobiera zawartość określonych elementów i strumieni obiekty wynikowe.|
|`Set-Content`|Zastępuje istniejącą zawartość dla określonego elementu. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfejs definiuje właściwość dostawcy środowiska Windows PowerShell, który wykonuje operacje na właściwości elementów w magazynie danych. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez ten interfejs.

> [!NOTE]
> `Path` Parametr na tych poleceń cmdlet wskazuje ścieżkę do elementu zamiast identyfikująca właściwość.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Clear-ItemProperty`|Ustawia właściwości określonych elementów na wartość "clear". To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Get-ItemProperty`|Pobiera właściwości z określonych elementów i strumieni obiekty wynikowe.|
|`Set-ItemProperty`|Ustawia właściwości określonych elementów wskazanej wartości. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfejsu, pochodzące z [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definiuje Dostawca określający parametrów dynamicznych do jego obsługiwanej poleceń cmdlet. Ten typ dostawcy obsługuje operacje, dla których można zdefiniować właściwości w czasie wykonywania, na przykład nową operację właściwości. Takie operacje nie są możliwe w elementach statycznie po określeniu właściwości. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez ten interfejs.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Copy-ItemProperty`|Kopiuje właściwości z określonego elementu z innym elementem. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`Move-ItemProperty`|Przenosi właściwości z określonego elementu z innym elementem. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|
|`New-ItemProperty`|Tworzy właściwość o określonych elementów i strumieni obiekty wynikowe.|
|`Remove-ItemProperty`|Usuwa właściwość dla określonych elementów.|
|`Rename-ItemProperty`|Zmienia nazwę właściwości określonych elementów. To polecenie cmdlet nie przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, chyba że jego `PassThru` określono parametr.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interfejsu dodaje funkcje deskryptora zabezpieczeń do dostawcy. Ten interfejs umożliwia użytkownikowi na pobieranie i ustawianie informacje deskryptora zabezpieczeń dla elementu w magazynie danych. Poniższa tabela zawiera listę poleceń cmdlet udostępnianych przez ten interfejs.

|Polecenie cmdlet|Definicja|
|------------|----------------|
|`Get-Acl`|Pobiera informacje zawarte w listy kontroli dostępu (ACL), który jest częścią deskryptor zabezpieczeń używane do zabezpieczenia zasobów systemu operacyjnego, na przykład, plik lub obiektu.|
|`Set-Acl`|Ustawia informacje dotyczące listy ACL. W formularzu wystąpienia [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) na elementy wyznaczony dla określonej ścieżki. To polecenie cmdlet można ustawić informacji o plikach, kluczy i podkluczy w rejestrze lub inny element dostawcy, jeśli dostawca programu Windows PowerShell obsługuje ustawienie informacji o zabezpieczeniach.|

## <a name="see-also"></a>Zobacz też

[Tworzenie programu Windows PowerShell dostawców](./how-to-create-a-windows-powershell-provider.md)

[Jak działa program Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)