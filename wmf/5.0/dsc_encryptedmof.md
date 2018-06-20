---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4c2a3fb15b108f1a8e9fd271a620bcb1cb8c77ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222340"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Domyślnie są szyfrowane MOF dokumentów

Konfiguracja dokumenty zawierają poufne informacje. W poprzednich wersjach usługi Konfiguracja DSC były wymagane do rozpowszechniania certyfikatów i zarządzania nimi Aby zabezpieczyć poświadczenia w ramach konfiguracji. Dla wielu to zarządzanie znaczne obciążenie i nawet w przypadku wszystkich prac zajęło w tym, które nadal pozostawiono niektóre informacje konfiguracji, które nie były i nie może być zabezpieczone.

Nie jest już przypadku ponieważ **cała konfiguracja za są domyślnie zabezpieczone**. Niezbędne są nie certyfikatów lub ustawienia konfiguracji meta. Wtedy konfiguracji MOF jest zapisywany na dysku przez lokalnego Menedżera konfiguracji (LCM) w docelowym węźle, są szyfrowane. Za są szyfrowane za pomocą [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Uwaga:** za generowane przez skrypt konfiguracji nie są szyfrowane.

**Przykład:** szyfrowania w trybie push ![szyfrowania MOF](../images/MOF_Encryption.jpg)

Jeśli korzystasz już z metody certyfikatu do szyfrowania haseł lub jeśli potrzebne są dodatkowe zabezpieczenia dla hasła, [istniejącą metodę szyfrowania opartego na certyfikatach](https://msdn.microsoft.com/powershell/dsc/securemof) będą nadal działać. Wynik zostanie dokument MOF, który jest w pełni szyfrowane przy użyciu DPAPIs i mieć Ponadto hasła szyfrowane w niej.

Szyfrowanie dotyczy tylko dokumentów MOF konfiguracji (pending.mof, current.mof, previous.mof i częściowe za). Meta konfiguracji za nadal są zapisywane w postaci zwykłego tekstu, ponieważ zawierają one mniej prawdopodobne kluczy tajnych.
