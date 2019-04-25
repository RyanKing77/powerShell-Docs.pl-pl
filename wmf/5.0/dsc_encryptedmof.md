---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085712"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Plik MOF dokumenty są domyślnie szyfrowane

Konfiguracja dokumentów zawierają poufne informacje. W poprzednich wersjach DSC były wymagane do rozpowszechniania certyfikatów i zarządzanie nimi w celu zabezpieczenia poświadczeń w ramach konfiguracji. Dla wielu to znaczny zarządzaniem, a nawet w przypadku wszystkich prac, jaki zajęło czynność, którą nadal pozostawiono niektórych informacji konfiguracyjnych, które nie były i nie może być zabezpieczone.

Nie są już tak jest ponieważ **cała konfiguracja pliki MOF są domyślnie zabezpieczone**. Nie certyfikatów lub ustawienia konfiguracji meta są wymagane. Ilekroć są zapisywane w pliku MOF konfiguracji na dysku przez Menedżera konfiguracji (LCM), lokalnych, w węźle docelowym, są szyfrowane. Pliki MOF są szyfrowane za pomocą [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Uwaga:** Pliki MOF wygenerowane przez skrypt konfiguracji nie są szyfrowane.

**Przykład:** Szyfrowanie w trybie wypychania ![szyfrowania pliku MOF](../images/MOF_Encryption.jpg)

Jeśli używana jest metoda certyfikatu do szyfrowania haseł lub jeśli potrzebne są dodatkowe zabezpieczenia dla hasła, [istniejącą metodę szyfrowania opartego na certyfikatach](https://msdn.microsoft.com/powershell/dsc/securemof) będą nadal działać. Wynik będzie dokument MOF, który jest w pełni zaszyfrowane przy użyciu DPAPIs i dodatkowo mają hasła szyfrowane w nim.

To szyfrowanie ma zastosowanie tylko do konfiguracji MOF dokumentów (pending.mof, current.mof, previous.mof i za częściowe). Pliki MOF konfiguracji meta nadal są zapisywane w postaci zwykłego tekstu, ponieważ zawierają one mniej prawdopodobne wpisów tajnych.
