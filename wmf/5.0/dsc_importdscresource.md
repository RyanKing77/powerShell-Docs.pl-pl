---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998524"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Słowo kluczowe Import-DscResource obsługuje parametr - ModuleVersion

Dodano nowy parametr w celu `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne w przypadku tworzenia konfiguracji DSC. Autorzy konfiguracji można teraz wprowadzić dokładnie wersji modułu można załadować zasobów DSC. Składnia nowe słowo kluczowe jest:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nazwa**: nazwy co najmniej jeden zasób do zaimportowania.
* **ModuleName**: nazwy modułów lub obiekty ModuleSpecification przynajmniej jeden moduł do zaimportowania.
* **ModuleVersion**: wersję modułu do zaimportowania. Jeśli używane, ModuleName musi reprezentować tylko jeden moduł według nazwy.

W środowisku Windows PowerShell ISE zostanie ona wyświetlona za pomocą funkcji IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Uwaga**: `–ModuleVersion` parametru należy używać tylko w połączeniu z `–ModuleName` parametru. Nie można używać z nazwami zasobów przy użyciu tylko `–Name` parametru.

Wcześniej jedynym sposobem, aby określić wersję modułu, podczas ładowania zasobów DSC zostało za pomocą obiektu specyfikacji modułu, np.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
