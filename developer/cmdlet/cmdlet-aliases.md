---
title: Aliasy polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849966"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="08699-102">Aliasy poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="08699-102">Cmdlet Aliases</span></span>

<span data-ttu-id="08699-103">Aliasy polecenia cmdlet można użyć, aby ulepszyć środowisko użytkownika polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08699-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="08699-104">Można dodawać aliasów do często używanych poleceń cmdlet, aby zmniejszyć, wpisując i ułatwiają wykonywanie zadań szybko.</span><span class="sxs-lookup"><span data-stu-id="08699-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="08699-105">Może zawierać aliasy wbudowanych poleceń cmdlet lub użytkownicy mogą definiować własnych niestandardowych aliasów.</span><span class="sxs-lookup"><span data-stu-id="08699-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="08699-106">Na przykład [Get-Command](/powershell/module/microsoft.powershell.core/get-command) polecenie cmdlet ma wbudowaną `gcm` aliasu.</span><span class="sxs-lookup"><span data-stu-id="08699-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="08699-107">Aliasy umożliwia również dodać nazwy poleceń w innych językach, tak, aby użytkownicy nie mają się nowych poleceń.</span><span class="sxs-lookup"><span data-stu-id="08699-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="08699-108">Wytyczne dotyczące aliasu</span><span class="sxs-lookup"><span data-stu-id="08699-108">Alias Guidelines</span></span>

<span data-ttu-id="08699-109">Podczas tworzenia aliasów wbudowanych poleceń cmdlet, należy przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="08699-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="08699-110">Przed przypisaniem aliasy, uruchom program Windows PowerShell, a następnie uruchom [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) polecenia cmdlet, aby wyświetlić aliasy, które są już używane.</span><span class="sxs-lookup"><span data-stu-id="08699-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="08699-111">Dołącz prefiks alias, który odwołuje się polecenie Nazwa polecenia cmdlet i sufiks alias, który odwołuje się do rzeczownikiem nazwa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08699-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="08699-112">Na przykład alias `Import-Module` polecenie cmdlet jest "ipmo".</span><span class="sxs-lookup"><span data-stu-id="08699-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="08699-113">Aby uzyskać listę wszystkich poleceń i ich aliasy, zobacz [czasowników poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="08699-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="08699-114">W przypadku poleceń cmdlet, które mają ten sam zlecenie zawiera ten sam prefiks aliasu.</span><span class="sxs-lookup"><span data-stu-id="08699-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="08699-115">Na przykład aliasów dla wszystkich Windows poleceń cmdlet programu PowerShell zawierających zlecenie "Get" w nazwie używać prefiksu "g".</span><span class="sxs-lookup"><span data-stu-id="08699-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="08699-116">Dla poleceń cmdlet, które mają ten sam rzeczownik zawiera ten sam sufiksu aliasu.</span><span class="sxs-lookup"><span data-stu-id="08699-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="08699-117">Na przykład aliasów dla wszystkich programu Windows PowerShell polecenia cmdlet które mają rzeczownik "Sesja" w nazwie Użyj sufiksu "sn".</span><span class="sxs-lookup"><span data-stu-id="08699-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="08699-118">Dla poleceń cmdlet, które są równoważne poleceń w innych językach Użyj nazwy polecenia.</span><span class="sxs-lookup"><span data-stu-id="08699-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="08699-119">Ogólnie rzecz biorąc należy możliwie krótkie aliasów.</span><span class="sxs-lookup"><span data-stu-id="08699-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="08699-120">Upewnij się, że alias ma co najmniej jeden znak distinct dla zlecenia i jeden znak distinct dla rzeczownikiem.</span><span class="sxs-lookup"><span data-stu-id="08699-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="08699-121">Dodawanie większej liczby znaków, zgodnie z potrzebami unikatowość alias.</span><span class="sxs-lookup"><span data-stu-id="08699-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="08699-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08699-122">See Also</span></span>

[<span data-ttu-id="08699-123">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08699-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
