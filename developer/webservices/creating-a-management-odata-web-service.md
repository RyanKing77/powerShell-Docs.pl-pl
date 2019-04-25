---
title: Tworzenie usługi sieci Web OData zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080700"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="8a281-102">Tworzenie internetowej usługi OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="8a281-103">Rozszerzenie do zarządzania ODATA IIS to infrastruktura do tworzenia ASP.NET sieci web punktu końcowego usługi, która udostępnia dane zarządzania dostępne za pośrednictwem poleceń cmdlet programu Windows PowerShell i skryptów, jako jednostki usługi sieci OData Web.</span><span class="sxs-lookup"><span data-stu-id="8a281-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="8a281-104">Robi, przetwarzanie żądań OData i konwertowania go do wywołania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a281-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="8a281-105">Zespoły produktu można tworzyć na podstawie tej infrastruktury, aby utworzyć punkty końcowe, które udostępniają określone zestawy danych zarządzania.</span><span class="sxs-lookup"><span data-stu-id="8a281-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="8a281-106">Pobierz i zainstaluj [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) próbki.</span><span class="sxs-lookup"><span data-stu-id="8a281-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="8a281-107">Postępuj zgodnie z instrukcjami, aby wdrożyć usługę sieci web.</span><span class="sxs-lookup"><span data-stu-id="8a281-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="8a281-108">Ta usługa sieci web udostępnia usług i procesów za pomocą operacji tworzenia, odczytu, aktualizowania lub usuwania (CRUD).</span><span class="sxs-lookup"><span data-stu-id="8a281-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="8a281-109">Żądań CRUD wysyłanych do usługi sieci web wywołania poleceń programu Windows PowerShell, które wykonywać żądanych operacji.</span><span class="sxs-lookup"><span data-stu-id="8a281-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="8a281-110">Mapowanie między operacji CRUD i podstawowe polecenia programu Windows PowerShell jest implementowany przez schemat dwa pliki, schema.mof i schema.xml.</span><span class="sxs-lookup"><span data-stu-id="8a281-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="8a281-111">Plik schema.mof używa [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="8a281-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="8a281-112">Plik schema.xml używa schematu XML, który jest opisany w [schemat mapowania zasobów](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8a281-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a281-113">Przed włączania zarządzania ODATA IIS rozszerzenia dla systemu Windows Server 2008 R2 z dodatkiem SP1 należy włączyć następujące funkcje.</span><span class="sxs-lookup"><span data-stu-id="8a281-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="8a281-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="8a281-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="8a281-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="8a281-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="8a281-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="8a281-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="8a281-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="8a281-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="8a281-118">Procedury służące do tworzenia usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="8a281-119">W następujących tematach opisano sposób tworzenia i wdrażania usługi sieci web OData zarządzania.</span><span class="sxs-lookup"><span data-stu-id="8a281-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="8a281-120">Dodawanie zasobów do zarządzania OData usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="8a281-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-121">Implementowanie niestandardowego autoryzacji dla usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-122">Implementowanie SessionConfiguration usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-123">Tworzenie pliku schematu pliku MOF usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-124">Tworzenie pliku schematu XML dla usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-125">Tworzenie pliku Web.config usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-126">Wdrażanie usługi sieci web OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="8a281-127">Kojarzenie jednostek OData zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="8a281-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a281-128">See Also</span></span>

[<span data-ttu-id="8a281-129">Pliki schematów rozszerzenie ODATA IIS zarządzania</span><span class="sxs-lookup"><span data-stu-id="8a281-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
