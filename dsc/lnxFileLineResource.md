---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxFileLine
ms.openlocfilehash: f2a989dd3a6746948e09ba94e279c02be8ebe2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893301"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="302fd-103">DSC dla systemu Linux zasób nxFileLine</span><span class="sxs-lookup"><span data-stu-id="302fd-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="302fd-104">**NxFileLine** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm do zarządzania wierszy w pliku konfiguracji w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="302fd-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="302fd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="302fd-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="302fd-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="302fd-106">Properties</span></span>

|  <span data-ttu-id="302fd-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="302fd-107">Property</span></span> |  <span data-ttu-id="302fd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="302fd-108">Description</span></span> |
|---|---|
| <span data-ttu-id="302fd-109">Ścieżka pliku</span><span class="sxs-lookup"><span data-stu-id="302fd-109">FilePath</span></span>| <span data-ttu-id="302fd-110">Pełna ścieżka do pliku, aby zarządzać linie w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="302fd-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="302fd-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="302fd-111">ContainsLine</span></span>| <span data-ttu-id="302fd-112">Aby upewnić się, istnieje wiersz w pliku.</span><span class="sxs-lookup"><span data-stu-id="302fd-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="302fd-113">Ten wiersz zostaną dołączone do pliku, jeśli nie istnieje w pliku.</span><span class="sxs-lookup"><span data-stu-id="302fd-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="302fd-114">**ContainsLine** jest wymagane, ale można ustawić na ciąg pusty (`ContainsLine = ""`) Jeśli nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="302fd-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="302fd-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="302fd-115">DoesNotContainPattern</span></span>| <span data-ttu-id="302fd-116">Wzorzec wyrażenia regularnego dla wierszy, które nie powinny istnieć w pliku.</span><span class="sxs-lookup"><span data-stu-id="302fd-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="302fd-117">Dla wszystkich wierszy, które istnieją w pliku, które pasują do tego wyrażenia regularnego wiersz zostaną usunięte z pliku.</span><span class="sxs-lookup"><span data-stu-id="302fd-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="302fd-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="302fd-118">DependsOn</span></span> | <span data-ttu-id="302fd-119">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="302fd-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="302fd-120">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="302fd-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="302fd-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="302fd-121">Example</span></span>

<span data-ttu-id="302fd-122">Ten przykład demonstruje użycie **nxFileLine** zasobów, aby skonfigurować `/etc/sudoers` pliku, upewniając się, że użytkownik: requiretty nie skonfigurowano monuser.</span><span class="sxs-lookup"><span data-stu-id="302fd-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```