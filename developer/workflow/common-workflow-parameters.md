---
title: Typowe parametry przepływu pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080411"
---
# <a name="common-workflow-parameters"></a>Typowe parametry przepływu pracy

Działania przepływu pracy, generowane przez polecenie cmdlet programu Windows PowerShell definiuje liczbę parametrów, które oznacza wspólne dla wszystkich działań. W czasie tworzenia, dzięki czemu autorzy przepływów pracy można dostosować działania można określić podzbiór tych parametrów. Innym podzbiorem te parametry można określić przez użytkownika podczas wywoływania działania.

Typowe parametry przepływu pracy są pogrupowane na kilka kategorii.

## <a name="connectivity-parameters"></a>Parametry połączenia

|Nazwa|Typ|Opis|Może być określony przez użytkownika końcowego w czasie wykonywania?|Można określić przez autora przepływu pracy w czasie tworzenia?|Można określić przez autora przepływu pracy przy konkretyzacji?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|Ciąg]|Lista nazw komputerów, dla których można uruchomić zadania.|Tak|Yes|Tak|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Poświadczenia uwierzytelniania do użycia do logowania się do określonych przez parametr PSComputerName komputerów. Ten parametr jest prawidłowy tylko wtedy, gdy określono PSComputerName.|Tak|Yes|Tak|
|PSPort|UInt32|Port, który ma być używany do uruchamiania przepływu pracy.|Tak|Yes|Tak|
|PSUseSSL|Wartość logiczna|Użyj protokołu Secure Sockets Layer (SSL), aby nawiązać bezpiecznego połączenia z komputerem zdalnym, aby uruchomić przepływ pracy.|Tak|Yes|Tak|
|PSConfigurationName|Ciąg|Konfiguracja sesji używane do uruchamiania przepływu pracy.|Tak|Yes|Tak|
|PSApplicationName|Ciąg|Aplikacja część nazwy połączenia identyfikatora URI w celu wykonywania przepływu pracy. Użyj tego parametru, tylko wtedy, gdy nie korzystasz z parametru ConnectionURI.|Tak|Yes|Tak|
|PSThrottleLimit|UInt32|Maksymalna liczba jednoczesnych połączeń, które można ustanowić w celu uruchomienia przepływu pracy.|Tak|TBD|Tak|
|PSConnectionURI|Ciąg]|Tablica pełną identyfikatory URI, które określ punkty końcowe dla interaktywnych sesji używane do uruchamiania przepływu pracy.|Tak|Yes|Tak|
|PSAllowRedirection|Wartość logiczna|Określa, czy w celu umożliwienia przekierowania tego połączenia do alternatywnego identyfikatora URI, aby uruchomić przepływ pracy.|Tak|Yes|Tak|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Zaawansowane opcje sesji używane do uruchamiania przepływu pracy.|Tak|Yes|Tak|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Wartość [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) wyliczenie, które określa mechanizm uwierzytelniania używany do uwierzytelniania poświadczeń użytkownika.|Tak|Yes|Tak|
|PSCertificateThumbprint|Ciąg|Cyfrowego certyfikatu klucza publicznego (X509) konta użytkownika, który ma uprawnienia do uruchamiania przepływu pracy.|Tak|Yes|Tak|

### <a name="behavior-parameters"></a>Parametry zachowania