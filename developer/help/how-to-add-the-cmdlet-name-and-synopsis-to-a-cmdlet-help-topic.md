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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850890"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="daa96-102">Jak dodać nazwę polecenia cmdlet i streszczenie do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa96-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="daa96-103">W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcjach nazwy i streszczenie pomocy dotyczącej poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa96-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="daa96-104">W pliku pomocy tej zawartości zostanie dodany do węzła polecenie dla każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa96-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="daa96-105">Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daa96-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="daa96-106">Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daa96-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="daa96-107">Aby dodać nazwę polecenia Cmdlet i streszczenie</span><span class="sxs-lookup"><span data-stu-id="daa96-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="daa96-108">Polecenia cmdlet pomocy można wyświetlić opisy dwa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa96-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="daa96-109">Pierwszy opis jest krótki opis, który jest określany jako streszczenie.</span><span class="sxs-lookup"><span data-stu-id="daa96-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="daa96-110">Opis druga jest bardziej szczegółowy opis, który został omówiony w [Dodawanie szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="daa96-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="daa96-111">Opisy te powinny być zapisywane jako pojedynczy akapit.</span><span class="sxs-lookup"><span data-stu-id="daa96-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="daa96-112">Streszczenie nie Powtórz nazwa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa96-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="daa96-113">Informujące użytkownika, że polecenia cmdlet Get-serwer pobiera serwer jest krótki, ale nie zawierającego wiele użytecznych informacji.</span><span class="sxs-lookup"><span data-stu-id="daa96-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="daa96-114">Zamiast tego należy używać synonimów i dodać szczegóły do opisu.</span><span class="sxs-lookup"><span data-stu-id="daa96-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="daa96-115">Przykład: "Pobiera obiekt, który reprezentuje komputer lokalny lub zdalny".</span><span class="sxs-lookup"><span data-stu-id="daa96-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="daa96-116">Użyj prostych zlecenia, takie jak "get", "Utwórz" i "Zmień" streszczenie.</span><span class="sxs-lookup"><span data-stu-id="daa96-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="daa96-117">Unikaj używania "set", ponieważ jest niejasne, a słowa ozdobnych takich jak "Modyfikuj."</span><span class="sxs-lookup"><span data-stu-id="daa96-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="daa96-118">Przykład: "Pobiera informacje o podpisie Authenticode w pliku".</span><span class="sxs-lookup"><span data-stu-id="daa96-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="daa96-119">Napisz aktywnego głosu.</span><span class="sxs-lookup"><span data-stu-id="daa96-119">Write in active voice.</span></span> <span data-ttu-id="daa96-120">Na przykład "Użyj obiektu TimeSpan..." jest znacznie bardziej zrozumiały, niż "Obiekt TimeSpan może służyć do..."</span><span class="sxs-lookup"><span data-stu-id="daa96-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="daa96-121">Należy unikać czasownik "display", podczas opisywania poleceń cmdlet, które uzyskać obiekty.</span><span class="sxs-lookup"><span data-stu-id="daa96-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="daa96-122">Mimo że program Windows PowerShell wyświetla dane polecenia cmdlet, ważne jest wprowadzenie użytkowników do koncepcji, które polecenie cmdlet zwraca obiekty .NET Framework, którego dane mogą być niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="daa96-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="daa96-123">Jeśli wyświetlanie należy podkreślić, użytkownik może nie należy pamiętać, że polecenia cmdlet mogła zostać zwrócona, wiele innych użytecznych właściwości i metod, które nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="daa96-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="daa96-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daa96-124">See Also</span></span>

 [<span data-ttu-id="daa96-125">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="daa96-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)