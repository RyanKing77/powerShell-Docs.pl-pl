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
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845724"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="ad47c-102">Deklaracja klasy polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad47c-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="ad47c-103">Klasa programu Microsoft .NET Framework jest zadeklarowany jako polecenia cmdlet, określając **polecenia Cmdlet** atrybutu jako metadane dla klasy.</span><span class="sxs-lookup"><span data-stu-id="ad47c-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="ad47c-104">( **Polecenia Cmdlet** atrybut jest tylko wymaganego atrybutu dla wszystkich poleceń cmdlet).</span><span class="sxs-lookup"><span data-stu-id="ad47c-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="ad47c-105">Po określeniu **polecenia Cmdlet** atrybut, możesz określić pary czasownik i rzeczownik, który identyfikuje polecenie cmdlet, aby użytkownik.</span><span class="sxs-lookup"><span data-stu-id="ad47c-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="ad47c-106">Ponadto należy opisać funkcji programu Windows PowerShell, która obsługuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad47c-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="ad47c-107">Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ad47c-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ad47c-108">**Polecenia Cmdlet** atrybutu jest definiowana przez [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="ad47c-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="ad47c-109">Właściwości tej klasy odpowiadają parametrów deklaracji, które są używane w przypadku deklarowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ad47c-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="ad47c-110">Rzeczowniki</span><span class="sxs-lookup"><span data-stu-id="ad47c-110">Nouns</span></span>

<span data-ttu-id="ad47c-111">Rzeczownik polecenia cmdlet określa zasoby, na których działa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad47c-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="ad47c-112">Rzeczownikiem odróżnia poleceń cmdlet z innymi poleceniami cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad47c-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="ad47c-113">Rzeczowniki w nazwy poleceń cmdlet musi być określone, a w przypadku ogólnych rzeczowników, takich jak *serwera*, warto dodać krótki prefiks, który odróżnia zasobu z poziomu innych zasobów podobne.</span><span class="sxs-lookup"><span data-stu-id="ad47c-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="ad47c-114">Na przykład to nazwa polecenia cmdlet, która obejmuje rzeczownik z prefiksem `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="ad47c-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="ad47c-115">Kombinacja określonych rzeczownik od ogólniejszych zlecenie umożliwia użytkownikowi szybko znaleźć polecenia cmdlet, jego działania, a następnie Zidentyfikuj polecenia cmdlet do jej zasobów, unikając dublowania nazwa polecenia cmdlet niepotrzebne.</span><span class="sxs-lookup"><span data-stu-id="ad47c-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="ad47c-116">Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="ad47c-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="ad47c-117">Zlecenia</span><span class="sxs-lookup"><span data-stu-id="ad47c-117">Verbs</span></span>

<span data-ttu-id="ad47c-118">Po określeniu zlecenie, wskazówki dotyczące programowania wymagają użycia jednej z wstępnie zdefiniowanych czasowników, udostępniane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad47c-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="ad47c-119">Przy użyciu jednej z tych wstępnie zdefiniowanych czasowników, użytkownik musi zagwarantować spójność między poleceń cmdlet, które piszesz i poleceń cmdlet, które są zapisywane przez firmę Microsoft i innych osób.</span><span class="sxs-lookup"><span data-stu-id="ad47c-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="ad47c-120">Na przykład polecenie "Get" jest używany dla poleceń cmdlet, które pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="ad47c-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="ad47c-121">Aby uzyskać więcej informacji na temat wytycznych dla zleceń zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ad47c-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="ad47c-122">Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="ad47c-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="ad47c-123">Obsługa programu Windows PowerShell funkcji</span><span class="sxs-lookup"><span data-stu-id="ad47c-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="ad47c-124">**Polecenia Cmdlet** atrybut umożliwia również określić, czy Twoje polecenie cmdlet obsługuje niektóre typowe funkcje, które są dostarczane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad47c-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="ad47c-125">Obejmuje to obsługę typowych funkcji, takich jak potwierdzenie przez użytkownika opinii (nazywane obsługę funkcji ShouldProcess) oraz dla transakcji.</span><span class="sxs-lookup"><span data-stu-id="ad47c-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="ad47c-126">(Obsługa transakcji została wprowadzona w programie Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="ad47c-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="ad47c-127">Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ad47c-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="ad47c-128">Definicja klasy polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad47c-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="ad47c-129">Poniższy kod jest definicja klasy polecenia cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="ad47c-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="ad47c-130">Należy zauważyć, że Pascal wielkość liter w wyrazie jest używany i że nazwa klasy zawiera czasownik i rzeczownik, polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad47c-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="ad47c-131">Pascal wielkość liter w wyrazie</span><span class="sxs-lookup"><span data-stu-id="ad47c-131">Pascal Casing</span></span>

<span data-ttu-id="ad47c-132">Po nadaniu nazwy poleceń cmdlet, użyj Pascal wielkość liter w wyrazie.</span><span class="sxs-lookup"><span data-stu-id="ad47c-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="ad47c-133">Na przykład `Get-Item` i `Get-ItemProperty` polecenia cmdlet pokazują poprawny sposób użycia wielkich liter, podczas nadawania nazw poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad47c-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad47c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad47c-134">See Also</span></span>

[<span data-ttu-id="ad47c-135">System.Management.Automation.Cmdletattribute</span><span class="sxs-lookup"><span data-stu-id="ad47c-135">System.Management.Automation.Cmdletattribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="ad47c-136">Deklaracja CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="ad47c-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="ad47c-137">Polecenie cmdlet nazwy</span><span class="sxs-lookup"><span data-stu-id="ad47c-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="ad47c-138">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad47c-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ad47c-139">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad47c-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
