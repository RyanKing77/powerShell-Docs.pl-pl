---
title: Dokumentacja programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: dfda6cb68b089a30a156760345420ee80d1d3ae9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851086"
---
# <a name="windows-powershell-reference"></a>Dokumentacja programu Windows PowerShell

Programu Windows PowerShell jest przeznaczony do automatyzacji administracyjne programu Microsoft .NET Framework — connected environment. Windows PowerShell udostępnia nowe podejście do tworzenia poleceń, tworzenie rozwiązań i tworzenia graficznego narzędzia do zarządzania oparte na interfejsie.

Program Windows PowerShell umożliwia administratorowi systemu można zautomatyzować administracji zasobów systemowych przez wykonywanie poleceń bezpośrednio lub za pomocą skryptów.

## <a name="developer-audience"></a>Docelowa grupa deweloperów

Windows PowerShell Software Development Kit (SDK) jest przeznaczony dla polecenia deweloperów, którzy potrzebują informacji referencyjnych na temat interfejsów API udostępnionych przez środowisko Windows PowerShell. Polecenie deweloperzy używać środowiska Windows PowerShell do tworzenia poleceń i dostawców, które rozszerzają zadania, które mogą być wykonywane przez środowisko Windows PowerShell.

## <a name="windows-powershell-resources"></a>Windows PowerShell zasobów

Oprócz zestawu SDK Windows PowerShell poniższe zasoby przedstawiają więcej informacji.

[Wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) zawiera wprowadzenie do programu Windows PowerShell: języka, poleceń cmdlet, dostawców i obiektów.

[Pisanie modułu programu Windows PowerShell](./module/writing-a-windows-powershell-module.md) zawiera informacje i przykłady dla administratorów, deweloperzy skryptu i polecenia cmdlet deweloperów, którzy potrzebują pakować i rozpowszechniać swoje rozwiązania programu Windows PowerShell przy użyciu modułów programu Windows PowerShell.

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) zapewnia informacje i przykłady kodów kierownikom programów, którzy projektowania poleceń cmdlet oraz dla deweloperów, którzy wdrażają kodzie polecenia cmdlet.

[Blog zespołu programu Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) zostanie najlepszy zasób wiedzy i współpracować z innymi użytkownikami programu Windows PowerShell. Przeczytaj wpis w blogu zespołu programu Windows PowerShell, a następnie dołącz do Forum użytkowników programu Windows PowerShell (microsoft.public.windows.powershell). Użyj usługi Windows Live Search, aby znaleźć inne środowiska Windows PowerShell, blogi i zasoby. Następnie podczas opracowywania wiedzę na temat swobodnie współtworzyć zawartość swoje pomysły.

[Przeglądarka modułów programu PowerShell](/powershell/module/) zawiera najnowsze wersje wiersza polecenia Tematy pomocy.

## <a name="class-libraries"></a>Biblioteki klas

[System.Management.Automation](/dotnet/api/System.Management.Automation) ta przestrzeń nazw jest przestrzeń nazw korzenia dla środowiska Windows PowerShell. Zawiera on klas, wyliczeń i interfejsy, które trzeba do zaimplementowania niestandardowych poleceń cmdlet. W szczególności [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasa to klasa bazowa, z których wszystkie polecenia cmdlet klasy musi pochodzić. Aby uzyskać więcej informacji na temat poleceń cmdlet Zobacz.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) ta przestrzeń nazw zawiera klasy, wyliczenia i połączeń wymaganych do implementowania dostawcy środowiska Windows PowerShell. W szczególności [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasa to klasa bazowa, z których wszystkie środowiska Windows PowerShell musi pochodzić klasy dostawcy.

[Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) ta przestrzeń nazw zawiera klasy dla poleceń cmdlet i dostawców implementowane przez środowisko Windows PowerShell. Podobnie, zalecane jest, że utworzono *twojanazwa*. Polecenia te polecenia cmdlet, które należy zaimplementować w obszarze nazw.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) ta przestrzeń nazw zawiera klasy, wyliczenia i interfejsy, które używa polecenia cmdlet w celu zdefiniowania interakcji między użytkownikiem i programu Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) ta przestrzeń nazw zawiera klasy bazowe, używane przez inne klasy w przestrzeni nazw. Na przykład [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) klasa jest klasą bazową dla [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasy.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) ta przestrzeń nazw zawiera klasy, wyliczenia i interfejsy, używany do tworzenia działania programu Windows PowerShell. W tym kontekście obszaru działania programu Windows PowerShell jest kontekst, w którym jeden lub wiele potoków programu Windows PowerShell wywoływanie polecenia cmdlet. Oznacza to, że polecenia cmdlet działają w kontekście działania programu Windows PowerShell. Aby uzyskać więcej informacji o aboutWindows obszary działania programu PowerShell, zobacz [obszary działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
