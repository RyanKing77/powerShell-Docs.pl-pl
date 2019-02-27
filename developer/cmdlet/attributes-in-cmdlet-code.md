---
title: Atrybuty w kodzie polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845262"
---
# <a name="attributes-in-cmdlet-code"></a>Atrybuty w kodzie polecenia cmdlet

Aby użyć typowe funkcje udostępniane przez środowisko Windows PowerShell, klas i właściwości publiczne zdefiniowane w kodzie polecenia cmdlet są oznaczone za pomocą atrybutów. Na przykład poniższą definicję klasy używa atrybutu polecenia Cmdlet, aby zidentyfikować klasy programu Microsoft .NET Framework, w której **Get-Proc** polecenia cmdlet jest zaimplementowana. (To polecenie cmdlet służy jako przykład w tym dokumencie i jest podobna do `Get-Process` dostarczane przez środowisko Windows PowerShell polecenia cmdlet.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Te atrybuty są uznawane za metadanych, ponieważ ich implementacji różni się od wykonania kodu polecenie cmdlet. Po uruchomieniu polecenia cmdlet programu Windows PowerShell środowiska uruchomieniowego rozpoznaje atrybutów, a następnie oblicza odpowiednią akcję dla każdego atrybutu.

Mimo że można zaimplementować własną wersję funkcje udostępniane przez te atrybuty, projekcie dobre polecenia cmdlet są używane następujące typowe funkcje.

Aby uzyskać więcej informacji na temat różnych atrybutów, które może być zadeklarowana w poleceń cmdlet, zobacz [typy atrybutów](./attribute-types.md).

## <a name="see-also"></a>Zobacz też

[Typy atrybutów](./attribute-types.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
