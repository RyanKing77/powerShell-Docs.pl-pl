---
title: Polecenia cmdlet przykłady | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058049"
---
# <a name="cmdlet-samples"></a>Przykłady poleceń cmdlet

W tej sekcji opisano przykładowy kod, który jest podawany jako zestawu SDK programu Windows PowerShell 2.0. Skopiuj kod z tematy w tej sekcji lub Otwórz pliki źródłowe, instalowane przy użyciu zestawu SDK. [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) zawiera pliki ReadMe, pliki źródłowe i pliki projektu programu Visual Studio dla każdego przykładu. Dzięki zainstalowany zestaw SDK można znaleźć przykłady w obszarze `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folderu.

## <a name="in-this-section"></a>W tej sekcji

[Przykładowe GetProcessSample01](./getprocesssample01-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, które pobiera procesów na komputerze lokalnym.

[Przykładowe GetProcessSample02](./getprocesssample02-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, które pobiera procesów na komputerze lokalnym. Zawiera parametr Name, który może służyć do określenia procesy, które mają zostać pobrane.

[Przykładowe GetProcessSample03](./getprocesssample03-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, które pobiera procesów na komputerze lokalnym. Zawiera parametr Name, który może akceptować wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru lub obiektu z potoku.

[Przykładowe GetProcessSample04](./getprocesssample04-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, które pobiera procesów na komputerze lokalnym. Generuje on niekończące błąd, jeśli wystąpi błąd podczas pobierania procesu.

[Przykładowe GetProcessSample05](./getprocesssample05-sample.md) w tym przykładzie pokazano polecenie cmdlet Get-Proc z pełną wersją.

[Przykładowe StopProcessSample01](./stopprocesssample01-sample.md) ten przykład pokazuje, jak napisać polecenia cmdlet, które żądania opinii od użytkownika, zanim spróbuje zatrzymać proces i jak implementować `PassThru` parametrem, który wskazuje, że użytkownik chce polecenia cmdlet, aby zwrócić obiekt.

[Przykładowe StopProcessSample02](./stopprocesssample02-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, które zapisuje verbose, debug i komunikaty ostrzegawcze podczas zatrzymywania procesów na komputerze lokalnym.

[Przykładowe StopProcessSample03](./stopprocesssample03-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, których parametry mają aliasy i który obsługuje znaki symboli wieloznacznych.

[Przykładowe StopProcessSample04](./stopprocesssample04-sample.md) ten przykład przedstawia sposób zapisania polecenia cmdlet, który deklaruje zestawów parametrów, określa domyślnego parametru zestawu i może akceptować wejściowego obiektu.

[Przykładowe Events01](./events01-sample.md) w tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które umożliwia użytkownikowi zarejestrowanie zdarzenia wygenerowane przez [Klasa System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Za pomocą tego polecenia cmdlet użytkowników na przykład zarejestrować akcję do wykonania po utworzeniu pliku w określonym katalogu. W tym przykładzie pochodzi z [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasy bazowej.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
