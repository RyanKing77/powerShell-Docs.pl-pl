---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zagnieżdżanie konfiguracji
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218998"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="ccba9-103">Zagnieżdżania konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="ccba9-103">Nesting DSC configurations</span></span>

<span data-ttu-id="ccba9-104">Konfiguracja zagnieżdżonych (nazywanych również konfiguracji złożonej) jest konfigurację, która jest wywoływana w innej konfiguracji, tak jakby był on zasobu.</span><span class="sxs-lookup"><span data-stu-id="ccba9-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="ccba9-105">Obie konfiguracje muszą być zdefiniowane w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="ccba9-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="ccba9-106">Oto prosty przykład:</span><span class="sxs-lookup"><span data-stu-id="ccba9-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="ccba9-107">W tym przykładzie `FileConfig` przyjmuje dwa parametry obowiązkowe, **CopyFrom** i **CopyTo**, które są używane jako wartości **Ścieżka_źródłowa** i  **Ścieżka_docelowa** właściwości w `File` bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="ccba9-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="ccba9-108">`NestedConfig` Wywołania konfiguracji `FileConfig` tak, jakby była zasobu.</span><span class="sxs-lookup"><span data-stu-id="ccba9-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="ccba9-109">Właściwości w `NestedConfig` bloku zasobów (**CopyFrom** i **CopyTo**) są parametry `FileConfig` konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ccba9-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccba9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccba9-110">See Also</span></span>

- [<span data-ttu-id="ccba9-111">Złożone zasobów — za pomocą konfiguracji DSC jako zasób</span><span class="sxs-lookup"><span data-stu-id="ccba9-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)