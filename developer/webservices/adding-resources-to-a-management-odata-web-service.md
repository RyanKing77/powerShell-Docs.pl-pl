---
title: Dodawanie zasobów do zarządzania OData usługi sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080785"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Dodawanie zasobów do internetowej usługi OData zarządzania

W tym przykładzie pokazano, jak można dodać zasobu do istniejącej usługi sieci web OData zarządzania przy użyciu projektanta schematu OData zarządzania. [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Przykładowa aplikacja tworzy usługi sieci web, która udostępnia zasoby przetwarzania i serwera. W tym przykładzie dodasz zasób maszynę wirtualną (VM) do usługi sieci web.

## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie założono, że pobrane i zainstalowane [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) przykładowy zgodnie z opisem w [Tworzenie usługi sieci Web Windows PowerShell](./creating-a-management-odata-web-service.md), oraz że zostały pobrane i zainstalowane [Projektanta schematu OData zarządzania](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). W tym temacie założono również, że masz zainstalowany na komputerze, w którym konfiguruje się punkt końcowy Odata zarządzania moduł funkcji Hyper-V Windows PowerShell.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Dodawanie maszyny Wirtualnej jako zasób do usługi sieci Web

Pierwszym krokiem jest importowanie schematu z istniejącego punktu końcowego OData zarządzania do projektanta schematu. Poniższa procedura opisuje, jak to zrobić.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importowanie schematu do projektanta schematu

1. Otwórz projektanta schematu OData zarządzania.

2. Z **pliku** menu, wybierz opcję **pliku** ; **Nowe** ; **Pliku**. **Nowy plik** zostanie wyświetlone okno dialogowe.

3. Kliknij przycisk **modelu OData zarządzania**, a następnie kliknij przycisk **Otwórz**.

4. Kliknij prawym przyciskiem myszy w oknie głównym, a następnie kliknij przycisk **pliku schematu** ; **Importu**. **Otwórz** zostanie wyświetlone okno dialogowe.

5. Przejdź do folderu, w którym konfiguruje się usługę sieci web OData zarządzania [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) próbki. Jeśli skrypt programu Windows PowerShell, wyposażone w tym przykładzie jest używany do konfigurowania punktu końcowego bez modyfikowania skryptu, wybrany folder jest **C:\inetpub\wwwroot\Modata**. Wybierz Schema.mof, a następnie kliknij przycisk **Otwórz**.

   W tym momencie otwierania plików Schema.mof i Schema.xml w edytorze tekstów i zwróć uwagę, że zawierają one mapowania dla zasobów przetwarzania i usługi. Plik Schema.mof używa [Distributed Management Task Force](https://www.dmtf.org/) standard (DTMF) MOF (Managed Object). Plik schema.xml używa schematu XML, który jest opisany w [schemat mapowania zasobów](./resource-mapping-schema.md).

   Poniższa procedura opisuje sposób importowania poleceń cmdlet funkcji Hyper-V, w modelu schematu.

#### <a name="importing-cmdlets-into-the-schema"></a>Importowanie poleceń cmdlet do schematu

1. Kliknij prawym przyciskiem myszy pusty obszar okna Projektanta schematu, a następnie kliknij przycisk **poleceń cmdlet importu**. **Kreatora importowania poleceń Cmdlet** zostanie wyświetlone okno dialogowe.

2. Upewnij się, że **komputera lokalnego** jest zaznaczone, a następnie kliknij przycisk **dalej**.

3. Upewnij się, że wybrano zainstalowanych modułów programu Windows PowerShell, a następnie z listy rozwijanej wybierz funkcji Hyper-V. Kliknij przycisk **dalej**. Kliknij przycisk **Dalej**.

4. W **rzeczownik polecenia Cmdlet** listy wybierz **maszyny Wirtualnej**. Kliknij przycisk **Dalej**.

5. W tym przykładzie firma Microsoft będzie powiązać tylko polecenia Get i Delete za pomocą poleceń cmdlet. Wyczyść **Utwórz** i **aktualizacji** pole wyboru i upewnij się, że **UZYSKAĆ** i **Usuń** są zaznaczone pola wyboru. Upewnij się, że `Get-VM` wybrano polecenie cmdlet **UZYSKAĆ**i `Remove-VM` wybrano polecenie cmdlet **Usuń**.

6. Ponieważ metadane dla poleceń cmdlet maszyny Wirtualnej nie określa typ danych wyjściowych, należy uruchomić polecenie cmdlet, aby określić typ danych wyjściowych. Wybierz **Podaj typ danych wyjściowych** i kliknij przycisk **Uruchom polecenie cmdlet**. **Uruchom polecenie Cmdlet** zostanie wyświetlone okno dialogowe. Kliknij pozycję **Run** (Uruchom). **Typu CLR** pole jest wypełniane `VirtualMachine` typu. Kliknij przycisk **OK**, następnie kliknij przycisk **dalej**.

7. Domyślnie wszystkie właściwości obiektu VirtualMachine zaznaczone. Możesz wyczyścić wszystkie właściwości, które mają być jako część danych zwracane, gdy żądanie tego zasobu z usługą sieci web. Kliknij przycisk **Dalej**.

8. Należy wybrać co najmniej jedna właściwość ma być używany jako klucz. Wybierz **nazwa** na liście i kliknij przycisk **dalej**.

9. Następne okno umożliwia mapowanie właściwości zasobu OData zarządzania właściwości podstawowych poleceń cmdlet. Kreator mapy właściwości o identycznych nazwach domyślnie. Na przykład `ComputerName` właściwość zasobu jest mapowana na `ComputerName` właściwości polecenia cmdlet.  Dzięki temu można określić `ComputerName` właściwości w żądaniu skierowanym do usługi sieci web i ma wartość, określaną przekazania do `Get-VM` polecenia cmdlet. `Id` i `Name` również są mapowane domyślnie.

   10. Kliknij przycisk **dalej**, następnie kliknij przycisk **Zakończ**.

       Zasób maszyny Wirtualnej, która jest teraz wyświetlany w oknie projektanta schematu. Można sprawdzić właściwości i operacje skojarzone z zasobem. Następnie zostaną wyeksportowane pliki schematów zaktualizowane na katalog wirtualny usługi sieci web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Eksportowanie plików schematów z projektanta schematu

1. Kliknij prawym przyciskiem myszy pusty obszar okna Projektanta schematu, a następnie kliknij przycisk **pliku schematu** ; **Wyeksportować**. **Zapisz jako** zostanie wyświetlone okno dialogowe.

2. Przejdź do katalogu, z którego importowany jest plik MOF. Nadaj plikowi nazwę taka sama jak oryginalny plik MOF (Schema.mof domyślnie), a następnie kliknij przycisk **Zapisz**. Upewnij się, że chcesz zastąpić istniejący plik.

   Mimo że nie został jawnie określony w **Zapisz jako** okno dialogowe, spowoduje to zastąpienie pliku Schema.mof, jak i Schema.xml w pliku.

## <a name="next-steps"></a>Następne kroki

Dostęp do nowego zasobu maszyny Wirtualnej z usługą sieci web OData zarządzania, należy zaktualizować plik RbacConfiguration.xml, aby zezwolić na dostęp do modułu funkcji Hyper-V Windows PowerShell, zgodnie z opisem w [autoryzacji opartej na rolach Konfigurowanie](./configuring-role-based-authorization.md), i należy również ponownie uruchomić usługę sieci web.