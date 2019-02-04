---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687916"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="eb06c-102">Polecenie GET-ChildItem ma parametr - Depth</span><span class="sxs-lookup"><span data-stu-id="eb06c-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="eb06c-103">**Polecenie GET-ChildItem** ma teraz **— głębokość** korzystasz z parametru **— Recurse** ograniczyć rekursji:</span><span class="sxs-lookup"><span data-stu-id="eb06c-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="eb06c-104">PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - głębokość 0</span><span class="sxs-lookup"><span data-stu-id="eb06c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="eb06c-105">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład</span><span class="sxs-lookup"><span data-stu-id="eb06c-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="eb06c-106">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="eb06c-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eb06c-107">d---Depth0 o godzinie 17:36 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="eb06c-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="eb06c-108">----4/14/2015 r. 13:19:00 więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="eb06c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="eb06c-109">----4/14/2015 r. 13:19:00 Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="eb06c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="eb06c-110">----4/14/2015 r. 13:19:00 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="eb06c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="eb06c-111">PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - 1 głębokości</span><span class="sxs-lookup"><span data-stu-id="eb06c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="eb06c-112">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład</span><span class="sxs-lookup"><span data-stu-id="eb06c-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="eb06c-113">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="eb06c-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eb06c-114">d---Depth0 o godzinie 17:36 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="eb06c-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="eb06c-115">----4/14/2015 r. 13:19:00 więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="eb06c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="eb06c-116">----4/14/2015 r. 13:19:00 Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="eb06c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="eb06c-117">----4/14/2015 r. 13:19:00 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="eb06c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="eb06c-118">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład\\Depth0</span><span class="sxs-lookup"><span data-stu-id="eb06c-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="eb06c-119">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="eb06c-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="eb06c-120">d---Depth1 o godzinie 17:33 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="eb06c-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
