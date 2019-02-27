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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="cee99-102">Schemat XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="cee99-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="cee99-103">Ten temat zawiera schemat XML dla plików można aktualizować informacje pomocy, powszechnie znane jako "HelpInfo XML files".</span><span class="sxs-lookup"><span data-stu-id="cee99-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="cee99-104">Schemat XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="cee99-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="cee99-105">Pliki HelpInfo XML opierają się na następujących schematu XML.</span><span class="sxs-lookup"><span data-stu-id="cee99-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="cee99-106">Elementy HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="cee99-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="cee99-107">Plik HelpInfo XML obejmuje następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="cee99-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="cee99-108">HelpContentURI zawiera identyfikator URI lokalizacji pomocy pliki CAB dla modułu.</span><span class="sxs-lookup"><span data-stu-id="cee99-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="cee99-109">Identyfikator URI musi zaczynać się od "http" lub "https".</span><span class="sxs-lookup"><span data-stu-id="cee99-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="cee99-110">Identyfikator URI powinien określać lokalizacji internetowej, ale nie mogą zawierać nazwę pliku CAB.</span><span class="sxs-lookup"><span data-stu-id="cee99-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="cee99-111">**HelpContentURI** wartość może być taki sam lub inny niż **HelpInfoURI** wartości.</span><span class="sxs-lookup"><span data-stu-id="cee99-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="cee99-112">Reprezentuje SupportedUICultures pomoc modułu pliki we wszystkich kulturach interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cee99-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="cee99-113">Zawiera **UICulture** elementów, z których każdy reprezentuje zestaw plików pomocy dla modułu w określonej kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cee99-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="cee99-114">Reprezentuje UICulture zbiór plików pomocy dla modułu w określonej kultury interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cee99-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="cee99-115">Dodaj **UICulture** elementu każda kultura interfejsu użytkownika, w którym zapisywane są pliki pomocy.</span><span class="sxs-lookup"><span data-stu-id="cee99-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="cee99-116">UICultureName zawiera kod języka dla kultury interfejsu użytkownika, w którym zapisywane są pliki pomocy.</span><span class="sxs-lookup"><span data-stu-id="cee99-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="cee99-117">UICultureVersion zawiera numer wersji 4 część w "N1. N2. N3. N4 "formatu, który reprezentuje wersję pliku pomocy pliku CAB w kultura interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cee99-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="cee99-118">Zwiększ numer wersji, zawsze wtedy, gdy przekażesz nowe pomocy pliki CAB w kultura interfejsu użytkownika, który jest określony przez **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="cee99-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="cee99-119">Aby uzyskać więcej informacji na temat tej wartości zobacz "Wersji Class (System)" w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="cee99-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>