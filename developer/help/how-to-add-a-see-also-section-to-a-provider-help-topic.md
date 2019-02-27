---
title: Jak dodać Zobacz także sekcję do tematu pomocy dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848454"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Jak dodać sekcję Zobacz także sekcję do tematu pomocy dotyczącego dostawcy

W tej sekcji wyjaśniono, jak wypełnić **Zobacz też** części tematu pomocy dostawcy.

**Zobacz też** sekcja zawiera listę tematów, które są związane z dostawcą lub może pomóc użytkownikowi zrozumieć i używać dostawcy. Na liście tematów mogą obejmować pomocy dotyczącej poleceń cmdlet, dostawca pomocy i pojęciach ("") Tematy Pomocy dotyczące programy w programie Windows PowerShell. Może również obejmować odwołań do książki, dokument i tematy usługi online, w tym wersji online tematu pomocy bieżącego dostawcy.

Gdy odwołujesz się do tematów, w trybie online, podaj identyfikator URI lub wyszukiwany termin w postaci zwykłego tekstu. `Get-Help` Polecenia cmdlet nie łącze lub przekierować do dowolny z tematów na liście. Ponadto `Online` parametru `Get-Help` polecenie cmdlet nie współpracuje z dostawcą pomocy.

W sekcji Zobacz też jest tworzona na podstawie `RelatedLinks` elementu i tagi, które zawiera. Następujący kod XML przedstawiono sposób dodawania tagów.

### <a name="to-add-see-also-topics"></a>Aby dodać "Zobacz też" — Tematy

1. W *AssemblyName*w pliku .dll help.xml `providerHelp` elementu Dodawanie `RelatedLinks` elementu. `RelatedLinks` Element powinien być ostatnim elementem w `providerHelp` elementu. Tylko jeden `RelatedLinks` element jest dozwolony w każdym temacie pomocy dostawcy.

   Przykład:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Dla każdego tematu w **Zobacz też** sekcji w ramach `RelatedLinks` elementu Dodawanie `navigationLink` elementu. Następnie, w ramach każdej `navigationLink` elementu, dodaj je `linkText` elementu i jeden `uri` elementu. Jeśli nie używasz `uri` elementu, można dodać go jako pusty element (\<identyfikatora uri / >).

   Przykład:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Wpisz nazwę tematu między `linkText` tagów. Jeśli udostępniasz identyfikatora URI, wpisz go między `uri` tagów. Aby wskazać wersję online bieżącego tematu pomocy dostawcy między `linkText` tagów, wpisz "wersji Online:" zamiast nazwy tematu. Zazwyczaj "wersja Online:" link jest pierwszym temacie na liście Zobacz też temat.

   Poniższy przykład zawiera trzy Zobacz też tematy. Pierwszy odnoszą się do bieżącego tematu wersji online. Druga dotyczy tematu pomocy polecenia cmdlet programu Windows PowerShell. Trzeci odnosi się do innego tematu w trybie online.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```