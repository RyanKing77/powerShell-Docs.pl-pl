---
title: Jak dodać parametry dynamiczne do tematu pomocy dostawcy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848120"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Jak dodać parametry dynamiczne do tematu pomocy dotyczącego dostawcy

W tej sekcji opisano sposób wypełniania sekcji **parametry dynamiczne** tematu pomocy dostawcy.

*Parametry dynamiczne* są parametrami polecenia cmdlet lub funkcji, które są dostępne tylko w określonych warunkach.

Parametry dynamiczne, które są udokumentowane w temacie pomocy dostawcy, to parametry dynamiczne, które dostawca dodaje do polecenia cmdlet lub funkcji, gdy polecenie cmdlet lub funkcja jest używana na dysku dostawcy.

Parametry dynamiczne mogą być również udokumentowane w niestandardowej pomocy dotyczącej poleceń cmdlet dla dostawcy. W przypadku pisania pomocy dostawcy i niestandardowej pomocy dotyczącej poleceń cmdlet dla dostawcy Dołącz dokumentację parametru dynamicznego w obu dokumentach.

Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, temat pomocy dostawcy zawiera pusty `DynamicParameters` element.

### <a name="to-add-dynamic-parameters"></a>Aby dodać parametry dynamiczne

1. W pliku *AssemblyName*. dll-help. XML w ramach `providerHelp` `DynamicParameters` elementu Dodaj element. Element powinien pojawić się `Tasks` po elemencie i przed `RelatedLinks` elementem. `DynamicParameters`

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

   Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, `DynamicParameters` element może być pusty.

2. W elemencie, dla każdego parametru dynamicznego, `DynamicParameter` Dodaj element. `DynamicParameters`

   Przykład:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. W każdym `DynamicParameter` elemencie `Name` Dodaj element i `CmdletSupported` .

   |Nazwa elementu|Opis|
   |------------------|-----------------|
   |Nazwa|Określa nazwę parametru.|
   |CmdletSupported|Określa polecenia cmdlet, w których parametr jest prawidłowy. Wpisz rozdzieloną przecinkami listę nazw poleceń cmdlet.|

   Na przykład następujące `Encoding` dokumenty XML zawiera parametr dynamiczny, który dostawca systemu plików programu Windows PowerShell dodaje `Add-Content`do, `Get-Content`, `Set-Content` polecenia cmdlet.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. W każdym `DynamicParameter` elemencie `Type` Dodaj element. Element jest kontenerem `Name` elementu, który zawiera typ .NET wartości parametru dynamicznego. `Type`

   Na przykład poniższy kod XML pokazuje, że typem `Encoding` .NET parametru dynamicznego jest Wyliczenie [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. `Description` Dodaj element, który zawiera krótki opis parametru dynamicznego. Podczas redagowania opisu należy użyć wytycznych wymaganych dla wszystkich parametrów polecenia cmdlet w temacie [jak dodać informacje o parametrach](./how-to-add-parameter-information.md).

   Na przykład poniższy kod XML zawiera opis `Encoding` parametru dynamicznego.

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

6. `PossibleValues` Dodaj element i jego elementy podrzędne. Razem te elementy opisują wartości parametru dynamicznego. Ten element jest przeznaczony do wyliczania wartości. Jeśli parametr dynamiczny nie przyjmuje wartości, na przykład w przypadku parametru Switch lub wartości nie można wyliczyć, Dodaj pusty `PossibleValues` element.

   W poniższej tabeli wymieniono i opisano `PossibleValues` element i jego elementy podrzędne.

   |Nazwa elementu|Opis|
   |------------------|-----------------|
   |PossibleValues|Ten element jest kontenerem. Elementy podrzędne są opisane poniżej. Dodaj jeden `PossibleValues` element do każdego tematu pomocy dostawcy. Element może być pusty.|
   |PossibleValue|Ten element jest kontenerem. Elementy podrzędne są opisane poniżej. Dodaj jeden `PossibleValue` element dla każdej wartości parametru dynamicznego.|
   |Wartość|Określa nazwę wartości.|
   |Opis|Ten element zawiera `Para` element. Tekst w `Para` elemencie zawiera opis wartości, która jest nazywana `Value` w elemencie.|

   Na przykład poniższy kod XML przedstawia jeden `PossibleValue` element `Encoding` parametru dynamicznego.

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

Poniższy przykład pokazuje `DynamicParameters` element `Encoding` parametru dynamicznego.

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