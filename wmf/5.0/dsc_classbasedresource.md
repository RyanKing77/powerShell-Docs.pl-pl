---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Zasoby DSC oparte na klasach

## <a name="defining-dsc-resources-with-classes"></a>Definiowanie konfiguracji DSC zasobów z klasami

Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia.
Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:

* Plik MOF do schematu nie jest wymagane.
* A **DSCResource** podfolderu w folderze modułu nie jest wymagana.
* Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.

Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).