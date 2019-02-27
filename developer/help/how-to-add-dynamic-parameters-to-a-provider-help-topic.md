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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="5f036-102">Jak dodać parametry dynamiczne do tematu pomocy dotyczącego dostawcy</span><span class="sxs-lookup"><span data-stu-id="5f036-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="5f036-103">W tej sekcji wyjaśniono, jak wypełnić **parametrów DYNAMICZNYCH** części tematu pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5f036-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="5f036-104">*Parametry dynamiczne* parametrów polecenia cmdlet lub funkcji, które są dostępne tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="5f036-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="5f036-105">Parametry dynamiczne, które są opisane w temacie pomocy dostawcy są parametrów dynamicznych, które umożliwiają dodanie dostawcy do polecenia cmdlet lub funkcji, gdy polecenia cmdlet lub funkcja jest używana w dysku dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5f036-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="5f036-106">Parametry dynamiczne również może być udokumentowane w pomocy polecenia cmdlet niestandardowego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5f036-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="5f036-107">Podczas zapisywania dostawcy pomocy i pomocy dotyczącej poleceń cmdlet niestandardowego dostawcy, obejmują dokumentacji parametr dynamiczny, oba dokumenty.</span><span class="sxs-lookup"><span data-stu-id="5f036-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="5f036-108">Aby uzyskać więcej informacji na temat pomocy dotyczącej poleceń cmdlet niestandardowe zobacz [pisania Windows PowerShell niestandardowe pomoc dotyczącą polecenia Cmdlet dla dostawców](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="5f036-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="5f036-109">Jeśli dostawca nie implementuje żadnych parametrów dynamicznych, dostawca tematu Pomocy zawiera pustą `DynamicParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="5f036-110">Aby dodać parametry dynamiczne</span><span class="sxs-lookup"><span data-stu-id="5f036-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="5f036-111">W *AssemblyName*w pliku .dll help.xml `providerHelp` elementu Dodawanie `DynamicParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="5f036-112">`DynamicParameters` Po powinien zostać wyświetlony element `Tasks` elementu i przed `RelatedLinks` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="5f036-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5f036-113">For example:</span></span>

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

   <span data-ttu-id="5f036-114">Jeśli dostawca nie implementuje żadnych parametrów dynamicznych `DynamicParameters` element może być pusty.</span><span class="sxs-lookup"><span data-stu-id="5f036-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="5f036-115">W ramach `DynamicParameters` element dla każdego parametru dynamicznego dodawania `DynamicParameter` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="5f036-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5f036-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="5f036-117">W każdym `DynamicParameter` elementu Dodawanie `Name` i `CmdletSupported` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="5f036-118">Nazwa elementu</span><span class="sxs-lookup"><span data-stu-id="5f036-118">Element Name</span></span>|<span data-ttu-id="5f036-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5f036-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="5f036-120">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5f036-120">Name</span></span>|<span data-ttu-id="5f036-121">Określa nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="5f036-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="5f036-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="5f036-122">CmdletSupported</span></span>|<span data-ttu-id="5f036-123">Określa polecenia cmdlet, w którym parametr jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5f036-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="5f036-124">Wpisz nazwy poleceń cmdlet listę rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5f036-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="5f036-125">Na przykład, następujące dokumenty XML `Encoding` parametrem dynamicznym, który dodaje dostawcy programu Windows PowerShell w systemie plików `Add-Content`, `Get-Content`, `Set-Content` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f036-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="5f036-126">W każdym `DynamicParameter` elementu Dodawanie `Type` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="5f036-127">`Type` Element jest kontenerem dla `Name` element, który zawiera typ architektury .NET wartości parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="5f036-128">Na przykład, następujący kod XML pokazuje, że typ .NET `Encoding` parametr dynamiczny to [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5f036-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="5f036-129">Dodaj `Description` element, który zawiera krótki opis parametru dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="5f036-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="5f036-130">Podczas redagowania opis, skorzystaj z wskazówek, określony dla wszystkich parametrów polecenia cmdlet w [jak dodać informacje o parametrach](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="5f036-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="5f036-131">Na przykład następujący kod XML zawiera opis `Encoding` parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="5f036-132">Dodaj `PossibleValues` elementu i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f036-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="5f036-133">Razem te elementy opisują wartości parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="5f036-134">Ten element jest przeznaczona dla wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5f036-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="5f036-135">Jeśli parametr dynamiczny nie przyjmuje wartości, takich jak jest to miejsce w przypadku parametru przełącznika lub nie można wyliczyć wartości, Dodaj pusty `PossibleValues` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="5f036-136">Poniższej tabeli wymieniono i opisano `PossibleValues` elementu i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f036-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="5f036-137">Nazwa elementu</span><span class="sxs-lookup"><span data-stu-id="5f036-137">Element Name</span></span>|<span data-ttu-id="5f036-138">Opis</span><span class="sxs-lookup"><span data-stu-id="5f036-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="5f036-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="5f036-139">PossibleValues</span></span>|<span data-ttu-id="5f036-140">Ten element jest kontenerem.</span><span class="sxs-lookup"><span data-stu-id="5f036-140">This element is a container.</span></span> <span data-ttu-id="5f036-141">Jego elementy podrzędne są opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="5f036-141">Its child elements are described below.</span></span> <span data-ttu-id="5f036-142">Dodaj jeden `PossibleValues` element do każdego tematu pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5f036-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="5f036-143">Element może być pusta.</span><span class="sxs-lookup"><span data-stu-id="5f036-143">The element can be empty.</span></span>|
   |<span data-ttu-id="5f036-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="5f036-144">PossibleValue</span></span>|<span data-ttu-id="5f036-145">Ten element jest kontenerem.</span><span class="sxs-lookup"><span data-stu-id="5f036-145">This element is a container.</span></span> <span data-ttu-id="5f036-146">Jego elementy podrzędne są opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="5f036-146">Its child elements are described below.</span></span> <span data-ttu-id="5f036-147">Dodaj jeden `PossibleValue` dla każdej wartości parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="5f036-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="5f036-148">Value</span></span>|<span data-ttu-id="5f036-149">Określa nazwę wartości.</span><span class="sxs-lookup"><span data-stu-id="5f036-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="5f036-150">Opis</span><span class="sxs-lookup"><span data-stu-id="5f036-150">Description</span></span>|<span data-ttu-id="5f036-151">Ten element zawiera `Para` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-151">This element contains a `Para` element.</span></span> <span data-ttu-id="5f036-152">Tekst w `Para` element w tym artykule opisano wartość, która jest wymieniony w polu `Value` elementu.</span><span class="sxs-lookup"><span data-stu-id="5f036-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="5f036-153">Na przykład, następujący kod XML przedstawia jedną `PossibleValue` elementu `Encoding` parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="5f036-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f036-154">Example</span></span>

<span data-ttu-id="5f036-155">W poniższym przykładzie przedstawiono `DynamicParameters` elementu `Encoding` parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f036-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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