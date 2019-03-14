---
title: Przykłady niestandardowego hosta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794148"
---
# <a name="custom-host-samples"></a><span data-ttu-id="9f241-102">Przykłady hosta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="9f241-102">Custom Host Samples</span></span>

<span data-ttu-id="9f241-103">Ta sekcja zawiera przykładowy kod do pisania niestandardowego hosta.</span><span class="sxs-lookup"><span data-stu-id="9f241-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="9f241-104">Microsoft Visual Studio umożliwia tworzenie aplikacji konsolowej, a następnie skopiować kod z tematy w tej sekcji, w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="9f241-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9f241-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9f241-105">In This Section</span></span>

 <span data-ttu-id="9f241-106">[Przykładowe Host01](./host01-sample.md) ten przykład pokazuje sposób implementacji aplikacji hosta, która używa podstawowe niestandardowego hosta.</span><span class="sxs-lookup"><span data-stu-id="9f241-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="9f241-107">[Przykładowe Host02](./host02-sample.md) w tym przykładzie pokazano, jak napisać aplikację hosta, która używa środowiska wykonawczego programu Windows PowerShell, oraz implementacji niestandardowego hosta.</span><span class="sxs-lookup"><span data-stu-id="9f241-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="9f241-108">Aplikacja hosta ustawia kulturę hosta na język niemiecki, przebiegów [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet i wyświetla wynik jako użytkownik je zobaczy przy użyciu pwrsh.exe, a następnie Drukuje bieżące data i godzina w języku niemieckim.</span><span class="sxs-lookup"><span data-stu-id="9f241-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="9f241-109">[Przykładowe Host03](./host03-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="9f241-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="9f241-110">[Przykładowe Host04](./host04-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="9f241-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="9f241-111">Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikom określić wiele opcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="9f241-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="9f241-112">[Przykładowe Host05](./host05-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="9f241-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="9f241-113">Ta aplikacja hosta obsługuje również połączenia z komputerami zdalnymi przy użyciu [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) i [PsSession zakończenia](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f241-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="9f241-114">[Przykładowe Host06](./host06-sample.md) w tym przykładzie pokazano, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="9f241-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="9f241-115">Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu, wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f241-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f241-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f241-116">See Also</span></span>
