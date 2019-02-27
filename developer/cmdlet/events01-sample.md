---
title: Przykładowe Events01 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 3edbcabeff0c8d84831823df11749d152b347566
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851947"
---
# <a name="events01-sample"></a>Przykład Events01

W tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które umożliwia użytkownikowi rejestrowania zdarzeń, które są wywoływane przez [Klasa System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Za pomocą tego polecenia cmdlet użytkownicy będą mogli zarejestrować akcję do wykonania po utworzeniu pliku w określonym katalogu. W tym przykładzie pochodzi z [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasy bazowej.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Jak skompilować przykład za pomocą programu Visual Studio.

1. Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu Events01. Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.

2. Kliknij dwukrotnie ikonę pliku rozwiązania (.sln). Spowoduje to otwarcie z przykładowym projektem w programie Microsoft Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

    Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.

### <a name="how-to-run-the-sample"></a>Jak uruchomić przykład

1. Utwórz następujący folder modułu:

    `[user]/documents/windowspowershell/modules/events01`

2. Skopiuj plik biblioteki, na przykład do folderu modułu.

3. Uruchom program Windows PowerShell.

4. Uruchom następujące polecenie, aby załadować polecenia cmdlet w programie Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Użyj polecenia cmdlet Register-FileSystemEvent zarejestrować akcję, która zapisze komunikat, gdy plik jest tworzony w katalogu TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Utwórz plik w katalogu TEMP i należy pamiętać, że akcja jest wykonywana (zostanie wyświetlony komunikat).

To przykładowe dane wyjściowe, powstałego wykonaj następujące czynności.

```output
Id              Name            State      HasMoreData     Location             Command
--              ----            -----      -----------     --------             -------
1               26932870-d3b... NotStarted False                                 Write-Host "A f...

```

```powershell
Set-Content $env:temp\test.txt "This is a test file"
```

```output
A file was created in the TEMP directory
```

## <a name="requirements"></a>Wymagania

Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.

## <a name="demonstrates"></a>Przedstawiono

W przykładzie pokazano poniżej.

- Jak napisać polecenie cmdlet służące do rejestrowania zdarzeń. Polecenia cmdlet jest pochodną [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasy, która zapewnia obsługę typowych parametrów do Register-* zdarzeń poleceń cmdlet. Polecenia cmdlet, które są uzyskiwane z [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) musi mieć możliwość definiowania ich poszczególnych parametrów i zastąpić `GetSourceObject` i `GetSourceObjectEventName` metody abstrakcyjne.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak zarejestrować zdarzenia wygenerowane przez [Klasa System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)