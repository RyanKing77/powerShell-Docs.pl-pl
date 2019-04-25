---
title: Nazwy plików pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082185"
---
# <a name="naming-help-files"></a>Nadawanie nazw plikom pomocy

W tym temacie wyjaśniono, jak nazwa pliku pomocy opartych na języku XML, aby [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, mogą ją odnaleźć. Wymagania dotyczące nazw różnią się dla każdego typu polecenia.

## <a name="cmdlet-help-files"></a>Pliki pomocy dotyczącej poleceń cmdlet

W pliku Pomocy C# polecenia cmdlet, musi nosić nazwę zestawu, w którym zdefiniowano polecenia cmdlet. Użyj następującego formatu nazwy pliku:

```
<AssemblyName>.dll-help.xml
```

Format nazwy zestawu jest wymagana, nawet wtedy, gdy zestaw jest zagnieżdżony moduł.

Na przykład [polecenia Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) polecenia cmdlet jest zdefiniowany w zestawie Microsoft.PowerShell.Diagnostics.dll. `Get-Help` Polecenie cmdlet wyszukuje utworzenia tematu Pomocy dotyczącego `Get-WinEvent` polecenia cmdlet tylko w pliku Microsoft.PowerShell.Diagnostics.dll help.xml w katalogu modułu.

## <a name="provider-help-files"></a>Pliki pomocy dostawcy

Dostawca programu Windows PowerShell można znaleźć w pliku pomocy musi mieć nazwę zestawu, w którym zdefiniowano dostawcy. Użyj następującego formatu nazwy pliku:

```
<AssemblyName>.dll-help.xml
```

Format nazwy zestawu jest wymagana, nawet wtedy, gdy zestaw jest zagnieżdżony moduł.

Na przykład dostawca certyfikatów jest zdefiniowany w zestawie Microsoft.PowerShell.Security.dll. `Get-Help` Polecenie cmdlet wyszukuje tematu pomocy dla dostawcy certyfikat tylko w pliku Microsoft.PowerShell.Security.dll help.xml w katalogu modułu.

## <a name="function-help-files"></a>Pliki Pomocy — funkcja

Funkcje mogą być udokumentowane przy użyciu [Pomoc oparta na komentarzach](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) lub zamieszczone w pliku pomocy XML. Gdy funkcja jest udokumentowany w pliku XML, funkcja musi mieć `.ExternalHelp` komentarz — słowo kluczowe, które kojarzy funkcji z pliku XML. W przeciwnym razie `Get-Help` polecenie cmdlet nie można odnaleźć pliku pomocy.

Nie istnieją wymagania techniczne dla nazwy pliku pomocy funkcji. Jednak najlepszym rozwiązaniem jest nazwa pliku pomocy dla modułu skryptów, w którym zdefiniowano funkcji. Na przykład następująca funkcja jest zdefiniowana w pliku Mójmoduł.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Pliki pomocy poleceń CIM

Plik pomocy dla poleceń CIM, musi mieć nazwę dla pliku CDXML, w którym zdefiniowano polecenia modelu wspólnych informacji. Użyj następującego formatu nazwy pliku:

```
<FileName>.cdxml-help.xml
```

CIM polecenia są definiowane w plików CDXML, które mogły zostać uwzględnione w modułach jako moduły zagnieżdżonych. Gdy polecenie modelu wspólnych informacji są importowane do sesji jako funkcja, programu Windows PowerShell dodaje `.ExternalHelp` komentarz — słowo kluczowe do definicji funkcji, które kojarzy funkcji przy pomocy XML pliku, który nosi nazwę pliku CDXML, w którym zdefiniowano polecenia modelu wspólnych informacji.

## <a name="script-workflow-help-files"></a>Pliki pomocy przepływu pracy skryptu

Skryptowymi przepływami pracy, które są uwzględnione w modułach mogą udokumentowane w plikach pomocy opartych na języku XML. Nie istnieją wymagania techniczne dla nazwy pliku pomocy. Jednak najlepszym rozwiązaniem jest nazwa pliku pomocy dla modułu skryptów, w którym zdefiniowano skryptowego przepływu pracy. Przykład:

```
<ScriptModule>.psm1-help.xml
```

W przeciwieństwie do innych poleceń przy użyciu skryptu, nie wymagają skryptowymi przepływami pracy `.ExternalHelp` komentarz — słowo kluczowe, aby skojarzyć je z pliku pomocy. Zamiast tego programu Windows PowerShell przeszukuje podkatalogów interfejsu użytkownika specyficznych dla kultury katalog modułu plików pomocy opartych na języku XML, a szuka pomocy dla skryptowego przepływu pracy we wszystkich plikach. `.ExternalHelp` komentarz — słowo kluczowe są ignorowane.

Ponieważ `.ExternalHelp` — słowo kluczowe komentarza jest ignorowane, `Get-Help` polecenia cmdlet można znaleźć pomoc skryptowymi przepływami pracy tylko wtedy, gdy są one uwzględnione w modułach.