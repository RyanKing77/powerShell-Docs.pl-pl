---
title: Deklaracja klasy polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845724"
---
# <a name="cmdlet-class-declaration"></a>Deklaracja klasy polecenia cmdlet

Klasa programu Microsoft .NET Framework jest zadeklarowany jako polecenia cmdlet, określając **polecenia Cmdlet** atrybutu jako metadane dla klasy. ( **Polecenia Cmdlet** atrybut jest tylko wymaganego atrybutu dla wszystkich poleceń cmdlet). Po określeniu **polecenia Cmdlet** atrybut, możesz określić pary czasownik i rzeczownik, który identyfikuje polecenie cmdlet, aby użytkownik. Ponadto należy opisać funkcji programu Windows PowerShell, która obsługuje polecenie cmdlet. Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> **Polecenia Cmdlet** atrybutu jest definiowana przez [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasy. Właściwości tej klasy odpowiadają parametrów deklaracji, które są używane w przypadku deklarowania atrybutu.

## <a name="nouns"></a>Rzeczowniki

Rzeczownik polecenia cmdlet określa zasoby, na których działa polecenia cmdlet. Rzeczownikiem odróżnia poleceń cmdlet z innymi poleceniami cmdlet.

Rzeczowniki w nazwy poleceń cmdlet musi być określone, a w przypadku ogólnych rzeczowników, takich jak *serwera*, warto dodać krótki prefiks, który odróżnia zasobu z poziomu innych zasobów podobne. Na przykład to nazwa polecenia cmdlet, która obejmuje rzeczownik z prefiksem `Get-SQLServer`. Kombinacja określonych rzeczownik od ogólniejszych zlecenie umożliwia użytkownikowi szybko znaleźć polecenia cmdlet, jego działania, a następnie Zidentyfikuj polecenia cmdlet do jej zasobów, unikając dublowania nazwa polecenia cmdlet niepotrzebne.

Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).

## <a name="verbs"></a>Zlecenia

Po określeniu zlecenie, wskazówki dotyczące programowania wymagają użycia jednej z wstępnie zdefiniowanych czasowników, udostępniane przez środowisko Windows PowerShell. Przy użyciu jednej z tych wstępnie zdefiniowanych czasowników, użytkownik musi zagwarantować spójność między poleceń cmdlet, które piszesz i poleceń cmdlet, które są zapisywane przez firmę Microsoft i innych osób. Na przykład polecenie "Get" jest używany dla poleceń cmdlet, które pobierania danych.

Aby uzyskać więcej informacji na temat wytycznych dla zleceń zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md). Aby uzyskać listę znaków specjalnych, które nie mogą być używane w nazwy poleceń cmdlet, zobacz [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Obsługa programu Windows PowerShell funkcji

**Polecenia Cmdlet** atrybut umożliwia również określić, czy Twoje polecenie cmdlet obsługuje niektóre typowe funkcje, które są dostarczane przez środowisko Windows PowerShell. Obejmuje to obsługę typowych funkcji, takich jak potwierdzenie przez użytkownika opinii (nazywane obsługę funkcji ShouldProcess) oraz dla transakcji. (Obsługa transakcji została wprowadzona w programie Windows PowerShell 2.0).

Aby uzyskać więcej informacji na temat składni deklaracji, która służy do określania **polecenia Cmdlet** atrybutów, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definicja klasy polecenia cmdlet

Poniższy kod jest definicja klasy polecenia cmdlet GetProc. Należy zauważyć, że Pascal wielkość liter w wyrazie jest używany i że nazwa klasy zawiera czasownik i rzeczownik, polecenia cmdlet.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal wielkość liter w wyrazie

Po nadaniu nazwy poleceń cmdlet, użyj Pascal wielkość liter w wyrazie. Na przykład `Get-Item` i `Get-ItemProperty` polecenia cmdlet pokazują poprawny sposób użycia wielkich liter, podczas nadawania nazw poleceń cmdlet.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Deklaracja CmdletAttribute](./cmdlet-attribute-declaration.md)

[Polecenie cmdlet nazwy](./approved-verbs-for-windows-powershell-commands.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
