---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie obiektów COM i .NET nowego obiektu
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="creating-net-and-com-objects-new-object"></a>Tworzenie usług .NET i obiektów COM (nowy obiekt)

Brak składników oprogramowania .NET Framework i COM interfejsów, które umożliwiają wykonywanie wielu zadań administracyjnych. Środowisko Windows PowerShell pozwala używać tych składników, dlatego nie są ograniczone do zadań, które mogą być wykonywane przy użyciu poleceń cmdlet. Wiele poleceń cmdlet w początkowa wersja programu Windows PowerShell nie działają na komputerach zdalnych. Zostanie przedstawiony sposób poruszania tego ograniczenia związane z zarządzaniem dzienników zdarzeń przy użyciu programu .NET Framework **System.Diagnostics.EventLog** klasy bezpośrednio z programu Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Za pomocą nowego obiektu dla dostępu do dziennika zdarzeń

Biblioteka klas programu .NET Framework zawiera klasę o nazwie **System.Diagnostics.EventLog** który może służyć do zarządzania dziennikami zdarzeń. Można utworzyć nowe wystąpienie klasy .NET Framework za pomocą **New-Object** polecenia cmdlet z **TypeName** parametru. Na przykład następujące polecenie tworzy odwołanie do dziennika zdarzeń:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Mimo że polecenie utworzone wystąpienie klasy dziennik zdarzeń, wystąpienie nie ma żadnych danych. To, ponieważ nie określono możemy określonego dziennika zdarzeń. Jak uzyskać rzeczywiste dziennika zdarzeń

#### <a name="using-constructors-with-new-object"></a>Używanie konstruktorów z nowego obiektu

Aby odwołać się do określonego dziennika zdarzeń, należy określić nazwę dziennika. **Nowy obiekt** ma **Listaargumentów** parametru. Argumenty przekazywane jako wartości tego parametru są używane przez metodę uruchamiania specjalne obiektu. Metoda jest wywoływana *Konstruktor* ponieważ jest używana do konstruowania obiektu. Na przykład aby odwołać się do dziennika aplikacji, należy określić ciąg "Aplikacja" jako argumentu:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Ponieważ większość podstawowe klasy .NET Framework znajdują się w przestrzeni nazw systemu, środowiska Windows PowerShell automatycznie podejmie próbę znaleźć klas, które określisz w przestrzeni nazw systemu, jeśli nie można odnaleźć dopasowania dla elementu typename, które określisz. Oznacza to, że można określić Diagnostics.EventLog zamiast System.Diagnostics.EventLog.

#### <a name="storing-objects-in-variables"></a>Przechowywania obiektów w zmiennych

Warto przechowywać odwołanie do obiektu, dzięki czemu można używać w bieżącym powłoki. Mimo że programu Windows PowerShell umożliwia dużo pracy korzystających z potoków, zmniejszenie potrzebę zmienne, czasami do przechowywania odwołań do obiektów w zmiennych wygodniej do manipulowania tych obiektów.

Środowisko Windows PowerShell umożliwia tworzenie zmiennych, które są zasadniczo o nazwie obiektów. Dane wyjściowe z wszystkie prawidłowe polecenia programu Windows PowerShell, mogą być przechowywane w zmiennej. Nazwy zmiennych zawsze rozpoczynać się od $. Jeśli chcesz przechowywać w zmiennej o nazwie $AppLog odwołanie do dziennika aplikacji, wpisz nazwę zmiennej, następuje znak równości, a następnie wpisz polecenie używane do utworzenia obiektu dziennika aplikacji:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Gdy program $AppLog, zobacz temat zawiera dziennik aplikacji:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Dostęp do zdalnego dziennika zdarzeń z nowego obiektu

Polecenia używane w poprzedniej sekcji docelowy komputer lokalny; **Get EventLog** polecenia cmdlet można to zrobić. Aby uzyskać dostęp do dziennika aplikacji na komputerze zdalnym, należy podać zarówno nazwę dziennika i nazwa komputera (lub adres IP) jako argumenty.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Teraz, gdy będziemy mieć odwołanie do dziennika zdarzeń przechowywana w zmiennej $RemoteAppLog, jakie zadania można możemy wykonać?

#### <a name="clearing-an-event-log-with-object-methods"></a>Wyczyszczenie dziennika zdarzeń za pomocą metod obiektu

Obiekty często mają metod, które mogą być wywoływane w celu wykonywania zadań. Można użyć **elementu członkowskiego Get** do wyświetlenia metody skojarzona z obiektem. Poniższe polecenie i wybranych danych wyjściowych Pokaż niektórych metod klasy dziennik zdarzeń:

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

