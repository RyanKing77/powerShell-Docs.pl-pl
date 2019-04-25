---
title: Public Resource Schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080581"
---
# <a name="public-resource-schema"></a><span data-ttu-id="7e036-102">Schemat zasobów publicznych</span><span class="sxs-lookup"><span data-stu-id="7e036-102">Public Resource Schema</span></span>

<span data-ttu-id="7e036-103">Zarządzanie OData używa pliku MOF w celu zdefiniowania zasobów i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e036-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="7e036-104">Właściwości elementu entity OData zarządzania odpowiadają bezpośrednio do właściwości typu zarządzanego zwracany przez polecenie cmdlet bazowego.</span><span class="sxs-lookup"><span data-stu-id="7e036-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="7e036-105">Definiowanie zasobu</span><span class="sxs-lookup"><span data-stu-id="7e036-105">Defining a resource</span></span>

<span data-ttu-id="7e036-106">Każdy zasób odnosi się do obiektu zwróconego przez polecenie cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e036-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="7e036-107">W zasobie publicznego pliku MOF należy zdefiniować od zadeklarowania klasy zasobem.</span><span class="sxs-lookup"><span data-stu-id="7e036-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="7e036-108">Klasa składa się z właściwościami, które odpowiadają właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="7e036-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="7e036-109">Na przykład w poniższym przykładzie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klasy jest reprezentowany przez następujące MOF.</span><span class="sxs-lookup"><span data-stu-id="7e036-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="7e036-110">Każda nazwa właściwości jest poprzedzony przez typ danych.</span><span class="sxs-lookup"><span data-stu-id="7e036-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="7e036-111">Typy danych, w tym przykładzie odpowiadają pierwotne typy danych CLR w .NET Framework, ale właściwości może być również odwołania do innych zasobów lub złożonych typów, które są zarówno opisane później.</span><span class="sxs-lookup"><span data-stu-id="7e036-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="7e036-112">`Key` Kwalifikator wskazuje, że właściwość jest używany do jednoznacznego identyfikowania wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="7e036-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="7e036-113">Zasób może mieć więcej niż jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="7e036-113">A resource can have more than one key.</span></span>

<span data-ttu-id="7e036-114">`Required` Kwalifikator wskazuje, że właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="7e036-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="7e036-115">Jeśli właściwość jest oznaczona za pomocą `Key` kwalifikatora, jest on uznawany za jest wymagane i `Required` kwalifikatora nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="7e036-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="7e036-116">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="7e036-116">Complex data types</span></span>

<span data-ttu-id="7e036-117">Właściwości jednostki może mieć złożone typy danych.</span><span class="sxs-lookup"><span data-stu-id="7e036-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="7e036-118">Złożone typy danych są typy, które składają się z innych typów, podobne do struktury w języku programowania C.</span><span class="sxs-lookup"><span data-stu-id="7e036-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="7e036-119">Typ złożony jest zadeklarowana w pliku MOF jako klasa ze `ComplexType` kwalifikatora, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7e036-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="7e036-120">Aby zadeklarować właściwość jednostek jako typ złożony, Zadeklaruj go jako `string` to typ `EmbeddedInstance` kwalifikatora, łącznie z nazwą typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="7e036-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="7e036-121">W poniższym przykładzie pokazano deklaracji z właściwością `PswsTest_ProcessModule` typ zadeklarowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7e036-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="7e036-122">Kojarzenie jednostki</span><span class="sxs-lookup"><span data-stu-id="7e036-122">Associating entities</span></span>

<span data-ttu-id="7e036-123">Dwie jednostki można skojarzyć za pomocą kwalifikatorów AssociationClass i skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="7e036-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="7e036-124">Aby uzyskać więcej informacji, zobacz [kojarzenie jednostek OData zarządzania](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="7e036-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="7e036-125">Typy pochodne</span><span class="sxs-lookup"><span data-stu-id="7e036-125">Derived types</span></span>

<span data-ttu-id="7e036-126">Typ może pochodzić z innego typu.</span><span class="sxs-lookup"><span data-stu-id="7e036-126">You can derive a type from another type.</span></span> <span data-ttu-id="7e036-127">Typ pochodny dziedziczy wszystkich właściwości typu, z którego pochodzi oprócz dowolne właściwości, które jawnie pochodnych.</span><span class="sxs-lookup"><span data-stu-id="7e036-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="7e036-128">Poniższy przykład przedstawia deklarację typu, a następnie deklaracji z dwóch typów pochodnych tego typu.</span><span class="sxs-lookup"><span data-stu-id="7e036-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```