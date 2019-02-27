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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847250"
---
# <a name="creating-a-management-odata-web-service"></a>Tworzenie internetowej usługi OData zarządzania

Rozszerzenie do zarządzania ODATA IIS to infrastruktura do tworzenia ASP.NET sieci web punktu końcowego usługi, która udostępnia dane zarządzania dostępne za pośrednictwem poleceń cmdlet programu Windows PowerShell i skryptów, jako jednostki usługi sieci OData Web. Robi, przetwarzanie żądań OData i konwertowania go do wywołania programu Windows PowerShell. Zespoły produktu można tworzyć na podstawie tej infrastruktury, aby utworzyć punkty końcowe, które udostępniają określone zestawy danych zarządzania.

Pobierz i zainstaluj [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) próbki. Postępuj zgodnie z instrukcjami, aby wdrożyć usługę sieci web. Ta usługa sieci web udostępnia usług i procesów za pomocą operacji tworzenia, odczytu, aktualizowania lub usuwania (CRUD). Żądań CRUD wysyłanych do usługi sieci web wywołania poleceń programu Windows PowerShell, które wykonywać żądanych operacji. Mapowanie między operacji CRUD i podstawowe polecenia programu Windows PowerShell jest implementowany przez schemat dwa pliki, schema.mof i schema.xml. Plik schema.mof używa [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object). Plik schema.xml używa schematu XML, który jest opisany w [schemat mapowania zasobów](./resource-mapping-schema.md).

> [!IMPORTANT]
> Przed włączania zarządzania ODATA IIS rozszerzenia dla systemu Windows Server 2008 R2 z dodatkiem SP1 należy włączyć następujące funkcje.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Procedury służące do tworzenia usługi sieci web OData zarządzania

W następujących tematach opisano sposób tworzenia i wdrażania usługi sieci web OData zarządzania.

- [Dodawanie zasobów do zarządzania OData usługi sieci Web](./adding-resources-to-a-management-odata-web-service.md)

- [Implementowanie niestandardowego autoryzacji dla usługi sieci web OData zarządzania](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementowanie SessionConfiguration usługi sieci web OData zarządzania](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Tworzenie pliku schematu pliku MOF usługi sieci web OData zarządzania](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Tworzenie pliku schematu XML dla usługi sieci web OData zarządzania](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Tworzenie pliku Web.config usługi sieci web OData zarządzania](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Wdrażanie usługi sieci web OData zarządzania](./deploying-a-management-odata-web-service.md)

- [Kojarzenie jednostek OData zarządzania](./associating-management-odata-entities.md)

## <a name="see-also"></a>Zobacz też

[Pliki schematów rozszerzenie ODATA IIS zarządzania](./management-odata-iis-extension-schema-files.md)
