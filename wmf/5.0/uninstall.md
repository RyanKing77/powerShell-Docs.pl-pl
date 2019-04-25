---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057529"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="81a79-102">Instrukcje dotyczące odinstalowywania</span><span class="sxs-lookup"><span data-stu-id="81a79-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="81a79-103">Przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="81a79-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="81a79-104">Otwórz **wiersza polecenia.**</span><span class="sxs-lookup"><span data-stu-id="81a79-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="81a79-105">Uruchom [Windows Update autonomicznego uruchamiania](https://support.microsoft.com/en-us/kb/934307) jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="81a79-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="81a79-106">W systemie Windows Server 2012 R2 i Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="81a79-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="81a79-107">W systemie Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="81a79-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="81a79-108">W systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:</span><span class="sxs-lookup"><span data-stu-id="81a79-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="81a79-109">Za pomocą Panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="81a79-109">Using Control Panel</span></span>
1.  <span data-ttu-id="81a79-110">Otwórz **w Panelu sterowania.**</span><span class="sxs-lookup"><span data-stu-id="81a79-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="81a79-111">Otwórz **programy**, a następnie otwórz **Odinstaluj program.**</span><span class="sxs-lookup"><span data-stu-id="81a79-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="81a79-112">Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**</span><span class="sxs-lookup"><span data-stu-id="81a79-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="81a79-113">Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="81a79-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="81a79-114">Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="81a79-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="81a79-115">Kliknij przycisk **odinstalować.**</span><span class="sxs-lookup"><span data-stu-id="81a79-115">Click **Uninstall.**</span></span>
