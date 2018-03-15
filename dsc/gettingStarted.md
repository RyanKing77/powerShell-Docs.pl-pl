---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Wprowadzenie do programu PowerShell Konfiguracja żądanego stanu"
ms.openlocfilehash: 04404696bef128805e4f1c191711eaab33cf7e4c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>Wprowadzenie do programu PowerShell Konfiguracja żądanego stanu #

W tym przewodniku opisano, jak rozpocząć tworzenie dokumentów konfiguracji żądanego stanu środowiska PowerShell i zastosować je do maszyny. Zakłada się znajomość podstawowych poleceń cmdlet programu PowerShell, moduły i funkcje. 


## <a name="create-a-configuration"></a>Tworzenie konfiguracji ##

[**Konfiguracje** ](https://msdn.microsoft.com/powershell/dsc/configurations) dokumentów, które opisują środowiska. Środowiskach składają się z "**węzłów**", które są często maszyn wirtualnych lub fizycznych. 

Konfiguracje mogą mieć różne formy. Najprostszym sposobem tworzenia nowej konfiguracji jest tworzenie pliku .ps1 (skrypt programu PowerShell). Aby to zrobić, Otwórz Edytor wybór. PowerShell ISE jest dobrym rozwiązaniem, ponieważ rozumie DSC natywnie. Zapisz poniższy jako PS1:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a>Elementy konfiguracji ##
**Konfiguracja** jest słowem kluczowym, który został dodany do programu PowerShell 4.0. Oznacza on specjalny rodzaj funkcji programu PowerShell używanego przez konfiguracji żądanego stanu. W tym przykładzie funkcja nosi nazwę myFirstConfiguration. 

Następnego wiersza jest instrukcję import, podobnie jak importowanie modułu. Będzie można omówione później.

"Węzeł" definiuje nazwę komputera, które będą działać tej konfiguracji. Chociaż ta konfiguracja jest edytowany lokalnie, konfiguracje mogą dotrzeć do zdalnego węzłów i skonfigurować je. 

Węzły mogą być nazwy komputerów lub adresy IP. Może mieć wiele węzłów w dokumencie pojedynczą konfiguracją. Przy użyciu [dane konfiguracji](https://msdn.microsoft.com/powershell/dsc/configdata), może także zawierać taką samą konfigurację dotyczą wiele węzłów. W takim przypadku ten węzeł jest "localhost" — co oznacza komputera lokalnego. 

Następny element jest [ **zasobów**](https://msdn.microsoft.com/powershell/dsc/resources). Zasoby są blokami konstrukcyjnymi konfiguracji. Każdy zasób jest moduł, który definiuje implementację logiki jeden aspekt maszyny. Na tym komputerze można wyświetlić wszystkich zasobów, uruchamiając **Get-DscResource** w programie PowerShell. Zasoby musi znajdować się na komputerze lokalnym i zaimportować przed ich użyciem w elemencie configuration z **DscResource importu** czyli w drugim wierszu tej konfiguracji. 

**Wprowadzania konfiguracji**

Jeśli skrypt powyżej jest zapisany i uruchom, nie zostaną zwrócone żadne dane wyjściowe. Jest tak, ponieważ konfiguracja jest tylko funkcji, a skrypt powyżej zdefiniował funkcji, ale nie zostały jeszcze ją uruchomić. Po zdefiniowaniu funkcji muszą być wywoływane:
```powershell
myFirstConfiguration
```

Po wykonaniu konfiguracji funkcji sprawdzania poprawności konfiguracji jest nieprawidłowy. Nie powinien mieć go ma błędów składni, zasobów musi mieć wszystkie obowiązkowe parametry zdefiniowany i wszystkie zasoby, które należy zaimportować przed realizacją.

Po wykonaniu konfiguracji tworzy folder o nazwie zawierających konfiguracji **. Plik MOF** dla każdego węzła w konfiguracji. . Plik MOF jest format opartych na standardach zarządzania, który jest używany przez DSC środowiska PowerShell do komunikacji za pośrednictwem sieci.

Wprowadzenie konfiguracji:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Spowoduje to utworzenie zadania programu PowerShell, osiągnie, węzły w konfiguracji i konfiguruje je. Aby wyświetlić dane wyjściowe zadania, użyj — oczekiwania. 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

