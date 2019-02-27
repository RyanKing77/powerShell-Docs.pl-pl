---
title: Pisanie tematów Pomocy dotyczących modułów programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845458"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Pisanie pomocy dotyczącej modułów programu Windows PowerShell

Moduły programu Windows PowerShell może obejmować tematy Pomocy dotyczące modułu i członków modułu, takie jak polecenia cmdlet, dostawców, funkcji i skryptów. `Get-Help` Polecenie cmdlet wyświetla tematy pomocy modułu w tym samym formacie jak Wyświetla Pomoc dla innych elementów programu Windows PowerShell, a użytkownicy standard `Get-Help` poleceń, aby uzyskać pomoc.

W tym dokumencie wyjaśniono, formatu i poprawne rozmieszczenie tematy pomocy modułu i sugerują one wskazówki dotyczące zawartości pomocy modułu.

## <a name="types-of-module-help"></a>Typy pomoc modułu

Moduł może obejmować następujące typy pomocy.

- **Pomocy dotyczącej poleceń cmdlet**. Tematy pomocy, które opisują poleceń cmdlet w module są pliki XML, które używają polecenia Pomoc schematu

- **Dostawca pomocy**. Tematy pomocy, które opisują dostawców w module są pliki XML, które używają dostawcy pomocy schematu.

- **Funkcja pomocy**. Tematy pomocy, które opisują funkcje w module może być plików XML, użyj polecenia pomocy schematu lub oparta na komentarzach tematy pomocy, w ramach funkcji lub skryptu lub moduł skryptu

- **Skrypt pomocy**. Tematy pomocy, które opisują skrypty w module może być plików XML, użyj polecenia pomocy schematu lub oparta na komentarzach tematów pomocy w skrypcie modułu skryptu.

- **Koncepcyjny ("o") pomocy**. Koncepcyjny ("o") tematu Pomocy można użyć do opisania moduł i jej elementów członkowskich i wyjaśnić, jak elementy członkowskie można razem wykonywać zadania. Koncepcyjne tematy pomocy są plikami tekstowymi przy użyciu kodowania Unicode (UTF-8). Nazwa pliku musi być `about_<name>.help.txt` formacie, na przykład about_MyModule.help.txt. Domyślnie środowisko Windows PowerShell zawiera ponad 100 tych pojęć dotyczących pomocy i są one formatowane tak jak w poniższym przykładzie.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Umieszczanie pomoc modułu

`Get-Help` Polecenia cmdlet szuka plików tematów pomocy modułu podkatalogi specyficzny dla języka katalog modułu.

Na przykład na poniższym diagramie strukturę katalogu przedstawiono lokalizację tematy pomocy dla modułu SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> W tym przykładzie  *\<ModulePath >* symbolu zastępczego jedna ze ścieżek używanych w `PSModulePath` zmiennej środowiskowej, np. $home\Documents\Modules, $pshome\Modules lub niestandardową ścieżkę podaną przez użytkownika.

## <a name="getting-module-help"></a>Uzyskiwanie pomocy modułu

Gdy użytkownik importuje modułu do sesji, tematy pomocy dla tego modułu są importowane do sesji, wraz z modułem. Możesz wyświetlić listę plików tematów pomocy w wartości klucza FileList w manifeście modułu, ale nie dotyczy tematy Pomocy `Export-ModuleMember` polecenia cmdlet.

Możesz podać tematy pomocy modułu w różnych językach. `Get-Help` Polecenie cmdlet automatycznie wyświetla tematy pomocy modułu w języku, który jest określony dla bieżącego użytkownika w elemencie Opcje regionalne i językowe w Panelu sterowania. W systemach Windows Vista i nowszych wersjach systemu Windows `Get-Help` Wyszukuje tematy pomocy podkatalogi specyficzny dla języka katalog modułu zgodnie ze standardami rezerwowego języka dla Windows.

