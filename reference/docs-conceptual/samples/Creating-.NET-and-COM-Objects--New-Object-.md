---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie obiektów .NET i COM nowego obiektu
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293371"
---
# <a name="creating-net-and-com-objects-new-object"></a>Tworzenie obiektów .NET i COM (New-Object)

Brak składników oprogramowania za pomocą środowiska .NET Framework i COM interfejsy, które umożliwiają wykonywanie wielu zadań administracyjnych. Program Windows PowerShell pozwala używać tych składników, więc nie są ograniczone do zadania, które mogą być wykonywane przy użyciu poleceń cmdlet. Wiele poleceń cmdlet w początkowym wydaniu programu Windows PowerShell nie działają na komputerach zdalnych. Przedstawiony zostanie sposób obejść to ograniczenie, gdy zarządzanie dziennikami zdarzeń za pomocą programu .NET Framework **System.Diagnostics.EventLog** klasy bezpośrednio z programu Windows PowerShell.

## <a name="using-new-object-for-event-log-access"></a>Za pomocą nowego obiektu dla dostępu do dziennika zdarzeń

Biblioteka klas programu .NET Framework zawiera klasę o nazwie **System.Diagnostics.EventLog** który może służyć do zarządzania dziennikami zdarzeń. Można utworzyć nowe wystąpienie klasy .NET Framework za pomocą **New-Object** polecenia cmdlet z **TypeName** parametru. Na przykład następujące polecenie tworzy odwołanie do dziennika zdarzeń:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Mimo że polecenie utworzone wystąpienie klasy w dzienniku zdarzeń, wystąpienie nie zawiera żadnych danych. To, ponieważ firma Microsoft nie określiła określonego dziennika zdarzeń. Jak uzyskać prawdziwe dziennika zdarzeń

### <a name="using-constructors-with-new-object"></a>Za pomocą nowego obiektu za pomocą konstruktorów

Aby odwołać się do określonego dziennika zdarzeń, należy określić nazwę dziennika. **Nowy obiekt** ma **Listaargumentów** parametru. Argumenty przekazywane jako wartości tego parametru są używane przez metodę uruchamiania specjalne obiektu. Metoda jest wywoływana *Konstruktor* ponieważ jest używana do konstruowania obiektu. Na przykład aby uzyskać odwołanie do dziennika aplikacji, należy określić ciąg "Aplikacja" jako argumentu:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Ponieważ większość klas podstawowych platformy .NET Framework są zawarte w przestrzeni nazw systemu, programu Windows PowerShell automatycznie podejmie próbę znalezienia klas, które określisz w przestrzeni nazw systemu, jeśli nie znajdzie dopasowania dla typename, które określisz. Oznacza to, że można określić Diagnostics.EventLog zamiast System.Diagnostics.EventLog.

### <a name="storing-objects-in-variables"></a>Przechowywanie obiektów w zmiennych

Możesz chcieć przechowywać odwołanie do obiektu, aby można było używać w bieżącej powłoce. Mimo że program Windows PowerShell umożliwia sporego nakładu pracy korzystających z potoków, zmniejszenie potrzebę zmiennych, czasem przechowywania odwołań do obiektów w zmiennych wygodniej do manipulowania tymi obiektami.

Program Windows PowerShell umożliwia tworzenie zmiennych, które zasadniczo są nazwane obiekty. Dane wyjściowe wszystkie prawidłowe polecenia programu Windows PowerShell, mogą być przechowywane w zmiennej. Nazwy zmiennych zawsze zaczynają się od $. Jeśli chcesz przechowywać odwołania dziennik aplikacji w zmiennej o nazwie $AppLog, wpisz nazwę zmiennej, następuje znak równości, a następnie wpisz polecenie używane do utworzenia obiektu dziennika aplikacji:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Następnie wpisz $AppLog, można wyświetlić, czy zawiera on w dzienniku aplikacji:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a>Dostęp do zdalnego dziennika zdarzeń za pomocą nowego obiektu

Polecenia używane w poprzedniej sekcji docelowe komputerze lokalnym; **Get EventLog** polecenia cmdlet można to zrobić. Aby uzyskać dostęp do dzienników aplikacji na komputerze zdalnym, należy podać zarówno nazwę dziennika i nazwę komputera (lub adres IP) jako argumenty.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Teraz, gdy odwołanie do dziennika zdarzeń, który jest przechowywany w zmiennej $RemoteAppLog, jakie zadania można możemy wykonać na nim?

### <a name="clearing-an-event-log-with-object-methods"></a>Wyczyszczenie dziennika zdarzeń za pomocą metod obiektów

