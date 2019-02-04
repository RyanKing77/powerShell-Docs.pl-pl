---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685753"
---
# <a name="class-based-dsc-resources"></a>Zasoby DSC oparte na klasach

## <a name="defining-dsc-resources-with-classes"></a>Definiowanie zasobów DSC przy użyciu klasy

Na podstawie opinii, które wprowadziliśmy tworzenia zasoby DSC oparte na klasie prostsze i łatwiejsze do zrozumienia.
Główne różnice między zasób DSC oparte na klasach i dostawcy zasobów DSC polecenia cmdlet są:

* Plik MOF dla schematu nie jest wymagane.
* A **DSCResource** podfolderu w folderze modułu nie jest wymagana.
* Plik modułu programu PowerShell może zawierać wielu klas zasobów DSC.

Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
