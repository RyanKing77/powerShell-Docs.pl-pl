---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z kluczami rejestru
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-keys"></a>Praca z kluczami rejestru

Ponieważ klucze rejestru są elementy na dyskach środowiska Windows PowerShell, pracy z nimi jest bardzo podobny do pracy z plikami i folderami. Jeden krytyczne różnica polega na tym, że każdy element na dysk programu Windows PowerShell opartych na rejestrze jest kontenerem, podobnie jak folder na dysku systemu plików. Wpisy rejestru oraz powiązanych wartości, są jednak właściwości elementów nie różne elementy.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Wyświetlanie listy wszystkich jego podkluczy klucza rejestru

Wszystkie elementy bezpośrednio w kluczu rejestru można wyświetlać za pomocą **Get-ChildItem**. Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub elementów systemu. Na przykład to polecenie wyświetla elementy bezpośrednio z poziomu środowiska Windows PowerShell dysku HKCU:, które odpowiada gałęzi HKEY_CURRENT_USER rejestru:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Są widoczne w gałęzi HKEY_CURRENT_USER w Edytorze rejestru (Regedit.exe) klucze najwyższego poziomu.

Ta ścieżka rejestru można również określić, określając nazwę dostawcy rejestru, a następnie "**::**". Pełna nazwa dostawcy rejestru **Microsoft.PowerShell.Core\\rejestru**, ale to może zostać skrócony nieco **rejestru**. Dowolne z poniższych poleceń, wyświetla zawartość bezpośrednio pod HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Te polecenia listy tylko bezpośrednio zawartych w niej elementów, podobnie jak przy użyciu jego Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX. Aby wyświetlić zawartych w niej elementów, należy określić **Recurse** parametru. Aby wyświetlić listę wszystkich kluczy rejestru HKCU, użyj następującego polecenia (Ta operacja może zająć bardzo dużo czasu.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** można wykonywać złożonych możliwości filtrowania, za pomocą jego **ścieżki**, **filtru**, **Include**, i **wykluczyć**parametrów, ale te parametry są zwykle tylko na podstawie nazwy. Można wykonać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object** polecenia cmdlet. Polecenie znajduje wszystkie klucze w HKCU:\\oprogramowania, które ma nie więcej niż jedną podkluczy, a także mieć dokładnie cztery wartości:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Kopiowanie kluczy

Kopiowanie wykonuje się za pomocą **Copy-Item**. Polecenie kopiuje HKLM:\\oprogramowania\\Microsoft\\Windows\\CurrentVersion i wszystkie jej właściwości w celu HKCU:\\, tworzenie nowy klucz o nazwie "CurrentVersion":

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Jeśli należy zbadać ten nowy klucz w Edytorze rejestru lub za pomocą **Get-ChildItem**, można zauważyć, że nie masz kopii podkluczy zawarte w nowej lokalizacji. Aby można było skopiować wszystkie zawartość kontenera, należy określić **Recurse** parametru. Aby poprzedniego cykliczne polecenia kopiowania, należy użyć tego polecenia:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Można nadal używać innych narzędzi, masz już dostępne do wykonywania kopii plików. Wszystkie narzędzia do edycji rejestru — tym reg.exe, regini.exe i regedit.exe—and obiektów COM, które obsługuje edycji rejestru (np. Klasa StdRegProv obiektu WScript.Shell i usługi WMI) można można używać wewnątrz środowiska Windows PowerShell.

### <a name="creating-keys"></a>Tworzenie kluczy

Tworzenie nowych kluczy w rejestrze jest łatwiejsze niż w przypadku tworzenia nowego elementu w systemie plików. Ponieważ wszystkie klucze rejestru są kontenerami, nie trzeba określić typ elementu; Możesz po prostu podać jawne ścieżkę, takich jak:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Umożliwia także ścieżkę opartej na dostawcy, aby określić klucz:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Usuwanie kluczy

Usuwanie elementów zasadniczo jest taka sama dla wszystkich dostawców. Następujące polecenia dyskretnie spowoduje usunięcie elementów:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Usunięcie wszystkich kluczy w określonym kluczu

Można usunąć zawartych w niej elementów, używając **Usuń element**, ale pojawi się monit o potwierdzenie usunięcia, jeśli element zawiera coś innego. Na przykład firma Microsoft podejmie próbę usunięcia HKCU:\\podklucza CurrentVersion utworzyliśmy, widzimy to:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Aby usunąć zawartych w niej elementów bez monitowania, określ **-Recurse** parametru:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Jeśli chcesz usunąć wszystkie elementy w HKCU:\\CurrentVersion, ale nie HKCU:\\CurrentVersion samego, możesz zamiast tego użyć:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```