---
title: Filtr parametrów wejściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067692"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="8e273-102">Parametry filtru danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="8e273-102">Input Filter Parameters</span></span>

<span data-ttu-id="8e273-103">Polecenia cmdlet można zdefiniować `Filter`, `Include`, i `Exclude` parametry, które filtrowania zestawu danych wejściowych obiektów, które ma wpływ na polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e273-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="8e273-104">Zazwyczaj, zestaw danych wejściowych obiektów jest określane przez `InputObject`, `Path`, lub `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="8e273-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="8e273-105">Na przykład można mieć polecenia cmdlet `Path` parametr, który akceptuje wiele ścieżek przy użyciu symboli wieloznacznych i poszczególnych punktów ścieżki do obiektu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="8e273-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="8e273-106">Używane wspólnie, `Filter`, `Include`, i `Exclude` dalszej parametrów kwalifikowania ścieżki, polecenie cmdlet działa na każdym razem jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8e273-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="8e273-107">Dołączanie i wykluczanie parametrów</span><span class="sxs-lookup"><span data-stu-id="8e273-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="8e273-108">`Include` i `Exclude` parametry zidentyfikować obiekty, które są dołączone lub wykluczone z zestawu danych wejściowych obiektów przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e273-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="8e273-109">Użyj tych parametrów, gdy filtr może być wyrażona w języku standardowych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="8e273-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="8e273-110">(Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [obsługi symboli wieloznacznych w parametrach polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` Parametr zawiera wszystkie obiekty, których nazwy są zgodne z filtrem dołączania.</span><span class="sxs-lookup"><span data-stu-id="8e273-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="8e273-111">`Exclude` Parametru nie obejmuje wszystkie obiekty, których nazwy są zgodne z filtrem.</span><span class="sxs-lookup"><span data-stu-id="8e273-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="8e273-112">Parametr filtru</span><span class="sxs-lookup"><span data-stu-id="8e273-112">Filter Parameter</span></span>

<span data-ttu-id="8e273-113">`Filter` Parametr określa filtr, który nie jest wyrażona w języku standardowych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="8e273-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="8e273-114">Na przykład interfejsy usługi Active Directory (ADSI) lub SQL filtry mogą być przekazywane do polecenia cmdlet, za pośrednictwem jego `Filter` parametru.</span><span class="sxs-lookup"><span data-stu-id="8e273-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="8e273-115">W poleceniach cmdlet dostarczane przez środowisko Windows PowerShell te filtry są określane przez dostawców środowiska Windows PowerShell, których należy użyć polecenia cmdlet dostępu do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="8e273-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="8e273-116">Każdy dostawca definiuje zazwyczaj ma własny filtr.</span><span class="sxs-lookup"><span data-stu-id="8e273-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="8e273-117">Filtrowanie, jeśli nie ustawiono zestawu obiektów danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="8e273-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="8e273-118">Jeśli nie ustawiono obiektów danych wejściowych jest określony, oznacza to, zwykle do filtrowania względem wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e273-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="8e273-119">Aby uzyskać więcej informacji, zobacz[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="8e273-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e273-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e273-120">See Also</span></span>

[<span data-ttu-id="8e273-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e273-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)