W programie Windows PowerShell 3.0, uruchamianie `Get-Help` polecenia dla polecenia cmdlet lub funkcji wyzwala automatyczne importowanie modułu. `Get-Help` Natychmiast polecenie cmdlet wyświetla zawartość tematów pomocy w module.

Jeśli moduł zawiera tematy pomocy i istnieją tematów pomocy dotyczącej poleceń w module na komputerze użytkownika `Get-Help` Wyświetla Pomoc wygenerowany automatycznie. Wygenerowany automatycznie pomocy zawiera polecenia składni, parametrów i typów wejściowych i wyjściowych, ale nie obejmuje wszystkie opisy. Wygenerowany automatycznie pomocy zawiera tekst, który kieruje użytkownika podjąć próbę użycia `Update-Help` polecenia cmdlet, aby pobrać Pomoc dla polecenia z Internetu lub udziału plików. Ponadto zaleca używanie **Online** parametru `Get-Help` polecenie cmdlet umożliwiające pobranie wersji online tematu Pomocy.

## <a name="supporting-updatable-help"></a>Obsługa aktualizowalnej pomocy

Użytkownicy programu Windows PowerShell 3.0 i nowszych wersjach środowiska Windows PowerShell można pobrać i zainstalować pliki zaktualizowane pomocy dla modułu z Internetu lub udziału pliku lokalnego. `Update-Help` i `Save-Help` poleceń cmdlet ukryć szczegóły zarządzania przez użytkownika. Użytkownicy mogą wykonywać `Update-Help` polecenia cmdlet, a następnie użyj `Get-Help` polecenia cmdlet, aby odczytać najnowszych plików pomocy dla modułu w wierszu polecenia programu Windows PowerShell. Użytkownicy muszą uruchomić system Windows lub programu Windows PowerShell.

Użytkownicy się za zaporami i tych, bez dostępu do Internetu mogą używać aktualizowalnej pomocy, jak również. Administratorzy z Internetu do sterowania dostępem `Save-Help` polecenia cmdlet, aby pobrać i zainstalować najnowszych plików pomocy do udziału plików. Następnie należy użyć użytkowników **ścieżki** parametru `Update-Help` polecenie cmdlet umożliwiające pobranie najnowszych plików pomocy z udziału plików.

Autorzy modułów uwzględnić pliki pomocy w module i za pomocą aktualizowalnej pomocy zaktualizować pliki pomocy lub Pomiń pliki pomocy w module i używać aktualizowalnej pomocy można zainstalować i zaktualizować je.

Aby uzyskać więcej informacji na temat aktualizowalnej pomocy zobacz [Obsługa aktualizowalnej pomocy](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Obsługa pomocy online

Użytkownicy, którzy nie może lub nie należy instalować zaktualizowano pomoc, której pliki na swoich komputerach zależą od często wersję modułu tematy Pomocy online. **Online** parametru `Get-Help` polecenia cmdlet spowoduje otwarcie wersji online polecenia cmdlet lub zaawansowanych funkcji tematu pomocy dla użytkownika w swojej domyślnej przeglądarki internetowej.

`Get-Help` Polecenie cmdlet używa wartości **HelpUri** właściwości polecenia cmdlet lub funkcję, aby znaleźć wersji online tematu Pomocy.

Począwszy od programu Windows PowerShell 3.0, możesz pomóc użytkownikom znajdowanie wersji online tematy pomocy polecenia cmdlet i funkcję, definiując atrybutu HelpUri w klasie polecenia cmdlet lub **HelpUri** właściwość **CmdletBinding** atrybutu. Wartość atrybutu jest wartość **HelpUri** właściwości polecenia cmdlet lub funkcji.

Aby uzyskać więcej informacji, zobacz [Obsługa pomocy Online](./supporting-online-help.md).

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)

[Obsługa aktualizowalnej pomocy](./supporting-updatable-help.md)

[Obsługa pomocy Online](./supporting-online-help.md)