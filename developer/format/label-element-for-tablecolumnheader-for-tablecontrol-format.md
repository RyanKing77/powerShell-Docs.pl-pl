---
title: Etykieta elementu dla TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054513"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="1b37c-102">Label, element — TableColumnHeader, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="1b37c-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="1b37c-103">Definiuje etykietę, która jest wyświetlana w górnej części kolumny.</span><span class="sxs-lookup"><span data-stu-id="1b37c-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="1b37c-104">Ten element jest używany podczas definiowania widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b37c-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="1b37c-105">— Element (w formacie) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji tablecontrol — (w formacie) elementu TableColumnHeader TableHeaders tablecontrol — (w formacie) etykiety elementu TableColumnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1b37c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b37c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b37c-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b37c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b37c-107">Attributes and Elements</span></span>

<span data-ttu-id="1b37c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Label` elementu.</span><span class="sxs-lookup"><span data-stu-id="1b37c-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="1b37c-109">Tylko jedna etykieta jest dozwolony dla każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="1b37c-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b37c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b37c-110">Attributes</span></span>

<span data-ttu-id="1b37c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="1b37c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b37c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b37c-112">Child Elements</span></span>

<span data-ttu-id="1b37c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="1b37c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b37c-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b37c-114">Parent Elements</span></span>

|<span data-ttu-id="1b37c-115">Element</span><span class="sxs-lookup"><span data-stu-id="1b37c-115">Element</span></span>|<span data-ttu-id="1b37c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1b37c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b37c-117">Element TableColumnHeader TableHeaders dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1b37c-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="1b37c-118">Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b37c-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b37c-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="1b37c-119">Text Value</span></span>

<span data-ttu-id="1b37c-120">Podaj tekst, który jest wyświetlany w górnej części kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b37c-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="1b37c-121">Nie istnieją żadne znaki w etykiecie kolumny.</span><span class="sxs-lookup"><span data-stu-id="1b37c-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b37c-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b37c-122">Remarks</span></span>

<span data-ttu-id="1b37c-123">Jeśli żadna etykieta nie zostanie określona, jest używana nazwa właściwości, którego wartość jest wyświetlana w wierszach.</span><span class="sxs-lookup"><span data-stu-id="1b37c-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="1b37c-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1b37c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b37c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b37c-125">Example</span></span>

<span data-ttu-id="1b37c-126">W tym przykładzie `TableColumnHeader` elementu, którego etykieta jest "Kolumna 1".</span><span class="sxs-lookup"><span data-stu-id="1b37c-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="1b37c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b37c-127">See Also</span></span>

[<span data-ttu-id="1b37c-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="1b37c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1b37c-129">Element TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="1b37c-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="1b37c-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="1b37c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
