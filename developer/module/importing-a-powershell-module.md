---
title: Importowanie modułu programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082249"
---
# <a name="importing-a-powershell-module"></a>Importowanie modułu programu PowerShell

Raz sieci został zainstalowany moduł w systemie, prawdopodobnie można zaimportować moduł. Importowanie jest proces, który ładuje moduł do aktywnej pamięci, tak aby użytkownik mógł korzystać z tego modułu, w swojej sesji programu PowerShell. W programie PowerShell 2.0, można zaimportować nowo zainstalowany moduł programu PowerShell przy użyciu wywołania do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet. W środowisku PowerShell 3.0 program PowerShell jest niejawnie zaimportować moduł, gdy funkcje lub poleceń cmdlet w module jest wywoływana przez użytkownika. Należy zauważyć, że obie wersje przyjęto założenie, zainstalować modułu w miejscu, gdzie może znaleźć; jest programu PowerShell Aby uzyskać więcej informacji, zobacz [Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md). Manifest modułu można użyć do ograniczenia, które części modułu są eksportowane i można używać parametrów `Import-Module` wywołanie, aby ograniczyć, jakie części są importowane.

## <a name="importing-a-snap-in-powershell-10"></a>Importowanie przystawki (program PowerShell 1.0)

Moduły nie istnieje w programie PowerShell 1.0: zamiast tego trzeba było rejestrowanie i używanie przystawek. Jednak nie jest zalecane używanie tej technologii w tym momencie moduły są zazwyczaj łatwiejszy, zainstaluj i zaimportuj. Aby uzyskać więcej informacji, zobacz [sposób tworzenia przystawki programu PowerShell Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Zaimportowanie modułu przy użyciu Import-Module (program PowerShell 2.0)

Program PowerShell 2.0 używa odpowiednio o silnych nazwach [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet, aby zaimportować moduły. Po uruchomieniu tego polecenia cmdlet programu Windows PowerShell wyszukuje określonego modułu w katalogach określonych w `PSModulePath` zmiennej. W przypadku odnalezienia określonego katalogu programu Windows PowerShell wyszukuje pliki w następującej kolejności: moduł plików manifestu (psd1), skrypt modułu plików (.psm1), moduł binarne (.dll). Aby uzyskać więcej informacji na temat dodawania katalogi do wyszukiwania, zobacz [Modyfikowanie ścieżki instalacji PSModulePath](./modifying-the-psmodulepath-installation-path.md). W poniższym kodzie opisano jak zaimportować moduł:

```powershell
Import-Module myModule
```

Przy założeniu, że myModule znajdują się na `PSModulePath`, programu PowerShell będzie załadować myModule do aktywnej pamięci. Jeśli myModule nie został umieszczony w `PSModulePath` ścieżki, można nadal jawnie podać PowerShell gdzie można znaleźć go:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Można również użyć - verbose parametr do identyfikowania co to jest eksportowany poza moduł i co to jest importowany do aktywnej pamięci. Eksportów i importów ograniczenia, co jest widoczne dla użytkownika: różnica polega na to, kto jest kontrolowanie widoczności. Zasadniczo eksportu są kontrolowane przez kod w module. Z kolei Importy są kontrolowane przez `Import-Module` wywołania. Aby uzyskać więcej informacji, zobacz **ograniczenie elementów członkowskich, są importowane**poniżej.

## <a name="implicitly-importing-a-module-powershell-30"></a>Niejawnie importowanie modułu (program PowerShell 3.0)

Począwszy od programu Windows PowerShell 3.0 moduły są importowane automatycznie stosowania wszystkie polecenia cmdlet lub funkcja w module za pomocą polecenia. Ta funkcja działa w dowolny moduł, w katalogu, który obejmuje wartości **PSModulePath** zmiennej środowiskowej. Jeśli nie zapiszesz modułu na prawidłową ścieżkę jednak, nadal można ładować je przy użyciu jawne [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opcji opisanych powyżej.

Następujące akcje wyzwalacza automatycznego importowania modułu, znany także jako "moduł automatyczne ładowanie".

- Przy użyciu polecenia cmdlet, za pomocą polecenia. Na przykład wpisanie `Get-ExecutionPolicy` importuje moduł Microsoft.PowerShell.Security, który zawiera `Get-ExecutionPolicy` polecenia cmdlet.

- Za pomocą [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) polecenia cmdlet, aby informacje o poleceniu.  Na przykład wpisanie `Get-Command Get-JobTrigger` importuje **PSScheduledJob** moduł, który zawiera `Get-JobTrigger` polecenia cmdlet. A `Get-Command` polecenia, który zawiera znaki symboli wieloznacznych jest uważany za odnajdywanie i nie będzie wyzwalać importowanie modułu.

- Za pomocą [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, aby uzyskać pomoc dotyczącą polecenia cmdlet. Na przykład wpisanie `Get-Help Get-WinEvent` importuje moduł Microsoft.PowerShell.Diagnostics, który zawiera `Get-WinEvent` polecenia cmdlet.

Aby obsługiwać automatyczne importowanie modułów, `Get-Command` polecenie cmdlet pobiera wszystkie polecenia cmdlet i funkcje we wszystkich modułach zainstalowanych, nawet jeśli moduł nie są importowane do sesji. Aby uzyskać więcej informacji, zobacz temat Pomocy dotyczący [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) polecenia cmdlet.

## <a name="the-importing-process"></a>Proces importowania

Po zaimportowaniu modułu do stanu nowa sesja jest tworzony dla modułu, a [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) tworzony jest obiekt w pamięci. Stan sesji jest tworzony dla każdego modułu, który jest importowany (obejmuje to moduł głównego i wszystkich modułów zagnieżdżone). Elementów członkowskich, które są eksportowane z modułu głównego, w tym wszystkie elementy członkowskie, które zostały wyeksportowane do modułu głównego przez wszelkie zagnieżdżone moduły są następnie importowane do obiektu wywołującego stanu sesji.

Metadane elementów członkowskich, które są eksportowane z modułu ma właściwości ModuleName. Ta właściwość jest wypełniana nazwę modułu, który wyeksportowany je.

> [!WARNING]
> Jeśli nazwa wyeksportowanej składowej używa niezatwierdzonych żądania lub jeśli nazwa elementu członkowskiego używa zastrzeżone znaki, wyświetlane jest ostrzeżenie podczas [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenie cmdlet jest uruchamiane.

Domyślnie [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenie cmdlet nie zwraca żadnych obiektów do potoku. Polecenie cmdlet obsługuje jednak `PassThru` parametr, który może służyć do zwrócenia [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) obiekt dla każdego modułu, który jest importowany. Aby wysłać dane wyjściowe do hosta, należy uruchomić [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) polecenia cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Ograniczanie elementów członkowskich, które są importowane

Po zaimportowaniu modułu przy użyciu [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet, domyślnie wszystkie modułu wyeksportowanego elementy członkowskie są importowane do sesji, dowolnych poleceń tym wyeksportowane do modułu przez moduł zagnieżdżonych. Domyślnie zmienne i aliasy nie są eksportowane. Aby ograniczyć elementów członkowskich, które są eksportowane, należy użyć [manifestu modułu](./how-to-write-a-powershell-module-manifest.md). Aby ograniczyć elementów członkowskich, które są importowane, należy użyć następujących parametrów `Import-Module` polecenia cmdlet.

- `Function`: Ten parametr ogranicza eksportowanych funkcji. (Jeśli używasz manifestu modułu, zobacz klucz FunctionsToExport).

- `Cmdlet`: Ten parametr ogranicza możliwość użycia poleceń cmdlet, które są eksportowane (Jeśli używasz manifestu, zobacz Moduł klucza CmdletsToExport.)

- `Variable`: Ten parametr ogranicza zmiennych, które są eksportowane (Jeśli używasz manifestu, zobacz Moduł klucza VariablesToExport.)

- `Alias`: Ten parametr ogranicza aliasy, które są eksportowane (Jeśli używasz manifestu, zobacz Moduł klucza AliasesToExport.)

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
