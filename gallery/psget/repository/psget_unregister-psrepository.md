---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Wyrejestrowuje repozytorium.

## <a name="description"></a>Opis

Polecenia cmdlet Unregister PSRepository wyrejestrowuje repozytorium dla bieżącego użytkownika.
- Wyrejestrowanie ponowna rejestracja repozytorium PSGallery jest dozwolony dla przedsiębiorstwa i odłączone scenariuszy.
- Użytkownicy mogą ponownie zarejestrować PSGallery po prostu uruchamiając `Register-PSRepository -Default`
- Ponieważ PSGallery jest domyślnie Publikuj repozytorium w poleceniach cmdlet Publish-Module i opublikuj skryptu, jeśli nie jest dostępny na liście zarejestrowanych repozytorium PSGallery zostanie zgłoszony błąd.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Przykładowe polecenia

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Wyrejestrowanie ponowna rejestracja repozytorium PSGallery jest dozwolony dla przedsiębiorstwa i odłączone scenariuszy.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```