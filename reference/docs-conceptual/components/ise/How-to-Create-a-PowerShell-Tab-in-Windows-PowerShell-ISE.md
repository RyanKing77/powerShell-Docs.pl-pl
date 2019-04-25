---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057744"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE

Karty w Windows PowerShell zintegrowane Scripting Environment (ISE) umożliwiają jednoczesne tworzenie i używanie kilku środowiskach wykonawczych w tej samej aplikacji.
Każda karta środowiska PowerShell odnosi się do środowiska wykonawczego oddzielne lub sesji.

> [!NOTE]
> Zmienne, funkcje i aliasy, które tworzysz w jednej karty nie jest przenoszone do innego. Są one różne sesje środowiska Windows PowerShell.

Wykonaj następujące kroki, aby otworzyć lub zamknąć kartę w programie Windows PowerShell.
Aby zmienić nazwę karty, należy ustawić [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) właściwości w obiekcie skryptów programu Windows PowerShell kartę.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Aby utworzyć nową kartę programu PowerShell

Na **pliku** menu, kliknij przycisk **Nowa karta programu PowerShell**. Jako aktywne okno zawsze zostanie otwarta nowa karta programu PowerShell.
Karty programu PowerShell przyrostowe są ponumerowane w kolejności ich otworzyć.
Każda karta jest skojarzony z własnego okna konsoli programu Windows PowerShell.
Może mieć maksymalnie 32 kart programu PowerShell za pomocą ich własnych sesji, które są otwarte w czasie (to jest ograniczony do 8 w wersji 2.0 programu Windows PowerShell ISE).

Należy pamiętać, że kliknięcie **New** lub **Otwórz** ikony na pasku narzędzi nie tworzy nową kartę z oddzielną sesję.
Te przyciski otwierać plik skryptu nowej lub istniejącej karty aktualnie aktywne w sesji.
Może mieć wiele skryptu, który pliki otwierane z każdej karty i sesji.
Karty skryptu dla sesji są wyświetlone poniżej karty sesji tylko wtedy, gdy skojarzona sesja jest aktywny.

Aby uaktywnić kartę programu PowerShell, kliknij kartę. Aby dokonać wyboru spośród wszystkich kart programu PowerShell, które są otwarte, w **widoku** menu, kliknij kartę programu PowerShell, którego chcesz użyć.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Tworzenie i używanie na nowej karcie zdalnego programu PowerShell

Na **pliku** menu, kliknij przycisk **Nowa karta programu PowerShell zdalnego** nawiązać sesji na komputerze zdalnym.
Okno dialogowe pojawia się i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.
Funkcje karty zdalny podobnie jak lokalne kartę programu PowerShell, ale polecenia i skrypty są uruchamiane na komputerze zdalnym.

## <a name="to-close-a-powershell-tab"></a>Aby zamknąć kartę programu PowerShell

Aby zamknąć kartę, można użyć dowolnego z następujących technik:

- Kliknij kartę która ma zostać zamknięte.

- Na **pliku** menu, kliknij przycisk **Zamknij kartę programu PowerShell**, lub kliknij przycisk Zamknij (**X**) w aktywnej karcie, aby zamknąć kartę.

Jeśli istnieją niezapisane pliki otwarte w kartę programu PowerShell, że zamykasz, zostanie wyświetlony monit o zapisać lub odrzucić je.
Aby uzyskać więcej informacji na temat zapisywania skryptu, zobacz [jak zapisać skrypt](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Jak używać okienka konsoli w środowisku Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)