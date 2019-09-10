---
title: Przykładowy kod programu Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847998"
---
# <a name="windows-powershell-sample-code"></a>Przykładowy kod programu Windows PowerShell

Przykłady® środowiska Windows PowerShell są dostępne za pomocą Windows SDK. Ta sekcja zawiera przykładowy kod, który znajduje się w przykładach Windows SDK.

> [!NOTE]
> Po zainstalowaniu Windows SDK zostanie utworzony katalog **Samples** , w którym zostaną udostępnione wszystkie przykłady programu Windows PowerShell. Typowy katalog instalacji to **C:\Program Files\Microsoft SDKs\Windows\v6.0**.
> Uruchom program Windows PowerShell i wpisz **"CD Samples\SysMgmt\PowerShell"** , aby zlokalizować katalog przykładów programu Windows PowerShell. W tym dokumencie katalog przykładów programu Windows PowerShell jest określany jako  **\<przykłady dla programu PowerShell >** .

## <a name="sample-code-listing"></a>Przykładowa lista kodu

|Przykładowy kod|Opis|
|-----------------|-----------------|
|[Przykład kodu AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie podstawowego dostawcy środowiska Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).|
|[Przykład kodu AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie dostawcy dysku programu Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Przykład kodu AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie dostawcy elementów środowiska Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[Przykład kodu AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie dostawcy kontenera programu Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Przykład kodu AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie dostawcy nawigacji programu Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[Przykład kodu AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Jest to dostawca opisany w temacie [Tworzenie dostawcy zawartości środowiska Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Przykłady kodu GetProc01](./getproc01-code-samples.md)|Jest to podstawowy `Get-Process` przykład polecenia cmdlet opisany podczas [tworzenia pierwszego polecenia cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Przykłady kodu GetProc02](./getproc02-code-samples.md)|Jest `Get-Process` to przykład polecenia cmdlet opisany w temacie [Dodawanie parametrów, które przetwarzają dane wejściowe wiersza polecenia](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Przykłady kodu GetProc03](./getproc03-code-samples.md)|Jest `Get-Process` to przykład polecenia cmdlet opisany w temacie [Dodawanie parametrów, które przetwarzają dane wejściowe potoku](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Przykłady kodu GetProc04](./getproc04-code-samples.md)|Jest `Get-Process` to przykład polecenia cmdlet opisany w temacie [Dodawanie niekończącego raportowania błędów do polecenia cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Przykłady kodu GetProc05](./getproc05-code-samples.md)|To `Get-Process` polecenie cmdlet jest podobne do polecenia cmdlet opisanego w temacie [Dodawanie niekończącego raportowania błędów do polecenia cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Przykłady kodu StopProc01](./stopproc01-code-samples.md)|Jest `Stop-Process` to przykład polecenia cmdlet opisany w temacie [Tworzenie polecenia cmdlet modyfikującego system](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Przykłady kodu StopProcessSample04](./stopprocesssample04-code-samples.md)|Jest `Stop-Process` to przykład polecenia cmdlet opisany w temacie [Dodawanie zestawów parametrów do polecenia cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Przykłady kodu Runspace01](./runspace01-code-samples.md)|Są to przykłady kodu dla obszaru działania opisanego w temacie [Tworzenie aplikacji konsolowej, która uruchamia określone polecenie](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Przykłady kodu Runspace02](./runspace02-code-samples.md)|Ten przykład używa klasy [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) , aby wykonać `Get-Process` polecenie cmdlet synchronicznie.|
|[Przykłady kodu RunSpace03](./runspace03-code-samples.md)|Są to przykłady kodu dla obszaru działania opisanego w temacie "Tworzenie aplikacji konsolowej, która uruchamia określony skrypt".|
|[Przykłady kodu RunSpace04](./runspace04-code-samples.md)|Jest to przykładowy kod dla obszaru działania, który używa klasy [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) do wykonywania skryptu generującego błąd powodujący przerwanie.|
|[Przykład kodu RunSpace05](./runspace05-code-sample.md)|Jest to kod źródłowy dla przykładu Runspace05 opisanego w temacie [Konfigurowanie obszaru działania przy użyciu RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Przykład kodu RunSpace06](./runspace06-code-sample.md)|Jest to kod źródłowy dla przykładu Runspace06 opisanego w temacie [Konfigurowanie obszaru działania przy użyciu przystawki programu Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Przykład kodu RunSpace07](./runspace07-code-sample.md)|Jest to kod źródłowy dla przykładu Runspace07 opisany w temacie [Tworzenie aplikacji konsolowej, która dodaje polecenia do potoku](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Przykład kodu RunSpace08](./runspace08-code-sample.md)|Jest to kod źródłowy dla przykładu Runspace08 opisany w temacie [Tworzenie aplikacji konsolowej, która dodaje parametry do polecenia](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Przykład kodu RunSpace09](./runspace09-code-sample.md)|Jest to kod źródłowy dla przykładu Runspace09 opisany w temacie [Tworzenie aplikacji konsolowej, która wywołuje potok asynchronicznie](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Przykład kodu RunSpace10](./runspace10-code-sample.md)|Jest to kod źródłowy przykładu Runspace10, który dodaje polecenie cmdlet do [System. Management. Automation. obszarami działania. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) , a następnie używa zmodyfikowanych informacji o konfiguracji do utworzenia obszaru działania.|

## <a name="see-also"></a>Zobacz też

[Przewodnik programisty programu Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)