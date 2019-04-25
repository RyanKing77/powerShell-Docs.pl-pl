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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080751"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="f13cb-102">Kojarzenie jednostek OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="f13cb-102">Associating Management OData Entities</span></span>

<span data-ttu-id="f13cb-103">Często jest to przydatne do tworzenia skojarzenia między dwoma obiektami zarządzania OData.</span><span class="sxs-lookup"><span data-stu-id="f13cb-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="f13cb-104">Na przykład usługi OData zarządzania można dysponują jednostkami, które zarządzają katalog produktów, które są zorganizowane w kategoriach i definiowanie jednostek `Product` i `Category`.</span><span class="sxs-lookup"><span data-stu-id="f13cb-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="f13cb-105">Kojarząc tymi dwoma jednostkami, klient może pobrać informacji o wszystkich produktów z kategorii z pojedynczym żądaniem usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="f13cb-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="f13cb-106">Pobrano przykład przedstawiający sposób tworzenia skojarzenia między jednostkami [przykładowe skojarzenie](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="f13cb-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="f13cb-107">Utworzenie skojarzenia w pliku schematu zasobów</span><span class="sxs-lookup"><span data-stu-id="f13cb-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="f13cb-108">Następujący plik MOF definiuje dwie jednostki.</span><span class="sxs-lookup"><span data-stu-id="f13cb-108">The following MOF defines two entities.</span></span> <span data-ttu-id="f13cb-109">Utworzymy skojarzenia między nimi.</span><span class="sxs-lookup"><span data-stu-id="f13cb-109">We will create an association between them.</span></span>

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

