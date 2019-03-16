---
title: Deklaracja klasy polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055091"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="1c6cb-102">Deklaracja klasy polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c6cb-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="1c6cb-103">Klasa programu Microsoft .NET Framework jest zadeklarowany jako polecenia cmdlet, określając **polecenia Cmdlet** atrybutu jako metadane dla klasy.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="1c6cb-104">( **Polecenia Cmdlet** atrybut jest tylko wymaganego atrybutu dla wszystkich poleceń cmdlet).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="1c6cb-105">Po określeniu **polecenia Cmdlet** atrybut, możesz określić pary czasownik i rzeczownik, który identyfikuje polecenie cmdlet, aby użytkownik.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="1c6cb-106">Ponadto należy opisać funkcji programu Windows PowerShell, która obsługuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="1c6cb-107">Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1c6cb-108">**Polecenia Cmdlet** atrybutu jest definiowana przez [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="1c6cb-109">Właściwości tej klasy odpowiadają parametrów deklaracji, które są używane w przypadku deklarowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="1c6cb-110">Rzeczowniki</span><span class="sxs-lookup"><span data-stu-id="1c6cb-110">Nouns</span></span>

<span data-ttu-id="1c6cb-111">Rzeczownik polecenia cmdlet określa zasoby, na których działa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="1c6cb-112">Rzeczownikiem odróżnia poleceń cmdlet z innymi poleceniami cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="1c6cb-113">Rzeczowniki w nazwy poleceń cmdlet musi być określone, a w przypadku ogólnych rzeczowników, takich jak *serwera*, warto dodać krótki prefiks, który odróżnia zasobu z poziomu innych zasobów podobne.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="1c6cb-114">Na przykład to nazwa polecenia cmdlet, która obejmuje rzeczownik z prefiksem `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="1c6cb-115">Kombinacja określonych rzeczownik od ogólniejszych zlecenie umożliwia użytkownikowi szybko znaleźć polecenia cmdlet, jego działania, a następnie Zidentyfikuj polecenia cmdlet do jej zasobów, unikając dublowania nazwa polecenia cmdlet niepotrzebne.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="1c6cb-116">Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="1c6cb-117">Zlecenia</span><span class="sxs-lookup"><span data-stu-id="1c6cb-117">Verbs</span></span>

<span data-ttu-id="1c6cb-118">Po określeniu zlecenie, wskazówki dotyczące programowania wymagają użycia jednej z wstępnie zdefiniowanych czasowników, udostępniane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="1c6cb-119">Przy użyciu jednej z tych wstępnie zdefiniowanych czasowników, użytkownik musi zagwarantować spójność między poleceń cmdlet, które piszesz i poleceń cmdlet, które są zapisywane przez firmę Microsoft i innych osób.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="1c6cb-120">Na przykład polecenie "Get" jest używany dla poleceń cmdlet, które pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="1c6cb-121">Aby uzyskać więcej informacji na temat wytycznych dla zleceń zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="1c6cb-122">Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="1c6cb-123">Obsługa programu Windows PowerShell funkcji</span><span class="sxs-lookup"><span data-stu-id="1c6cb-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="1c6cb-124">**Polecenia Cmdlet** atrybut umożliwia również określić, czy Twoje polecenie cmdlet obsługuje niektóre typowe funkcje, które są dostarczane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="1c6cb-125">Obejmuje to obsługę typowych funkcji, takich jak potwierdzenie przez użytkownika opinii (nazywane obsługę funkcji ShouldProcess) oraz dla transakcji.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="1c6cb-126">(Obsługa transakcji została wprowadzona w programie Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="1c6cb-127">Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1c6cb-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="1c6cb-128">Definicja klasy polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c6cb-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="1c6cb-129">Poniższy kod jest definicja klasy polecenia cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="1c6cb-130">Należy zauważyć, że Pascal wielkość liter w wyrazie jest używany i że nazwa klasy zawiera czasownik i rzeczownik, polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="1c6cb-131">Pascal wielkość liter w wyrazie</span><span class="sxs-lookup"><span data-stu-id="1c6cb-131">Pascal Casing</span></span>

<span data-ttu-id="1c6cb-132">Po nadaniu nazwy poleceń cmdlet, użyj Pascal wielkość liter w wyrazie.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="1c6cb-133">Na przykład `Get-Item` i `Get-ItemProperty` polecenia cmdlet pokazują poprawny sposób użycia wielkich liter, podczas nadawania nazw poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c6cb-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c6cb-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c6cb-134">See Also</span></span>

[<span data-ttu-id="1c6cb-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="1c6cb-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="1c6cb-136">Deklaracja CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="1c6cb-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="1c6cb-137">Polecenie cmdlet nazwy</span><span class="sxs-lookup"><span data-stu-id="1c6cb-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="1c6cb-138">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c6cb-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1c6cb-139">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c6cb-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