Obiekty mają często metod, które mogą być wywoływane w celu wykonywania zadań. Możesz użyć **Get-Member** do wyświetlenia metody skojarzona z obiektem. Poniższe polecenie i wybrane dane wyjściowe pokazują niektóre metody klasy w dzienniku zdarzeń:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

**Clear()** metoda można wyczyścić dziennik zdarzeń. Podczas wywoływania metody, należy zawsze wykonać nazwę metody przez nawiasy, nawet jeśli metoda nie wymaga argumentów. Dzięki temu Windows PowerShell rozróżnienia metody i potencjalne właściwości o takiej samej nazwie. Wpisz następujące polecenie, aby wywołać **wyczyść** metody:

```
PS> $RemoteAppLog.Clear()
```

Wpisz następujące polecenie, aby wyświetlić dziennik. Zostanie wyświetlony w dzienniku zdarzeń zostały wyczyszczone, a teraz jest 0 wpisów zamiast 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>Tworzenie obiektów COM za pomocą nowego obiektu
Możesz użyć **New-Object** pracę dzięki składnikom Component Object Model (COM). Składniki z zakresu od różnych bibliotek dodane za pomocą Windows Script Host (WSH) w celu aplikacji ActiveX, takich jak program Internet Explorer, które są zainstalowane na większości systemów.

**Nowy obiekt** używa otok wywoływanych w czasie wykonywania Framework .NET do tworzenia obiektów COM, dlatego ma te same ograniczenia, które .NET Framework obsługuje podczas wywoływania obiektów COM. Aby utworzyć obiekt COM, należy określić **ComObject** parametrem identyfikator programowy lub *ProgId* klasy COM, którego chcesz użyć. Wyczerpujące omówienie ograniczeń użytkowania COM i określania, jakie są dostępne w systemie ProgID jest poza zakresem niniejszego podręcznika użytkownika, ale dobrze znane obiekty ze środowisk, takich jak hosta skryptów systemu Windows mogą być używane w programie Windows PowerShell.

Obiekty hosta skryptów systemu Windows można tworzyć, określając te ProgID: **Obiektu WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, i **Scripting.FileSystemObject**. Następujące polecenia tworzą następujące obiekty:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Mimo że większość funkcjonalności tych klas są udostępniane w inny sposób w środowisku Windows PowerShell, nadal łatwiej zrobić za pomocą klasy funkcji jest kilka zadań, takich jak tworzenie skrótów.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Tworzenie skrótu na pulpicie za pomocą obiektu WScript.Shell.

Jedno zadanie, które mogą być wykonywane szybko za pomocą obiektu COM jest utworzenie skrótu. Załóżmy, że chcesz utworzyć skrót na pulpicie prowadzący do folderu macierzystego dla środowiska Windows PowerShell. Najpierw należy utworzyć odwołanie do **obiektu WScript.Shell**, które będą przechowywane w zmiennej o nazwie **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member działa z obiektami COM, dzięki czemu możesz zapoznać się z elementów członkowskich obiektu, wpisując:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** ma opcjonalny **InputObject** parametru zamiast przesyłanie potokowe umożliwia podanie danych wejściowych do **Get-Member**. Takie same dane wyjściowe, jak pokazano powyżej, jeśli zamiast tego użyto polecenia otrzymamy **Get-Member — InputObject $WshShell**. Jeśli używasz **InputObject**, traktuje jej argument jako pojedynczy element. Oznacza to, że jeśli masz kilka obiektów w zmiennej, **Get-Member** traktuje je jako tablica obiektów. Przykład:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**CreateShortcut obiektu WScript.Shell** metoda przyjmuje jeden argument, a ścieżka do pliku skrótów do utworzenia. Firma Microsoft może wpisz pełną ścieżkę do programu desktop, ale jest łatwiejsze. Pulpit jest zwykle reprezentowany przez folder o nazwie pulpitu bieżącego użytkownika w folderze głównym. Program Windows PowerShell ma zmienną **$Home** zawierający ścieżkę do tego folderu. Możemy określić ścieżkę do folderu macierzystego przy użyciu tej zmiennej, a następnie dodaj nazwę folderu pulpitu i nazwy skrótu do tworzenia, wpisując:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Gdy używasz coś, co przypomina nazwę zmiennej w podwójne cudzysłowy, programu Windows PowerShell próbuje zastąpić o pasującej wartości. Jeśli używasz jednego ofert, programu Windows PowerShell nie podejmuje próby podstawiania wartości zmiennej. Na przykład wpisz następujące polecenia:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Teraz mamy zmienną o nazwie **$lnk** zawiera nowe odwołanie skrótów. Jeśli chcesz wyświetlić jej elementów członkowskich, można przekazać go do **Get-Member**. Danych wyjściowych poniżej przedstawiono elementy członkowskie, że należy wykonać, aby zakończyć tworzenie naszej skrótów:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Trzeba określić **TargetPath**, czyli do folderu aplikacji dla programu Windows PowerShell, a następnie Zapisz skrót **$lnk** przez wywołanie metody **Zapisz** metody. Ścieżka folderu aplikacji programu Windows PowerShell jest przechowywana w zmiennej **$PSHome**, dzięki czemu możemy to zrobić, wpisując:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Za pomocą programu Internet Explorer w programie Windows PowerShell

