---
title: Sposób dodawania parametrów dynamicznych do tematu pomocy dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849525"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Jak dodać parametry dynamiczne do tematu pomocy dotyczącego dostawcy

W tej sekcji wyjaśniono, jak wypełnić **parametrów DYNAMICZNYCH** części tematu pomocy dostawcy.

*Parametry dynamiczne* parametrów polecenia cmdlet lub funkcji, które są dostępne tylko w określonych warunkach.

Parametry dynamiczne, które są opisane w temacie pomocy dostawcy są parametrów dynamicznych, które umożliwiają dodanie dostawcy do polecenia cmdlet lub funkcji, gdy polecenia cmdlet lub funkcja jest używana w dysku dostawcy.

Parametry dynamiczne również może być udokumentowane w pomocy polecenia cmdlet niestandardowego dostawcy. Podczas zapisywania dostawcy pomocy i pomocy dotyczącej poleceń cmdlet niestandardowego dostawcy, obejmują dokumentacji parametr dynamiczny, oba dokumenty. Aby uzyskać więcej informacji na temat pomocy dotyczącej poleceń cmdlet niestandardowe zobacz [pisania Windows PowerShell niestandardowe pomoc dotyczącą polecenia Cmdlet dla dostawców](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, dostawca tematu Pomocy zawiera pustą `DynamicParameters` elementu.

### <a name="to-add-dynamic-parameters"></a>Aby dodać parametry dynamiczne

1. W *AssemblyName*w pliku .dll help.xml `providerHelp` elementu Dodawanie `DynamicParameters` elementu. `DynamicParameters` Po powinien zostać wyświetlony element `Tasks` elementu i przed `RelatedLinks` elementu.

   Przykład:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Jeśli dostawca nie implementuje żadnych parametrów dynamicznych `DynamicParameters` element może być pusty.

2. W ramach `DynamicParameters` element dla każdego parametru dynamicznego dodawania `DynamicParameter` elementu.

   Przykład:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. W każdym `DynamicParameter` elementu Dodawanie `Name` i `CmdletSupported` elementu.

   |Nazwa elementu|Opis|
   |------------------|-----------------|
   |Nazwa|Określa nazwę parametru.|
   |CmdletSupported|Określa polecenia cmdlet, w którym parametr jest prawidłowy. Wpisz nazwy poleceń cmdlet listę rozdzielonych przecinkami.|

   Na przykład, następujące dokumenty XML `Encoding` parametrem dynamicznym, który dodaje dostawcy programu Windows PowerShell w systemie plików `Add-Content`, `Get-Content`, `Set-Content` polecenia cmdlet.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. W każdym `DynamicParameter` elementu Dodawanie `Type` elementu. `Type` Element jest kontenerem dla `Name` element, który zawiera typ architektury .NET wartości parametrów dynamicznych.

   Na przykład, następujący kod XML pokazuje, że typ .NET `Encoding` parametr dynamiczny to [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) wyliczenia.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Dodaj `Description` element, który zawiera krótki opis parametru dynamicznego. Podczas redagowania opis, skorzystaj z wskazówek, określony dla wszystkich parametrów polecenia cmdlet w [jak dodać informacje o parametrach](./how-to-add-parameter-information.md).

   Na przykład następujący kod XML zawiera opis `Encoding` parametrów dynamicznych.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Dodaj `PossibleValues` elementu i jego elementy podrzędne. Razem te elementy opisują wartości parametrów dynamicznych. Ten element jest przeznaczona dla wartości wyliczenia. Jeśli parametr dynamiczny nie przyjmuje wartości, takich jak jest to miejsce w przypadku parametru przełącznika lub nie można wyliczyć wartości, Dodaj pusty `PossibleValues` elementu.

   Poniższej tabeli wymieniono i opisano `PossibleValues` elementu i jego elementy podrzędne.

   |Nazwa elementu|Opis|
   |------------------|-----------------|
   |PossibleValues|Ten element jest kontenerem. Jego elementy podrzędne są opisane poniżej. Dodaj jeden `PossibleValues` element do każdego tematu pomocy dostawcy. Element może być pusta.|
   |PossibleValue|Ten element jest kontenerem. Jego elementy podrzędne są opisane poniżej. Dodaj jeden `PossibleValue` dla każdej wartości parametrów dynamicznych.|
   |Wartość|Określa nazwę wartości.|
   |Opis|Ten element zawiera `Para` elementu. Tekst w `Para` element w tym artykule opisano wartość, która jest wymieniony w polu `Value` elementu.|

   Na przykład, następujący kod XML przedstawia jedną `PossibleValue` elementu `Encoding` parametrów dynamicznych.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `DynamicParameters` elementu `Encoding` parametrów dynamicznych.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```