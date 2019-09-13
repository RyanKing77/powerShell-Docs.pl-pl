---
title: Zestawy parametrów poleceń cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936200"
---
# <a name="cmdlet-parameter-sets"></a>Zestawy parametrów poleceń cmdlet

Program PowerShell używa zestawów parametrów, aby umożliwić pisanie pojedynczego polecenia cmdlet, które może wykonywać różne akcje dla różnych scenariuszy. Zestawy parametrów umożliwiają udostępnienie użytkownikowi różnych parametrów. I, aby zwrócić różne informacje na podstawie parametrów określonych przez użytkownika.

## <a name="examples-of-parameter-sets"></a>Przykłady zestawów parametrów

Na przykład polecenie cmdlet programu `Get-EventLog` PowerShell zwraca różne informacje w zależności od tego, czy użytkownik określa **listę** lub parametr **Nazwa** . Jeśli parametr **listy** jest określony, polecenie cmdlet zwraca informacje o plikach dziennika, ale nie informacje o zdarzeniach, które zawierają. Jeśli parametr **Nazwa** jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w określonym dzienniku zdarzeń. Parametry **list** i **Nazwa** identyfikują dwa oddzielne zestawy parametrów.

## <a name="unique-parameter"></a>Unikatowy parametr

Każdy zestaw parametrów musi mieć unikatowy parametr, którego środowisko uruchomieniowe programu PowerShell używa do uwidocznienia odpowiedniego zestawu parametrów. Jeśli to możliwe, unikatowy parametr powinien być obowiązkowym parametrem. Gdy parametr jest obowiązkowy, użytkownik musi określić parametr, a środowisko uruchomieniowe programu PowerShell używa tego parametru do identyfikacji zestawu parametrów. Nie można określić unikatowego parametru, jeśli polecenie cmdlet zostało zaprojektowane do uruchomienia bez określenia żadnych parametrów.

## <a name="multiple-parameter-sets"></a>Wiele zestawów parametrów

Na poniższej ilustracji w lewej kolumnie są wyświetlane trzy prawidłowe zestawy parametrów. **Parametr A** jest unikatowy dla pierwszego zestawu parametrów **parametr B** jest unikatowy dla drugiego zestawu parametrów, a **parametr C** jest unikatowy dla trzeciego zestawu parametrów. W prawej kolumnie zestawy parametrów nie mają unikatowego parametru.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Wymagania dotyczące zestawu parametrów

Poniższe wymagania dotyczą wszystkich zestawów parametrów.

- Każdy zestaw parametrów musi mieć co najmniej jeden unikatowy parametr. Jeśli to możliwe, ustaw ten parametr jako obowiązkowy.

- Zestaw parametrów, który zawiera wiele parametrów pozycyjnych, musi definiować unikatowe położenia dla każdego parametru. Dwa parametry pozycyjne nie mogą określać tego samego położenia.

- Tylko jeden parametr w zestawie może deklarować `ValueFromPipeline` słowo kluczowe z `true`wartością.
  Wiele parametrów może definiować `ValueFromPipelineByPropertyName` słowo kluczowe o `true`wartości.

- Jeśli nie określono zestawu parametrów dla parametru, parametr należy do wszystkich zestawów parametrów.

> [!NOTE]
> W przypadku polecenia cmdlet lub funkcji istnieje limit 32 zestawów parametrów.

## <a name="default-parameter-sets"></a>Domyślne zestawy parametrów

Jeśli zdefiniowano wiele zestawów parametrów, można użyć `DefaultParameterSetName` słowa kluczowego **polecenia cmdlet** w celu określenia domyślnego zestawu parametrów. Program PowerShell używa domyślnego parametru ustawionego, jeśli nie może ustalić parametru ustawionego do użycia na podstawie informacji podanych przez polecenie. Aby uzyskać więcej informacji o atrybucie **polecenia cmdlet** , zobacz [polecenie cmdlet Attribute deklaracji](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarowanie zestawów parametrów

Aby utworzyć zestaw parametrów, należy określić `ParameterSetName` słowo kluczowe przy deklarowaniu atrybutu **Parameter** dla każdego parametru w zestawie parametrów. Dla parametrów, które należą do wielu zestawów parametrów, Dodaj atrybut **parametrów** dla każdego zestawu parametrów. Ten atrybut umożliwia definiowanie parametru inaczej dla każdego zestawu parametrów. Na przykład można zdefiniować parametr jako obowiązkowy w jednym zestawie i opcjonalny w innym. Jednak każdy zestaw parametrów musi zawierać jeden unikatowy parametr. Aby uzyskać więcej informacji, zobacz [Deklaracja atrybutu parametru](parameter-attribute-declaration.md).

W poniższym przykładzie parametr **username** jest unikatowym parametrem `Test01` zestawu parametrów, a parametr **ComputerName** `Test02` jest unikatowym parametrem zestawu parametrów. Parametr **SharedParam** należy do obu zestawów i jest obowiązkowy dla `Test01` zestawu parametrów, `Test02` ale opcjonalny dla zestawu parametrów.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
