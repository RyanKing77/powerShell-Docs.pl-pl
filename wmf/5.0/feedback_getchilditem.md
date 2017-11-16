---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="b13f8-102">Get-ChildItem ma - parametr głębokość</span><span class="sxs-lookup"><span data-stu-id="b13f8-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="b13f8-103">**Get-ChildItem** ma teraz **— głębokość** korzystasz z parametru **— Recurse** ograniczenie rekursji:</span><span class="sxs-lookup"><span data-stu-id="b13f8-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="b13f8-104">PS C:\\użytkowników\\slee\\pobiera\\przykład&gt; Get-ChildItem-Recurse - głębokość 0</span><span class="sxs-lookup"><span data-stu-id="b13f8-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="b13f8-105">Katalog: C:\\użytkowników\\slee\\pobiera\\przykład</span><span class="sxs-lookup"><span data-stu-id="b13f8-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="b13f8-106">Nazwa trybu LastWriteTime długość</span><span class="sxs-lookup"><span data-stu-id="b13f8-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="b13f8-107">d---4/14/2015 Depth0 17:36:00</span><span class="sxs-lookup"><span data-stu-id="b13f8-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="b13f8-108">----2015-4-14 13:19 będzie więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="b13f8-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="b13f8-109">----2015-4-14:19 godz Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="b13f8-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="b13f8-110">----2015-4-14:19 godz 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="b13f8-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="b13f8-111">PS C:\\użytkowników\\slee\\pobiera\\przykład&gt; Get-ChildItem-Recurse - głębokość 1</span><span class="sxs-lookup"><span data-stu-id="b13f8-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="b13f8-112">Katalog: C:\\użytkowników\\slee\\pobiera\\przykład</span><span class="sxs-lookup"><span data-stu-id="b13f8-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="b13f8-113">Nazwa trybu LastWriteTime długość</span><span class="sxs-lookup"><span data-stu-id="b13f8-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="b13f8-114">d---4/14/2015 Depth0 17:36:00</span><span class="sxs-lookup"><span data-stu-id="b13f8-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="b13f8-115">----2015-4-14 13:19 będzie więc Plik1.txt 0</span><span class="sxs-lookup"><span data-stu-id="b13f8-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="b13f8-116">----2015-4-14:19 godz Plik2.txt 0</span><span class="sxs-lookup"><span data-stu-id="b13f8-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="b13f8-117">----2015-4-14:19 godz 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="b13f8-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="b13f8-118">Katalog: C:\\użytkowników\\slee\\pobiera\\przykład\\Depth0</span><span class="sxs-lookup"><span data-stu-id="b13f8-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="b13f8-119">Nazwa trybu LastWriteTime długość</span><span class="sxs-lookup"><span data-stu-id="b13f8-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="b13f8-120">d---Depth1 5:33 PM 4/14/2015</span><span class="sxs-lookup"><span data-stu-id="b13f8-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