**Clear()** metody można użyć, aby wyczyścić dziennik zdarzeń. Podczas wywoływania metody, należy zawsze wykonać nazwę metody w nawiasach, nawet jeśli metoda nie wymaga argumentów. Dzięki temu rozróżnienia metoda i potencjalnych właściwości o tej samej nazwie w programie Windows PowerShell. Wpisz następujące polecenie, aby wywołać **wyczyść** metody:

```
PS> $RemoteAppLog.Clear()
```

Wpisz następujące polecenie, aby wyświetlić dziennik. Zobaczysz, że dziennik zdarzeń został wyczyszczony, a teraz ma 0 wpisów zamiast 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Tworzenie obiektów COM z nowego obiektu
Można użyć **New-Object** do pracy ze składnikami modelu COM (Component Object). Zakres składniki z różnych biblioteki dołączony z systemu Windows Script Host (WSH) do aplikacji ActiveX takich jak program Internet Explorer, które są zainstalowane na większości systemów.

**Nowy obiekt** używa otoki można wywołać środowiska uruchomieniowego .NET Framework w celu utworzenia obiektów COM, więc te same ograniczenia, które jest .NET Framework podczas wywoływania metody obiektów COM. Aby utworzyć obiekt COM, należy określić **ComObject** parametr identyfikator programowy lub *ProgId* klasy COM, którego chcesz użyć. Szczegółowe omówienie ograniczenia użycia COM i określania, jakie są dostępne w systemie ProgID wykracza poza zakres niniejszego podręcznika użytkownika, ale dobrze znane obiekty ze środowisk, takich jak WSH mogą być używane w programie Windows PowerShell.

Można utworzyć obiektów WSH przez określenie tych ProgID: **obiektu WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, i  **Scripting.FileSystemObject**. Następujące polecenia Utwórz tych obiektów:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Mimo że większość funkcjonalności tych klas są udostępniane w inny sposób w programie Windows PowerShell, nadal łatwiej zrobić przy użyciu klasy WSH jest kilka zadań, takich jak tworzenie skrótów.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Tworzenie skrótu na pulpicie z obiektu WScript.Shell.

Jedno zadanie, które mogą być wykonywane szybkie obiektu modelu COM jest tworzenie skrótu. Załóżmy, że chcesz utworzyć skrót na pulpicie prowadzący do folderu macierzystego dla środowiska Windows PowerShell. Najpierw należy utworzyć odwołanie do **obiektu WScript.Shell**, które będą przechowywane w zmiennej o nazwie **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Element członkowski Get działa z obiektami COM, aby można było eksplorować elementów członkowskich obiektu, wpisując:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Element członkowski GET** ma opcjonalny **InputObject** zamiast przesyłanie potokowe umożliwia podawanie danych wejściowych do parametru **elementu członkowskiego Get**. Jak takie same dane wyjściowe zgodnie z powyższym, jeśli zamiast tego użyto polecenia **elementu członkowskiego Get - InputObject $WshShell**. Jeśli używasz **InputObject**, traktuje jej argument jako pojedynczy element. Oznacza to, że jeśli masz wiele obiektów w zmiennej, **elementu członkowskiego Get** traktowane jako tablica obiektów. Przykład:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**CreateShortcut obiektu WScript.Shell** metoda przyjmuje jeden argument, ścieżka do pliku skrótów do utworzenia. Firma Microsoft może wpisz pełną ścieżkę do pulpitu, ale jest prostsze. Pulpit jest zazwyczaj reprezentowany przez folder o nazwie pulpitu wewnątrz folderu macierzystego bieżącego użytkownika. Środowisko Windows PowerShell jest zmienną **$Home** zawiera ścieżkę do tego folderu. Firma Microsoft Określ ścieżkę do folderu macierzystego za pomocą tej zmiennej, a następnie dodaj nazwę folderu pulpitu i nazwy skrótu do tworzenia, wpisując:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Gdy używasz coś, która wygląda jak nazwę zmiennej w cudzysłów podwójny środowiska Windows PowerShell próbuje zastępuje pasującej wartości. Jeśli używasz pojedynczego cudzysłowu, programu Windows PowerShell nie będzie próbował zastąpić wartość zmiennej. Na przykład wpisz następujące polecenia:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Mamy teraz zmiennej o nazwie **$lnk** zawiera nowe odwołanie skrótów. Jeśli chcesz zobaczyć jego elementy członkowskie, możesz przekazać go do **elementu członkowskiego Get**. Danych wyjściowych poniżej zamieszczono elementów członkowskich należy użyć, aby zakończyć tworzenie skrótów naszych:

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

