---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222058"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="a57b2-102">Instrukcje dotyczące odinstalowywania</span><span class="sxs-lookup"><span data-stu-id="a57b2-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="a57b2-103">Przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a57b2-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="a57b2-104">Otwórz **wiersza polecenia.**</span><span class="sxs-lookup"><span data-stu-id="a57b2-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="a57b2-105">Uruchom [uruchamianie autonomicznej usługi Windows Update](https://support.microsoft.com/en-us/kb/934307) w sposób przedstawiony poniżej:</span><span class="sxs-lookup"><span data-stu-id="a57b2-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="a57b2-106">W systemie Windows Server 2012 R2 i Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="a57b2-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="a57b2-107">W systemie Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="a57b2-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="a57b2-108">W systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:</span><span class="sxs-lookup"><span data-stu-id="a57b2-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="a57b2-109">Za pomocą Panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="a57b2-109">Using Control Panel</span></span>
1.  <span data-ttu-id="a57b2-110">Otwórz **w Panelu sterowania.**</span><span class="sxs-lookup"><span data-stu-id="a57b2-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="a57b2-111">Otwórz **programy**, następnie otwórz **Odinstaluj program.**</span><span class="sxs-lookup"><span data-stu-id="a57b2-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="a57b2-112">Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**</span><span class="sxs-lookup"><span data-stu-id="a57b2-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="a57b2-113">Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a57b2-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="a57b2-114">Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="a57b2-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="a57b2-115">Kliknij przycisk **odinstalować.**</span><span class="sxs-lookup"><span data-stu-id="a57b2-115">Click **Uninstall.**</span></span>
