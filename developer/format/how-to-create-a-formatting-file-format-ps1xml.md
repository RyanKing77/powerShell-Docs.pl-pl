---
title: Jak utworzyć plik formatowania (. format.ps1xml) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851688"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="d4de5-102">Jak utworzyć plik formatujący (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="d4de5-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="d4de5-103">W tym temacie opisano sposób tworzenia pliku formatowania (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="d4de5-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="d4de5-104">Można również utworzyć plik formatowania przez skopiowanie jednego z plików udostępniane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4de5-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="d4de5-105">Możesz utworzyć kopię istniejącego pliku, Usuń istniejące podpisu cyfrowego ale dodanie własnego podpisu do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="d4de5-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="d4de5-106">Aby utworzyć. format.ps1xml pliku.</span><span class="sxs-lookup"><span data-stu-id="d4de5-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="d4de5-107">Utwórz plik tekstowy (txt) przy użyciu tekstu edytora, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="d4de5-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="d4de5-108">Skopiuj następujące wiersze do formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="d4de5-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="d4de5-109">\<Konfiguracji >\</Configuration > Znaczniki określają główne `Configuration` węzła.</span><span class="sxs-lookup"><span data-stu-id="d4de5-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="d4de5-110">Wszystkie dodatkowe znaczniki XML będzie ujęte w ramach tego węzła.</span><span class="sxs-lookup"><span data-stu-id="d4de5-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="d4de5-111"><ViewDefinitions> </ViewDefinitions> Tagi definiują `ViewDefinitions` węzła.</span><span class="sxs-lookup"><span data-stu-id="d4de5-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="d4de5-112">Wszystkie widoki są definiowane w tym węźle.</span><span class="sxs-lookup"><span data-stu-id="d4de5-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="d4de5-113">Zapisz plik do folderu instalacyjnego programu Windows PowerShell, do folderu modułu lub podfolder folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="d4de5-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="d4de5-114">Użyj następującego formatu nazwy, podczas zapisywania pliku: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="d4de5-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="d4de5-115">Należy użyć plików formatowania `.format.ps1xml` rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d4de5-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="d4de5-116">Teraz można przystąpić do dodawania widoków do formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="d4de5-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="d4de5-117">Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="d4de5-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="d4de5-118">Aby dodać pojedynczego widoku dla każdego obiektu, wielu widoków do tego samego obiektu lub pojedynczy widok, który jest używany przez wielu obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4de5-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4de5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4de5-119">See Also</span></span>

[<span data-ttu-id="d4de5-120">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="d4de5-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
