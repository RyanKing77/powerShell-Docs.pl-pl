---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Odinstaluj program WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856189"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="0849f-103">Instrukcje dotyczące odinstalowywania</span><span class="sxs-lookup"><span data-stu-id="0849f-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="0849f-104">Przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0849f-104">Using Command Prompt</span></span>

1. <span data-ttu-id="0849f-105">Otwórz **wiersza polecenia.**</span><span class="sxs-lookup"><span data-stu-id="0849f-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="0849f-106">Uruchom [Windows Update autonomicznego uruchamiania](https://support.microsoft.com/en-us/kb/934307) jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="0849f-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="0849f-107">W systemie Windows Server 2012 R2 i Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="0849f-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="0849f-108">W systemie Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="0849f-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="0849f-109">W systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:</span><span class="sxs-lookup"><span data-stu-id="0849f-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="0849f-110">Za pomocą Panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="0849f-110">Using Control Panel</span></span>

1. <span data-ttu-id="0849f-111">Otwórz **w Panelu sterowania.**</span><span class="sxs-lookup"><span data-stu-id="0849f-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="0849f-112">Otwórz **programy**, a następnie otwórz **Odinstaluj program.**</span><span class="sxs-lookup"><span data-stu-id="0849f-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="0849f-113">Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**</span><span class="sxs-lookup"><span data-stu-id="0849f-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="0849f-114">Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="0849f-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="0849f-115">Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="0849f-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="0849f-116">Kliknij przycisk **odinstalować.**</span><span class="sxs-lookup"><span data-stu-id="0849f-116">Click **Uninstall.**</span></span>
