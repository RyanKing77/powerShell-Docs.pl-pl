---
title: Parametr aliasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844933"
---
# <a name="parameter-aliases"></a>Aliasy parametrów

Parametry polecenia cmdlet mogą również mieć aliasy. Podczas wpisywania lub określić parametr w poleceniu, można użyć aliasów zamiast nazw parametrów.

## <a name="benefits-of-using-aliases"></a>Korzyści z używania aliasów

Dodawanie aliasów parametrów zapewnia następujące korzyści.

- Możesz podać skrót, dzięki czemu użytkownik musi używać nazwy parametru ukończone po wywołaniu polecenia cmdlet. Na przykład można użyć aliasu "CN" zamiast nazwy parametru "Nazwa_komputera".

- Jeśli chcesz zapewnić różne nazwy dla tego samego parametru, można zdefiniować wiele aliasów. Można zdefiniować wiele aliasów, jeśli trzeba pracować z wieloma grupami użytkowników, które odwołują się do tych samych danych na różne sposoby.

- Możesz podać wstecznej zgodności istniejące skrypty przypadku zmiany nazwy parametru.

- Za pomocą atrybutu Alias wraz z atrybutem ValueFromPipelineByName można zdefiniować parametr, który umożliwia Twojego polecenia cmdlet powiązać z różnych typów obiektów. Na przykład załóżmy, że masz dwa obiekty o różnych typach i pierwszy obiekt ma właściwość zapisywania i drugi obiekt ma właściwość edytora. Jeśli Twojego polecenia cmdlet parametr, który ma składnik zapisywania i Edytor aliasy i polecenia cmdlet zaakceptowane wejście potokowe w nazw właściwości, Twojego polecenia cmdlet można dowiązać do obu obiektów za pomocą dwóch aliasów parametrów.

Aby uzyskać więcej informacji na temat aliasy, które mogą być używane z określonymi parametrami, zobacz [typowych nazw parametrów](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definiowanie aliasów parametrów

Aby zdefiniować alias dla parametru, należy zadeklarować atrybut aliasu, jak pokazano w poniższej deklaracji parametru. W tym przykładzie wiele aliasów są zdefiniowane dla tego samego parametru. (Aby uzyskać więcej informacji, zobacz[jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Zobacz też

[Nazwy wspólnych parametrów](./common-parameter-names.md)

[Sposób deklarowania parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
