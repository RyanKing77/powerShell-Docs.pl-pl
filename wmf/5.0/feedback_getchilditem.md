---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085298"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="7c151-102">Polecenie GET-ChildItem ma parametr - Depth</span><span class="sxs-lookup"><span data-stu-id="7c151-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="7c151-103">**Polecenie GET-ChildItem** ma teraz **— głębokość** korzystasz z parametru **— Recurse** ograniczyć rekursji:</span><span class="sxs-lookup"><span data-stu-id="7c151-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="7c151-104">PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - głębokość 0</span><span class="sxs-lookup"><span data-stu-id="7c151-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="7c151-105">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład</span><span class="sxs-lookup"><span data-stu-id="7c151-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7c151-106">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="7c151-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7c151-107">d---Depth0 o godzinie 17:36 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="7c151-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7c151-108">----4/14/2015 r. 13:19:00 więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="7c151-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7c151-109">----4/14/2015 r. 13:19:00 Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="7c151-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7c151-110">----4/14/2015 r. 13:19:00 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7c151-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7c151-111">PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - 1 głębokości</span><span class="sxs-lookup"><span data-stu-id="7c151-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="7c151-112">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład</span><span class="sxs-lookup"><span data-stu-id="7c151-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7c151-113">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="7c151-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7c151-114">d---Depth0 o godzinie 17:36 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="7c151-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7c151-115">----4/14/2015 r. 13:19:00 więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="7c151-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7c151-116">----4/14/2015 r. 13:19:00 Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="7c151-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7c151-117">----4/14/2015 r. 13:19:00 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7c151-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7c151-118">Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład\\Depth0</span><span class="sxs-lookup"><span data-stu-id="7c151-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="7c151-119">Tryb LastWriteTime długość nazwy</span><span class="sxs-lookup"><span data-stu-id="7c151-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7c151-120">d---Depth1 o godzinie 17:33 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="7c151-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