Należy określić **TargetPath**, czyli folderu aplikacji dla środowiska Windows PowerShell, a następnie Zapisz skrót **$lnk** przez wywołanie metody **zapisać** metody. Ścieżka folderu aplikacji programu Windows PowerShell jest przechowywana w zmiennej **$PSHome**, dlatego firma Microsoft można to zrobić, wpisując:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Przy użyciu programu Internet Explorer ze środowiska Windows PowerShell

Wiele aplikacji (w tym rodziny Microsoft Office, aplikacji i programu Internet Explorer) można zautomatyzować za pomocą modelu COM. Program Internet Explorer przedstawiono niektóre typowe techniki i zagadnieniach dotyczących pracy z opartą na modelu COM aplikacji.

Utwórz wystąpienie programu Internet Explorer, określając Internet Explorer identyfikatora ProgId **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

To polecenie uruchamia program Internet Explorer, ale nie była widoczna. Wpisanie polecenia Get-Process widać, że proces o nazwie iexplore działa. W rzeczywistości Jeśli zakończysz środowiska Windows PowerShell, proces będzie kontynuował pracę. Musisz ponownego uruchamiania komputera lub zakończyć proces iexplore za pomocą narzędzia, podobnie jak w Menedżerze zadań.

> [!NOTE]
> Obiekty COM, które uruchomione jako osobne procesy, często nazywane *pliki wykonywalne ActiveX*mogą nie być wyświetlane okna interfejsu użytkownika podczas uruchamiania, może. Jeśli tworzenie okna, ale nie była widoczna, takich jak program Internet Explorer, zazwyczaj przeniesie fokus na pulpicie systemu Windows i należy okna widoczne na interakcję z nią.

Wpisując **$ie | Element członkowski GET**, można wyświetlić właściwości i metody dla programu Internet Explorer. Aby otworzyć okno programu Internet Explorer, należy ustawić właściwość Visible $true, wpisując:

```powershell
$ie.Visible = $true
```

Następnie można przejść do określonego adresu sieci Web przy użyciu metody Nawigacja:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Przy użyciu innych elementach członkowskich modelu obiektów programu Internet Explorer, prawdopodobnie można pobrać ze strony sieci Web zawartości tekstowej. Następujące polecenie spowoduje wyświetlenie tekstu w formacie HTML w treści bieżącej strony sieci Web:

```powershell
$ie.Document.Body.InnerText
```

Aby zamknąć Internet Explorer z programu PowerShell, wywołaj jej metodę Quit():

```powershell
$ie.Quit()
```

Spowoduje to wymuszenie go zamknąć. $Ie zmiennej nie zawiera już prawidłowe odwołania mimo że nadal jest wyświetlany jako obiekt COM. Jeśli spróbujesz użyć otrzymasz błąd automatyzacji:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Można usunąć pozostałe odwołania za pomocą polecenia, takie jak $ie = $null lub całkowicie usunąć zmienną, wpisując:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Nie istnieje dla plików wykonywalnych ActiveX zakończyć czy kontynuować działanie po usunięciu odwołanie do jednej wspólnej standard. W zależności od sytuacji takich jak określa, czy aplikacja jest widoczny, czy zmieniony dokument jest uruchomiony w nim i nawet czy środowiska Windows PowerShell jest nadal uruchomiona aplikacja może lub nie może zakończyć. Z tego powodu należy przetestować zachowanie po przerwaniu dla każdego pliku wykonywalnego, którego chcesz użyć w programie Windows PowerShell ActiveX.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Wyświetlanie ostrzeżeń dotyczących obiektów COM opakowana Framework .NET

W niektórych przypadkach obiekt COM może mieć skojarzone .NET Framework *środowiska uruchomieniowego wywoływana otoka* lub otoki RCW i będzie używane przez **New-Object**. Ponieważ zachowanie otoki RCW mogą być różne od zachowania normalnego obiektu COM **New-Object** ma **Strict** parametr, aby ostrzec użytkownika o dostępie otoki RCW. Jeśli określisz **Strict** parametr, a następnie utwórz obiekt COM, który używa otoki RCW, zostanie wyświetlony komunikat ostrzegawczy:

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

Mimo że obiekt nadal jest tworzony, zostanie wyświetlone ostrzeżenie, że nie jest standard obiektu COM.