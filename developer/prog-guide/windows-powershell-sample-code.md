---
title: Windows PowerShell przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 264e9f7538e13b48d899e87541239250eb88f14e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081210"
---
# <a name="windows-powershell-sample-code"></a>Przykładowy kod programu Windows PowerShell

Windows PowerShell® przykłady są dostępne za pośrednictwem zestawu Windows SDK. Ta sekcja zawiera przykładowy kod, który jest zawarty w przykładowych zestawach Windows SDK.

> [!NOTE]
> Po zainstalowaniu zestawu Windows SDK **przykłady** katalog jest tworzony, w którym są udostępniane wszystkie przykłady środowiska Windows PowerShell. Katalog instalacji standardowej jest **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Uruchom program Windows PowerShell i wpisz **"cd Samples\SysMgmt\PowerShell"** można zlokalizować katalogu przykłady dla programu Windows PowerShell. W tym dokumencie katalogu przykłady dla programu Windows PowerShell jest nazywany  **\<przykłady programu PowerShell >**.

## <a name="sample-code-listing"></a>Lista przykładowego kodu

|Przykładowy kod|Opis|
|-----------------|-----------------|
|[Przykładowy kod AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Jest to dostawca opisanego w [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md).|
|[Przykładowy kod AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Jest to dostawca opisanego w [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Przykładowy kod AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Jest to dostawca opisanego w [tworzenia dostawcy usługi Windows PowerShell elementu](./creating-a-windows-powershell-item-provider.md).|
|[Przykładowy kod AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Jest to dostawca opisanego w [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Przykładowy kod AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Jest to dostawca opisanego w [tworzenia dostawcy usługi Windows PowerShell nawigacji](./creating-a-windows-powershell-navigation-provider.md).|
|[Przykładowy kod AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Jest to dostawca opisanego w [Tworzenie dostawcy zawartości programu PowerShell Windows](./creating-a-windows-powershell-content-provider.md).|
|[Przykłady kodu GetProc01](./getproc01-code-samples.md)|Jest to podstawowa `Get-Process` przykładowe polecenia cmdlet opisane w [tworzenia Your pierwsze polecenie Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Przykłady kodu GetProc02](./getproc02-code-samples.md)|Jest to `Get-Process` przykładowe polecenia cmdlet opisane w [dodając parametry te dane wejściowe wiersza polecenia procesu](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Przykłady kodu GetProc03](./getproc03-code-samples.md)|Jest to `Get-Process` przykładowe polecenia cmdlet opisane w [dodając parametry tego procesu wejście potokowe](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Przykłady kodu GetProc04](./getproc04-code-samples.md)|Jest to `Get-Process` przykładowe polecenia cmdlet opisane w [Dodawanie niekończące raportowania z błędów, do polecenia Cmdlet usługi](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Przykłady kodu GetProc05](./getproc05-code-samples.md)|To `Get-Process` polecenie cmdlet jest podobne do polecenia cmdlet opisane w [Dodawanie niekończące raportowania z błędów, do polecenia Cmdlet usługi](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Przykłady kodu StopProc01](./stopproc01-code-samples.md)|Jest to `Stop-Process` przykładowe polecenia cmdlet opisane w [tworzenia polecenia Cmdlet, modyfikuje System](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Przykłady kodu StopProcessSample04](./stopprocesssample04-code-samples.md)|Jest to `Stop-Process` przykładowe polecenia cmdlet opisane w [dodanie zestawów parametrów do polecenia Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Przykłady kodu Runspace01](./runspace01-code-samples.md)|Oto przykłady kodu dla obszaru działania opisane w [tworzenia działa konsola aplikacji czy określone polecenie](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).|
|[Przykłady kodu Runspace02](./runspace02-code-samples.md)|W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy w celu wykonania `Get-Process` polecenia cmdlet synchronicznie.|
|[Przykłady kodu RunSpace03](./runspace03-code-samples.md)|Oto przykłady kodu dla obszaru działania opisane w [tworzenia działa konsola aplikacji czy określony skrypt](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).|
|[Przykłady kodu RunSpace04](./runspace04-code-samples.md)|To jest przykładowy kod dla obszaru działania, który używa [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który generuje błąd powodujący zakończenie.|
|[Przykładowy kod RunSpace05](./runspace05-code-sample.md)|To kod źródłowy przykładowej Runspace05 opisanego w [konfigurowania obszaru działania przy użyciu RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Przykładowy kod RunSpace06](./runspace06-code-sample.md)|To kod źródłowy przykładowej Runspace06 opisanego w [konfigurowania obszaru działania, za pomocą przystawki programu PowerShell Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Przykładowy kod RunSpace07](./runspace07-code-sample.md)|To kod źródłowy przykładowej Runspace07 opisanego w [tworzenia aplikacji, dodaje poleceń konsoli dla potoku](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Przykładowy kod RunSpace08](./runspace08-code-sample.md)|To kod źródłowy przykładowej Runspace08 opisanego w [tworzyć konsoli aplikacji, dodaje parametry do polecenia](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Przykładowy kod RunSpace09](./runspace09-code-sample.md)|To kod źródłowy przykładowej Runspace09 opisanego w [tworzenia konsoli aplikacji, wywołuje potok asynchronicznie](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Przykładowy kod RunSpace10](./runspace10-code-sample.md)|Jest to kod źródłowy przykładowej Runspace10, który dodaje polecenia cmdlet, aby [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) , a następnie używa informacji o modyfikacji konfiguracji do utworzenia obszaru działania.|

## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)