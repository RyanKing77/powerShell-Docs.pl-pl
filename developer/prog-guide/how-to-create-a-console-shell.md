---
title: Jak utworzyć powłoki konsoli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081590"
---
# <a name="how-to-create-a-console-shell"></a>Jak utworzyć powłokę konsoli

Program Windows PowerShell udostępnia narzędzia powłoki upewnij, nazywane także "Upewnij kit", który jest używany do tworzenia powłoki konsoli, który nie jest rozszerzalny. Utworzone za pomocą tego nowego narzędzia powłoki, nie można później rozszerzyć za pomocą przystawki programu Windows PowerShell.

## <a name="syntax"></a>Składnia

Poniżej przedstawiono składnię wykorzystywaną do uruchamiania powłoki upewnij z w obrębie pliku upewnij.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parametry

Poniżej przedstawiono krótki opis parametrów upewnij powłoki.

> [!CAUTION]
> Ścieżki UNC do zestawów nie są obsługiwane przez usługę Shell na marki.

|Parametr|Opis|
|---------------|-----------------|
|-out n.exe|Element wymagany. Nazwa powłoki do produkcji. Ścieżka nie jest określona jako część tego parametru.<br /><br /> Marka powłoki są dołączane ".exe" tej wartości, jeśli nie określono. **Uwaga:**  Nie należy tworzyć plik wyjściowy z taką samą nazwę jak plik dll. Jeśli spróbujesz to narzędzie powłoki upewnij tworzy pliku CS o takiej samej nazwie spowoduje zastąpienie pliku .cs, zawierający kod źródłowy polecenia cmdlet.|
|ns — przestrzeń nazw|Element wymagany. Przestrzeń nazw do użycia dla pochodnej [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) klasę, która zestawie upewnij generuje i kompiluje.|
|-lib libdirectory1 [, libdirectory2,...]|Katalogi, które są przeszukiwane pod kątem zestawów platformy .NET, w tym zestawy programu Windows PowerShell, zestawy określone przez `reference` parametr, zestawy pośrednio odwołuje się innego zestawu i zestawy systemowe platformy .NET.|
|-odwołać ca1.dll[,ca2.dll,...]|Rozdzielana przecinkami lista zestawów do uwzględnienia w powłoce. Te zestawy obejmuje wszystkie polecenia cmdlet i zestawy dostawcy, a także zestawy zasobów, które powinny być załadowane. Jeśli ten parametr nie jest określony, powłoki jest realizowane zawierający tylko podstawowych poleceń cmdlet i dostawcy udostępniane przez środowisko Windows PowerShell.<br /><br /> Można określić zestawy, korzystając z ich pełną ścieżkę, w przeciwnym razie one będą wyszukiwane przy użyciu ścieżka określona przez plik `lib` parametru.|
|-fd1.format.ps1xml[,fd2.format.ps1xml klasy formatdata,...]|Rozdzielana przecinkami lista formatowanie danych do uwzględnienia w powłoce. Jeśli ten parametr nie jest określony, powłoki jest realizowane zawierający tylko dane formatu dostarczane przez środowisko Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Rozdzielana przecinkami lista dane typu do uwzględnienia w powłoce. Jeśli ten parametr nie jest określony, powłoki jest realizowane zawierający tylko dane typu dostarczane przez środowisko Windows PowerShell.|
|-c1.cs źródła [, c2.cs,...]|Nazwa pliku, dostarczoną przez dewelopera powłoki, który zawiera kod źródłowy niezbędne do utworzenia powłoki.<br /><br /> Plik kodu źródłowego może zawierać żadnego z następujących kodu źródłowego:<br /><br /> Implementacji Menedżera autoryzacji, który zastępuje domyślnego menedżera autoryzacji. (To może również zostać dostarczona kompilowane do zestawu.)<br />— Deklaracji atrybutu informacyjne zestawu: takich jak AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, i AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Typ, który zawiera implementację Menedżera autoryzacji. To mogą być zdefiniowane w kodzie źródłowym lub kompilowane do zestawu (określony przez `reference` parametru). Jeśli ten parametr nie jest określony, domyślnego menedżera zabezpieczeń jest używany. Wartość powinna być pełna nazwa typu, łącznie z przestrzeni nazw.|
|-win32icon i.ico|Ikona dla pliku .exe, dla powłoki. Jeśli nie zostanie określony, powłoki mają ikonę, która zawiera kompilator języka c#, (jeśli istnieje).|
|-initscript p.ps1|Profil uruchamiania powłoki. Dołączono plik "jako — jest"; bez sprawdzania poprawności jest wykonywane przez markę powłoki.|
|-builtinscript s1.ps1[,s2.ps1,...]|Lista wbudowanej skrypty dla powłoki. Te skrypty są odnajdywane przed skrypty w ścieżce, a ich zawartość, nie można zmienić po skompilowaniu powłoki.<br /><br /> Dołączane są pliki "jako — jest"; bez sprawdzania poprawności jest wykonywane przez markę powłoki.|
|-resourcefile.txt zasobów|Plik txt, zawierający zasoby pomocy i transparent dla powłoki. Pierwszy zasób o nazwie ShellHelp i zawiera tekst wyświetlany, gdy powłoka jest wywoływana z `help` parametru. Drugi zasób o nazwie ShellBanner i zawiera tekst i informacje o prawach autorskich wyświetlane, gdy powłoki jest uruchamiana w trybie interaktywnym.<br /><br /> Jeśli ten parametr nie zostanie podany, lub te zasoby nie są obecne, następnie ogólnego pomocy i transparent są używane.|
|-cscflags cscFlags|Flagi, które powinny być przekazywane do C# kompilatora (csc.exe). Te są przekazywane bez zmian. Jeśli ten parametr zawiera spacje, powinny być ujęte w cudzysłów podwójny.|
|-?<br /><br /> — Pomoc|Wyświetla komunikat o prawach autorskich oraz opcje wiersza polecenia powłoki marki.|
|-verbose|Wyświetla szczegółowe informacje, podczas tworzenia powłoki.|

## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)