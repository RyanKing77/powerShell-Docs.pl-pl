---
title: Wskazówki dotyczące porad dotyczących programowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854864"
---
# <a name="advisory-development-guidelines"></a>Pomocnicze wskazówki dotyczące projektowania

W tej sekcji opisano wskazówki, które należy wziąć pod uwagę zapewnienie dobrej środowiska programowania i użytkowników. Czasami mogą być stosowane, a czasami mogą być może nie.

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Podczas projektowania poleceń cmdlet, należy rozważyć następujące wskazówki. Po znalezieniu wskazówek dotyczących projektu, która ma zastosowanie do konkretnej sytuacji, pamiętaj przyjrzeć się wskazówki dotyczące kodu podobne wskazówki dotyczące.

### <a name="support-an-inputobject-parameter-ad01"></a>Obsługuje parametru InputObject (AD01)

Ponieważ działania programu Windows PowerShell bezpośrednio z obiektami programu Microsoft .NET Framework, obiekt .NET Framework jest często dostępne, że dokładnie dopasowań typu użytkownik musi wykonać określonej operacji. `InputObject` jest to nazwa standardowa parametru, który przyjmuje obiekt jako dane wejściowe. Na przykład próbki **Stop-Proc** polecenia cmdlet w [samouczek StopProc](./stopproc-tutorial.md) definiuje `InputObject` parametr typu procesu, który obsługuje dane wejściowe z potoku. Użytkownika można pobrać zestaw obiektów procesu, manipulować nimi, aby wybrać dokładnie obiektów, aby zatrzymać, a następnie przekazać je do **Stop-Proc** bezpośrednio polecenia cmdlet.

### <a name="support-the-force-parameter-ad02"></a>Obsługa parametru Force (AD02)

Od czasu do czasu polecenia cmdlet należy chronić użytkownika przed wykonaniem żądanej operacji. Polecenia cmdlet powinny obsługiwać `Force` parametr umożliwia użytkownikowi przesłanianie ochrona, jeśli użytkownik ma uprawnienia do wykonania tej operacji.

Na przykład [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) polecenie cmdlet nie powoduje usunięcia zwykle plików tylko do odczytu. To polecenie cmdlet obsługuje jednak `Force` parametr, dzięki czemu użytkownik może wymusić usunięcie plików tylko do odczytu. Jeśli użytkownik ma już uprawnienia do modyfikowania atrybut tylko do odczytu, a użytkownik usuwa plik, użyj `Force` parametru upraszcza wykonać operację. Jednakże, jeśli użytkownik nie ma uprawnienia do usunięcia pliku `Force` parametr nie ma wpływu.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Obsługa poświadczeń za pomocą programu Windows PowerShell (AD03)

