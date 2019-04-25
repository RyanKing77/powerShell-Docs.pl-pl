---
title: Format parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068117"
---
# <a name="format-parameters"></a><span data-ttu-id="2c218-102">Parametry formatu</span><span class="sxs-lookup"><span data-stu-id="2c218-102">Format Parameters</span></span>

<span data-ttu-id="2c218-103">W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów, które są używane do formatowania lub do generowania danych.</span><span class="sxs-lookup"><span data-stu-id="2c218-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="2c218-104">Parametr</span><span class="sxs-lookup"><span data-stu-id="2c218-104">Parameter</span></span>|<span data-ttu-id="2c218-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="2c218-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="2c218-106">**As**</span><span class="sxs-lookup"><span data-stu-id="2c218-106">**As**</span></span><br><span data-ttu-id="2c218-107">Typ danych: Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="2c218-107">Data type: Keyword</span></span>|<span data-ttu-id="2c218-108">Implementowanie tego parametru, aby określić format danych wyjściowych polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c218-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="2c218-109">Możliwe wartości można na przykład tekstu lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="2c218-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="2c218-110">**Binary**</span><span class="sxs-lookup"><span data-stu-id="2c218-110">**Binary**</span></span><br><span data-ttu-id="2c218-111">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2c218-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="2c218-112">Implementowanie tego parametru, aby wskazać, że polecenie cmdlet obsługuje wartości binarnych.</span><span class="sxs-lookup"><span data-stu-id="2c218-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="2c218-113">**Kodowanie**</span><span class="sxs-lookup"><span data-stu-id="2c218-113">**Encoding**</span></span><br><span data-ttu-id="2c218-114">Typ danych: Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="2c218-114">Data type: Keyword</span></span>|<span data-ttu-id="2c218-115">Implementowanie tego parametru, aby określić typu kodowania, która jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="2c218-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="2c218-116">Możliwe wartości można na przykład ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bajt i ciąg.</span><span class="sxs-lookup"><span data-stu-id="2c218-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="2c218-117">**Nowy wiersz**</span><span class="sxs-lookup"><span data-stu-id="2c218-117">**NewLine**</span></span><br><span data-ttu-id="2c218-118">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2c218-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="2c218-119">Implementowanie tego parametru i znaki nowego wiersza są obsługiwane, jeśli parametr jest określony.</span><span class="sxs-lookup"><span data-stu-id="2c218-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="2c218-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="2c218-120">**ShortName**</span></span><br><span data-ttu-id="2c218-121">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2c218-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="2c218-122">Implementowanie tego parametru, krótkich nazw są obsługiwane, jeśli parametr jest określony.</span><span class="sxs-lookup"><span data-stu-id="2c218-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="2c218-123">**Szerokość**</span><span class="sxs-lookup"><span data-stu-id="2c218-123">**Width**</span></span><br><span data-ttu-id="2c218-124">Typ danych: Int32</span><span class="sxs-lookup"><span data-stu-id="2c218-124">Data type: Int32</span></span>|<span data-ttu-id="2c218-125">Implementowanie tego parametru, użytkownik może określić szerokość urządzenia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="2c218-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="2c218-126">**OPAKOWYWANIE**</span><span class="sxs-lookup"><span data-stu-id="2c218-126">**Wrap**</span></span><br><span data-ttu-id="2c218-127">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2c218-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="2c218-128">Implementowanie tego parametru, zawijania tekstu jest obsługiwana, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="2c218-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="2c218-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c218-129">See Also</span></span>

[<span data-ttu-id="2c218-130">Parametry polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c218-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="2c218-131">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c218-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="2c218-132">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c218-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
