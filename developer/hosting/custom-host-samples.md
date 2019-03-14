---
title: Przykłady niestandardowego hosta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794148"
---
# <a name="custom-host-samples"></a>Przykłady hosta niestandardowego

Ta sekcja zawiera przykładowy kod do pisania niestandardowego hosta. Microsoft Visual Studio umożliwia tworzenie aplikacji konsolowej, a następnie skopiować kod z tematy w tej sekcji, w aplikacji hosta.

## <a name="in-this-section"></a>W tej sekcji

 [Przykładowe Host01](./host01-sample.md) ten przykład pokazuje sposób implementacji aplikacji hosta, która używa podstawowe niestandardowego hosta.

 [Przykładowe Host02](./host02-sample.md) w tym przykładzie pokazano, jak napisać aplikację hosta, która używa środowiska wykonawczego programu Windows PowerShell, oraz implementacji niestandardowego hosta. Aplikacja hosta ustawia kulturę hosta na język niemiecki, przebiegów [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet i wyświetla wynik jako użytkownik je zobaczy przy użyciu pwrsh.exe, a następnie Drukuje bieżące data i godzina w języku niemieckim.

 [Przykładowe Host03](./host03-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.

 [Przykładowe Host04](./host04-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikom określić wiele opcji do wyboru.

 [Przykładowe Host05](./host05-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ta aplikacja hosta obsługuje również połączenia z komputerami zdalnymi przy użyciu [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) i [PsSession zakończenia](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) poleceń cmdlet

 [Przykładowe Host06](./host06-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu, wprowadzonej przez użytkownika.

## <a name="see-also"></a>Zobacz też
