---
title: Ładowanie i eksportowanie danych formatowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 08c64d4094d8ba6c551b454887331666f0694f11
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850050"
---
# <a name="loading-and-exporting-formatting-data"></a>Ładowanie i eksportowanie danych formatowania

Po utworzeniu pliku formatowania, należy zaktualizować dane formatu sesji przez ładowanie plików do bieżącej sesji. (Pliki formatowania dostarczane przez środowisko Windows PowerShell są ładowane przez przystawki, które są zarejestrowane podczas bieżącej sesji). Po zaktualizowaniu dane formatu w bieżącej sesji, programu Windows PowerShell używa tych danych, aby wyświetlić obiekty .NET skojarzony z widoki zdefiniowane w plikach formatowania załadowane. Nie ma żadnego limitu liczby plików formatowania, które można załadować do bieżącej sesji. Oprócz aktualizowanie formatowania danych, możesz wyeksportować dane formatu w bieżącej sesji, wróć do pliku formatowania.

## <a name="loading-format-data"></a>Trwa ładowanie format danych

Pliki formatowania mogą zostać załadowane do bieżącej sesji przy użyciu następujących metod:

- Można zaimportować plik formatowania, do bieżącej sesji, z poziomu wiersza polecenia. Użyj [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet, zgodnie z opisem w poniższej procedurze.
- Można zaimportować plik formatowania, do bieżącej sesji, z poziomu wiersza polecenia. Użyj [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet, zgodnie z opisem w poniższej procedurze.

- Można utworzyć manifestu modułu, który odwołuje się do pliku formatowania. Moduły umożliwiają możesz formatowanie plików do dystrybucji pakietu. Użyj [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) polecenia cmdlet, aby utworzyć manifest, a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet, aby załadować moduł do bieżącej sesji. Aby uzyskać więcej informacji na temat modułów, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).
- Można utworzyć manifestu modułu, który odwołuje się do pliku formatowania. Moduły umożliwiają możesz formatowanie plików do dystrybucji pakietu. Użyj [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) polecenia cmdlet, aby utworzyć manifest, a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet, aby załadować moduł do bieżącej sesji. Aby uzyskać więcej informacji na temat modułów, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Można utworzyć przystawki, który odwołuje się do pliku formatowania. Użyj [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) k odkazu formatowania plików. Jest to zdecydowanie zaleca się korzystanie z modułów, poleceń cmdlet pakietu i formatowanie skojarzone oraz typy plików do dystrybucji. Aby uzyskać więcej informacji na temat modułów, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Jeśli są programowane wywoływania poleceń, możesz dodać formatowania wpis pliku, aby stan sesji początkowej obszaru działania, w której polecenia są uruchamiane. Aby uzyskać więcej informacji o typ architektury .NET umożliwia dodanie formatowaniu pliku, zobacz [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) klasy.

Po załadowaniu pliku formatowania go do wewnętrznej listy jest dodawany, że używa programu Windows PowerShell, aby określić, którego widoku używany podczas wyświetlania obiektów w wierszu polecenia. Można poprzedzić formatowania pliku na początku listy, lub dołącz go na końcu listy. Wiedząc, gdzie formatowania plik zostanie dodany do tej listy jest ważne, jeśli są ładowane formatowania pliku, który definiuje widoku dla obiektu, który został zdefiniowany, np. Jeśli chcesz zmienić, jak obiekt, który jest zwracany przez polecenie cmdlet programu Windows PowerShell core to istniejącemu widokowi  wyświetlane. Jeśli są ładowane formatowania pliku, który definiuje Wyświetl tylko dla obiektu, można użyć dowolnej z metod opisanych powyżej.  Jeśli są ładowane formatowania pliku, który definiuje innego widoku dla obiektu, należy użyć [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet i Dodaj plik do początku listy.
Po załadowaniu pliku formatowania go do wewnętrznej listy jest dodawany, że używa programu Windows PowerShell, aby określić, którego widoku używany podczas wyświetlania obiektów w wierszu polecenia. Można poprzedzić formatowania pliku na początku listy, lub dołącz go na końcu listy. Wiedząc, gdzie formatowania plik zostanie dodany do tej listy jest ważne, jeśli są ładowane formatowania pliku, który definiuje widoku dla obiektu, który został zdefiniowany, np. Jeśli chcesz zmienić, jak obiekt, który jest zwracany przez polecenie cmdlet programu Windows PowerShell core to istniejącemu widokowi  wyświetlane. Jeśli są ładowane formatowania pliku, który definiuje Wyświetl tylko dla obiektu, można użyć dowolnej z metod opisanych powyżej.  Jeśli są ładowane formatowania pliku, który definiuje innego widoku dla obiektu, należy użyć [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet i Dodaj plik do początku listy.

## <a name="storing-your-formatting-file"></a>Plik formatowania

Nie jest wymagane do przechowywania plików formatowania na dysku. Zaleca się jednak przechowywać je w następującym folderze: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Podczas ładowania pliku formatu przy użyciu klasy FormatData importu

1. Store formatowania pliku na dysku.

2. Uruchom [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) przy użyciu jednej z następujących poleceń cmdlet.
2. Uruchom [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) przy użyciu jednej z następujących poleceń cmdlet.

   Aby dodać format odpowiadający ustawieniom lokalnym pliku na początku listy, użyj tego polecenia. Użyj tego polecenia, w przypadku zmiany sposobu wyświetlania obiektu.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Aby dodać format odpowiadający ustawieniom lokalnym plik na końcu listy, użyj tego polecenia.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Po dodaniu pliku przy użyciu [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet, nie można usunąć go z listy podczas sesji jest otwarty. Należy zamknąć sesję Aby usunąć plik formatowania z listy.
   Po dodaniu pliku przy użyciu [klasy FormatData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) polecenia cmdlet, nie można usunąć go z listy podczas sesji jest otwarty. Należy zamknąć sesję Aby usunąć plik formatowania z listy.

## <a name="exporting-format-data"></a>Eksportowanie danych z formatu

Tutaj wstaw treść sekcji.
