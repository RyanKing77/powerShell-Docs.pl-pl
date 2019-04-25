---
title: Rozszerzanie danych wyjściowych obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068168"
---
# <a name="extending-output-objects"></a>Rozszerzanie obiektów danych wyjściowych

Możesz rozszerzyć obiektów .NET Framework, które są zwracane przez polecenia cmdlet, funkcji i skryptów przy użyciu typów plików (.ps1xml). Typy plików są plikami XML, umożliwiające dodawanie właściwości i metod do istniejących obiektów. Na przykład programu Windows PowerShell udostępnia plik Types.ps1xml, który dodaje elementy do wielu istniejących obiektów .NET Framework. Plik Types.ps1xml znajduje się w katalogu instalacyjnym programu Windows PowerShell (`$pshome`). Można utworzyć własny plik typów, aby dodatkowo rozszerzać te obiekty, albo aby rozszerzyć innych obiektów. Rozszerzając obiektu przy użyciu pliku typów, dowolne wystąpienie obiektu jest rozszerzona o nowe elementy.

## <a name="extending-the-systemarray-object"></a>Rozszerzanie obiektu System.Array

W poniższym przykładzie pokazano, jak rozszerza środowisko Windows PowerShell [System.Array](/dotnet/api/System.Array) obiektu w pliku Types.ps1xml. Domyślnie [System.Array](/dotnet/api/System.Array) obiekty mają `Length` właściwość, która wyświetla liczbę obiektów w tablicy. Jednak ponieważ wyraźnie "długość nazwy" nie zawiera opisu właściwości, programu Windows PowerShell zwiększa `Count` alias właściwość, która wyświetla taką samą wartość jak `Length` właściwości. Dodaje następujący kod XML `Count` właściwości [System.Array](/dotnet/api/System.Array) typu.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Aby wyświetlić tej nowej właściwości alias, należy użyć [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) polecenia w dowolnej macierzy, jak pokazano w poniższym przykładzie.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Polecenie zwraca następujące wyniki.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Można użyć dowolnego `Count` właściwości lub `Length` właściwość, aby określić liczbę obiektów w tablicy. Przykład:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Niestandardowe typy plików

Aby utworzyć plik niestandardowych typów, zacznij od skopiowania istniejący plik typów. Nowy plik może mieć dowolną nazwę, ale musi mieć rozszerzenie nazwy pliku .ps1xml. Skopiuj plik, nowy plik zostanie umieszczony w dowolnym katalogu, który jest dostępny dla programu Windows PowerShell, ale warto umieścić pliki w katalogu instalacyjnym programu Windows PowerShell (`$pshome`) lub w podkatalogu katalogu instalacyjnego.

Aby dodać własne typy rozszerzonych do pliku, należy dodać element typy dla każdego obiektu, który ma zostać rozszerzony. Przykłady można znaleźć w następujących tematach.

- Aby uzyskać więcej informacji na temat dodawania właściwości i ustawia właściwość zobacz [właściwości rozszerzone](./extending-properties-for-objects.md)

- Aby uzyskać więcej informacji na temat dodawania metod, zobacz [rozszerzone metody](./defining-default-methods-for-objects.md).

- Aby uzyskać więcej informacji na temat dodawania zestawów elementów członkowskich, zobacz [rozszerzone zestawów elementów członkowskich](./defining-default-member-sets-for-objects.md).

Po zdefiniowaniu typów rozszerzonej, użyj jedną z następujących metod udostępniania rozszerzonych obiektów:

- Aby jednak udostępnić plik rozszerzone typy bieżącej sesji, należy użyć [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia cmdlet, aby dodać nowy plik. Jeśli chcesz, aby typów na mają pierwszeństwo względem typów, które są zdefiniowane w innych typów plików (w tym pliku Types.ps1xml), należy użyć `PrependData` parametru [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia cmdlet.
- Aby udostępnić plik rozszerzone typy do wszystkich przyszłych sesji, Dodaj plik typów do modułu, eksportu w bieżącej sesji lub Dodaj [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia do Twojego profilu programu Windows PowerShell.

## <a name="signing-types-files"></a>Podpisywanie typów plików

Typy plików powinny podpisane cyfrowo, aby zapobiec modyfikowaniu, ponieważ kod XML może zawierać Bloki skryptu. Aby uzyskać więcej informacji na temat dodawania podpisów cyfrowych, zobacz [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Zobacz też

[Definiowanie domyślnych właściwości dla obiektów](./extending-properties-for-objects.md)

[Definiowanie domyślnych metod dla obiektów](./defining-default-methods-for-objects.md)

[Definiowanie domyślnego zestawów elementów członkowskich dla obiektów](./defining-default-member-sets-for-objects.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
