---
title: Kojarzenie jednostek OData zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850190"
---
# <a name="associating-management-odata-entities"></a>Kojarzenie jednostek OData zarządzania

Często jest to przydatne do tworzenia skojarzenia między dwoma obiektami zarządzania OData. Na przykład usługi OData zarządzania można dysponują jednostkami, które zarządzają katalog produktów, które są zorganizowane w kategoriach i definiowanie jednostek `Product` i `Category`. Kojarząc tymi dwoma jednostkami, klient może pobrać informacji o wszystkich produktów z kategorii z pojedynczym żądaniem usługi sieci web.

Pobrano przykład przedstawiający sposób tworzenia skojarzenia między jednostkami [przykładowe skojarzenie](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Utworzenie skojarzenia w pliku schematu zasobów

Następujący plik MOF definiuje dwie jednostki. Utworzymy skojarzenia między nimi.

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

`Category` Klasa definiuje właściwość, która jest tablicą nazwy produktów, które należą do tej kategorii.

Aby skojarzyć dwie jednostki, należy zdefiniować klasę z `Association` atrybutu w pliku MOF schematu zasobów dla usługi. Klasy należy zdefiniować dwie jednostki skojarzone, o nazwie `ends` skojarzenia. Poniższy przykład przedstawia definicję klasy, która definiuje skojarzenia między jednostkami kategorii i produktów.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Należy także zmienić deklaracji właściwości klasy kategorii produktów. Możesz użyć `AssociationClass` — słowo kluczowe, aby określić, czy właściwość jest jednym końcu skojarzenia. Właściwość również musi być zdefiniowany jako odwołanie do osobne jednostki, a nie tablicę ciągów. Możesz to zrobić przy użyciu `ref` — słowo kluczowe. Poniższy przykład przedstawia definicję właściwości, dla skojarzenia.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Na koniec należy zadeklarować drugim końcu skojarzenia, dodając do definicji właściwości `Product` klasy. To jest odwołanie do obu tablicy lub do pojedynczej jednostki. Przy założeniu, że każdy z produktów należy tylko do jednej kategorii, definicja będzie następujący.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Właściwości, które stanowią dwa końce skojarzenie noszą nazwę właściwości nawigacji.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Kroki do kojarzenia jednostki w pliku schematu zasobów

- Zdefiniuj skojarzenie jako klasę za pomocą `Association` — słowo kluczowe.

- Zdefiniuj końcach asocjacji za pomocą słowa kluczowego AssociationClass kwalifikowania właściwości skojarzone jednostki.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Utworzenie skojarzenia w pliku XML Mapowanie zasobów

Istnieją trzy różne przypadki wziąć pod uwagę podczas mapowania skojarzenia w pliku XML Mapowanie zasobów.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Określanie sposobu kojarzenia jednostki w pliku mapowania zasobów

- Jeśli właściwość nawigacji jest obecny w źródłowym. Typ .NET framework, a właściwość zawiera klucze obce nie jawnego mapowania jest konieczne.

- Jeśli właściwość nawigacji nie istnieje w typie podstawowym .NET Framework, należy określić polecenia cmdlet, które pobiera listę kluczy skojarzonych wystąpień. Możesz to zrobić, dodając `Association` element zagnieżdżony w ramach `CmdletImplementation` elementu, po elementach, które definiują `cmdlets` dla innych poleceń CRUD.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Jeśli właściwość nawigacji istnieje w podstawowym typem .NET Framework, ale zawiera wystąpienia obiektu zamiast kluczy obcych, a następnie utworzysz polecenia cmdlet (tworząc funkcji programu Windows PowerShell lub skryptów) można pobrać kluczy obcych. Następnie możesz określić to polecenie cmdlet w pliku mapowania zasobów. Na przykład skrypt, aby pobrać klucze będzie wyglądać następująco.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  I XML w pliku mapowania zasobów będzie wyglądać następująco.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Oprócz określenia polecenia cmdlet, aby pobrać skojarzone jednostki, można również określić polecenia cmdlet umożliwiające dodawanie i usuwanie odwołań z kolekcji. W poniższym przykładzie założono, że istnieją polecenia cmdlet Add ProductToCategory i Remove-ProductFromCategory (one również można zdefiniować w skrypcie lub funkcji, jak w poprzednim przykładzie).

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a>Wykonywanie zapytań skojarzone jednostki

Klienta można pobrać listę wystąpień skojarzony z jednostką, tworząc określonego zapytania.

#### <a name="constructing-queries-for-associated-entities"></a>Konstruowanie zapytań dotyczących jednostek skojarzonych

- Szczegółowe informacje o kategorii bez pobierania związane z nimi produkty może żądać klient. Na przykład, następujące żądanie pobiera szczegóły `food` kategorii.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Aby uzyskać skojarzone produkty z kategorii (ale nie szczegółowe informacje o kategorii, klient określa właściwość nawigacji w żądaniu.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Aby pobrać tylko adresy URL produktów, użyj `$links` kwalifikatora w żądaniu.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Klienta można uzyskać szczegółów kategorii i jego skojarzone produkty za pomocą `$expand` kwalifikator.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Zobacz też

[Tworzenie usługi sieci Web rozszerzenie OData IIS zarządzania](./creating-a-management-odata-web-service.md)