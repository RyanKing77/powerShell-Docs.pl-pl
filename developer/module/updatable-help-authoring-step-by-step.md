---
title: 'Tworzenie aktualizowalnej pomocy: Instrukcje krok po kroku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082128"
---
# <a name="updatable-help-authoring-step-by-step"></a>Tworzenie aktualizowalnej pomocy: instrukcje krok po kroku

Dokumenty ten zawiera listę czynności w procesie tworzenia aktualizowalnej pomocy.

## <a name="authoring-updatable-help-step-by-step"></a>Tworzenie aktualizowalnej pomocy: instrukcje krok po kroku

Aktualizowalnej pomocy jest przeznaczona dla użytkowników końcowych, ale również zapewnia znaczące korzyści związane autorzy modułów i moduły zapisujące pomocy, w tym możliwość dodawania zawartości, napraw błędy, dostarczania w wielu kulturach interfejsu użytkownika i odpowiadać na komentarze użytkowników dotyczące i żądań, po jakim Moduł zostało wysłane. W tym temacie wyjaśniono, jak spakować i pomocy przekazywania plików dzięki czemu użytkownicy mogą pobierać i zainstalować je przy użyciu [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) polecenia cmdlet.

W poniższych krokach przedstawiono przegląd procesu obsługi aktualizowalnej pomocy.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Krok 1. Znajdź w witrynie internetowej plików pomocy

Pierwszym krokiem w tworzeniu aktualizowalnej pomocy jest można znaleźć lokalizacji internetowej plików pomocy z modułu. W rzeczywistości można użyć dwóch różnych lokalizacjach. Plik informacji o pomocy usługi modułu (HelpInfo XML - opisanych poniżej) można przechowywać w jednej lokalizacji w Internecie i zawartości pliku CAB pliki pomocy w innej lokalizacji w Internecie. Wszystkie zawartości pliku CAB pliki pomocy dla modułu musi być w tej samej lokalizacji. Pliki zawartości pliku CAB pomocy dla różnych modułów można umieścić w tej samej lokalizacji.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Krok 2. Dodaj klucz HelpInfoURI do pliku z manifestu modułu

Dodaj **HelpInfoURI** klucza w manifeście modułu. Wartość klucza jest jednolity identyfikator zasobów (URI) lokalizacji pliku informacji HelpInfo XML dla modułu. Dla bezpieczeństwa adres musi rozpoczynać się od "http" lub "https". Identyfikator URI powinien określać lokalizacji internetowej, ale nie mogą zawierać nazwę pliku HelpInfo XML.

Przykład:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Krok 3. Utwórz plik HelpInfo XML

Plik informacji HelpInfo XML zawierający identyfikator URI lokalizacji Internet pliki pomocy i numery wersji najnowszych plików pomocy dla modułu w każdej obsługiwanej kultury interfejsu użytkownika. Każdy moduł programu Windows PowerShell ma jeden plik HelpInfo XML. Po zaktualizowaniu plików pomocy, edytować lub zamienić plik HelpInfo XML; nie należy dodawać inny. Aby uzyskać więcej informacji, zobacz [jak utworzyć plik XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Krok 4: Zarejestruj swoje pliki pomocy

Podpisy cyfrowe nie są wymagane, ale są one rekomendacji najlepszych zawsze wtedy, gdy udostępniasz pliki.

### <a name="step-5-create-cab-files"></a>Krok 5: Tworzenie plików CAB

Narzędzie tworzy pliki cabinet (cab), takie jak MakeCab.exe do utworzenia. Plik CAB, który zawiera pliki pomocy dla modułu. Utwórz osobny plik CAB dla plików pomocy w każdej obsługiwanej kultury interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak przygotować aktualizowalnej pomocy pliki CAB](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Krok 6: Przekazywanie plików

Aby opublikować pliki pomocy nowych lub zaktualizowanych, przekazać pliki CAB do lokalizacji internetowej, który jest określony przez **HelpContentUri** elementu w pliku HelpInfo XML. Następnie przekaż plik HelpInfo XML do lokalizacji internetowej, który jest określony przez wartość **HelpInfoUri** klucza w manifeście modułu.
