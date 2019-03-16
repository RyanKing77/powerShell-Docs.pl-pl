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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057250"
---
# <a name="public-resource-schema"></a>Schemat zasobów publicznych

Zarządzanie OData używa pliku MOF w celu zdefiniowania zasobów i ich właściwości. Właściwości elementu entity OData zarządzania odpowiadają bezpośrednio do właściwości typu zarządzanego zwracany przez polecenie cmdlet bazowego.

## <a name="defining-a-resource"></a>Definiowanie zasobu

Każdy zasób odnosi się do obiektu zwróconego przez polecenie cmdlet programu Windows PowerShell. W zasobie publicznego pliku MOF należy zdefiniować od zadeklarowania klasy zasobem. Klasa składa się z właściwościami, które odpowiadają właściwości obiektu. Na przykład w poniższym przykładzie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klasy jest reprezentowany przez następujące MOF.

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

Każda nazwa właściwości jest poprzedzony przez typ danych. Typy danych, w tym przykładzie odpowiadają pierwotne typy danych CLR w .NET Framework, ale właściwości może być również odwołania do innych zasobów lub złożonych typów, które są zarówno opisane później.

`Key` Kwalifikator wskazuje, że właściwość jest używany do jednoznacznego identyfikowania wystąpienia zasobu. Zasób może mieć więcej niż jeden klucz.

`Required` Kwalifikator wskazuje, że właściwość jest wymagana. Jeśli właściwość jest oznaczona za pomocą `Key` kwalifikatora, jest on uznawany za jest wymagane i `Required` kwalifikatora nie jest konieczne.

### <a name="complex-data-types"></a>Złożone typy danych

Właściwości jednostki może mieć złożone typy danych. Złożone typy danych są typy, które składają się z innych typów, podobne do struktury w języku programowania C. Typ złożony jest zadeklarowana w pliku MOF jako klasa ze `ComplexType` kwalifikatora, jak w poniższym przykładzie.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Aby zadeklarować właściwość jednostek jako typ złożony, Zadeklaruj go jako `string` to typ `EmbeddedInstance` kwalifikatora, łącznie z nazwą typu złożonego. W poniższym przykładzie pokazano deklaracji z właściwością `PswsTest_ProcessModule` typ zadeklarowany w poprzednim przykładzie.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Kojarzenie jednostki

Dwie jednostki można skojarzyć za pomocą kwalifikatorów AssociationClass i skojarzenia. Aby uzyskać więcej informacji, zobacz [kojarzenie jednostek OData zarządzania](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Typy pochodne

Typ może pochodzić z innego typu. Typ pochodny dziedziczy wszystkich właściwości typu, z którego pochodzi oprócz dowolne właściwości, które jawnie pochodnych. Poniższy przykład przedstawia deklarację typu, a następnie deklaracji z dwóch typów pochodnych tego typu.

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