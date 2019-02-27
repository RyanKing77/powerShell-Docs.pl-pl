---
title: Jak dodać opis polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851429"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="cee71-102">Jak dodać opis polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="cee71-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="cee71-103">W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcji Opis pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cee71-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="cee71-104">W pliku pomocy tej zawartości zostanie dodany do węzła polecenie dla każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cee71-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="cee71-105">Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cee71-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="cee71-106">Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cee71-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="cee71-107">Aby dodać opis</span><span class="sxs-lookup"><span data-stu-id="cee71-107">To Add a Description</span></span>

- <span data-ttu-id="cee71-108">Rozpocznij od wyjaśniających podstawowe funkcje polecenia cmdlet, które bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="cee71-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="cee71-109">W wielu przypadkach można wyjaśnić terminów używanych w nazwa polecenia cmdlet i zilustrowania koncepcji zaznajomiony z przykładem.</span><span class="sxs-lookup"><span data-stu-id="cee71-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="cee71-110">Na przykład jeśli polecenie cmdlet dołącza dane do pliku, wyjaśniono, dodaje dane na końcu istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="cee71-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="cee71-111">Aby znaleźć wszystkie funkcje polecenia cmdlet, przejrzyj listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="cee71-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="cee71-112">Opisano podstawową funkcją polecenia cmdlet, a następnie dołącz inne funkcje i możliwości.</span><span class="sxs-lookup"><span data-stu-id="cee71-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="cee71-113">Załóżmy na przykład, jeśli jest główna funkcja polecenia cmdlet, aby zmienić jedną właściwość, ale polecenia cmdlet można zmienić wszystkie właściwości, więc w szczegółowy opis.</span><span class="sxs-lookup"><span data-stu-id="cee71-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="cee71-114">Jeśli parametry polecenia cmdlet umożliwiają użytkownikom uzyskania informacji na różne sposoby, opisano je.</span><span class="sxs-lookup"><span data-stu-id="cee71-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="cee71-115">Zawierają informacje dotyczące sposobów, w których użytkownicy mogą używać polecenia cmdlet, oprócz używa oczywiste.</span><span class="sxs-lookup"><span data-stu-id="cee71-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="cee71-116">Na przykład, można użyć obiektu, `Get-Host` polecenie cmdlet pobiera, aby zmienić kolor tekstu w oknie wiersza polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cee71-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="cee71-117">Przykład:  " `Get-Acl` Polecenie cmdlet pobiera obiekty reprezentujące deskryptor zabezpieczeń plik lub zasób.</span><span class="sxs-lookup"><span data-stu-id="cee71-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="cee71-118">Deskryptor zabezpieczeń zawiera listy kontroli dostępu (ACL) zasobu.</span><span class="sxs-lookup"><span data-stu-id="cee71-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="cee71-119">Listy ACL określa uprawnienia, które użytkownicy i grupy użytkowników mają dostęp do zasobu".</span><span class="sxs-lookup"><span data-stu-id="cee71-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="cee71-120">Szczegółowy opis powinna opisywać polecenia cmdlet, ale nie powinien on zawierać pojęcia, które korzysta z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cee71-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="cee71-121">Umieść definicje pojęcie w dodatkowe uwagi.</span><span class="sxs-lookup"><span data-stu-id="cee71-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="cee71-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cee71-122">See Also</span></span>

[<span data-ttu-id="cee71-123">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cee71-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
