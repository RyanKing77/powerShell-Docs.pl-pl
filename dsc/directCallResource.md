---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Bezpośrednie wywoływanie metod zasobów DSC"
ms.openlocfilehash: ab00e66d526eda244500a41e450c56b0151274ee
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="calling-dsc-resource-methods-directly"></a>Bezpośrednie wywoływanie metod zasobów DSC

>Dotyczy: Środowiska Windows PowerShell 5.0

Można użyć [Invoke DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) polecenia cmdlet, aby bezpośrednio wywoływać funkcje i metody zasobu DSC ( **Get-TargetResource**, **TargetResource zestaw**i  **Test-TargetResource** funkcje zasobu na podstawie MOF lub **uzyskać**, **ustawić**, i **testu** metod klasy zasobu). To może służyć przez osoby trzecie, które chcą korzystać z zasobów DSC lub jako narzędzia pomocne podczas tworzenia zasobów. 

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

