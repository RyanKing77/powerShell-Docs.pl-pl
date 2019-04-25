---
title: Pisanie programu PowerShell, formatowanie pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083579"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="865bd-102">Pisanie pliku formatującego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="865bd-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="865bd-103">"Zapisywanie pliku formatowania programu PowerShell" jest dla deweloperów polecenia, którzy pisania poleceń cmdlet lub funkcje, które zwracają obiekty w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="865bd-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="865bd-104">Pliki formatowania zdefiniować sposób wyświetlania tych obiektów programu PowerShell w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="865bd-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="865bd-105">Ta dokumentacja zawiera omówienie formatowania plików wyjaśnienie pojęcia, które należy rozumieć w przypadku zapisywania tych plików, przykłady kodu XML używane w tych plików, a sekcja odwołania dla elementów XML.</span><span class="sxs-lookup"><span data-stu-id="865bd-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="865bd-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="865bd-106">In This Section</span></span>

<span data-ttu-id="865bd-107">[Omówienie pliku formatowania](./formatting-file-overview.md) w tym artykule opisano to plik formatu i ogólne składniki formatowania pliku, znajdującego się w tym wspólne cechy, które mogą być definiowane w pliku różne typy widoków formatu, które mogą być definiowane dla obiektów platformy .NET i uproszczony przykład XML używany do definiowania widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="865bd-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="865bd-108">[Formatowanie pliku pojęcia](./formatting-file-concepts.md) zawiera informacje, które być może musisz wiedzieć, podczas tworzenia własnego formatowania plików, takich jak różne typy widoków, które można zdefiniować i składniki specjalnych widoków.</span><span class="sxs-lookup"><span data-stu-id="865bd-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="865bd-109">[Przykłady formatowania plików](./examples-of-formatting-files.md) przykłady XML zawiera kilka plików formatowania, w tym przykłady widoku tabeli, widoku listy oraz szerokie, a także przykłady pokazujące, jak zdefiniować funkcje, takie jak zaznaczenie zestawów, warunki wybór i Typowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="865bd-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="865bd-110">[Format XML — odwołanie](./format-schema-xml-reference.md) zawiera tematy referencyjne dotyczące elementów XML, używany w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="865bd-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
