---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxSshAuthorizedKeys
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687804"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="96c6d-103">DSC dla systemu Linux zasób nxSshAuthorizedKeys</span><span class="sxs-lookup"><span data-stu-id="96c6d-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="96c6d-104">**NxAuthorizedKeys** zasobów w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania autoryzacji ssh klucze dla określonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96c6d-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="96c6d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="96c6d-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="96c6d-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="96c6d-106">Properties</span></span>

|  <span data-ttu-id="96c6d-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="96c6d-107">Property</span></span> |  <span data-ttu-id="96c6d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="96c6d-108">Description</span></span> |
|---|---|
| <span data-ttu-id="96c6d-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="96c6d-109">KeyComment</span></span>| <span data-ttu-id="96c6d-110">Komentarz Unikatowy klucz.</span><span class="sxs-lookup"><span data-stu-id="96c6d-110">A unique comment for the key.</span></span> <span data-ttu-id="96c6d-111">Służy do jednoznacznego identyfikowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="96c6d-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="96c6d-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="96c6d-112">Ensure</span></span>| <span data-ttu-id="96c6d-113">Określa, czy klucz jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="96c6d-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="96c6d-114">Ustaw tę właściwość na "Brak", aby upewnić się, że klucz nie istnieje w pliku autoryzowanych kluczy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96c6d-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="96c6d-115">Ustaw ją na "Obecny", aby upewnić się, że klucz jest zdefiniowana w pliku autoryzowanych kluczy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96c6d-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="96c6d-116">Nazwa użytkownika</span><span class="sxs-lookup"><span data-stu-id="96c6d-116">Username</span></span>| <span data-ttu-id="96c6d-117">Nazwa użytkownika do zarządzania ssh autoryzacji kluczy.</span><span class="sxs-lookup"><span data-stu-id="96c6d-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="96c6d-118">Jeśli nie zdefiniowana, użytkownik domyślny jest "root".</span><span class="sxs-lookup"><span data-stu-id="96c6d-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="96c6d-119">Klawisz</span><span class="sxs-lookup"><span data-stu-id="96c6d-119">Key</span></span>| <span data-ttu-id="96c6d-120">Zawartość klucza.</span><span class="sxs-lookup"><span data-stu-id="96c6d-120">The contents of the key.</span></span> <span data-ttu-id="96c6d-121">Jest to wymagane, jeśli **upewnij się, że** jest ustawiona na "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="96c6d-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="96c6d-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="96c6d-122">DependsOn</span></span> | <span data-ttu-id="96c6d-123">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="96c6d-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="96c6d-124">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="96c6d-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="96c6d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="96c6d-125">Example</span></span>

<span data-ttu-id="96c6d-126">W poniższym przykładzie zdefiniowano publiczny autoryzacji ssh klucza dla użytkownika "monuser".</span><span class="sxs-lookup"><span data-stu-id="96c6d-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```