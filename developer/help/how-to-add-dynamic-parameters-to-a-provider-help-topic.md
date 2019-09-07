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
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737601"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="597a0-102">Jak dodać parametry dynamiczne do tematu pomocy dotyczącego dostawcy</span><span class="sxs-lookup"><span data-stu-id="597a0-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="597a0-103">W tej sekcji opisano sposób wypełniania sekcji **parametry dynamiczne** tematu pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="597a0-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="597a0-104">*Parametry dynamiczne* są parametrami polecenia cmdlet lub funkcji, które są dostępne tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="597a0-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="597a0-105">Parametry dynamiczne, które są udokumentowane w temacie pomocy dostawcy, to parametry dynamiczne, które dostawca dodaje do polecenia cmdlet lub funkcji, gdy polecenie cmdlet lub funkcja jest używana na dysku dostawcy.</span><span class="sxs-lookup"><span data-stu-id="597a0-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="597a0-106">Parametry dynamiczne mogą być również udokumentowane w niestandardowej pomocy dotyczącej poleceń cmdlet dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="597a0-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="597a0-107">W przypadku pisania pomocy dostawcy i niestandardowej pomocy dotyczącej poleceń cmdlet dla dostawcy Dołącz dokumentację parametru dynamicznego w obu dokumentach.</span><span class="sxs-lookup"><span data-stu-id="597a0-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="597a0-108">Aby uzyskać więcej informacji na temat niestandardowej pomocy polecenia cmdlet, zobacz [pisanie niestandardowej pomocy poleceń cmdlet programu Windows PowerShell dla dostawców](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="597a0-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="597a0-109">Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, temat pomocy dostawcy zawiera pusty `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="597a0-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="597a0-110">Aby dodać parametry dynamiczne</span><span class="sxs-lookup"><span data-stu-id="597a0-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="597a0-111">W pliku *AssemblyName*. dll-help. XML w ramach `providerHelp` `DynamicParameters` elementu Dodaj element.</span><span class="sxs-lookup"><span data-stu-id="597a0-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="597a0-112">Element powinien pojawić się `Tasks` po elemencie i przed `RelatedLinks` elementem. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="597a0-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="597a0-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="597a0-113">For example:</span></span>

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

   <span data-ttu-id="597a0-114">Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, `DynamicParameters` element może być pusty.</span><span class="sxs-lookup"><span data-stu-id="597a0-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="597a0-115">W elemencie, dla każdego parametru dynamicznego, `DynamicParameter` Dodaj element. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="597a0-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="597a0-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="597a0-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="597a0-117">W każdym `DynamicParameter` elemencie `Name` Dodaj element i `CmdletSupported` .</span><span class="sxs-lookup"><span data-stu-id="597a0-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="597a0-118">Nazwa elementu</span><span class="sxs-lookup"><span data-stu-id="597a0-118">Element Name</span></span>|<span data-ttu-id="597a0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="597a0-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="597a0-120">Nazwa</span><span class="sxs-lookup"><span data-stu-id="597a0-120">Name</span></span>|<span data-ttu-id="597a0-121">Określa nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="597a0-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="597a0-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="597a0-122">CmdletSupported</span></span>|<span data-ttu-id="597a0-123">Określa polecenia cmdlet, w których parametr jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="597a0-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="597a0-124">Wpisz rozdzieloną przecinkami listę nazw poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="597a0-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="597a0-125">Na przykład następujące `Encoding` dokumenty XML zawiera parametr dynamiczny, który dostawca systemu plików programu Windows PowerShell dodaje `Add-Content`do, `Get-Content`, `Set-Content` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="597a0-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="597a0-126">W każdym `DynamicParameter` elemencie `Type` Dodaj element.</span><span class="sxs-lookup"><span data-stu-id="597a0-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="597a0-127">Element jest kontenerem `Name` elementu, który zawiera typ .NET wartości parametru dynamicznego. `Type`</span><span class="sxs-lookup"><span data-stu-id="597a0-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="597a0-128">Na przykład poniższy kod XML pokazuje, że typem `Encoding` .NET parametru dynamicznego jest Wyliczenie [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="597a0-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="597a0-129">`Description` Dodaj element, który zawiera krótki opis parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="597a0-130">Podczas redagowania opisu należy użyć wytycznych wymaganych dla wszystkich parametrów polecenia cmdlet w temacie [jak dodać informacje o parametrach](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="597a0-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="597a0-131">Na przykład poniższy kod XML zawiera opis `Encoding` parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="597a0-132">`PossibleValues` Dodaj element i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="597a0-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="597a0-133">Razem te elementy opisują wartości parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="597a0-134">Ten element jest przeznaczony do wyliczania wartości.</span><span class="sxs-lookup"><span data-stu-id="597a0-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="597a0-135">Jeśli parametr dynamiczny nie przyjmuje wartości, na przykład w przypadku parametru Switch lub wartości nie można wyliczyć, Dodaj pusty `PossibleValues` element.</span><span class="sxs-lookup"><span data-stu-id="597a0-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="597a0-136">W poniższej tabeli wymieniono i opisano `PossibleValues` element i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="597a0-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="597a0-137">Nazwa elementu</span><span class="sxs-lookup"><span data-stu-id="597a0-137">Element Name</span></span>|<span data-ttu-id="597a0-138">Opis</span><span class="sxs-lookup"><span data-stu-id="597a0-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="597a0-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="597a0-139">PossibleValues</span></span>|<span data-ttu-id="597a0-140">Ten element jest kontenerem.</span><span class="sxs-lookup"><span data-stu-id="597a0-140">This element is a container.</span></span> <span data-ttu-id="597a0-141">Elementy podrzędne są opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="597a0-141">Its child elements are described below.</span></span> <span data-ttu-id="597a0-142">Dodaj jeden `PossibleValues` element do każdego tematu pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="597a0-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="597a0-143">Element może być pusty.</span><span class="sxs-lookup"><span data-stu-id="597a0-143">The element can be empty.</span></span>|
   |<span data-ttu-id="597a0-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="597a0-144">PossibleValue</span></span>|<span data-ttu-id="597a0-145">Ten element jest kontenerem.</span><span class="sxs-lookup"><span data-stu-id="597a0-145">This element is a container.</span></span> <span data-ttu-id="597a0-146">Elementy podrzędne są opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="597a0-146">Its child elements are described below.</span></span> <span data-ttu-id="597a0-147">Dodaj jeden `PossibleValue` element dla każdej wartości parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="597a0-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="597a0-148">Value</span></span>|<span data-ttu-id="597a0-149">Określa nazwę wartości.</span><span class="sxs-lookup"><span data-stu-id="597a0-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="597a0-150">Opis</span><span class="sxs-lookup"><span data-stu-id="597a0-150">Description</span></span>|<span data-ttu-id="597a0-151">Ten element zawiera `Para` element.</span><span class="sxs-lookup"><span data-stu-id="597a0-151">This element contains a `Para` element.</span></span> <span data-ttu-id="597a0-152">Tekst w `Para` elemencie zawiera opis wartości, która jest nazywana `Value` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="597a0-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="597a0-153">Na przykład poniższy kod XML przedstawia jeden `PossibleValue` element `Encoding` parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="597a0-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="597a0-154">Example</span></span>

<span data-ttu-id="597a0-155">Poniższy przykład pokazuje `DynamicParameters` element `Encoding` parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="597a0-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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