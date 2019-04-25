---
title: Jak zaktualizować pliki pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082317"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="02528-102">Jak zaktualizować pliki pomocy</span><span class="sxs-lookup"><span data-stu-id="02528-102">How to Update Help Files</span></span>

<span data-ttu-id="02528-103">W tym temacie wyjaśniono, jak można zaktualizować pliki pomocy dla modułu, który obsługuje aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="02528-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="02528-104">Aktualizowanie plików pomocy</span><span class="sxs-lookup"><span data-stu-id="02528-104">Updating Help Files</span></span>

<span data-ttu-id="02528-105">Istnieje wiele powodów, aby zaktualizować pliki pomocy, takich jak usuwanie błędów, wyjaśnienia koncepcji, udzielenie odpowiedzi na często zadawane pytania, dodanie nowych plików lub dodanie nowych i lepszych przykłady.</span><span class="sxs-lookup"><span data-stu-id="02528-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="02528-106">Aby zaktualizować plik pomocy:</span><span class="sxs-lookup"><span data-stu-id="02528-106">To update a help file:</span></span>

1. <span data-ttu-id="02528-107">Zmiana plików.</span><span class="sxs-lookup"><span data-stu-id="02528-107">Change the files.</span></span>

2. <span data-ttu-id="02528-108">Pliki przekłada się na inne kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02528-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="02528-109">Zbieraj wszystkie pliki pomocy (nowych, zmiany i niezmienione) dla modułu w każda kultura interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02528-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="02528-110">Sprawdź poprawność plików względem schematu XML.</span><span class="sxs-lookup"><span data-stu-id="02528-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="02528-111">Ponownie skompiluj pliki CAB każda kultura interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02528-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="02528-112">W pliku HelpInfo XML zwiększyć numery wersji pliku CAB każda kultura interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02528-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="02528-113">Przekaż nowe pliki CAB do lokalizacji, który jest określony przez wartość **HelpContentUri** elementu w pliku HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="02528-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="02528-114">Zastąp starsze pliki CAB nowych plików CAB.</span><span class="sxs-lookup"><span data-stu-id="02528-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="02528-115">Przekaż zaktualizowany plik HelpInfo XML do lokalizacji, która jest określona przez **HelpInfoUri** klucza w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="02528-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="02528-116">Zastąp starszy plik HelpInfo XML za pomocą nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="02528-116">Replace the older HelpInfo XML file with the new file.</span></span>