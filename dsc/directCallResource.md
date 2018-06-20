---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Bezpośrednie wywoływanie metod zasobów DSC
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189622"
---
# <a name="calling-dsc-resource-methods-directly"></a>Bezpośrednie wywoływanie metod zasobów DSC

>Dotyczy: Środowiska Windows PowerShell 5.0

Można użyć [Invoke DscResource](https://technet.microsoft.com/library/mt517869.aspx) polecenia cmdlet, aby bezpośrednio wywoływać funkcje i metody zasobu DSC ( **Get-TargetResource**, **TargetResource zestaw**i  **Test-TargetResource** funkcje zasobu na podstawie MOF lub **uzyskać**, **ustawić**, i **testu** metod klasy zasobu).
To może służyć przez osoby trzecie, które chcą korzystać z zasobów DSC lub jako narzędzia pomocne podczas tworzenia zasobów.

To polecenie cmdlet jest zwykle używana w połączeniu z właściwością metakonfigurację `refreshMode = 'Disabled'`, ale mogą być używane niezależnie od tego, co **refreshMode** ma ustawioną wartość.

Podczas wywoływania metody **Invoke DscResource** polecenia cmdlet, określić metody lub funkcji do wywołania przy użyciu **metody** parametru. Określ właściwości zasobu przez przekazanie obiektu hashtable jako wartość **właściwości** parametru.

Poniżej przedstawiono przykłady bezpośrednio wywołać metody zasobów:

## <a name="ensure-a-file-is-present"></a>Upewnij się, że plik istnieje

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

>**Uwaga:** bezpośrednie wywoływanie metod złożonego zasobu nie jest obsługiwane. Zamiast tego należy wywoływać metody zasobów wchodzące w skład złożonych zasobów.

## <a name="see-also"></a>Zobacz też
- [Pisanie niestandardowych zasobów DSC z MOF](authoringResourceMOF.md)
- [Pisanie niestandardowych zasobów DSC z klasami programu PowerShell](authoringResourceClass.md)
- [Debugowanie zasobów DSC](debugResource.md)