---
title: Wskazówki dotyczące programowania polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- development guidelines [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], development guidelines
ms.assetid: c30cc3c0-e958-4a8f-b81f-1e38de772f13
caps.latest.revision: 14
ms.openlocfilehash: 89c7682e87fa6f389349fc44275be0d2ffc83957
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068576"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="fb0c5-102">Wskazówki dotyczące projektowania poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="fb0c5-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="fb0c5-103">Tematy w tej sekcji zawierają wskazówki dotyczące programowania, używane do wygenerowania poprawnie sformułowanym poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb0c5-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="fb0c5-104">Wykorzystując typowe funkcje udostępniane przez środowisko uruchomieniowe programu Windows PowerShell i postępując zgodnie z tymi wytycznymi, mogą tworzyć niezawodne polecenia cmdlet przy minimalnym nakładzie pracy i zapewnić spójne środowisko użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fb0c5-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="fb0c5-105">Ponadto będzie zmniejszyć obciążenie testu, ponieważ często używane funkcje wymagają przetestowanie.</span><span class="sxs-lookup"><span data-stu-id="fb0c5-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fb0c5-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fb0c5-106">In This Section</span></span>

- [<span data-ttu-id="fb0c5-107">Wskazówki dotyczące programowania wymagane</span><span class="sxs-lookup"><span data-stu-id="fb0c5-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="fb0c5-108">Wskazówki dotyczące programowania zalecamy</span><span class="sxs-lookup"><span data-stu-id="fb0c5-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="fb0c5-109">Wskazówki dotyczące porad dotyczących programowania</span><span class="sxs-lookup"><span data-stu-id="fb0c5-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="fb0c5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb0c5-110">See Also</span></span>

[<span data-ttu-id="fb0c5-111">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb0c5-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="fb0c5-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb0c5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
