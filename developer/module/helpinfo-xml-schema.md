---
title: Schemat HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851233"
---
# <a name="helpinfo-xml-schema"></a>Schemat XML HelpInfo

Ten temat zawiera schemat XML dla plików można aktualizować informacje pomocy, powszechnie znane jako "HelpInfo XML files".

## <a name="helpinfo-xml-schema"></a>Schemat XML HelpInfo

Pliki HelpInfo XML opierają się na następujących schematu XML.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>Elementy HelpInfo XML

Plik HelpInfo XML obejmuje następujące elementy.

HelpContentURI zawiera identyfikator URI lokalizacji pomocy pliki CAB dla modułu. Identyfikator URI musi zaczynać się od "http" lub "https". Identyfikator URI powinien określać lokalizacji internetowej, ale nie mogą zawierać nazwę pliku CAB. **HelpContentURI** wartość może być taki sam lub inny niż **HelpInfoURI** wartości.

Reprezentuje SupportedUICultures pomoc modułu pliki we wszystkich kulturach interfejsu użytkownika. Zawiera **UICulture** elementów, z których każdy reprezentuje zestaw plików pomocy dla modułu w określonej kultury interfejsu użytkownika.

Reprezentuje UICulture zbiór plików pomocy dla modułu w określonej kultury interfejsu użytkownika. Dodaj **UICulture** elementu każda kultura interfejsu użytkownika, w którym zapisywane są pliki pomocy.

UICultureName zawiera kod języka dla kultury interfejsu użytkownika, w którym zapisywane są pliki pomocy.

UICultureVersion zawiera numer wersji 4 część w "N1. N2. N3. N4 "formatu, który reprezentuje wersję pliku pomocy pliku CAB w kultura interfejsu użytkownika. Zwiększ numer wersji, zawsze wtedy, gdy przekażesz nowe pomocy pliki CAB w kultura interfejsu użytkownika, który jest określony przez **UICultureName**. Aby uzyskać więcej informacji na temat tej wartości zobacz "Wersji Class (System)" w bibliotece MSDN.