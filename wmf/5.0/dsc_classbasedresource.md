---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221854"
---
# <a name="class-based-dsc-resources"></a>Zasoby DSC oparte na klasach

## <a name="defining-dsc-resources-with-classes"></a>Definiowanie konfiguracji DSC zasobów z klasami

Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia.
Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:

* Plik MOF do schematu nie jest wymagane.
* A **DSCResource** podfolderu w folderze modułu nie jest wymagana.
* Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.

Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).
