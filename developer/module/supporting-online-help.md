---
title: Obsługa pomocy online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848079"
---
# <a name="supporting-online-help"></a><span data-ttu-id="83eb6-102">Obsługa pomocy online</span><span class="sxs-lookup"><span data-stu-id="83eb6-102">Supporting Online Help</span></span>

<span data-ttu-id="83eb6-103">Począwszy od programu Windows PowerShell 3,0, istnieją dwa sposoby obsługi `Get-Help` funkcji online dla poleceń programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83eb6-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="83eb6-104">W tym temacie wyjaśniono, jak zaimplementować tę funkcję dla różnych typów poleceń.</span><span class="sxs-lookup"><span data-stu-id="83eb6-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="83eb6-105">Informacje o pomocy online</span><span class="sxs-lookup"><span data-stu-id="83eb6-105">About Online Help</span></span>

<span data-ttu-id="83eb6-106">Pomoc online była zawsze istotną częścią programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83eb6-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="83eb6-107">Mimo że `Get-Help` polecenie cmdlet wyświetla tematy pomocy w wierszu polecenia, wielu użytkowników preferuje środowisko odczytywania w trybie online, w tym kolorowanie, hiperłącza i udostępnianie pomysłów w treści społeczności i dokumentach opartych na witrynie typu wiki.</span><span class="sxs-lookup"><span data-stu-id="83eb6-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="83eb6-108">Co najważniejsze, przed pojawieniu aktualizowalnej pomocy, pomoc online zapewniała najbardziej aktualną wersję plików pomocy.</span><span class="sxs-lookup"><span data-stu-id="83eb6-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="83eb6-109">Dzięki pojawieniu aktualizowalnej pomocy w programie Windows PowerShell 3,0 pomoc online nadal odgrywa istotną rolę.</span><span class="sxs-lookup"><span data-stu-id="83eb6-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="83eb6-110">Oprócz elastycznego środowiska użytkownika Pomoc Online zapewnia użytkownikom, którzy nie są lub nie mogą używać aktualizowalnej pomocy do pobierania tematów pomocy.</span><span class="sxs-lookup"><span data-stu-id="83eb6-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="83eb6-111">Jak działa metoda Get-Help-online</span><span class="sxs-lookup"><span data-stu-id="83eb6-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="83eb6-112">Aby ułatwić użytkownikom znalezienie tematów pomocy online dla poleceń, `Get-Help` polecenie zawiera parametr online, który otwiera informacje o wersji online tematu pomocy dla polecenia w domyślnej przeglądarce internetowej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83eb6-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="83eb6-113">Na przykład następujące polecenie otwiera temat pomocy online dla tego `Invoke-Command` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83eb6-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="83eb6-114">W celu `Get-Help` zaimplementowania trybu `Get-Help` online polecenie cmdlet wyszukuje Uniform Resource Identifier (URI) tematu pomocy dotyczącej wersji online w poniższych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="83eb6-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="83eb6-115">Pierwszy link w sekcji powiązane linki tematu pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="83eb6-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="83eb6-116">Temat pomocy musi być zainstalowany na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83eb6-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="83eb6-117">Ta funkcja została wprowadzona w programie Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="83eb6-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="83eb6-118">Właściwość HelpUri dowolnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="83eb6-118">The HelpUri property of any command.</span></span> <span data-ttu-id="83eb6-119">Właściwość HelpUri jest dostępna, nawet jeśli nie zainstalowano tematu pomocy dla tego polecenia na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83eb6-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="83eb6-120">Ta funkcja została wprowadzona w programie Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="83eb6-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="83eb6-121">`Get-Help`szuka identyfikatora URI w pierwszym wpisie w sekcji powiązane linki przed pobraniem wartości właściwości HelpUri.</span><span class="sxs-lookup"><span data-stu-id="83eb6-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="83eb6-122">Jeśli wartość właściwości jest niepoprawna lub została zmieniona, można ją zastąpić, wprowadzając inną wartość w pierwszym połączonym łączu.</span><span class="sxs-lookup"><span data-stu-id="83eb6-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="83eb6-123">Jednak pierwsze powiązane łącze działa tylko wtedy, gdy tematy pomocy są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83eb6-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="83eb6-124">Dodawanie identyfikatora URI do pierwszego powiązanego linku tematu pomocy polecenia</span><span class="sxs-lookup"><span data-stu-id="83eb6-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="83eb6-125">W trybie online `Get-Help` można obsługiwać dowolne polecenie, dodając prawidłowy identyfikator URI do pierwszego wpisu w sekcji powiązane linki tematu pomocy opartej na języku XML dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="83eb6-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="83eb6-126">Ta opcja jest prawidłowa tylko w tematach pomocy opartych na języku XML i działa tylko po zainstalowaniu tematu pomocy na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83eb6-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="83eb6-127">Gdy zainstalowano temat pomocy i wypełniono identyfikator URI, ta wartość ma pierwszeństwo przed właściwością **HelpUri** polecenia.</span><span class="sxs-lookup"><span data-stu-id="83eb6-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="83eb6-128">Aby obsługiwać tę funkcję, identyfikator URI musi pojawić się `maml:uri` w elemencie pod pierwszym `maml:relatedLinks/maml:navigationLink` elementem w `maml:relatedLinks` elemencie.</span><span class="sxs-lookup"><span data-stu-id="83eb6-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="83eb6-129">Poniższy kod XML przedstawia poprawne umieszczanie identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="83eb6-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="83eb6-130">Tekst "wersja online:" w `maml:linkText` elemencie jest najlepszym rozwiązaniem, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="83eb6-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="83eb6-131">Dodawanie właściwości HelpUri do polecenia</span><span class="sxs-lookup"><span data-stu-id="83eb6-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="83eb6-132">W tej sekcji pokazano, jak dodać właściwość HelpUri do poleceń różnych typów.</span><span class="sxs-lookup"><span data-stu-id="83eb6-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="83eb6-133">Dodawanie właściwości HelpUri do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="83eb6-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="83eb6-134">W przypadku poleceń cmdlet pisanych C#w programie Dodaj atrybut **HelpUri** do klasy poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83eb6-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="83eb6-135">Wartość atrybutu musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="83eb6-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="83eb6-136">Poniższy kod przedstawia atrybut `Get-History` HelpUri klasy cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83eb6-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="83eb6-137">Dodawanie właściwości HelpUri do funkcji zaawansowanej</span><span class="sxs-lookup"><span data-stu-id="83eb6-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="83eb6-138">W przypadku funkcji zaawansowanych Dodaj właściwość **HelpUri** do atrybutu **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="83eb6-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="83eb6-139">Wartość właściwości musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="83eb6-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="83eb6-140">Poniższy kod przedstawia atrybut HelpUri funkcji New-Calendar</span><span class="sxs-lookup"><span data-stu-id="83eb6-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="83eb6-141">Dodawanie atrybutu HelpUri do polecenia CIM</span><span class="sxs-lookup"><span data-stu-id="83eb6-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="83eb6-142">Dla poleceń CIM Dodaj atrybut **HelpUri** do elementu **CMDLETMETADATA** w pliku CDXML.</span><span class="sxs-lookup"><span data-stu-id="83eb6-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="83eb6-143">Wartość atrybutu musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="83eb6-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="83eb6-144">Poniższy kod przedstawia atrybut HelpUri polecenia Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="83eb6-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="83eb6-145">Dodawanie atrybutu HelpUri do przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="83eb6-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="83eb6-146">W przypadku przepływów pracy, które są zapisywane w języku Windows PowerShell, Dodaj **. ExternalHelp** komentarz dyrektywy do kodu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83eb6-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="83eb6-147">Wartość dyrektywy musi być identyfikatorem URI rozpoczynającym się od ciągu "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="83eb6-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="83eb6-148">Właściwość HelpUri nie jest obsługiwana w przypadku przepływów pracy opartych na języku XAML w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83eb6-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="83eb6-149">Poniższy kod przedstawia. ExternalHelp dyrektywę w pliku przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83eb6-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```