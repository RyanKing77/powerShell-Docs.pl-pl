---
title: Jak utworzyć plik HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082417"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="dfe5d-102">Jak utworzyć plik XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="dfe5d-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="dfe5d-103">Ten temat w tej sekcji wyjaśniono, jak tworzyć i wypełniać plik informacji pomocy, powszechnie znane jako "HelpInfo plikiem XML," dla funkcji programu Windows PowerShell aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="dfe5d-104">Omówienie plików HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="dfe5d-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="dfe5d-105">Plik HelpInfo XML jest podstawowym źródłem informacji na temat aktualizowalnej pomocy dla modułu.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="dfe5d-106">Zawiera lokalizację plików pomocy dla modułów, obsługiwanych kultur interfejsu użytkownika i numer wersji, które aktualizowalnej pomocy używa w celu ustalenia, czy użytkownik ma najnowszych plików pomocy.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="dfe5d-107">Każdy moduł ma tylko jeden plik HelpInfo XML, nawet jeśli moduł zawiera wiele plików pomocy dla różnych kultur interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="dfe5d-108">Autora modułu tworzy plik HelpInfo XML i umieszcza je w lokalizacji internetowej, który jest określony przez **HelpInfoUri** klucza w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="dfe5d-109">Gdy moduł pliki pomocy są aktualizowane i przekazać, autora modułu aktualizuje plik HelpInfo XML i zastępuje oryginalny plik HelpInfo XML nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="dfe5d-110">Koniecznie dokładnie utrzymania pliku HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="dfe5d-111">Jeśli przekazywanie nowych plików, ale nie pamięta ma zostać zwiększony wersji aktualizowalnej pomocy nie pobierze nowych plików na komputerach użytkowników.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="dfe5d-112">Jeśli dodasz plików pomocy dla nowych kultura interfejsu użytkownika, ale nie należy zaktualizować plik HelpInfo XML lub umieścić go w poprawnej lokalizacji, aktualizowalnej pomocy nie pobierze nowe pliki.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dfe5d-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dfe5d-113">In this section</span></span>

<span data-ttu-id="dfe5d-114">Ta sekcja zawiera następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="dfe5d-115">Schemat HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="dfe5d-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="dfe5d-116">HelpInfo XML przykładowy plik</span><span class="sxs-lookup"><span data-stu-id="dfe5d-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="dfe5d-117">Jak nazwać plik HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="dfe5d-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="dfe5d-118">Jak skonfigurować numery wersji HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="dfe5d-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="dfe5d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfe5d-119">See Also</span></span>

[<span data-ttu-id="dfe5d-120">Obsługa aktualizowalnej pomocy</span><span class="sxs-lookup"><span data-stu-id="dfe5d-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)