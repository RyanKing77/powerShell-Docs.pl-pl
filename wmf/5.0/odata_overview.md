---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9849feb01cd7be41703bdd1e8cb2c5a86cccff52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685781"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>Generowanie poleceń cmdlet programu PowerShell w oparciu o punkt końcowy OData
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Generowanie poleceń cmdlet programu Windows PowerShell, oparte na punkt końcowy OData
--------------------------------------------------------------

**Export-ODataEndpointProxy** to polecenie cmdlet, które generuje zestaw poleceń cmdlet programu Windows PowerShell, w oparciu o funkcje udostępniane przez dany punkt końcowy OData.

Poniższy przykład pokazuje, jak to nowe polecenie cmdlet:

\# Przypadek użycia podstawowego ODataEndpointProxy eksportu

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

Nadal istnieją części przypadki użycia klucza w rozwoju dla tej funkcji, w tym między innymi:
-   Skojarzenia
-   Przekazywanie strumieni

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generowanie poleceń cmdlet programu Windows PowerShell, oparte na punkt końcowy OData z ODataUtils
------------------------------------------------------------------------------
Moduł ODataUtils umożliwia generowanie poleceń cmdlet programu Windows PowerShell z punkty końcowe REST, które obsługują OData. Następujące ulepszenia przyrostowe znajdują się w module Microsoft.PowerShell.ODataUtils Windows PowerShell.
-   Kanał dodatkowe informacje z punktu końcowego po stronie serwera po stronie klienta.
-   Obsługa stronicowania po stronie klienta
-   Filtrowanie po stronie serwera, za pomocą wybierz parametr -
-   Obsługa nagłówków żądań sieci web

Polecenia cmdlet serwera proxy generowany przez polecenie cmdlet Export-ODataEndPointProxy zawierają dodatkowe informacje (niewymienione w $metadata używane podczas generowania serwera proxy po stronie klienta) z serwera punktu końcowego OData po stronie w usłudze stream informacji (nowe Windows Funkcja w środowisku PowerShell 5.0). Poniżej przedstawiono przykładowy sposób uzyskać te informacje.
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

Rekordy można uzyskać po stronie serwera w partiach, za pomocą obsługę stronicowania po stronie klienta. Jest to przydatne, jeśli musi pobrać dużą ilość danych z serwera za pośrednictwem sieci.
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

Polecenia cmdlet wygenerowany serwer proxy obsługuje wybierz parametr, który służy jako filtr do odbierania właściwości rekordu, które klient musi. Zmniejsza to ilość danych transferowanych za pośrednictwem sieci, ponieważ filtrowanie odbywa się po stronie serwera.
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Polecenie cmdlet Export-ODataEndpointProxy i polecenia cmdlet serwera proxy, generowane przez nią, obsługują teraz parametru nagłówki (podaj wartości jako tabelę mieszania), który służy do kanału wszelkie dodatkowe informacje, który jest oczekiwany przez punkt końcowy OData po stronie serwera. W poniższym przykładzie można kanału klucz subskrypcji przy użyciu nagłówków dla usług, które są oczekiwane klucz subskrypcji na potrzeby uwierzytelniania.
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
