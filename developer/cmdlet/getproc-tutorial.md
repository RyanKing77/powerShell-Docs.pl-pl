---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068100"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="defec-102">GetProc — samouczek</span><span class="sxs-lookup"><span data-stu-id="defec-102">GetProc Tutorial</span></span>

<span data-ttu-id="defec-103">Ta sekcja zawiera samouczek tworzenia polecenia cmdlet Get-Proc, która jest bardzo podobne do [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) dostarczane przez środowisko Windows PowerShell polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="defec-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="defec-104">Ten samouczek zawiera fragmenty kodu, które ilustrują implementacji poleceń cmdlet oraz objaśnienia dotyczące kodu.</span><span class="sxs-lookup"><span data-stu-id="defec-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="defec-105">Tematy w tym samouczku</span><span class="sxs-lookup"><span data-stu-id="defec-105">Topics in this Tutorial</span></span>

<span data-ttu-id="defec-106">Tematy w tym samouczku są przeznaczone do przeczytania po kolei, za pomocą każdego tematu, opierając się na co zostało omówione w poprzednim temacie.</span><span class="sxs-lookup"><span data-stu-id="defec-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="defec-107">[Tworzenie polecenia Cmdlet bez parametrów](./creating-a-cmdlet-without-parameters.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które pobiera informacje z komputera lokalnego bez użycia parametrów, a następnie zapisuje informacje do potoku.</span><span class="sxs-lookup"><span data-stu-id="defec-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="defec-108">[Dodawanie parametrów wejściowych tego procesu wiersza polecenia](./adding-parameters-that-process-command-line-input.md) tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc, tak aby polecenie cmdlet może przetwarzać dane wejściowe na podstawie jawnych obiektów przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="defec-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="defec-109">Implementacja opisane tutaj pobiera procesów na podstawie ich nazwy, a następnie zapisuje informacje do potoku.</span><span class="sxs-lookup"><span data-stu-id="defec-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="defec-110">[Dodawanie parametrów tego procesu wejście potokowe](./adding-parameters-that-process-pipeline-input.md) tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc, tak aby polecenie cmdlet może przetwarzać obiektów przekazywane do niego za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="defec-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="defec-111">Polecenia cmdlet wdrażania opisanych tutaj pobiera procesów na podstawie obiektów przekazywane do polecenia cmdlet, a następnie zapisuje informacje do potoku.</span><span class="sxs-lookup"><span data-stu-id="defec-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="defec-112">[Dodawanie niekończące raportowanie błędów do polecenia Cmdlet usługi](./adding-non-terminating-error-reporting-to-your-cmdlet.md) w tej sekcji opisano sposób dodawania niekończące raportów o błędach do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="defec-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="defec-113">Implementacja opisane w tym miejscu wykrywa błędy niekończące, które występują podczas przetwarzania danych wejściowych i zapisuje rekord błędu strumienia błędów.</span><span class="sxs-lookup"><span data-stu-id="defec-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="defec-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="defec-114">See Also</span></span>

[<span data-ttu-id="defec-115">Tworzenie polecenia Cmdlet bez parametrów</span><span class="sxs-lookup"><span data-stu-id="defec-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="defec-116">Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="defec-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="defec-117">Dodając parametry, z których potok przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="defec-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="defec-118">Dodawanie niekończące raportów o błędach do Twojego polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="defec-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="defec-119">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="defec-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
