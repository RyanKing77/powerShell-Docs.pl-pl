---
title: Tworzenie pliku schematu XML dla usługi sieci web OData zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848195"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="d6b0a-102">Tworzenie pliku schematu XML na potrzeby internetowej usługi OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="d6b0a-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="d6b0a-103">Po zdefiniowaniu zasoby udostępni usługi sieci web (zobacz [tworzenia pliku schematu pliku MOF usługi sieci web OData zarządzania](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), możesz mapować te zasoby do podstawowych poleceń cmdlet programu Windows PowerShell, które implementuje obsługiwane operacje dotyczące poszczególnych zasobów, tworząc plik XML, który jest zgodny z [schemat mapowania zasobów](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="d6b0a-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="d6b0a-104">Plik XML określa również adresy URL, które są używane przez klienta do dostępu do zasobów.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="d6b0a-105">Zasoby Mappng do adresów URL</span><span class="sxs-lookup"><span data-stu-id="d6b0a-105">Mappng resources to URLs</span></span>

<span data-ttu-id="d6b0a-106">Pierwsza część pliku XML mapuje zasoby zdefiniowane w pliku MOF schematu do adresów URL, które są używane do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="d6b0a-107">Poniższy przykład pokazuje, że to mapowanie.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="d6b0a-108">Mapowanie poleceń cmdlet do obsługi operacji CRUD</span><span class="sxs-lookup"><span data-stu-id="d6b0a-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="d6b0a-109">Następnie możesz określić poleceń cmdlet, które odpowiadają CRUD (tworzenia, odczytu, aktualizacji i usuwania) operacje, które obsługują zasoby.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="d6b0a-110">W protokole OData zarządzania [schemat mapowania zasobów](./resource-mapping-schema.md), operacji CRUD są mapowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="d6b0a-111">Polecenie CRUD</span><span class="sxs-lookup"><span data-stu-id="d6b0a-111">CRUD command</span></span>|<span data-ttu-id="d6b0a-112">— Element XML</span><span class="sxs-lookup"><span data-stu-id="d6b0a-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="d6b0a-113">Utworzenie</span><span class="sxs-lookup"><span data-stu-id="d6b0a-113">Create</span></span>|<span data-ttu-id="d6b0a-114">Utworzenie</span><span class="sxs-lookup"><span data-stu-id="d6b0a-114">Create</span></span>|
|<span data-ttu-id="d6b0a-115">Odczyt</span><span class="sxs-lookup"><span data-stu-id="d6b0a-115">Read</span></span>|<span data-ttu-id="d6b0a-116">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d6b0a-116">Query</span></span>|
|<span data-ttu-id="d6b0a-117">Aktualizacja</span><span class="sxs-lookup"><span data-stu-id="d6b0a-117">Update</span></span>|<span data-ttu-id="d6b0a-118">Aktualizacja</span><span class="sxs-lookup"><span data-stu-id="d6b0a-118">Update</span></span>|
|<span data-ttu-id="d6b0a-119">Usuń</span><span class="sxs-lookup"><span data-stu-id="d6b0a-119">Delete</span></span>|<span data-ttu-id="d6b0a-120">Usuń</span><span class="sxs-lookup"><span data-stu-id="d6b0a-120">Delete</span></span>|

<span data-ttu-id="d6b0a-121">W poniższym przykładzie przedstawiono mapowania dla operacji tworzenia, odczytu i aktualizacji na `Service` zasobów.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="d6b0a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6b0a-122">See Also</span></span>

[<span data-ttu-id="d6b0a-123">Tworzenie pliku schematu pliku MOF usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="d6b0a-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="d6b0a-124">Zasób mapowanie schematu</span><span class="sxs-lookup"><span data-stu-id="d6b0a-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="d6b0a-125">Tworzenie usługi sieci Web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="d6b0a-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)