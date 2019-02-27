---
title: Obsługa pomocy Online | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848153"
---
# <a name="supporting-online-help"></a><span data-ttu-id="33f8e-102">Obsługa pomocy online</span><span class="sxs-lookup"><span data-stu-id="33f8e-102">Supporting Online Help</span></span>

<span data-ttu-id="33f8e-103">Począwszy od programu Windows PowerShell 3.0, istnieją dwa sposoby obsługi `Get-Help` funkcja Online dla poleceń programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33f8e-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="33f8e-104">W tym temacie wyjaśniono, jak zaimplementować tę funkcję dla różnych typów.</span><span class="sxs-lookup"><span data-stu-id="33f8e-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="33f8e-105">Temat pomocy Online</span><span class="sxs-lookup"><span data-stu-id="33f8e-105">About Online Help</span></span>

<span data-ttu-id="33f8e-106">Pomoc online zawsze było to ważna część programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33f8e-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="33f8e-107">Mimo że `Get-Help` polecenie cmdlet wyświetla Pomoc w wierszu polecenia tak, wielu użytkowników środowisko odczytu w trybie online, w tym kodowania kolorami, hiperłącza i udostępniania pomysły w sekcji Zawartość społeczności i dokumentów na podstawie typu wiki.</span><span class="sxs-lookup"><span data-stu-id="33f8e-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="33f8e-108">Co najważniejsze przed pojawieniu aktualizowalnej pomocy pomocy online pod warunkiem najnowszą wersję plików pomocy.</span><span class="sxs-lookup"><span data-stu-id="33f8e-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="33f8e-109">Pojawienie aktualizowalnej pomocy w środowisku Windows PowerShell 3.0 pomocy online nadal odgrywa kluczową rolę.</span><span class="sxs-lookup"><span data-stu-id="33f8e-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="33f8e-110">Oprócz elastyczne komfortu pomocy online udostępnia pomoc dla użytkowników, którzy nie obsługują lub nie można użyć aktualizowalnej pomocy do pobrania tematy Pomocy.</span><span class="sxs-lookup"><span data-stu-id="33f8e-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="33f8e-111">Jak Get-Help-działa w trybie Online</span><span class="sxs-lookup"><span data-stu-id="33f8e-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="33f8e-112">Aby ułatwić użytkownikom znajdowanie online tematy pomocy dla poleceń, `Get-Help` polecenie ma parametr Online, który spowoduje otwarcie wersji online tematu Pomocy dotyczącego polecenia w użytkownika domyślnej przeglądarki internetowej.</span><span class="sxs-lookup"><span data-stu-id="33f8e-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="33f8e-113">Na przykład następujące polecenie otwiera online tematu Pomocy dotyczącego `Invoke-Command` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33f8e-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="33f8e-114">Aby zaimplementować `Get-Help` -Online, `Get-Help` polecenia cmdlet wygląda dla zasobów identyfikator URI (Uniform) dla wersji online tematu pomocy w następujących lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="33f8e-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="33f8e-115">Pierwszy link w sekcji linki powiązane tematu pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="33f8e-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="33f8e-116">Temat pomocy musi być zainstalowany na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33f8e-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="33f8e-117">Ta funkcja została wprowadzona w programie Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="33f8e-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="33f8e-118">Właściwości HelpUri dowolnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="33f8e-118">The HelpUri property of any command.</span></span> <span data-ttu-id="33f8e-119">Właściwości HelpUri jest dostępna, nawet wtedy, gdy tematu Pomocy dotyczącego polecenia nie jest zainstalowany na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33f8e-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="33f8e-120">Ta funkcja została wprowadzona w środowisku Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="33f8e-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="33f8e-121">`Get-Help` sprawdza, czy identyfikatora URI w pierwszy wpis w sekcji linki powiązane, zanim uzyska wartość właściwości HelpUri.</span><span class="sxs-lookup"><span data-stu-id="33f8e-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="33f8e-122">Jeśli wartość właściwości jest nieprawidłowa lub została zmieniona, można zastąpić go przez wprowadzenie innej wartości w pierwszym łącza powiązane.</span><span class="sxs-lookup"><span data-stu-id="33f8e-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="33f8e-123">Jednak pierwszy łącza pokrewnego działa tylko wtedy, gdy tematy pomocy są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33f8e-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="33f8e-124">Dodawanie identyfikatora URI do pierwszego łącza powiązane tematu pomocy polecenia</span><span class="sxs-lookup"><span data-stu-id="33f8e-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="33f8e-125">Może obsługiwać `Get-Help` -Online dla dowolnego polecenia, dodając prawidłowy identyfikator URI do pierwszej pozycji w sekcji linki powiązane tematu pomocy oparty na składni XML dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="33f8e-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="33f8e-126">Ta opcja jest prawidłowa tylko w opartych na języku XML tematy pomocy i działa tylko wtedy, gdy tematu Pomocy jest zainstalowany na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33f8e-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="33f8e-127">Po zainstalowaniu tematu pomocy, natomiast identyfikatora URI jest wypełniana, ta wartość ma pierwszeństwo przed **HelpUri** właściwość polecenia.</span><span class="sxs-lookup"><span data-stu-id="33f8e-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="33f8e-128">Aby uzyskać informacje oparte na języku XML tematy Pomocy dotyczące poleceń, zobacz [Writing XML-Based tematy pomocy dla poleceń](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="33f8e-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="33f8e-129">Aby obsługiwać tę funkcję, identyfikator URI musi znajdować się w `maml:uri` elementu w pierwszym `maml:relatedLinks/maml:navigationLink` element `maml:relatedLinks` elementu.</span><span class="sxs-lookup"><span data-stu-id="33f8e-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="33f8e-130">Następujący kody XML pokazuje poprawne położenie identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="33f8e-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="33f8e-131">"Wersja Online:" tekst w `maml:linkText` element jest najlepszym rozwiązaniem, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="33f8e-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="33f8e-132">Dodawanie właściwości HelpUri do polecenia</span><span class="sxs-lookup"><span data-stu-id="33f8e-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="33f8e-133">W tej sekcji przedstawiono sposób dodawania właściwości HelpUri do poleceń o różnych typach.</span><span class="sxs-lookup"><span data-stu-id="33f8e-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="33f8e-134">Dodawanie właściwości HelpUri do polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="33f8e-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="33f8e-135">Dla poleceń cmdlet napisane w C#, Dodaj **HelpUri** atrybutów klasy polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33f8e-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="33f8e-136">Wartość atrybutu musi być identyfikator URI, który rozpoczyna się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="33f8e-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="33f8e-137">Poniższy kod przedstawia atrybutu HelpUri `Get-History` klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33f8e-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="33f8e-138">Dodawanie właściwości HelpUri do funkcji zaawansowanych</span><span class="sxs-lookup"><span data-stu-id="33f8e-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="33f8e-139">Zaawansowane funkcje, można dodać **HelpUri** właściwości **CmdletBinding** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="33f8e-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="33f8e-140">Wartość właściwości musi być identyfikator URI, który rozpoczyna się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="33f8e-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="33f8e-141">Poniższy kod przedstawia atrybutu HelpUri funkcji New-kalendarza</span><span class="sxs-lookup"><span data-stu-id="33f8e-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="33f8e-142">Dodawanie atrybutu HelpUri do polecenia CIM</span><span class="sxs-lookup"><span data-stu-id="33f8e-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="33f8e-143">W przypadku poleceń CIM, dodać **HelpUri** atrybutu **CmdletMetadata** elementu w pliku CDXML.</span><span class="sxs-lookup"><span data-stu-id="33f8e-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="33f8e-144">Wartość atrybutu musi być identyfikator URI, który rozpoczyna się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="33f8e-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="33f8e-145">Poniższy kod przedstawia atrybutu HelpUri polecenia CIM rozpoczęcia debugowania</span><span class="sxs-lookup"><span data-stu-id="33f8e-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="33f8e-146">Dodawanie atrybutu HelpUri do przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="33f8e-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="33f8e-147">W przypadku przepływów pracy, które są napisane w języku środowiska Windows PowerShell, należy dodać **. ExternalHelp** dyrektywy komentarza do kodu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="33f8e-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="33f8e-148">Wartość dyrektywy musi być identyfikator URI, który rozpoczyna się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="33f8e-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="33f8e-149">Właściwości HelpUri nie jest obsługiwana dla przepływów pracy opartych na XAML w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33f8e-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="33f8e-150">Poniższy kod przedstawia. Dyrektywa ExternalHelp w plik przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="33f8e-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```