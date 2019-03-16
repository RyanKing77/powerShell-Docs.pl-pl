---
title: Pojęcia dotyczące raportów o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054411"
---
# <a name="error-reporting-concepts"></a>Pojęcia dotyczące raportowania błędów

Windows PowerShell udostępnia dwa mechanizmy zgłaszania błędów: jeden mechanizm *przerywa błędy* i inny mechanizm *błędy niepowodujące*. Ważne jest dla Twojego polecenia cmdlet, aby włączyć raportowanie błędów poprawnie tak, aby aplikacji hosta, która jest uruchomiona poleceń cmdlet pozwala reagować w odpowiedni sposób.

Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody, gdy wystąpi błąd, który nie jest lub nie powinien zezwalać na polecenia cmdlet kontynuować przetwarzanie jej danych wejściowych obiektów. Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, aby zgłaszać błędy niepowodujące w przypadku polecenia cmdlet można kontynuować przetwarzanie danych wejściowych obiektów. Obie metody zapewniają rekord błędu, używanego przez aplikację hosta można zbadać przyczynę błędu.

Skorzystaj z poniższych wskazówek, aby określić, czy błąd jest kończącym lub błąd niepowodujący.

- Błąd jest błąd, jeśli uniemożliwia Twojego polecenia cmdlet, z dalszego przetwarzania bieżącego obiektu lub pomyślnie przetwarzania wszelkich dalszych danych wejściowych obiektów, niezależnie od ich zawartości.

- Błąd jest błąd powodujący zakończenie, jeśli nie chcesz Twojego polecenia cmdlet kontynuować przetwarzanie bieżącego obiektu lub wszelkich dalszych danych wejściowych obiektów, niezależnie od ich zawartości.

- Błąd jest błąd powodujący zakończenie go w poleceniu cmdlet, które przyjmują ani nie zwraca obiektu lub jeśli nastąpi to w poleceniu cmdlet, który akceptuje lub zwraca tylko jeden obiekt.

- Błąd jest błąd niepowodujący, jeśli chcesz Twojego polecenia cmdlet kontynuować przetwarzanie bieżący obiekt i wszystkie obiekty dalszych danych wejściowych.

- Błąd jest błąd niepowodujący, jeżeli jest powiązany do określonego obiektu wejściowego lub podzbiór obiektów danych wejściowych.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell błąd rekordów](./windows-powershell-error-records.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
