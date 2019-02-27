---
title: Tworzenie niestandardowego interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852213"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="75d94-102">Tworzenie niestandardowego interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="75d94-102">Creating a custom user interface</span></span>

<span data-ttu-id="75d94-103">Windows PowerShell udostępnia, klasy abstrakcyjne i interfejsy, które pozwalają tworzyć niestandardowe interaktywnego interfejsu użytkownika, który jest hostem aparatu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75d94-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="75d94-104">Aby utworzyć niestandardowy interfejs użytkownika, należy zaimplementować [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) klasy.</span><span class="sxs-lookup"><span data-stu-id="75d94-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="75d94-105">Opcjonalnie możesz również wdrożyć [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)i [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) klasy i [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) i [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="75d94-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
