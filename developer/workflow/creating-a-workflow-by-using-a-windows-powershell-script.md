---
title: Tworzenie przepływu pracy przy użyciu skryptu programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844744"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Tworzenie przepływu pracy przy użyciu skryptu programu Windows PowerShell

Możesz utworzyć przepływ pracy, przez napisanie skryptu programu Windows PowerShell. Aby utworzyć przepływ pracy, użyj przepływu pracy — słowo kluczowe, następuje nazwa przepływu pracy przed treść skryptu. Przykład:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Przepływ pracy można znaleźć w taki sam sposób jak w przypadku innych poleceń programu Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementowanie równoległe i sekwencyjne

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) obsługuje wykonanie czynności równolegle. Aby zaimplementować tę funkcję w skrypcie programu Windows PowerShell, należy użyć `parallel` — słowo kluczowe przed blok skryptu. Można również użyć `foreach -parallel` konstrukcji do iterowania po kolekcji obiektów równolegle. Do grupy działań są wykonywane w kolejności sekwencyjnej, w ramach bloku równoległego, należy ująć tej grupy działań w bloku skryptu i poprzedzać bloku ze słowem kluczowym sekwencji.

## <a name="joining-computers-to-a-domain"></a>Przyłączanie komputerów do domeny

Poniższy skrypt tworzy przepływ pracy, który umożliwia sprawdzenie stanu domeny grupy komputerów określonych przez użytkownika, jeśli nie są już połączone, a następnie umożliwia sprawdzenie stanu dołączania ich do domeny. To jest wersja skryptu przepływu pracy XAML, które wyjaśniono w [tworzenia przepływu pracy przy użyciu programu Windows PowerShell działania](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```