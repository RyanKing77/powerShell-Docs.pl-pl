---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Bezpośrednie wywoływanie metod zasobów DSC
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404753"
---
# <a name="calling-dsc-resource-methods-directly"></a>Bezpośrednie wywoływanie metod zasobów DSC

>Dotyczy: Windows PowerShell 5.0

Możesz użyć [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) polecenia cmdlet, aby bezpośrednio wywoływać funkcje lub metod zasobów DSC ( **Get TargetResource**, **TargetResource zestaw**i  **Test-TargetResource** funkcje zasób oparty na pliku MOF lub **uzyskać**, **ustaw**, i **testu** metody oparte na klasach zasobów).
To może służyć przez osoby trzecie, które mają być używane zasoby DSC lub jako narzędzia pomocne podczas tworzenia zasobów.

To polecenie cmdlet jest zwykle używana w połączeniu z właściwością metaconfiguration `refreshMode = 'Disabled'`, ale można ich używać niezależnie od tego, co **refreshMode** jest równa.

Podczas wywoływania **Invoke-DscResource** polecenia cmdlet, określ metoda lub funkcja do wywołania przy użyciu **metoda** parametru. Określ właściwości zasobu przez przekazanie skrótów jako wartość **właściwość** parametru.

Poniżej przedstawiono przykłady bezpośrednie wywoływanie metod zasobów:

## <a name="ensure-a-file-is-present"></a>Upewnij się, że plik znajduje się

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testowanie, czy plik istnieje

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Pobierz zawartość pliku

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Uwaga:** Bezpośrednie wywoływanie metod zasobów złożonego nie jest obsługiwane. Zamiast tego należy wywołać metodę zasobów, które tworzą złożonego zasobów.

## <a name="see-also"></a>Zobacz też
- [Pisanie zasobu DSC niestandardowych z pliku MOF](../resources/authoringResourceMOF.md)
- [Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](../resources/authoringResourceClass.md)
- [Debugowanie zasobów DSC](../troubleshooting/debugResource.md)