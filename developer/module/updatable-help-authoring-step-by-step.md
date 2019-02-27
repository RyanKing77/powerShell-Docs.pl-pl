---
title: 'Tworzenie aktualizowalnej pomocy: Instrukcje krok po kroku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849833"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="9bf42-102">Tworzenie aktualizowalnej pomocy: instrukcje krok po kroku</span><span class="sxs-lookup"><span data-stu-id="9bf42-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="9bf42-103">Dokumenty ten zawiera listę czynności w procesie tworzenia aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="9bf42-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="9bf42-104">Tworzenie aktualizowalnej pomocy: instrukcje krok po kroku</span><span class="sxs-lookup"><span data-stu-id="9bf42-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="9bf42-105">Aktualizowalnej pomocy jest przeznaczona dla użytkowników końcowych, ale również zapewnia znaczące korzyści związane autorzy modułów i moduły zapisujące pomocy, w tym możliwość dodawania zawartości, napraw błędy, dostarczania w wielu kulturach interfejsu użytkownika i odpowiadać na komentarze użytkowników dotyczące i żądań, po jakim Moduł zostało wysłane.</span><span class="sxs-lookup"><span data-stu-id="9bf42-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="9bf42-106">W tym temacie wyjaśniono, jak spakować i pomocy przekazywania plików dzięki czemu użytkownicy mogą pobierać i zainstalować je przy użyciu [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bf42-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="9bf42-107">W poniższych krokach przedstawiono przegląd procesu obsługi aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="9bf42-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="9bf42-108">Krok 1. Znajdź w witrynie internetowej plików pomocy</span><span class="sxs-lookup"><span data-stu-id="9bf42-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="9bf42-109">Pierwszym krokiem w tworzeniu aktualizowalnej pomocy jest można znaleźć lokalizacji internetowej plików pomocy z modułu.</span><span class="sxs-lookup"><span data-stu-id="9bf42-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="9bf42-110">W rzeczywistości można użyć dwóch różnych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="9bf42-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="9bf42-111">Plik informacji o pomocy usługi modułu (HelpInfo XML - opisanych poniżej) można przechowywać w jednej lokalizacji w Internecie i zawartości pliku CAB pliki pomocy w innej lokalizacji w Internecie.</span><span class="sxs-lookup"><span data-stu-id="9bf42-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="9bf42-112">Wszystkie zawartości pliku CAB pliki pomocy dla modułu musi być w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9bf42-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="9bf42-113">Pliki zawartości pliku CAB pomocy dla różnych modułów można umieścić w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9bf42-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="9bf42-114">Krok 2. Dodaj klucz HelpInfoURI do pliku z manifestu modułu</span><span class="sxs-lookup"><span data-stu-id="9bf42-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="9bf42-115">Dodaj **HelpInfoURI** klucza w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="9bf42-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="9bf42-116">Wartość klucza jest jednolity identyfikator zasobów (URI) lokalizacji pliku informacji HelpInfo XML dla modułu.</span><span class="sxs-lookup"><span data-stu-id="9bf42-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="9bf42-117">Dla bezpieczeństwa adres musi rozpoczynać się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="9bf42-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="9bf42-118">Identyfikator URI powinien określać lokalizacji internetowej, ale nie mogą zawierać nazwę pliku HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="9bf42-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="9bf42-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9bf42-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="9bf42-120">Krok 3. Utwórz plik HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="9bf42-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="9bf42-121">Plik informacji HelpInfo XML zawierający identyfikator URI lokalizacji Internet pliki pomocy i numery wersji najnowszych plików pomocy dla modułu w każdej obsługiwanej kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9bf42-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="9bf42-122">Każdy moduł programu Windows PowerShell ma jeden plik HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="9bf42-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="9bf42-123">Po zaktualizowaniu plików pomocy, edytować lub zamienić plik HelpInfo XML; nie należy dodawać inny.</span><span class="sxs-lookup"><span data-stu-id="9bf42-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="9bf42-124">Aby uzyskać więcej informacji, zobacz [jak utworzyć plik XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="9bf42-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="9bf42-125">Krok 4. Zarejestruj swoje pliki pomocy</span><span class="sxs-lookup"><span data-stu-id="9bf42-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="9bf42-126">Podpisy cyfrowe nie są wymagane, ale są one rekomendacji najlepszych zawsze wtedy, gdy udostępniasz pliki.</span><span class="sxs-lookup"><span data-stu-id="9bf42-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="9bf42-127">Krok 5. Tworzenie plików CAB</span><span class="sxs-lookup"><span data-stu-id="9bf42-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="9bf42-128">Narzędzie tworzy pliki cabinet (cab), takie jak MakeCab.exe do utworzenia. Plik CAB, który zawiera pliki pomocy dla modułu.</span><span class="sxs-lookup"><span data-stu-id="9bf42-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="9bf42-129">Utwórz osobny plik CAB dla plików pomocy w każdej obsługiwanej kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9bf42-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="9bf42-130">Aby uzyskać więcej informacji, zobacz [jak przygotować aktualizowalnej pomocy pliki CAB](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="9bf42-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="9bf42-131">Krok 6. Przekazywanie plików</span><span class="sxs-lookup"><span data-stu-id="9bf42-131">Step 6: Upload your files</span></span>

<span data-ttu-id="9bf42-132">Aby opublikować pliki pomocy nowych lub zaktualizowanych, przekazać pliki CAB do lokalizacji internetowej, który jest określony przez **HelpContentUri** elementu w pliku HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="9bf42-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="9bf42-133">Następnie przekaż plik HelpInfo XML do lokalizacji internetowej, który jest określony przez wartość **HelpInfoUri** klucza w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="9bf42-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
