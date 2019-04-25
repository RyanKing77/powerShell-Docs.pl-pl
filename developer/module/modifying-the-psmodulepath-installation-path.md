---
title: Modyfikowanie ścieżki instalacji PSModulePath | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082213"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modyfikowanie ścieżki instalacji PSModulePath

`PSModulePath` Zmiennej środowiskowej przechowuje ścieżki do lokalizacji modułów, które są zainstalowane na dysku. Programu Windows PowerShell korzysta z tej zmiennej do zlokalizowania modułów, gdy użytkownik nie określi Pełna ścieżka do modułu. Ścieżki w tej zmiennej są przeszukiwane w kolejności, w jakiej są wyświetlane.

Po uruchomieniu programu Windows PowerShell `PSModulePath` jest tworzona jako zmienna środowiskowa z następującą wartością domyślną: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Aby wyświetlić zmiennej PSModulePath

Aby wyświetlić ścieżek, które są określone w `PSModulePath` zmiennej, wpisz następujące polecenie:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Aby dodać lokalizacje do zmiennej PSModulePath

Aby dodać ścieżki do zmiennej, użyj jednej z następujących metod:

- Aby dodać wartości tymczasowej, która jest dostępna tylko dla bieżącej sesji, uruchom następujące polecenie w wierszu polecenia:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Aby dodać wartością stałą, która jest dostępna, przy każdym otwarciu sesji, należy dodać następujące polecenie do profilu programu Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Aby uzyskać więcej informacji na temat profilów, zobacz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) w bibliotece Microsoft TechNet.

- Aby dodać zmienną trwałego w rejestrze, Utwórz nową zmienną środowiskową użytkownika o nazwie `PSModulePath` za pomocą edytora zmiennych środowiskowych w **właściwości systemu** okno dialogowe.

- Aby dodać zmienną trwałych, za pomocą skryptu, użyj **setenvironmentvariable nie zawiera** metody w klasie środowiska. Na przykład poniższy skrypt dodaje "C:\Program Files\Fabrikam\Module ścieżkę do wartości zmiennej środowiskowej PSModulePath dla komputera. Aby dodać ścieżkę do zmiennej środowiskowej PSModulePath użytkownika, Ustaw element docelowy "User".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Usuwanie lokalizacji PSModulePath

Możesz usunąć ścieżki ze zmiennej za pomocą metod podobnych: na przykład `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` spowoduje usunięcie **c:\ModulePath** ścieżki z bieżącej sesji.

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
