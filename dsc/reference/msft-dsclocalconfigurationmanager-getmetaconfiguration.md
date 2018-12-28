---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405275"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b8193-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b8193-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b8193-104">Pobiera lokalne ustawienia programu Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8193-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8193-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8193-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="b8193-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8193-106">Parameters</span></span>

<span data-ttu-id="b8193-107">*MetaConfiguration* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasę, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b8193-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8193-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b8193-108">Return value</span></span>

<span data-ttu-id="b8193-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b8193-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8193-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8193-110">Remarks</span></span>

<span data-ttu-id="b8193-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="b8193-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8193-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8193-112">Requirements</span></span>

<span data-ttu-id="b8193-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b8193-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b8193-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8193-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b8193-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8193-115">See also</span></span>

[<span data-ttu-id="b8193-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b8193-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)