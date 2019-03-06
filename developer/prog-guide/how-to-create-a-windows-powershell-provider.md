---
title: Jak utworzyć dostawcę Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 286df63e75d6372cb41c974e60e79b02bd13686e
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429673"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Jak utworzyć dostawcę programu Windows PowerShell

Ta sekcja zawiera opis sposobu tworzenia dostawcy środowiska Windows PowerShell. Dostawca programu Windows PowerShell, mogą zostać uwzględnione na dwa sposoby. Użytkownikowi dostawca reprezentuje zestaw przechowywanych danych. Na przykład przechowywanych danych może być metabazy usług Internet Information Services (IIS), rejestru systemu Microsoft Windows, system plików Windows, usługi Active Directory i zmienną i alias danych przechowywanych przez środowisko Windows PowerShell.

Do deweloperów dostawca programu Windows PowerShell to interfejs między użytkownikiem i dane, które użytkownik chce uzyskać dostęp. Z tego punktu widzenia każdy typ dostawcy opisane w tej sekcji obsługuje zestaw określonych klas podstawowych i interfejsy, które umożliwiają środowiska uruchomieniowego programu Windows PowerShell do udostępnienia niektórych poleceń cmdlet dla użytkownika w typowy sposób.

## <a name="providers-provided-by-windows-powershell"></a>Dostawcy udostępniane przez środowisko Windows PowerShell

Windows PowerShell udostępnia kilku dostawców (na przykład dostawcy FileSystem, dostawca rejestru i Alias dostawcy), które umożliwiają dostęp do magazynów danych znane. Aby uzyskać więcej informacji na temat dostawców dostarczanych przez program Windows PowerShell Użyj następującego polecenia, aby uzyskać pomoc online:

**PS > get-help about_provider**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Uzyskiwanie dostępu do przechowywanych danych przy użyciu programu Windows PowerShell ścieżek

Dostawcy programu Windows PowerShell są dostępne do środowiska wykonawczego programu Windows PowerShell i polecenia programowo przy użyciu ścieżki środowiska Windows PowerShell. W większości przypadków, te ścieżki są używane do uzyskania bezpośredniego dostępu do danych za pośrednictwem dostawcy. Jednak niektóre ścieżki, może być rozpoznana jako wewnętrzny dostawcę ścieżkach, które umożliwiają dostęp do danych przy użyciu interfejsów programowania aplikacji (API) — Windows PowerShell polecenia cmdlet. Aby uzyskać więcej informacji o sposób działania dostawcy programu Windows PowerShell w programie Windows PowerShell, zobacz [sposób działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Udostępnianie za pomocą programu Windows PowerShell polecenia cmdlet dostawcy dysków

Dostawca programu Windows PowerShell udostępnia jego obsługiwanych poleceń cmdlet przy użyciu wirtualnych dysków programu Windows PowerShell. Program Windows PowerShell mają zastosowanie następujące reguły dotyczące dysk programu Windows PowerShell:

- Nazwa dysku może być dowolną sekwencją alfanumeryczne.

- Dysk może być określona w dowolnym momencie prawidłowe ścieżki o nazwie "root".

- Dysk może być zaimplementowany dla przechowywanych danych, nie tylko w systemie plików.

- Każdy dysk przechowuje swój własny bieżącej lokalizacji pracy, dzięki czemu użytkownik do zachowania kontekstu przy przesuwaniu między dysków.

## <a name="in-this-section"></a>W tej sekcji

Poniższa tabela zawiera listę tematów, które zawierają przykłady kodu, które są kompilowane na siebie nawzajem. Począwszy od drugiego tematu podstawowego dostawcy środowiska Windows PowerShell może być zainicjowany i niezainicjowana przez środowisko uruchomieniowe programu Windows PowerShell, następny temat dodaje funkcje do uzyskiwania dostępu do danych, następny temat dodaje funkcje do manipulowania (danych elementy w przechowywanych danych), i tak dalej.

|Temat|Definicja|
|-----------|----------------|
|[Projektowanie dostawcą Windows PowerShell](./designing-your-windows-powershell-provider.md)|W tym temacie omówiono czynności, które należy wziąć pod uwagę przed wdrożeniem dostawcy środowiska Windows PowerShell. Plik ten zawiera podsumowanie klas bazowych dostawcy środowiska Windows PowerShell i interfejsów, które są używane.|
|[Tworzenie dostawcy podstawowy Windows PowerShell](./creating-a-basic-windows-powershell-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia inicjowania i uninitialize dostawcy środowiska uruchomieniowego programu Windows PowerShell.|
|[Tworzenie dostawcy dysku środowiska PowerShell Windows](./creating-a-windows-powershell-drive-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi dostęp do magazynu danych za pośrednictwem dysk programu Windows PowerShell.|
|[Tworzenie dostawcy programu PowerShell elementu Windows](./creating-a-windows-powershell-item-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi manipulowania elementów w magazynie danych.|
|[Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi pracować nad magazyny danych wielowarstwowych.|
|[Tworzenie dostawcy nawigacji Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi nawigację elementy do przechowywania danych hierarchicznie.|
|[Tworzenie dostawcy zawartość programu PowerShell Windows](./creating-a-windows-powershell-content-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi manipulować zawartością elementów w magazynie danych.|
|[Tworzenie dostawcy właściwości programu PowerShell Windows](./creating-a-windows-powershell-property-provider.md)|W tym temacie przedstawiono sposób tworzenia dostawcy środowiska Windows PowerShell, który umożliwia użytkownikowi manipulowania właściwości elementów w magazynie danych.|

## <a name="see-also"></a>Zobacz też

[Jak działa program Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)