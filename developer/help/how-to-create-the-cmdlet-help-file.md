---
title: Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083250"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Jak utworzyć plik pomocy dotyczącej poleceń cmdlet

W tej sekcji opisano, jak utworzyć prawidłowy plik XML zawierający zawartość tematy pomocy do poleceń cmdlet programu Windows PowerShell. W tej sekcji omówiono, jak nazwa pliku pomocy, jak dodać odpowiednie nagłówki XML i sposób dodawania węzłów zawierających różne sekcje zawartości pomocy polecenia cmdlet.

> [!NOTE]
> Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell. Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet

1. Utwórz plik tekstowy i zapisz go przy użyciu kodowania UTF8. Nazwa pliku musi mieć następujący format, tak aby program Windows PowerShell można wykryć je jako plik pomocy polecenia cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Dodaj następujące nagłówki XML do pliku tekstowego. Należy pamiętać, że plik zostanie zweryfikowana względem schematu wielu agentów modelowania języka (MAML). Obecnie usługa programu Windows PowerShell nie zapewnia żadnych narzędzi do sprawdzania poprawności pliku.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Dodaj węzeł polecenia do pliku pomocy polecenia cmdlet dla każdego polecenia cmdlet w zestawie. Każdy węzeł w węźle polecenia odnosi się do różnych części tematu pomocy polecenia cmdlet.

   W poniższej tabeli wymieniono elementu XML dla każdego węzła, następuje opisy dla każdego węzła.

   |Węzeł|Opis|
   |----------|-----------------|
   |`<details>`|Dodaje zawartość dla nazwy i streszczenie części tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [sposobu dodawania nazwa polecenia Cmdlet i streszczenie](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Dodaje zawartość w sekcji Opis tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [sposób dodawania szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Dodaje zawartość w sekcji SKŁADNI tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [jak dodać składnię do tematu pomocy polecenia Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Dodaje zawartość sekcji Parametry tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [jak dodawanie parametrów do tematu pomocy polecenia Cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Dodaje zawartość dla danych wejściowych części tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [sposób dodawania typów wejściowych do tematu pomocy polecenia Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Dodaje zawartość dla danych wyjściowych części tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [jak dodać zwrócić wartości do tematu pomocy polecenia Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Dodaje zawartość do sekcji Notatki tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [sposób dodawania notatki do tematu pomocy polecenia Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Dodaje zawartość sekcji Przykłady tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [jak Dodaj przykłady do tematu pomocy polecenia Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Dodaje zawartość w sekcji LINKI powiązane tematu pomocy polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [jak dodać powiązane linki do tematu pomocy polecenia Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Przykład

 Oto przykład węzeł polecenia, który zawiera węzły dla różnych części tematu pomocy polecenia cmdlet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Zobacz też

 [Jak dodać nazwę polecenia Cmdlet i streszczenie](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Jak dodać szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Jak dodać składnię do tematu pomocy polecenia Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Jak dodać parametry do tematu pomocy polecenia Cmdlet](./how-to-add-parameter-information.md)

 [Jak dodać typów wejściowych do tematu pomocy polecenia Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Jak dodać wartości zwracane do tematu pomocy polecenia Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Jak dodać informacje o do tematu pomocy polecenia Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Jak dodawać przykłady do tematu pomocy polecenia Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Jak dodać powiązane linki do tematu pomocy polecenia Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)