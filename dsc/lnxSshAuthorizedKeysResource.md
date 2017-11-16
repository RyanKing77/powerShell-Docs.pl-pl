---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxSshAuthorizedKeys zasobów"
ms.openlocfilehash: 3c145eeb86d971dc00e1c7cea60fb50c83d7b9a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="cc8c1-103">DSC dla systemu Linux nxSshAuthorizedKeys zasobów</span><span class="sxs-lookup"><span data-stu-id="cc8c1-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="cc8c1-104">**NxAuthorizedKeys** zasobów w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania autoryzowany ssh kluczy dla określonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc8c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc8c1-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="cc8c1-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cc8c1-106">Properties</span></span>

|  <span data-ttu-id="cc8c1-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc8c1-107">Property</span></span> |  <span data-ttu-id="cc8c1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cc8c1-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="cc8c1-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="cc8c1-109">KeyComment</span></span>| <span data-ttu-id="cc8c1-110">Komentarz Unikatowy klucz.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-110">A unique comment for the key.</span></span> <span data-ttu-id="cc8c1-111">To jest używany do jednoznacznego identyfikowania kluczy.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="cc8c1-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="cc8c1-112">Ensure</span></span>| <span data-ttu-id="cc8c1-113">Określa, czy klucz jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="cc8c1-114">Ustaw tę właściwość na "Brak", aby upewnić się, że klucz nie istnieje w pliku kluczy autoryzowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="cc8c1-115">Ustaw ją na "Brak", aby upewnić się, że klucz jest zdefiniowana w pliku klucza autoryzowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="cc8c1-116">Nazwa użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc8c1-116">Username</span></span>| <span data-ttu-id="cc8c1-117">Nazwa użytkownika do zarządzania ssh uprawnień klucze.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="cc8c1-118">Jeśli nie jest zdefiniowany, użytkownik domyślną jest "root".</span><span class="sxs-lookup"><span data-stu-id="cc8c1-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="cc8c1-119">Klawisz</span><span class="sxs-lookup"><span data-stu-id="cc8c1-119">Key</span></span>| <span data-ttu-id="cc8c1-120">Zawartość klucza.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-120">The contents of the key.</span></span> <span data-ttu-id="cc8c1-121">Jest to wymagane, jeśli **upewnij się, że** ma ustawioną wartość "Brak".</span><span class="sxs-lookup"><span data-stu-id="cc8c1-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="cc8c1-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="cc8c1-122">DependsOn</span></span> | <span data-ttu-id="cc8c1-123">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cc8c1-124">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="cc8c1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc8c1-125">Example</span></span>

<span data-ttu-id="cc8c1-126">W poniższym przykładzie zdefiniowano autoryzowany ssh publicznego klucza dla użytkownika "monuser".</span><span class="sxs-lookup"><span data-stu-id="cc8c1-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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

