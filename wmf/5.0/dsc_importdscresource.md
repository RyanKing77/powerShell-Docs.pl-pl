---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219654"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Parametr - ModuleVersion obsługuje importu DscResource — słowo kluczowe

Dodano nowy parametr `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne podczas tworzenia konfiguracji DSC. Autorzy konfiguracji można teraz określić dokładnie wersji modułu ładowania zasobów DSC z. Nowej składni słowa kluczowego jest:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nazwa**: nazwy co najmniej jeden zasób do zaimportowania.
* **Nazwa modułu**: nazwy modułu lub obiektów ModuleSpecification co najmniej jednego modułu do zaimportowania.
* **ModuleVersion**: wersja modułu ot importu. Jeśli używana, nazwa modułu musi reprezentować tylko jeden moduł według nazwy.

W środowisku Windows PowerShell ISE jest wyświetlane z IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Uwaga**: `–ModuleVersion` parametru można używać tylko w połączeniu z `–ModuleName` parametru. Nie można użyć nazwy zasobu tylko przy użyciu `–Name` parametru.

Przed, jedynym sposobem określania wersji modułu podczas ładowania zasobów DSC była za pomocą obiektu specyfikacji modułu, np.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
