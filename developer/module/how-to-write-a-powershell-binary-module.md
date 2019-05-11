---
title: Jak napisać plik binarny programu PowerShell Module | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229334"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Jak napisać moduł pliku binarnego programu PowerShell

Binarny może być moduł zestawu (.dll), który zawiera polecenie cmdlet klasy. Domyślnie wszystkie polecenia cmdlet w zestawie są importowane podczas importowania modułu binarnego. Może jednak ograniczyć poleceń cmdlet, które są importowane, tworząc manifest modułu, którego moduł głównego to zestaw. (Na przykład klucz CmdletsToExport manifestu można wyeksportować tylko tych poleceń cmdlet, które są wymagane.) Ponadto moduł binarny może zawierać dodatkowe pliki, struktura katalogów i innych rodzajów informacji o zarządzaniu przydatne, w których jednego polecenia cmdlet nie może.

Poniższa procedura opisuje sposób tworzenia i zainstaluj moduł programu PowerShell binarnego.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Jak tworzyć i instalować binarne modułu programu PowerShell

1. Tworzenie rozwiązania binarne programu PowerShell (takich jak polecenia cmdlet napisane w C#), korzystając z możliwości potrzebne i upewnij się, że działa prawidłowo.

   Z punktu widzenia kod podstawowy moduł binarnego jest po prostu zestaw polecenia cmdlet. W rzeczywistości programu PowerShell będzie traktować zestawu jednego polecenia cmdlet jako moduł, ładowanie i zwalnianie z nie dodatkowego nakładu pracy ze strony dewelopera. Aby uzyskać więcej informacji na temat pisania polecenia cmdlet, zobacz [pisania polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Jeśli to konieczne, należy utworzyć pozostałą część rozwiązania: (dodatkowych poleceń cmdlet, pliki XML i tak dalej) i opisano je z manifestu modułu.

   Oprócz opisujący zestawy polecenia cmdlet w rozwiązaniu, manifestu modułu opisujący, jak chcesz eksportować i importować modułu, jakie polecenia cmdlet zostaną ujawnione i dodatkowe pliki przejdzie do modułu.
   Jak wspomniano wcześniej jednak, programu PowerShell można traktować binarne polecenia cmdlet, takich jak moduł o nie dodatkowego nakładu pracy.
   W efekcie manifestu modułu przydaje się głównie na łączenie wielu plików w jednym pakiecie lub jawnie kontrolowania publikacji dla danego zestawu.
   Aby uzyskać więcej informacji, zobacz [jak napisać Manifest modułu programu PowerShell](how-to-write-a-powershell-module-manifest.md).

   Poniższy kod jest bardzo proste C# blok kodu, który zawiera trzy polecenia cmdlet w tym samym pliku, który może służyć jako moduł.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Pakiet rozwiązania i zapisać pakiet w innym miejscu w ścieżce modułu programu PowerShell.

   `PSModulePath` Zmiennej środowiskowej globalne w tym artykule opisano ścieżek domyślnych, używających programu PowerShell można znaleźć modułu. Na przykład będzie wspólną ścieżkę można zapisać modułu w systemie `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Jeśli nie używasz domyślnych ścieżek, należy jawnie określać lokalizację modułu podczas instalacji. Należy utworzyć folder do zapisania modułu, ponieważ folder do przechowywania wielu zestawów i plików, dla danego rozwiązania może być konieczne.

   Należy pamiętać, że z technicznego punktu widzenia nie trzeba zainstalować modułu w dowolnym miejscu na `PSModulePath` — są po prostu domyślne lokalizacje wyglądające programu PowerShell dla modułu. Jednak uważa się najlepszym rozwiązaniem jest, aby to zrobić, chyba że masz powód przechowywania modułu gdzie indziej. Aby uzyskać więcej informacji, zobacz [Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md) i [modyfikowania ścieżki instalacji modułu PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importowanie modułu programu PowerShell przy użyciu wywołania do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Wywoływanie [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) załaduje modułu do aktywnej pamięci. Jeśli używasz programu PowerShell 3.0, a później, po prostu wywoływania Nazwa modułu w kodzie, będzie również zaimportować go; Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importowanie zestawów przystawki jako moduły

Polecenia cmdlet i dostawców, które istnieją w przystawce w zestawach, może być załadowany jako moduły binarne. Po przystawki zespoły są ładowane jako moduły binarne, poleceń cmdlet i dostawców w przystawce są dostępne dla użytkownika, ale klasy przystawki w zestawie jest ignorowana, a ta przystawka nie jest zarejestrowany. Co w efekcie cmdlet przystawki dostarczane przez środowisko Windows PowerShell nie może wykryć przystawki, nawet jeśli polecenia cmdlet i dostawcy będą dostępne dla sesji.

Ponadto formatowania lub typów plików, których odwołuje się ta przystawka nie można zaimportować jako część modułu binarnego.
Aby zaimportować pliki formatowania i typów należy utworzyć manifestu modułu.
Zobacz, [jak napisać Manifest modułu programu PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
