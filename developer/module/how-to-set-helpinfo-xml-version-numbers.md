---
title: Jak skonfigurować numery wersji HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794352"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="32b79-102">Jak konfigurować numery wersji pliku XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="32b79-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="32b79-103">W tym temacie wyjaśniono, jak ustawić i zwiększyć numery wersji w pliku nadaje się do aktualizacji informacji pomocy, powszechnie znane jako "plik HelpInfo XML".</span><span class="sxs-lookup"><span data-stu-id="32b79-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="32b79-104">Jak konfigurować numery wersji pliku XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="32b79-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="32b79-105">Numery wersji w pliku HelpInfo XML są krytyczne dla działania aktualizowalnej pomocy.</span><span class="sxs-lookup"><span data-stu-id="32b79-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="32b79-106">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) poleceń cmdlet Pobierz nowe pliki pomocy, tylko wtedy, gdy jest to numer wersji dla kultury interfejsu użytkownika w pliku HelpInfo XML zdalnego jest większy niż numer wersji dla tej kultury interfejsu użytkownika w lokalne HelpInfo XML, lub nie ma pliku lokalnego HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="32b79-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="32b79-107">Plik HelpInfo XML używa numeru wersji część 4, która jest zdefiniowana w **System.Version** klasy programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32b79-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="32b79-108">Format jest `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="32b79-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="32b79-109">Autorzy modułów można użyć dowolnej wersji schematu, który jest dozwolony przez numerowania **System.Version** klasy.</span><span class="sxs-lookup"><span data-stu-id="32b79-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="32b79-110">Aktualizowalnej pomocy wymaga tylko numer wersji do zwiększenia kultury interfejsu użytkownika po przekazaniu nowej wersji pliku CAB dla tej kultury interfejsu użytkownika do lokalizacji, która jest określona przez **HelpContentURI** elementu w pliku HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="32b79-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="32b79-111">Poniższy kod przedstawia elementów pliku HelpInfo XML dla kultury niemiecki (de-DE) interfejsu użytkownika, gdy wersja jest 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="32b79-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="32b79-112">Numer wersji, kultury interfejsu użytkownika odzwierciedla wersję pliku CAB dla tej kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="32b79-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="32b79-113">Numer wersji ma zastosowanie do całego pliku CAB.</span><span class="sxs-lookup"><span data-stu-id="32b79-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="32b79-114">Numery wersji różne dla różnych plików nie można ustawić w pliku CAB.</span><span class="sxs-lookup"><span data-stu-id="32b79-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="32b79-115">Numer wersji dla każdej kultury interfejsu użytkownika jest szacowana osobno i nie muszą być związane z numerami wersji dla innych języków interfejsu użytkownika, obsługiwanych przez moduł.</span><span class="sxs-lookup"><span data-stu-id="32b79-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>