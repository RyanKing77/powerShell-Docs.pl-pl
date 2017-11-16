---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Zasoby oparte na klasie DSC

## <a name="defining-dsc-resources-with-classes"></a>Definiowanie konfiguracji DSC zasobów z klasami

Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia. Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:

* Plik MOF do schematu nie jest wymagane.
* A **DSCResource** podfolderu w folderze modułu nie jest wymagana.
* Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.

Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).

