---
title: Jak dodać opis polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083522"
---
# <a name="how-to-add-a-cmdlet-description"></a>Jak dodać opis polecenia cmdlet

W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcji Opis pomocy polecenia cmdlet. W pliku pomocy tej zawartości zostanie dodany do węzła polecenie dla każdego polecenia cmdlet.

> [!NOTE]
> Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell. Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.

### <a name="to-add-a-description"></a>Aby dodać opis

- Rozpocznij od wyjaśniających podstawowe funkcje polecenia cmdlet, które bardziej szczegółowo. W wielu przypadkach można wyjaśnić terminów używanych w nazwa polecenia cmdlet i zilustrowania koncepcji zaznajomiony z przykładem. Na przykład jeśli polecenie cmdlet dołącza dane do pliku, wyjaśniono, dodaje dane na końcu istniejącego pliku.

- Aby znaleźć wszystkie funkcje polecenia cmdlet, przejrzyj listę parametrów. Opisano podstawową funkcją polecenia cmdlet, a następnie dołącz inne funkcje i możliwości. Załóżmy na przykład, jeśli jest główna funkcja polecenia cmdlet, aby zmienić jedną właściwość, ale polecenia cmdlet można zmienić wszystkie właściwości, więc w szczegółowy opis. Jeśli parametry polecenia cmdlet umożliwiają użytkownikom uzyskania informacji na różne sposoby, opisano je.

- Zawierają informacje dotyczące sposobów, w których użytkownicy mogą używać polecenia cmdlet, oprócz używa oczywiste. Na przykład, można użyć obiektu, `Get-Host` polecenie cmdlet pobiera, aby zmienić kolor tekstu w oknie wiersza polecenia programu Windows PowerShell.

  Przykład:  " `Get-Acl` Polecenie cmdlet pobiera obiekty reprezentujące deskryptor zabezpieczeń plik lub zasób. Deskryptor zabezpieczeń zawiera listy kontroli dostępu (ACL) zasobu. Listy ACL określa uprawnienia, które użytkownicy i grupy użytkowników mają dostęp do zasobu".

- Szczegółowy opis powinna opisywać polecenia cmdlet, ale nie powinien on zawierać pojęcia, które korzysta z polecenia cmdlet. Umieść definicje pojęcie w dodatkowe uwagi.

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
