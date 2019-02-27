---
title: Sposób deklarowania zestawów parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849399"
---
# <a name="how-to-declare-parameter-sets"></a>Jak zadeklarować zestawy parametrów

W tym przykładzie pokazano, jak zdefiniować dwa zestawy parametrów, kiedy Deklarujesz parametry polecenia cmdlet. Każdy zestaw parametrów ma unikatowy parametr i udostępniony parametr, który jest używany przez oba zestawy parametrów. Aby uzyskać więcej informacji na temat zestawów parametrów, w tym jak określić domyślny zestaw parametrów, zobacz [zestawy parametrów polecenia Cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Jeśli to możliwe, należy zdefiniować unikatowy parametr parametrem, który został ustawiony jako wymaganego parametru. Jednak jeśli chcesz, aby Twoje polecenie cmdlet do uruchomienia bez określenia wszystkich parametrów, unikatowy parametr może być opcjonalny parametr. Na przykład, unikatową wartość parametru `Get-Command` polecenia cmdlet jest opcjonalne.

## <a name="how-to-define-two-parameter-sets"></a>Jak zdefiniować dwa zestawy parametrów

1. Dodaj `ParameterSet` — słowo kluczowe do atrybutu parametru dla parametru unikatowy pierwszy zestaw parametrów.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Dodaj `ParameterSet` — słowo kluczowe do atrybutu parametru dla parametru unikatowy drugi zestaw parametrów.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Dla parametru, który należy do obu zestawów parametrów, Dodaj atrybut parametr, dla każdego zestawu parametrów, a następnie dodaj `ParameterSet` — słowo kluczowe do każdej grupy. Każdy atrybut parametru można określić, jak ten parametr jest zdefiniowany. Parametr może być opcjonalny w jednym zestawie i obowiązkowe w innym.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Zobacz też

[Zestawy parametrów polecenia cmdlet](./cmdlet-parameter-sets.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
