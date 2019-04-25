---
title: Tworzenie przepływu pracy za pomocą programu Windows PowerShell działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080442"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Tworzenie przepływu pracy przy użyciu działań programu Windows PowerShell

Możesz utworzyć przepływ pracy programu Windows PowerShell, zaznaczając działań do przybornika Visual Studio i przeciągając je w oknie projektanta przepływów pracy. Aby uzyskać informacji na temat dodawania działania programu Windows PowerShell do przybornika Visual Studio, zobacz [Dodawanie Windows PowerShell działań do przybornika Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

W poniższych procedurach opisano sposób tworzenia przepływu pracy, który umożliwia sprawdzenie stanu domeny grupy komputerów określonych przez użytkownika, jeśli nie są już połączone, a następnie umożliwia sprawdzenie stanu dołączania ich do domeny.

### <a name="setting-up-the-project"></a>Konfigurowanie projektu

1. Postępuj zgodnie z procedurą w [Dodawanie Windows PowerShell działań do przybornika Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) do tworzenia projektu przepływu pracy i dodawanie działań z [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) i [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) zestawów do przybornika.

2. Dodaj System.Management.Automation Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities i Microsoft.PowerShell.Commands.Management tego projektu jako zestawy odwołań.

### <a name="adding-activities-to-the-workflow"></a>Dodawanie działań do przepływu pracy

1. Dodaj **sekwencji** działania w przepływie pracy.

2. Utwórz argument o nazwie `ComputerName` z typem argumentu `String[]`. Ten argument reprezentuje nazwy komputerów, aby sprawdzić i Dołącz.

3. Utwórz argument o nazwie `DomainCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Ten argument reprezentuje poświadczenia domeny konta domeny, który jest autoryzowany do przyłączenia komputera do domeny.

4. Utwórz argument o nazwie `MachineCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Ten argument reprezentuje poświadczenia administratora na komputerach w celu sprawdzenia i Dołącz do.

5. Dodaj **ParallelForEach** działania wewnątrz **sekwencji** działania. Wprowadź `comp` i `ComputerName` w tekst pola tak, aby pętla wykonuje iterację przez elementy `ComputerName` tablicy.

6. Dodaj **sekwencji** działania do treści **ParallelForEach** działania. Ustaw **DisplayName** właściwości Sekwencja `JoinDomain`.

7. Dodaj **GetWmiObject** działanie **JoinDomain** sekwencji.

8. Edytowanie właściwości **GetWmiObject** działania w następujący sposób.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Class**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Dodaj **AddComputer** działanie **JoinDomain** sekwencji po **GetWmiObject** działania.

10. Edytowanie właściwości **AddComputer** działania w następujący sposób.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**NazwaKomputera**|{comp}|
    |**DomainCredential**|DomainCred|

11. Dodaj **RestartComputer** działanie **JoinDomain** sekwencji po **AddComputer** działania.

12. Edytowanie właściwości **RestartComputer** działania w następujący sposób.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**NazwaKomputera**|{comp}|
    |**Poświadczenie**|MachineCred|
    |**Aby uzyskać**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Czekaj|True|
    |PSComputerName|{""}|

13. Dodaj **GetWmiObject** działanie **JoinDomain** sekwencji po **RestartComputer** działania. Edycja jej właściwości na taki sam jak poprzedni **GetWmiObject** działania.

    Po zakończeniu procedury okna projektu przepływu pracy powinien wyglądać następująco.

    ![JoinDomain XAML w Projektancie przepływu pracy](../media/joindomainworkflow.png)
    ![JoinDomain XAML w Projektancie przepływu pracy](../media/joindomainworkflow.png "JoinDomainWorkflow")