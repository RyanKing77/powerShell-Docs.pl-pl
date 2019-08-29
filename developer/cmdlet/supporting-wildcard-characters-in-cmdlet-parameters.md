---
title: Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104443"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet

Często należy zaprojektować polecenie cmdlet do uruchamiania względem grupy zasobów, a nie do pojedynczego zasobu. Na przykład polecenie cmdlet może potrzebować znaleźć wszystkie pliki w magazynie danych, które mają taką samą nazwę lub rozszerzenie. Należy zapewnić obsługę symboli wieloznacznych podczas projektowania polecenia cmdlet, które zostanie uruchomione względem grupy zasobów.

> [!NOTE]
> Używanie symboli wieloznacznych jest czasami określane jako *obsługi symboli wieloznacznych*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Polecenia cmdlet programu Windows PowerShell, które używają symboli wieloznacznych

 Wiele poleceń cmdlet programu Windows PowerShell obsługuje symbole wieloznaczne dla wartości parametrów. Na przykład niemal każde polecenie cmdlet, które ma `Name` parametr `Path` lub obsługuje symbole wieloznaczne dla tych parametrów. (Chociaż większość poleceń cmdlet, które mają `Path` parametr ma również `LiteralPath` parametr, który nie obsługuje symboli wieloznacznych). Następujące polecenie pokazuje, w jaki sposób symbol wieloznaczny jest używany do zwracania wszystkich poleceń cmdlet w bieżącej sesji, których nazwa zawiera zlecenie get.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Obsługiwane symbole wieloznaczne

Program Windows PowerShell obsługuje następujące symbole wieloznaczne.

| Znaku |                             Opis                             |  Przykład   |     Zgodne      | Nie jest zgodny z |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Dopasowuje zero lub więcej znaków, zaczynając od określonej pozycji | `a*`       | A, AG, Apple     |                |
| ?        | Dopasowuje dowolny znak na określonej pozycji                     | `?n`       | , W, na       | został            |
| [ ]      | Dopasowuje zakres znaków                                       | `[a-l]ook` | książka, Cooka, wygląd | NOOK, trwało     |
| [ ]      | Dopasowuje określone znaki                                    | `[bn]ook`  | książka, NOOK       | Cooka, spójrz     |

Podczas projektowania poleceń cmdlet, które obsługują symbole wieloznaczne, Zezwalaj na kombinacje symboli wieloznacznych. Na przykład następujące polecenie używa `Get-ChildItem` polecenia cmdlet w celu pobrania wszystkich plików. txt, które znajdują się w folderze c:\Techdocs i zaczynają się od liter od "a" do "l".

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Poprzednie polecenie korzysta z symbolu wieloznacznego `[a-l]` zakresu, aby określić, że nazwa pliku powinna zaczynać się od znaków od "a" do "l" i `*` używa znaku wieloznacznego jako symbolu zastępczego dla wszelkich znaków między pierwszą literą nazwy pliku i rozszerzenie **. txt** .

W poniższym przykładzie użyto wzorca wieloznacznego zakresu, który wyklucza literę "d", ale zawiera wszystkie inne litery od "a" do "f".

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Obsługa znaków literału w wzorcach symboli wieloznacznych

Jeśli określony wzorzec wieloznaczny zawiera znaki literału, które nie powinny być interpretted jako symbole wieloznaczne, użyj znaku cudzysłowu (`` ` ``) jako znaku ucieczki. W przypadku określenia znaków literału int w interfejsie API programu PowerShell należy użyć pojedynczego znacznika. W przypadku określenia znaków literału w wierszu polecenia programu PowerShell należy użyć dwóch znaczników.

Na przykład poniższy wzorzec zawiera dwa nawiasy, które muszą być wykonane dosłownie.

W przypadku użycia w interfejsie API programu PowerShell:

- "Jan Kowalski \`[*"] "

Gdy jest używany z wiersza polecenia programu PowerShell:

- "Jan Kowalski \` \`[*\`"] "

Ten wzorzec pasuje do "Jan Kowalski [Marketing]" lub "Jan Kowalski [programowanie]". Przykład:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Znaki danych wyjściowych polecenia cmdlet i symboli wieloznacznych

Gdy parametry poleceń cmdlet obsługują symbole wieloznaczne, operacja zwykle generuje tablicę wyjściową.
Czasami nie ma sensu, aby obsługiwał tablicę wyjściową, ponieważ użytkownik może użyć tylko jednego elementu. Na przykład `Set-Location` polecenie cmdlet nie obsługuje danych wyjściowych tablicy, ponieważ użytkownik ustawia tylko jedną lokalizację. W tym wystąpieniu polecenie cmdlet nadal obsługuje symbole wieloznaczne, ale wymusza rozpoznawanie do pojedynczej lokalizacji.

## <a name="see-also"></a>Zobacz też

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Klasa WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
