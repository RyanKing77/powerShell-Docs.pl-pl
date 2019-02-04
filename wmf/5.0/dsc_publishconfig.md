---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684507"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Dostarczanie dokumentu konfiguracji bez stosowania

[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) polecenia cmdlet kopiuje pliku MOF konfiguracji do węzła docelowego, ale nie ma zastosowania konfiguracji.
Ta konfiguracja jest stosowana podczas następnego przebiegu spójności lub po uruchomieniu [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) polecenia cmdlet.
