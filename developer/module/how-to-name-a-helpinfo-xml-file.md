---
title: Jak nazwać plik HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794811"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="332f7-102">Jak nazwać plik XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="332f7-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="332f7-103">W tym temacie wyjaśniono format plików można aktualizować informacje pomocy, powszechnie znane jako pliki HelpInfo XML wymaganą nazwą.</span><span class="sxs-lookup"><span data-stu-id="332f7-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="332f7-104">Jak nazwać plik XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="332f7-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="332f7-105">Plik HelpInfo XML musi mieć nazwę w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="332f7-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="332f7-106">Dostępne są następujące elementy o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="332f7-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="332f7-107">Modulename: wartość z **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.</span><span class="sxs-lookup"><span data-stu-id="332f7-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="332f7-108">ModuleGUID wartość z **GUID** klucza w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="332f7-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="332f7-109">Na przykład jeśli moduł identyfikator GUID jest 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 Nazwa modułu jest "TestModule", nazwa pliku HelpInfo XML modułu będzie:</span><span class="sxs-lookup"><span data-stu-id="332f7-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`