---
title: Tworzenie niestandardowych formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844849"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="e67a6-102">Tworzenie kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e67a6-102">Creating Custom Controls</span></span>

<span data-ttu-id="e67a6-103">Kontrolki niestandardowe są składnikami najbardziej elastyczny formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="e67a6-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="e67a6-104">W przeciwieństwie do tabeli, listy i szeroki widoki, które zdefiniowanie formalnego struktury danych, takich jak tabela danych formanty niestandardowe umożliwiają definiowanie sposobu wyświetlania każdej części danych.</span><span class="sxs-lookup"><span data-stu-id="e67a6-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="e67a6-105">Można zdefiniować wspólny zbiór niestandardowych formantów, które są dostępne dla wszystkich widoków formatowania pliku, można zdefiniować niestandardowe formanty, które są dostępne dla określonego widoku, lub można zdefiniować zestaw kontrolek, które są dostępne dla grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="e67a6-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="e67a6-106">Przykład formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="e67a6-106">Custom Control Example</span></span>

<span data-ttu-id="e67a6-107">Poniższy przykład pokazuje niestandardowy formant, który jest zdefiniowany w pliku Certificates.Format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e67a6-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="e67a6-108">Ten formant niestandardowy jest używany do oddzielania [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) obiekty wyświetlane w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e67a6-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="e67a6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e67a6-109">See Also</span></span>

[<span data-ttu-id="e67a6-110">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e67a6-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