Wiele aplikacji (w tym aplikacji i programu Internet Explorer z rodziny Microsoft Office) można zautomatyzować za pomocą modelu COM. Program Internet Explorer przedstawiono niektóre typowe techniki i zagadnieniach dotyczących pracy z aplikacji opartych na modelu COM.

Utwórz wystąpienie programu Internet Explorer, określając Internet Explorer ProgId, **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

To polecenie uruchamia program Internet Explorer, ale nie była widoczna. Jeśli wpiszesz Get-Process, widać, że proces o nazwie iexplore działa. W rzeczywistości Jeśli zakończysz programu Windows PowerShell, proces będzie kontynuował pracę. Należy ponownie uruchomić komputer lub użyć narzędzia takie jak Menedżer zadań, aby zakończyć proces iexplore.

> [!NOTE]
> Często nazywane obiektami COM, które Uruchom jako oddzielne procesy *pliki wykonywalne ActiveX*, może, mogą nie być wyświetlane okno interfejsu użytkownika podczas uruchamiania. Jeśli tworzenie okna, ale nie była widoczna, takich jak Internet Explorer, zazwyczaj przeniesie fokus na pulpit Windows i należy okna widoczne wchodzić w interakcje z nią.

Wpisując **$ie | Get-Member**, możesz wyświetlić właściwości i metody dla programu Internet Explorer. Aby wyświetlić okno programu Internet Explorer, należy ustawić właściwość Visible $true, wpisując:

```powershell
$ie.Visible = $true
```

Następnie można przejść do określonego adresu sieci Web przy użyciu metody Nawigacja:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Korzystając z innymi członkami modelu obiektów programu Internet Explorer, istnieje możliwość pobrania zawartości tekstowej ze strony internetowej. Następujące polecenie spowoduje wyświetlenie tekstu w formacie HTML w treści bieżącej strony sieci Web:

```powershell
$ie.Document.Body.InnerText
```

Aby zamknąć program Internet Explorer z wnętrza programu PowerShell, należy wywołać jej metodę Quit():

```powershell
$ie.Quit()
```

Spowoduje to wymuszenie go zamknąć. $Ie zmiennej nie zawiera już prawidłowe odwołanie, mimo że nadal jest wyświetlany jako obiekt COM. Jeśli spróbujesz go używać, zostanie wyświetlony błąd automatyzacji:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Można usunąć pozostałe odwoływać przy użyciu polecenia, takie jak $ie = $null lub całkowicie usunąć zmienną, wpisując:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Nie istnieje dla tego, czy pliki wykonywalne ActiveX zamknąć lub będą nadal działać po usunięciu odwołanie do jednej wspólnej standard. W zależności od okoliczności, takich jak tego, czy aplikacja jest widoczna, czy zmieniony dokument jest uruchomiona w nim i nawet tego, czy program Windows PowerShell jest nadal uruchomiona aplikacja może być lub może nie zakończyć. Z tego powodu należy przetestować zachowanie po przerwaniu dla każdego pliku wykonywalnego, aby użyć w programie Windows PowerShell ActiveX.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Wyświetlanie ostrzeżeń dotyczących obiektów COM opakowane w ramach platformy .NET

W niektórych przypadkach obiekt COM może mieć skojarzone .NET Framework *otoka wywoływana w czasie wykonywania* lub RCW i spowoduje używane przez **New-Object**. Ponieważ zachowanie RCW może różnić się od zachowania normalnego obiektu COM **New-Object** ma **Strict** parametru ostrzegania o RCW dostępu. Jeśli określisz **Strict** parametru i następnie utworzyć obiekt COM, który używa RCW, pojawi się komunikat ostrzegawczy:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Mimo, że obiekt nadal jest tworzony, zostanie wyświetlone ostrzeżenie, że nie jest standardowy obiekt COM.