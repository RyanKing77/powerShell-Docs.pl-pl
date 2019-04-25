---
title: Jak dodać nazwę polecenia Cmdlet i streszczenie do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083341"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Jak dodać nazwę polecenia cmdlet i streszczenie do tematu pomocy dotyczącego polecenia cmdlet

W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcjach nazwy i streszczenie pomocy dotyczącej poleceń cmdlet. W pliku pomocy tej zawartości zostanie dodany do węzła polecenie dla każdego polecenia cmdlet.

> [!NOTE]
> Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell. Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Aby dodać nazwę polecenia Cmdlet i streszczenie

- Polecenia cmdlet pomocy można wyświetlić opisy dwa polecenia cmdlet. Pierwszy opis jest krótki opis, który jest określany jako streszczenie. Opis druga jest bardziej szczegółowy opis, który został omówiony w [Dodawanie szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md). Opisy te powinny być zapisywane jako pojedynczy akapit.

- Streszczenie nie Powtórz nazwa polecenia cmdlet. Informujące użytkownika, że polecenia cmdlet Get-serwer pobiera serwer jest krótki, ale nie zawierającego wiele użytecznych informacji. Zamiast tego należy używać synonimów i dodać szczegóły do opisu.

  Przykład: "Pobiera obiekt, który reprezentuje komputer lokalny lub zdalny".

- Użyj prostych zlecenia, takie jak "get", "Utwórz" i "Zmień" streszczenie. Unikaj używania "set", ponieważ jest niejasne, a słowa ozdobnych takich jak "Modyfikuj."

  Przykład: "Pobiera informacje o podpisie Authenticode w pliku".

- Napisz aktywnego głosu. Na przykład "Użyj obiektu TimeSpan..." jest znacznie bardziej zrozumiały, niż "Obiekt TimeSpan może służyć do..."

- Należy unikać czasownik "display", podczas opisywania poleceń cmdlet, które uzyskać obiekty. Mimo że program Windows PowerShell wyświetla dane polecenia cmdlet, ważne jest wprowadzenie użytkowników do koncepcji, które polecenie cmdlet zwraca obiekty .NET Framework, którego dane mogą być niewidoczne. Jeśli wyświetlanie należy podkreślić, użytkownik może nie należy pamiętać, że polecenia cmdlet mogła zostać zwrócona, wiele innych użytecznych właściwości i metod, które nie są wyświetlane.

## <a name="see-also"></a>Zobacz też

 [Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)