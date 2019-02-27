---
title: Dodawanie programu Windows PowerShell działań do przybornika programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852108"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="b41b9-102">Dodawanie działań programu Windows PowerShell do przybornika programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b41b9-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="b41b9-103">Przed utworzeniem przepływu pracy programu PowerShell za pomocą projektanta przepływów pracy, należy najpierw dodać działania programu PowerShell do przybornika w przepływ pracy programu Visual Studio projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b41b9-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="b41b9-104">Poniższa procedura pokazuje, jak dodać działania z zestawu Microsoft.PowerShell.Core.Activities do przybornika Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b41b9-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="b41b9-105">Dodawanie programu Windows PowerShell działań do przybornika</span><span class="sxs-lookup"><span data-stu-id="b41b9-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="b41b9-106">Utwórz nowy projekt aplikacji konsoli przepływu pracy w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b41b9-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="b41b9-107">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="b41b9-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="b41b9-108">Dodaj nową kartę w przyborniku kliknij prawym przyciskiem myszy w przyborniku, a następnie klikając polecenie **Dodaj zakładkę**i nazwij nową kartę takich jak "Działania programu PowerShell".</span><span class="sxs-lookup"><span data-stu-id="b41b9-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="b41b9-109">Dodawanie karty pozwala grupować oddzielnie od innych narzędzi w przyborniku działań programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b41b9-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="b41b9-110">Na nowej karcie przybornika, kliknij przycisk **wybierz elementy...** . **Wybierz elementy przybornika** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b41b9-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="b41b9-111">W **wybierz elementy przybornika** okno dialogowe, kliknij przycisk **System.Activities** kartę.</span><span class="sxs-lookup"><span data-stu-id="b41b9-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="b41b9-112">Kliknij przycisk **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="b41b9-112">Click **Browse**.</span></span>

7. <span data-ttu-id="b41b9-113">Przejdź do folderu %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, a następnie kliknij dwukrotnie Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="b41b9-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="b41b9-114">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b41b9-114">Click **OK**.</span></span> <span data-ttu-id="b41b9-115">Działania zdefiniowane przez zestaw Microsoft.PowerShell.Core.Activities są teraz dostępne w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="b41b9-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="b41b9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b41b9-116">See Also</span></span>

[<span data-ttu-id="b41b9-117">Pisanie przepływu pracy środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b41b9-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="b41b9-118">Tworzenie przepływu pracy za pomocą programu Windows PowerShell działań</span><span class="sxs-lookup"><span data-stu-id="b41b9-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)