---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: d19f3c47af858eb18a39847050f80ffa013c59bb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="mof-documents-are-encrypted-by-default"></a>Domyślnie są szyfrowane MOF dokumentów

Konfiguracja dokumenty zawierają poufne informacje. W poprzednich wersjach usługi Konfiguracja DSC były wymagane do rozpowszechniania certyfikatów i zarządzania nimi Aby zabezpieczyć poświadczenia w ramach konfiguracji. Dla wielu to zarządzanie znaczne obciążenie i nawet w przypadku wszystkich prac zajęło w tym, które nadal pozostawiono niektóre informacje konfiguracji, które nie były i nie może być zabezpieczone. 

Nie jest już przypadku ponieważ **cała konfiguracja za są domyślnie zabezpieczone**. Niezbędne są nie certyfikatów lub ustawienia konfiguracji meta. Wtedy konfiguracji MOF jest zapisywany na dysku przez lokalnego Menedżera konfiguracji (LCM) w docelowym węźle, są szyfrowane. Za są szyfrowane za pomocą [DPAPI](https://msdn.microsoft.com/en-us/library/ms995355.aspx). **Uwaga:** za generowane przez skrypt konfiguracji nie są szyfrowane.

**Przykład:** szyfrowania w trybie push ![szyfrowania MOF](../images/MOF_Encryption.jpg)

Jeśli korzystasz już z metody certyfikatu do szyfrowania haseł lub jeśli potrzebne są dodatkowe zabezpieczenia dla hasła, [istniejącą metodę szyfrowania opartego na certyfikatach](https://msdn.microsoft.com/en-us/powershell/dsc/securemof) będą nadal działać. Wynik zostanie dokument MOF, który jest w pełni szyfrowane przy użyciu DPAPIs i mieć Ponadto hasła szyfrowane w niej.

Szyfrowanie dotyczy tylko dokumentów MOF konfiguracji (pending.mof, current.mof, previous.mof i częściowe za). Meta konfiguracji za nadal są zapisywane w postaci zwykłego tekstu, ponieważ zawierają one mniej prawdopodobne kluczy tajnych.

