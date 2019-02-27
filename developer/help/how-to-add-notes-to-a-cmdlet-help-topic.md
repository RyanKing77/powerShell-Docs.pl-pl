---
title: Jak dodawać notatki do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851198"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="a7370-102">Jak dodać notatki do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a7370-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a7370-103">W tej sekcji opisano sposób dodawania sekcja uwagi do tematu pomocy polecenia cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="a7370-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="a7370-104">Sekcję uwag służy do wyjaśnienia szczegółowe informacje, które nie mieszczą się łatwo na inne strukturalne sekcje, takie jak uzyskać bardziej szczegółowy opis parametru.</span><span class="sxs-lookup"><span data-stu-id="a7370-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="a7370-105">Ta zawartość można dołączyć komentarze dotyczące działania polecenia cmdlet przy użyciu określonego dostawcy, do niektórych zastosowań unikatowy, ale ważne jest, polecenia cmdlet lub sposobów uniknięcia wyświetlania możliwe warunki wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="a7370-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="a7370-106">Nie ma ograniczeń liczby uwagi, które można dodać do sekcji Uwagi.</span><span class="sxs-lookup"><span data-stu-id="a7370-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="a7370-107">Dla każdego notatki, Dodaj parę \<maml:alert > tagi \<maml:alertset > węzła.</span><span class="sxs-lookup"><span data-stu-id="a7370-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="a7370-108">Zawartość każdego uwaga zostanie dodany w ramach zestawu \<MAML: para > tagów.</span><span class="sxs-lookup"><span data-stu-id="a7370-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="a7370-109">Użyj pustego \<MAML: para > Znaczniki odstępy.</span><span class="sxs-lookup"><span data-stu-id="a7370-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="a7370-110">Pokazano w poniższym XML \<maml:alertset > węzeł o dwie notatki.</span><span class="sxs-lookup"><span data-stu-id="a7370-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="a7370-111">Zwróć uwagę, że każdy Uwaga ma opcjonalny \<MAML: TITLE > tag (tytuły może służyć do grupowania dowolny zbiór \<maml:alert > tagi), i że każdy Uwaga ma pusty wiersz po zawartości do rozdzielenia.</span><span class="sxs-lookup"><span data-stu-id="a7370-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



