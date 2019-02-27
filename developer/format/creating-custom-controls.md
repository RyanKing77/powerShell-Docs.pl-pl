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
# <a name="creating-custom-controls"></a>Tworzenie kontrolek niestandardowych

Kontrolki niestandardowe są składnikami najbardziej elastyczny formatowania pliku. W przeciwieństwie do tabeli, listy i szeroki widoki, które zdefiniowanie formalnego struktury danych, takich jak tabela danych formanty niestandardowe umożliwiają definiowanie sposobu wyświetlania każdej części danych. Można zdefiniować wspólny zbiór niestandardowych formantów, które są dostępne dla wszystkich widoków formatowania pliku, można zdefiniować niestandardowe formanty, które są dostępne dla określonego widoku, lub można zdefiniować zestaw kontrolek, które są dostępne dla grupy obiektów.

## <a name="custom-control-example"></a>Przykład formantu niestandardowego

Poniższy przykład pokazuje niestandardowy formant, który jest zdefiniowany w pliku Certificates.Format.ps1xml. Ten formant niestandardowy jest używany do oddzielania [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) obiekty wyświetlane w widoku tabeli.

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

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
