---
title: Obsługa pomocy online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848079"
---
# <a name="supporting-online-help"></a>Obsługa pomocy online

Począwszy od programu Windows PowerShell 3,0, istnieją dwa sposoby obsługi `Get-Help` funkcji online dla poleceń programu Windows PowerShell. W tym temacie wyjaśniono, jak zaimplementować tę funkcję dla różnych typów poleceń.

## <a name="about-online-help"></a>Informacje o pomocy online

Pomoc online była zawsze istotną częścią programu Windows PowerShell. Mimo że `Get-Help` polecenie cmdlet wyświetla tematy pomocy w wierszu polecenia, wielu użytkowników preferuje środowisko odczytywania w trybie online, w tym kolorowanie, hiperłącza i udostępnianie pomysłów w treści społeczności i dokumentach opartych na witrynie typu wiki. Co najważniejsze, przed pojawieniu aktualizowalnej pomocy, pomoc online zapewniała najbardziej aktualną wersję plików pomocy.

Dzięki pojawieniu aktualizowalnej pomocy w programie Windows PowerShell 3,0 pomoc online nadal odgrywa istotną rolę. Oprócz elastycznego środowiska użytkownika Pomoc Online zapewnia użytkownikom, którzy nie są lub nie mogą używać aktualizowalnej pomocy do pobierania tematów pomocy.

## <a name="how-get-help--online-works"></a>Jak działa metoda Get-Help-online

Aby ułatwić użytkownikom znalezienie tematów pomocy online dla poleceń, `Get-Help` polecenie zawiera parametr online, który otwiera informacje o wersji online tematu pomocy dla polecenia w domyślnej przeglądarce internetowej użytkownika.

Na przykład następujące polecenie otwiera temat pomocy online dla tego `Invoke-Command` polecenia cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

W celu `Get-Help` zaimplementowania trybu `Get-Help` online polecenie cmdlet wyszukuje Uniform Resource Identifier (URI) tematu pomocy dotyczącej wersji online w poniższych lokalizacjach.

- Pierwszy link w sekcji powiązane linki tematu pomocy dla polecenia. Temat pomocy musi być zainstalowany na komputerze użytkownika. Ta funkcja została wprowadzona w programie Windows PowerShell 2,0.

- Właściwość HelpUri dowolnego polecenia. Właściwość HelpUri jest dostępna, nawet jeśli nie zainstalowano tematu pomocy dla tego polecenia na komputerze użytkownika. Ta funkcja została wprowadzona w programie Windows PowerShell 3,0.

  `Get-Help`szuka identyfikatora URI w pierwszym wpisie w sekcji powiązane linki przed pobraniem wartości właściwości HelpUri. Jeśli wartość właściwości jest niepoprawna lub została zmieniona, można ją zastąpić, wprowadzając inną wartość w pierwszym połączonym łączu. Jednak pierwsze powiązane łącze działa tylko wtedy, gdy tematy pomocy są zainstalowane na komputerze użytkownika.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Dodawanie identyfikatora URI do pierwszego powiązanego linku tematu pomocy polecenia

W trybie online `Get-Help` można obsługiwać dowolne polecenie, dodając prawidłowy identyfikator URI do pierwszego wpisu w sekcji powiązane linki tematu pomocy opartej na języku XML dla polecenia. Ta opcja jest prawidłowa tylko w tematach pomocy opartych na języku XML i działa tylko po zainstalowaniu tematu pomocy na komputerze użytkownika. Gdy zainstalowano temat pomocy i wypełniono identyfikator URI, ta wartość ma pierwszeństwo przed właściwością **HelpUri** polecenia.

Aby obsługiwać tę funkcję, identyfikator URI musi pojawić się `maml:uri` w elemencie pod pierwszym `maml:relatedLinks/maml:navigationLink` elementem w `maml:relatedLinks` elemencie.

Poniższy kod XML przedstawia poprawne umieszczanie identyfikatora URI. Tekst "wersja online:" w `maml:linkText` elemencie jest najlepszym rozwiązaniem, ale nie jest to wymagane.

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

W tej sekcji pokazano, jak dodać właściwość HelpUri do poleceń różnych typów.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Dodawanie właściwości HelpUri do polecenia cmdlet

W przypadku poleceń cmdlet pisanych C#w programie Dodaj atrybut **HelpUri** do klasy poleceń cmdlet. Wartość atrybutu musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".

Poniższy kod przedstawia atrybut `Get-History` HelpUri klasy cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Dodawanie właściwości HelpUri do funkcji zaawansowanej

W przypadku funkcji zaawansowanych Dodaj właściwość **HelpUri** do atrybutu **CmdletBinding** . Wartość właściwości musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".

Poniższy kod przedstawia atrybut HelpUri funkcji New-Calendar

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Dodawanie atrybutu HelpUri do polecenia CIM

Dla poleceń CIM Dodaj atrybut **HelpUri** do elementu **CMDLETMETADATA** w pliku CDXML. Wartość atrybutu musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".

Poniższy kod przedstawia atrybut HelpUri polecenia Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Dodawanie atrybutu HelpUri do przepływu pracy

W przypadku przepływów pracy, które są zapisywane w języku Windows PowerShell, Dodaj **. ExternalHelp** komentarz dyrektywy do kodu przepływu pracy. Wartość dyrektywy musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".

> [!NOTE]
> Właściwość HelpUri nie jest obsługiwana w przypadku przepływów pracy opartych na języku XAML w programie Windows PowerShell.

Poniższy kod przedstawia. ExternalHelp dyrektywę w pliku przepływu pracy.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```