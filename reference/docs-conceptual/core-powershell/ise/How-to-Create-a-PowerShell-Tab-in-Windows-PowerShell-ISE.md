---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE

Karty w Windows PowerShell Integrated Scripting Environment (ISE) umożliwiają jednoczesne tworzenie i używanie kilku środowiskach wykonywania w tej samej aplikacji.
Każdej karcie PowerShell odnosi się do środowiska wykonawczego oddzielne lub sesję.

> **UWAGA**:
>
> Zmienne, funkcje i aliasy, które możesz utworzyć w jednej karty nie jest przenoszone do innego. Są one różnych sesjach programu Windows PowerShell.

Wykonaj następujące kroki, aby otworzyć lub zamknąć kartę w programie Windows PowerShell.
Aby zmienić nazwę karty, ustaw [DisplayName](The-PowerShellTab-Object.md#displayname) właściwości w obiekcie skryptów Windows PowerShell kartę.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Tworzenie i używanie na nowej karcie środowiska PowerShell

Na **pliku** menu, kliknij przycisk **nową kartę PowerShell**. Nowa karta programu PowerShell zawsze otwierany jako aktywne okno.
Karty PowerShell przyrostowo są numerowane w kolejności, że są otwarte.
Każda karta jest skojarzony z osobnym oknie konsoli środowiska Windows PowerShell.
Może mieć maksymalnie 32 kart programu PowerShell za pomocą ich własnych sesji otwarte w czasie (to jest ograniczone do 8 w programie Windows PowerShell ISE 2.0).

Należy pamiętać, że kliknięcie pozycji **nowy** lub **Otwórz** ikon na pasku narzędzi nie powoduje utworzenia nowej karty w oddzielnym sesji.
Zamiast tego tych przycisków Otwieranie pliku skryptu nowego lub istniejącego na karcie aktualnie aktywne w sesji.
Może mieć wiele skryptów, plików otwartych z każdej karcie i sesji.
Karty skryptu dla sesji są wyświetlone poniżej karty sesji tylko, gdy skojarzona sesja jest aktywny.

Aby uaktywnić kartę programu PowerShell, kliknij kartę. Aby dokonać wyboru spośród wszystkich kart programu PowerShell, które są otwarte na **widoku** menu, kliknij kartę programu PowerShell, którego chcesz użyć.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Tworzenie i używanie na nowej karcie zdalnego programu PowerShell

Na **pliku** menu, kliknij przycisk **nową kartę zdalne programu PowerShell** ustanowienie sesji na komputerze zdalnym.
Okno dialogowe zostanie wyświetlone i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.
Funkcje zdalnego kartę podobnie jak lokalny kartę programu PowerShell, ale poleceń i skryptów są uruchamiane na komputerze zdalnym.

## <a name="to-close-a-powershell-tab"></a>Aby zamknąć kartę programu PowerShell

Aby zamknąć kartę, można użyć dowolnego z poniższych:

- Kliknij kartę, która ma zostać zamknięte.

- Na **pliku** menu, kliknij przycisk **zamknąć kartę PowerShell**, lub kliknij przycisk Zamknij (**X**) na aktywną kartę, aby zamknąć kartę.

Jeśli istnieją niezapisane pliki otwarte w karcie programu PowerShell, że zamykasz, zostanie wyświetlony monit o Zapisz lub Odrzuć je.
Aby uzyskać więcej informacji na temat zapisywania skryptu, zobacz [jak zapisać skrypt](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Jak używać okienku konsoli w środowisku Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)