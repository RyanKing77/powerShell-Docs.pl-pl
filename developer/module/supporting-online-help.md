---
title: Obsługa pomocy Online | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082145"
---
# <a name="supporting-online-help"></a>Obsługa pomocy Online

Począwszy od programu Windows PowerShell 3.0, istnieją dwa sposoby obsługi `Get-Help` funkcja Online dla poleceń programu Windows PowerShell. W tym temacie wyjaśniono, jak zaimplementować tę funkcję dla różnych typów.

## <a name="about-online-help"></a>Temat pomocy Online

Pomoc online zawsze było to ważna część programu Windows PowerShell. Mimo że `Get-Help` polecenie cmdlet wyświetla Pomoc w wierszu polecenia tak, wielu użytkowników środowisko odczytu w trybie online, w tym kodowania kolorami, hiperłącza i udostępniania pomysły w sekcji Zawartość społeczności i dokumentów na podstawie typu wiki. Co najważniejsze przed pojawieniu aktualizowalnej pomocy pomocy online pod warunkiem najnowszą wersję plików pomocy.

Pojawienie aktualizowalnej pomocy w środowisku Windows PowerShell 3.0 pomocy online nadal odgrywa kluczową rolę. Oprócz elastyczne komfortu pomocy online udostępnia pomoc dla użytkowników, którzy nie obsługują lub nie można użyć aktualizowalnej pomocy do pobrania tematy Pomocy.

## <a name="how-get-help--online-works"></a>Jak Get-Help-działa w trybie Online

Aby ułatwić użytkownikom znajdowanie online tematy pomocy dla poleceń, `Get-Help` polecenie ma parametr Online, który spowoduje otwarcie wersji online tematu Pomocy dotyczącego polecenia w użytkownika domyślnej przeglądarki internetowej.

Na przykład następujące polecenie otwiera online tematu Pomocy dotyczącego `Invoke-Command` polecenia cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Aby zaimplementować `Get-Help` -Online, `Get-Help` polecenia cmdlet wygląda dla zasobów identyfikator URI (Uniform) dla wersji online tematu pomocy w następujących lokalizacjach.

- Pierwszy link w sekcji linki powiązane tematu pomocy dla polecenia. Temat pomocy musi być zainstalowany na komputerze użytkownika. Ta funkcja została wprowadzona w programie Windows PowerShell 2.0.

- Właściwości HelpUri dowolnego polecenia. Właściwości HelpUri jest dostępna, nawet wtedy, gdy tematu Pomocy dotyczącego polecenia nie jest zainstalowany na komputerze użytkownika. Ta funkcja została wprowadzona w środowisku Windows PowerShell 3.0.

  `Get-Help` sprawdza, czy identyfikatora URI w pierwszy wpis w sekcji linki powiązane, zanim uzyska wartość właściwości HelpUri. Jeśli wartość właściwości jest nieprawidłowa lub została zmieniona, można zastąpić go przez wprowadzenie innej wartości w pierwszym łącza powiązane. Jednak pierwszy łącza pokrewnego działa tylko wtedy, gdy tematy pomocy są zainstalowane na komputerze użytkownika.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Dodawanie identyfikatora URI do pierwszego łącza powiązane tematu pomocy polecenia

Może obsługiwać `Get-Help` -Online dla dowolnego polecenia, dodając prawidłowy identyfikator URI do pierwszej pozycji w sekcji linki powiązane tematu pomocy oparty na składni XML dla polecenia. Ta opcja jest prawidłowa tylko w opartych na języku XML tematy pomocy i działa tylko wtedy, gdy tematu Pomocy jest zainstalowany na komputerze użytkownika. Po zainstalowaniu tematu pomocy, natomiast identyfikatora URI jest wypełniana, ta wartość ma pierwszeństwo przed **HelpUri** właściwość polecenia. Aby uzyskać informacje oparte na języku XML tematy Pomocy dotyczące poleceń, zobacz [Writing XML-Based tematy pomocy dla poleceń](../help/writing-xml-based-help-topics-for-commands.md).

Aby obsługiwać tę funkcję, identyfikator URI musi znajdować się w `maml:uri` elementu w pierwszym `maml:relatedLinks/maml:navigationLink` element `maml:relatedLinks` elementu.

Następujący kody XML pokazuje poprawne położenie identyfikatora URI. "Wersja Online:" tekst w `maml:linkText` element jest najlepszym rozwiązaniem, ale nie jest wymagane.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Dodawanie właściwości HelpUri do polecenia

W tej sekcji przedstawiono sposób dodawania właściwości HelpUri do poleceń o różnych typach.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Dodawanie właściwości HelpUri do polecenia Cmdlet

Dla poleceń cmdlet napisane w C#, Dodaj **HelpUri** atrybutów klasy polecenia Cmdlet. Wartość atrybutu musi być identyfikator URI, który rozpoczyna się od "http" lub "https".

Poniższy kod przedstawia atrybutu HelpUri `Get-History` klasy polecenia cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Dodawanie właściwości HelpUri do funkcji zaawansowanych

Zaawansowane funkcje, można dodać **HelpUri** właściwości **CmdletBinding** atrybutu. Wartość właściwości musi być identyfikator URI, który rozpoczyna się od "http" lub "https".

Poniższy kod przedstawia atrybutu HelpUri funkcji New-kalendarza

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Dodawanie atrybutu HelpUri do polecenia CIM

W przypadku poleceń CIM, dodać **HelpUri** atrybutu **CmdletMetadata** elementu w pliku CDXML. Wartość atrybutu musi być identyfikator URI, który rozpoczyna się od "http" lub "https".

Poniższy kod przedstawia atrybutu HelpUri polecenia CIM rozpoczęcia debugowania

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Dodawanie atrybutu HelpUri do przepływu pracy

W przypadku przepływów pracy, które są napisane w języku środowiska Windows PowerShell, należy dodać **. ExternalHelp** dyrektywy komentarza do kodu przepływu pracy. Wartość dyrektywy musi być identyfikator URI, który rozpoczyna się od "http" lub "https".

> [!NOTE]
> Właściwości HelpUri nie jest obsługiwana dla przepływów pracy opartych na XAML w programie Windows PowerShell.

Poniższy kod przedstawia. Dyrektywa ExternalHelp w plik przepływu pracy.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```