---
title: Pisanie przepływu pracy środowiska Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847796"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="dd55d-102">Pisanie przepływu pracy programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd55d-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="dd55d-103">Przepływ pracy XAML można utworzyć przez dodanie działania udostępnianych przez zestawy programu Windows PowerShell do projektanta przepływów pracy w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dd55d-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="dd55d-104">Następujące zestawy programu Windows PowerShell uwidocznić działania korzystające z przepływu.</span><span class="sxs-lookup"><span data-stu-id="dd55d-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd55d-105">Musi zostać spakowana XAML przepływu pracy jako moduł, jeśli chcesz udostępnić pomocy dla przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dd55d-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="dd55d-106">Aby uzyskać informacje o modułach, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="dd55d-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="dd55d-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="dd55d-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="dd55d-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="dd55d-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="dd55d-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="dd55d-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="dd55d-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="dd55d-113">W następujących tematach opisano sposób tworzenia przepływu pracy przy użyciu działania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd55d-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="dd55d-114">Dodawanie programu Windows PowerShell działań do przybornika programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd55d-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="dd55d-115">Tworzenie przepływu pracy za pomocą programu Windows PowerShell działań</span><span class="sxs-lookup"><span data-stu-id="dd55d-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="dd55d-116">Tworzenie przepływu pracy przy użyciu skryptu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd55d-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="dd55d-117">Importowanie i wywoływania przepływu pracy Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd55d-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="dd55d-118">Tworzenie działania przepływu pracy z polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd55d-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)