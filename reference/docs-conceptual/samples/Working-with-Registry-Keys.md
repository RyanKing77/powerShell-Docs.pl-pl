---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z kluczami rejestru
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: e7b497ec2fccf9ba3934439a9c1e9be3cf70a705
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293201"
---
# <a name="working-with-registry-keys"></a>Praca z kluczami rejestru

Ponieważ klucze rejestru są elementy na dyskach programu Windows PowerShell, Praca z nimi jest bardzo podobna do pracy z plikami i folderami. Jeden krytyczne różnica polega na tym, że każdy element na dysk programu Windows PowerShell opartych na rejestrze to kontener, podobnie jak folder na dysku systemu plików. Jednakże wpisy rejestru i ich skojarzone wartości są właściwości elementów, a nie odrębne elementy.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Wyświetlanie listy wszystkich jego podkluczy klucza rejestru

Możesz wyświetlić wszystkie elementy bezpośrednio w ramach klucza rejestru za pomocą **Get-ChildItem**. Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub systemu elementów. Na przykład, to polecenie wyświetla elementy bezpośrednio z poziomu środowiska Windows PowerShell dysku HKCU:, która odnosi się do gałęzi rejestru HKEY_CURRENT_USER:

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

Są to klucze najwyższego poziomu, widoczne w gałęzi HKEY_CURRENT_USER w Edytorze rejestru (Regedit.exe).

Można również określić tę ścieżkę rejestru, określając nazwę dostawcy rejestru, a następnie "**::**". Pełna nazwa dostawcy rejestru jest **Microsoft.PowerShell.Core\\rejestru**, ale to może zostać skrócony tylko **rejestru**. Dowolne z następujących poleceń spowoduje wyświetlanie zawartości bezpośrednio pod HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Te polecenia powodują wyświetlenie listy tylko bezpośrednio zawartych elementów, podobnie jak przy użyciu przez Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX. Aby wyświetlić zawartych w niej elementów, należy określić **Recurse** parametru. Aby wyświetlić listę wszystkich kluczy rejestru w HKCU, użyj następującego polecenia (Ta operacja może potrwać bardzo długo.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Polecenie GET-ChildItem** mogą wykonywać złożonych możliwości filtrowania, za pośrednictwem jego **ścieżki**, **filtru**, **Include**, i **wykluczyć**parametrów, ale te parametry są zwykle tylko na podstawie nazwy. Można wykonywać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object** polecenia cmdlet. Poniższe polecenie znajduje wszystkie klucze w ramach HKCU:\\oprogramowania, które mają nie więcej niż jednego podklucza, a także mieć dokładnie cztery wartości:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Kopiowanie kluczy

Kopiowanie odbywa się za pomocą **Copy-Item**. Następujące polecenie kopiuje HKLM:\\oprogramowania\\Microsoft\\Windows\\CurrentVersion i wszystkich jego właściwości w celu HKCU:\\, tworząc nowy klucz o nazwie "CurrentVersion":

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Jeśli Sprawdź ten nowy klucz w Edytorze rejestru lub za pomocą **Get-ChildItem**, zauważysz, że nie masz kopii podkluczy zawarte w nowej lokalizacji. Aby skopiować całą zawartość kontenerów, musisz określić **Recurse** parametru. Aby poprzedniego cyklicznego polecenia kopiowania, należy użyć tego polecenia:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Nadal można użyć innych narzędzi, masz już dostępny, aby wykonać kopie plików. Wszystkie narzędzia do edytowania rejestru — w tym reg.exe regini.exe i regedit.exe—and obiektów COM, które obsługują edytowanie rejestru (np. Klasa StdRegProv obiektu WScript.Shell i usługi WMI) można można używać wewnątrz środowiska Windows PowerShell.

## <a name="creating-keys"></a>Tworzenie kluczy

Tworzenie nowych kluczy w rejestrze jest łatwiejsze niż Tworzenie nowego elementu w systemie plików. Wszystkie klucze rejestru są kontenerami, dlatego nie musisz określić typ elementu; Możesz po prostu podać jawna ścieżka, takich jak:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Aby określić klucz umożliwia także ścieżkę opartą na dostawcy:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a>Usuwanie kluczy

Usuwanie elementów zasadniczo jest taka sama dla wszystkich dostawców. Następujące polecenia dyskretnie spowoduje usunięcie elementów:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Usunięcie wszystkich kluczy w określonym kluczu

Można usunąć zawartych w niej elementów przy użyciu **Remove-Item**, ale użytkownik jest monitowany o potwierdzenie usunięcia, jeśli element zawiera coś innego. Na przykład, jeśli firma Microsoft podejmie próbę usunięcia HKCU:\\podklucz CurrentVersion utworzyliśmy, zobaczymy to:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Aby usunąć zawartych w niej elementów bez monitowania użytkownika, należy określić **-Recurse** parametru:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Jeśli chcesz usunąć wszystkie elementy w ramach HKCU:\\CurrentVersion, ale nie HKCU:\\CurrentVersion samego, możesz zamiast tego użyć:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```