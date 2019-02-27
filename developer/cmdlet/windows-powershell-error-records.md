---
title: Rejestruje program Windows PowerShell błąd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: bbe04a8fb556f0f6807bc0eae6634e3cf505759e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850995"
---
# <a name="windows-powershell-error-records"></a>Rekordy błędów programu Windows PowerShell

Polecenia cmdlet należy przekazać [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt, który identyfikuje warunek błędu, jak i niepowodujące błędów.

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt zawiera następujące informacje:

- Wyjątek, który opisuje błąd. Często jest to wyjątek, który polecenie cmdlet przechwycony i przekonwertowane na rekord błędu. Każdy rekord błędu musi zawierać wyjątek.

Jeśli polecenie cmdlet nie przechwytywać wyjątek, musi utworzyć nowy wyjątek i wybierz klasę wyjątku, która najlepiej opisuje warunku błędu. Jednak nie należy zgłosić wyjątek, ponieważ jest możliwy za pośrednictwem [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) właściwość [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu.

- Identyfikator błędu, który zawiera oznaczenie docelowego, który może służyć do celów diagnostycznych i skryptów programu Windows PowerShell do obsługi określone warunki błędów za pomocą obsługi błędu. Każdy rekord błędu musi zawierać identyfikator błędu (zobacz Identyfikator błędu).

- Kategoria błędu, który zawiera oznaczenie ogólnego, który może służyć do celów diagnostycznych. Każdy rekord błędu należy określić do kategorii błędów (patrz kategoria błędu).

- Komunikat o błędzie opcjonalne zastąpienia i zalecaną akcję (zobacz komunikat o błędzie zastępczy).

- Wywołanie opcjonalne informacje na temat polecenia cmdlet, który wygenerował błąd. Informacja ta jest określona przez środowisko Windows PowerShell (zobacz komunikat dotyczący wywołania).

- Obiekt docelowy, który był przetwarzany, gdy wystąpił błąd. Może to być obiekt wejściowy lub może być inny obiekt, który przetwarza Twojego polecenia cmdlet. Na przykład polecenie `remove-item -recurse c:\somedirectory`, ten błąd może być wystąpienie obiektu FileInfo dla "c:\somedirectory\lockedfile". Informacji o obiekcie docelowym jest opcjonalne.

## <a name="error-identifier"></a>Identyfikator błędu

Kiedy tworzysz rekord błędu, należy określić identyfikator, który wskazuje warunek błędu w ramach Twojego polecenia cmdlet. Programu Windows PowerShell łączy Identyfikator docelowego o nazwie Twojego polecenia cmdlet, aby utworzyć identyfikator błędu w pełni kwalifikowaną. Identyfikator błędu w pełni kwalifikowana jest możliwy za pośrednictwem [System.Management.Automation.Errorrecord.Fullyqualifiederrorid*](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) właściwość [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)obiektu. Identyfikator błędu nie jest dostępna przez siebie. Jest on dostępny tylko jako część identyfikatora o FQDN.

Do generowania identyfikatorów błąd podczas tworzenia rekordów błędów, użyj następujących wytycznych:

- Wprowadź identyfikatory błąd określonych warunek błędu. Docelowe identyfikatory błąd do celów diagnostycznych i skrypty, które obsługują określone warunki błędów za pomocą obsługi błędu. Użytkownik powinien móc zidentyfikować ten błąd i jego źródło za pomocą identyfikatora błędu. Błąd identyfikatory umożliwia także raportowanie dla określone warunki błędów z istniejących wyjątków, tak aby nowe przypadku podklas wyjątku nie są wymagane.

- Ogólnie rzecz biorąc należy przypisać błąd różne identyfikatorach na inny kod ścieżki. Użytkownik końcowy korzysta z określonych identyfikatorów. Często każda ścieżka kodu, który wywołuje [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) lub [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ma swój własny identyfikator. Zgodnie z zasadą Zdefiniuj nowy identyfikator, gdy zdefiniujesz nowe parametry szablonu komunikatu o błędzie i na odwrót. Nie należy używać jako identyfikator komunikatu o błędzie.

- Podczas publikowania kodu przy użyciu identyfikatora określony błąd można ustanawiać semantykę błędów przy użyciu identyfikatora produktu pełny cykl pomocy technicznej. Nie należy używać go w kontekście, który semantycznie różni się od oryginalnego kontekstu. Jeśli zmienisz semantyki wystąpienia tego błędu, należy utworzyć, a następnie użyj nowego identyfikatora.

- Identyfikator określony błąd należy generalnie używać tylko w przypadku wyjątki określonego typu CLR. Jeśli zmieni się typu wyjątku lub typ obiektu docelowego, należy utworzyć, a następnie użyj nowego identyfikatora.

- Wybierz tekst dla Twojego identyfikatora błąd, odpowiadający zwięźle błędu, który dotyczy zgłoszenie. Użyj standardowych konwencji nazewnictwa i wielkości liter, .NET Framework. Nie należy używać biały znak lub znaki interpunkcyjne. Nie jest lokalizowany identyfikatory błędu.

- Dynamicznie generuje błąd identyfikatorów w sposób do nieodtwarzalne. Na przykład nie zawierają informacje o błędzie, takich jak identyfikatora procesu. Identyfikatory błędu są użyteczne tylko wtedy, gdy odnoszą się do identyfikatorów błąd widoczne dla innych użytkowników, którzy napotykają ten sam błąd.

## <a name="error-category"></a>Kategoria błędu

Kiedy tworzysz rekord błędu, należy określić kategorię, która błędu przy użyciu jednej z stałe zdefiniowane przez [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) wyliczenia. Programu Windows PowerShell używa kategorii błędów, aby wyświetlić informacje o błędzie, gdy użytkownicy `$ErrorView` zmienną `"CategoryView"`.

Unikaj używania [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) stałej. Jeśli masz wszystkie informacje o błędzie lub dotyczące działania, które spowodowały błąd, wybierz kategorię, która najlepiej opisuje błąd lub operacji, nawet jeśli kategoria nie jest idealnym stopniu spełniają.

Informacje wyświetlane przez środowisko Windows PowerShell jest określany jako ciąg widoku kategorii i jest tworzona na podstawie właściwości [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) klasy. (Ta klasa jest dostępny za pośrednictwem błąd [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) właściwości.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

Poniższa lista zawiera opis są wyświetlane następujące informacje:

- Kategoria: Definicja środowiska Windows PowerShell [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) stałej.

- TargetName: Domyślnie nazwa obiektu cmdlet przetwarzającą po wystąpieniu błędu. Lub inny ciąg zdefiniowany przez polecenie cmdlet.

- TargetType: Domyślnie typ obiektu docelowego. Lub inny ciąg zdefiniowany przez polecenie cmdlet.

- Działania: Domyślnie nazwa polecenia cmdlet, który utworzył rekord błędu. Lub niektórych innych ciągu zdefiniowany przez polecenia cmdlet.

- Przyczyna: Domyślnie typ wyjątku. Lub inny ciąg zdefiniowany przez polecenie cmdlet.

## <a name="replacement-error-message"></a>Komunikat o błędzie zastąpienia

Podczas opracowywania rekord błędu dla polecenia cmdlet domyślny komunikat o błędzie dla błędu pochodzi z domyślnym tekstem komunikatu w [System.Exception.Message](/dotnet/api/System.Exception.Message) właściwości. Jest to właściwość tylko do odczytu, którego tekst komunikatu jest przeznaczony tylko do debugowania (zgodnie z wytycznymi dla .NET Framework). Firma Microsoft zaleca utworzenie komunikat o błędzie, który zastępuje lub rozszerzają domyślny tekst komunikatu. Komunikat był bardziej przyjazny dla użytkownika i bardziej specyficznych dla danego polecenia cmdlet.

Komunikat zamieniania są dostarczane przez [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) obiektu. Użyj jednej z następujących konstruktorów tego obiektu, ponieważ zapewniają one informacje dodatkowe lokalizacji, które mogą być używane przez program Windows PowerShell.

- [ErrorDetails.ErrorDetails (polecenia Cmdlet, String, String, obiekt\[System.Management.Automation.Errordetails.%23Ctor%28System.Management.Automation.Cmdlet%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Użyj tego konstruktora, jeśli parametry szablonu usługi jest ciągiem zasobów z tego samego zestawu, w którym zaimplementowano polecenia cmdlet lub jeśli chcesz załadować ciąg szablonu za pomocą zastępowania metody [System.Management.Automation.Cmdlet.Getresourcestring* ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) metody.

- [ErrorDetails.ErrorDetails (zestawu, String, String, obiekt\[System.Management.Automation.Errordetails.%23Ctor%28System.Reflection.Assembly%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = imię i nazwisko](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Użyj tego konstruktora, jeśli ciąg szablonu jest w innym zestawie, a nie załadowała jej za pomocą zastępowania metody [System.Management.Automation.Cmdlet.Getresourcestring*](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Komunikat o zastąpienie powinny być zgodne z wytycznych projektowania programu .NET Framework do zapisywania komunikatów o wyjątkach z niewielkie różnice. Stan wytycznych komunikaty o wyjątkach powinny być napisane dla deweloperów. Te komunikaty zastąpienie mają być zapisywane dla użytkownika polecenia cmdlet.

Komunikat o błędzie zamieniania, należy dodać przed [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) lub [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody są wywoływane. . Aby dodać komunikat zamieniania, należy ustawić [System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) właściwości rekordu błędu. Gdy ta właściwość jest ustawiona, programu Windows PowerShell Wyświetla [System.Management.Automation.Errordetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) właściwości zamiast domyślny tekst komunikatu.

## <a name="recommended-action-information"></a>Zaleca się informacje o akcji

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) obiektu można również zawierają informacje dotyczące działania, jakie są zalecane, gdy wystąpi błąd.

## <a name="invocation-information"></a>Informacje o wywołania

Jeśli polecenie cmdlet używa [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) lub [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) zgłosić rekord błędu programu Windows PowerShell automatycznie dodaje informacje opisujące polecenia, która została wywołana, gdy wystąpił błąd. Te informacje są dostarczane przez [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) obiekt, który zawiera nazwę polecenia cmdlet, która została wywołana przy użyciu polecenia polecenia i informacje na temat procesu lub skryptu. Ta właściwość jest tylko do odczytu.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Raportowanie błędów programu Windows PowerShell](./error-reporting-concepts.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