Polecenia cmdlet należy zdefiniować `Credential` parametr do reprezentowania poświadczeń. Ten parametr musi być typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) i muszą być zdefiniowane przy użyciu deklaracji atrybutu poświadczeń. Ta obsługa automatycznie monituje użytkownika dla nazwy użytkownika, hasła lub dla obu, gdy pełna poświadczenia nie są dostarczane bezpośrednio. Aby uzyskać więcej informacji o atrybucie poświadczeń, zobacz [deklaracji atrybutu poświadczeń](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Obsługuje kodowanie parametrów (AD04)

Jeśli Twojego polecenia cmdlet odczytuje lub zapisuje tekst z formy binarnej, takie jak zapisywanie do lub odczytywanie z pliku w systemie plików, lub Twojego polecenia cmdlet musi mieć parametr kodowania, który określa, jak tekst jest zakodowany w formacie binarnym.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Polecenia cmdlet test powinna zwracać wartość logiczną (AD05)

Polecenia cmdlet do wykonywania testów w odniesieniu do ich zasobów powinien zwrócić [System.Boolean](/dotnet/api/System.Boolean) wpisz do potoku, dzięki czemu mogą być używane w wyrażeniach warunkowych.

## <a name="code-guidelines"></a>Wytyczne dotyczące kodu

Należy rozważyć następujące wskazówki podczas pisania kodu, polecenia cmdlet. Po znalezieniu wskazówki, które mają zastosowanie do sytuacji, pamiętaj przyjrzeć się podobne wytycznych dotyczących projektowania.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Zgodne z konwencjami nazewnictwa klasy polecenia Cmdlet (AC01)

Przez następujące standardowe konwencje nazewnictwa poleceń cmdlet upewnij mogą szybciej odnajdywać, i pomóc użytkownikowi zrozumieć dokładnie poleceń cmdlet działania. Tej praktyką jest szczególnie ważne w przypadku innych deweloperów przy użyciu programu Windows PowerShell, ponieważ typy publiczne są polecenia cmdlet.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definiowanie polecenia Cmdlet w poprawne Namespace

Zwykle zdefiniować klasy związane z poleceniem cmdlet w przestrzeni nazw .NET Framework, która dołącza ". Polecenia"do przestrzeni nazw, który reprezentuje produkt, w którym jest uruchamiane polecenie cmdlet. Na przykład polecenia cmdlet, które są uwzględniane przy użyciu programu Windows PowerShell są zdefiniowane w `Microsoft.PowerShell.Commands` przestrzeni nazw.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nazwa klasy polecenia Cmdlet, aby dopasować nazwę polecenia Cmdlet

Nazwa klasy .NET Framework, która implementuje polecenia cmdlet nazwę klasy "*\<czasownik >**\<rzeczownik >**\<polecenia >*", gdzie zamiany  *\<Czasownik >* i  *\<rzeczownik >* zastępcze czasownik i rzeczownik używana jako nazwa polecenia cmdlet. Na przykład [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet jest implementowany przez klasę o nazwie `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Jeśli nie wejście potokowe przesłonić metodę BeginProcessing (AC02)

Jeśli Twojego polecenia cmdlet nie akceptuje dane wejściowe z potoku, przetwarzanie powinny być zrealizowane w [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody. Użyj tej metody umożliwia programu Windows PowerShell, aby zachować kolejność między poleceniami cmdlet. Pierwsze polecenie cmdlet w potoku zawsze zwraca jej obiektów, zanim pozostałe polecenia cmdlet w potoku uzyskać szansę na start ich przetwarzania.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Aby obsłużyć żądania zatrzymania przesłonić metodę StopProcessing (AC03)

Zastąp [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) metody, aby Twoje polecenie cmdlet może obsłużyć sygnał zatrzymania. Niektóre polecenia cmdlet zająć dużo czasu do wykonania ich operacji i umożliwiają one przez długi czas przekazania między wywołaniami do środowiska wykonawczego programu Windows PowerShell, np. gdy polecenia cmdlet blokuje wątek w długim wywołania RPC. Obejmuje to polecenia cmdlet, które są wybierane [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody do [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody i inne opinie mechanizmy, które może potrwać bardzo długo. W tych przypadkach użytkownik może być konieczne wysyłać sygnał zatrzymania tych poleceń cmdlet.

### <a name="implement-the-idisposable-interface-ac04"></a>Zaimplementuj interfejs IDisposable (AC04)

Jeśli Twojego polecenia cmdlet zawiera obiekty, które nie są usuwane z (zapisany w potoku) [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody Twojego polecenia cmdlet mogą wymagać usunięcia obiektów dodatkowych. Na przykład Twoje polecenie cmdlet otwiera dojście do pliku w jego [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody i przechowuje dojście Otwórz do użytku przez [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody tego dojścia musi być zamknięty po zakończeniu przetwarzania.

Środowisko wykonawcze programu Windows PowerShell, nie zawsze wywołuje [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody. Na przykład [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoda nie może być wywoływana, jeśli polecenie cmdlet zostanie anulowana w środku za pośrednictwem jego działania lub gdy kończącym błędu w jakichkolwiek pracach związanych z polecenia cmdlet. W związku z tym, powinny implementować pełne klasy .NET Framework dla polecenia cmdlet, które wymaga czyszczenia obiektu [System.IDisposable](/dotnet/api/System.IDisposable) wzorzec interfejsu, w tym finalizatora, dzięki czemu można wywołać w czasie wykonywania programu Windows PowerShell [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) i [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) metody po zakończeniu przetwarzania.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Użyj parametru przyjaznego dla serializacji typów (AC05)

Aby zapewnić obsługę Twoje polecenie cmdlet uruchomione na komputerach zdalnych, należy użyć typów, które można łatwo jest serializowana na komputerze klienckim i następnie wypełnienia na komputerze serwera. Postępuj zgodnie z typy nie są przyjazne dla serializacji.

Typy pierwotne:

- Byte, SByte, Decimal, jednego, Double, Int16, Int32, Int64, Uint16, UInt32 i UInt64.

- Atrybut typu wartość logiczna, Guid, Byte [], przedział czasu, daty/godziny, identyfikatora Uri i wersji.

- Char, String, XmlDocument.

Typy wbudowane rehydratable:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- Informacje o języku

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Inne typy:

- SecureString

- Kontenery (listy i słowników powyższego typu)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Użyj SecureString poufnych danych (AC06)

Podczas obsługi poufnych danych zawsze używać [System.Security.Securestring](/dotnet/api/System.Security.SecureString) typu danych. Może to obejmować wejście potokowe do parametrów, a także zwracanie danych poufnych do potoku.

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące programowania wymagane](./required-development-guidelines.md)

[Wskazówki dotyczące programowania zalecamy](./strongly-encouraged-development-guidelines.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
