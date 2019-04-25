---
title: Przykłady dla programu Windows PowerShell interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082587"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="82276-102">Przykłady interfejsów API programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82276-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="82276-103">Ta sekcja zawiera przykładowy kod, który przedstawia sposób tworzenia obszarach działania, który ogranicza funkcję oraz asynchronicznie Uruchom polecenia przy użyciu puli obszarem działania umożliwiają określanie wartości obszary działania.</span><span class="sxs-lookup"><span data-stu-id="82276-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="82276-104">Microsoft Visual Studio umożliwia tworzenie aplikacji konsolowej, a następnie skopiować kod z tematy w tej sekcji, w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="82276-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="82276-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="82276-105">In This Section</span></span>

<span data-ttu-id="82276-106">[Przykładowe PowerShell01](./windows-powershell01-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt, aby ograniczyć funkcjonalność obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="82276-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="82276-107">Dane wyjściowe w tym przykładzie pokazano, jak ograniczyć tryb języka w obszarze działania, jak Oznacz jako prywatne polecenia cmdlet, jak dodać i polecenia cmdlet remove i dostawców, jak dodać polecenia serwera proxy i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="82276-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="82276-108">[Przykładowe PowerShell02](./windows-powershell02-sample.md) ten przykład pokazuje sposób uruchamiania poleceń asynchronicznie przy użyciu obszary działania puli obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="82276-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="82276-109">Przykład generuje listę poleceń, a następnie uruchomić tych poleceń, podczas gdy aparatu programu Windows PowerShell otwiera obszarem działania z puli, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="82276-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>