---
title: Jak przetestować aktualizowalnej pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845927"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="3eb1b-102">Jak przetestować aktualizowalną pomoc</span><span class="sxs-lookup"><span data-stu-id="3eb1b-102">How to Test Updatable Help</span></span>

<span data-ttu-id="3eb1b-103">W tym temacie opisano sposoby testowania aktualizowalnej pomocy dla modułu.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="3eb1b-104">Za pomocą Verbose, aby wykrywać błędy</span><span class="sxs-lookup"><span data-stu-id="3eb1b-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="3eb1b-105">Po przekazaniu pliku HelpInfo XML i pliki CAB dla modułu, testować, uruchamiając [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia **pełne** parametru.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="3eb1b-106">**Pełne** kieruje parametr `Update-Help` zgłosić krytycznych czynności opisane w jego operacje odczytu **HelpInfoUri** klucza w manifeście modułu weryfikowania typów plików w pliku CAB nierozpakowane i umieszczanie plików w katalogu modułu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="3eb1b-107">Po przekazaniu pliku HelpInfo XML i pliki CAB dla modułu, testować, uruchamiając [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia **pełne** parametru.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="3eb1b-108">**Pełne** kieruje parametr `Update-Help` zgłosić krytycznych czynności opisane w jego operacje odczytu **HelpInfoUri** klucza w manifeście modułu weryfikowania typów plików w pliku CAB nierozpakowane i umieszczanie plików w katalogu modułu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="3eb1b-109">Gdy wszystkie komunikaty pełne są rozwiązywane, uruchom `Update-Help` polecenia **debugowania** parametru.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="3eb1b-110">Ten parametr powinien wykryć wszystkie pozostałe problemy z plików aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="3eb1b-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>