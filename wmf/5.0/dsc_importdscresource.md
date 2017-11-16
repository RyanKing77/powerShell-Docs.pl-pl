---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
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

Przed, jedynym sposobem określania wersji modułu podczas ładowania zasobów DSC była za pomocą obiektu specyfikacji modułu, np.:`–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`

