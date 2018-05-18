---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxFileLine zasobów
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="98a38-103">DSC dla systemu Linux nxFileLine zasobów</span><span class="sxs-lookup"><span data-stu-id="98a38-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="98a38-104">**NxFileLine** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania wierszy w pliku konfiguracji w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="98a38-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="98a38-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98a38-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="98a38-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="98a38-106">Properties</span></span>

|  <span data-ttu-id="98a38-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="98a38-107">Property</span></span> |  <span data-ttu-id="98a38-108">Opis</span><span class="sxs-lookup"><span data-stu-id="98a38-108">Description</span></span> |
|---|---|
| <span data-ttu-id="98a38-109">Ścieżka pliku</span><span class="sxs-lookup"><span data-stu-id="98a38-109">FilePath</span></span>| <span data-ttu-id="98a38-110">Pełna ścieżka do pliku, aby zarządzać wierszy w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="98a38-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="98a38-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="98a38-111">ContainsLine</span></span>| <span data-ttu-id="98a38-112">Wiersz, aby upewnić się, istnieje w pliku.</span><span class="sxs-lookup"><span data-stu-id="98a38-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="98a38-113">Ten wiersz zostanie dołączona do pliku, jeśli nie istnieje w pliku.</span><span class="sxs-lookup"><span data-stu-id="98a38-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="98a38-114">**ContainsLine** jest wymagane, ale może być ustawiony na ciąg pusty ("ContainsLine =" "), jeśli nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="98a38-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="98a38-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="98a38-115">DoesNotContainPattern</span></span>| <span data-ttu-id="98a38-116">Wzorzec wyrażenia regularnego wierszy, które nie powinny istnieć w pliku.</span><span class="sxs-lookup"><span data-stu-id="98a38-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="98a38-117">Dla wszystkich wierszy, które znajdują się w pliku pasuje do tego wyrażenia regularnego wiersz zostaną usunięte z pliku.</span><span class="sxs-lookup"><span data-stu-id="98a38-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="98a38-118">dependsOn</span><span class="sxs-lookup"><span data-stu-id="98a38-118">DependsOn</span></span> | <span data-ttu-id="98a38-119">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="98a38-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="98a38-120">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="98a38-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="98a38-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="98a38-121">Example</span></span>

<span data-ttu-id="98a38-122">W tym przykładzie pokazano, za pomocą **nxFileLine** zasobów, aby skonfigurować `/etc/sudoers` pliku, upewniając się, że użytkownik: requiretty nie skonfigurowano monuser.</span><span class="sxs-lookup"><span data-stu-id="98a38-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```