<span data-ttu-id="f13cb-110">`Category` Klasa definiuje właściwość, która jest tablicą nazwy produktów, które należą do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="f13cb-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="f13cb-111">Aby skojarzyć dwie jednostki, należy zdefiniować klasę z `Association` atrybutu w pliku MOF schematu zasobów dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f13cb-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="f13cb-112">Klasy należy zdefiniować dwie jednostki skojarzone, o nazwie `ends` skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f13cb-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="f13cb-113">Poniższy przykład przedstawia definicję klasy, która definiuje skojarzenia między jednostkami kategorii i produktów.</span><span class="sxs-lookup"><span data-stu-id="f13cb-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="f13cb-114">Należy także zmienić deklaracji właściwości klasy kategorii produktów.</span><span class="sxs-lookup"><span data-stu-id="f13cb-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="f13cb-115">Możesz użyć `AssociationClass` — słowo kluczowe, aby określić, czy właściwość jest jednym końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f13cb-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="f13cb-116">Właściwość również musi być zdefiniowany jako odwołanie do osobne jednostki, a nie tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="f13cb-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="f13cb-117">Możesz to zrobić przy użyciu `ref` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f13cb-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="f13cb-118">Poniższy przykład przedstawia definicję właściwości, dla skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f13cb-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="f13cb-119">Na koniec należy zadeklarować drugim końcu skojarzenia, dodając do definicji właściwości `Product` klasy.</span><span class="sxs-lookup"><span data-stu-id="f13cb-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="f13cb-120">To jest odwołanie do obu tablicy lub do pojedynczej jednostki.</span><span class="sxs-lookup"><span data-stu-id="f13cb-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="f13cb-121">Przy założeniu, że każdy z produktów należy tylko do jednej kategorii, definicja będzie następujący.</span><span class="sxs-lookup"><span data-stu-id="f13cb-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="f13cb-122">Właściwości, które stanowią dwa końce skojarzenie noszą nazwę właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="f13cb-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="f13cb-123">Kroki do kojarzenia jednostki w pliku schematu zasobów</span><span class="sxs-lookup"><span data-stu-id="f13cb-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="f13cb-124">Zdefiniuj skojarzenie jako klasę za pomocą `Association` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f13cb-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="f13cb-125">Zdefiniuj końcach asocjacji za pomocą słowa kluczowego AssociationClass kwalifikowania właściwości skojarzone jednostki.</span><span class="sxs-lookup"><span data-stu-id="f13cb-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="f13cb-126">Utworzenie skojarzenia w pliku XML Mapowanie zasobów</span><span class="sxs-lookup"><span data-stu-id="f13cb-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="f13cb-127">Istnieją trzy różne przypadki wziąć pod uwagę podczas mapowania skojarzenia w pliku XML Mapowanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="f13cb-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="f13cb-128">Określanie sposobu kojarzenia jednostki w pliku mapowania zasobów</span><span class="sxs-lookup"><span data-stu-id="f13cb-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="f13cb-129">Jeśli właściwość nawigacji jest obecny w źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f13cb-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="f13cb-130">Typ .NET framework, a właściwość zawiera klucze obce nie jawnego mapowania jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="f13cb-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="f13cb-131">Jeśli właściwość nawigacji nie istnieje w typie podstawowym .NET Framework, należy określić polecenia cmdlet, które pobiera listę kluczy skojarzonych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f13cb-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="f13cb-132">Możesz to zrobić, dodając `Association` element zagnieżdżony w ramach `CmdletImplementation` elementu, po elementach, które definiują `cmdlets` dla innych poleceń CRUD.</span><span class="sxs-lookup"><span data-stu-id="f13cb-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="f13cb-133">Jeśli właściwość nawigacji istnieje w podstawowym typem .NET Framework, ale zawiera wystąpienia obiektu zamiast kluczy obcych, a następnie utworzysz polecenia cmdlet (tworząc funkcji programu Windows PowerShell lub skryptów) można pobrać kluczy obcych.</span><span class="sxs-lookup"><span data-stu-id="f13cb-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="f13cb-134">Następnie możesz określić to polecenie cmdlet w pliku mapowania zasobów.</span><span class="sxs-lookup"><span data-stu-id="f13cb-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="f13cb-135">Na przykład skrypt, aby pobrać klucze będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="f13cb-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="f13cb-136">I XML w pliku mapowania zasobów będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="f13cb-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="f13cb-137">Oprócz określenia polecenia cmdlet, aby pobrać skojarzone jednostki, można również określić polecenia cmdlet umożliwiające dodawanie i usuwanie odwołań z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f13cb-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="f13cb-138">W poniższym przykładzie założono, że istnieją polecenia cmdlet Add ProductToCategory i Remove-ProductFromCategory (one również można zdefiniować w skrypcie lub funkcji, jak w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="f13cb-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="f13cb-139">Wykonywanie zapytań skojarzone jednostki</span><span class="sxs-lookup"><span data-stu-id="f13cb-139">Querying associated entities</span></span>

<span data-ttu-id="f13cb-140">Klienta można pobrać listę wystąpień skojarzony z jednostką, tworząc określonego zapytania.</span><span class="sxs-lookup"><span data-stu-id="f13cb-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="f13cb-141">Konstruowanie zapytań dotyczących jednostek skojarzonych</span><span class="sxs-lookup"><span data-stu-id="f13cb-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="f13cb-142">Szczegółowe informacje o kategorii bez pobierania związane z nimi produkty może żądać klient.</span><span class="sxs-lookup"><span data-stu-id="f13cb-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="f13cb-143">Na przykład, następujące żądanie pobiera szczegóły `food` kategorii.</span><span class="sxs-lookup"><span data-stu-id="f13cb-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="f13cb-144">Aby uzyskać skojarzone produkty z kategorii (ale nie szczegółowe informacje o kategorii, klient określa właściwość nawigacji w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="f13cb-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="f13cb-145">Aby pobrać tylko adresy URL produktów, użyj `$links` kwalifikatora w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="f13cb-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="f13cb-146">Klienta można uzyskać szczegółów kategorii i jego skojarzone produkty za pomocą `$expand` kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="f13cb-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="f13cb-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f13cb-147">See Also</span></span>

[<span data-ttu-id="f13cb-148">Tworzenie usługi sieci Web rozszerzenie OData IIS zarządzania</span><span class="sxs-lookup"><span data-stu-id="f13cb-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)