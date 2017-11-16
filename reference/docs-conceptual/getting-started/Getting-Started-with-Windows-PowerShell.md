---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Wprowadzenie do korzystania z programu Windows PowerShell
ms.assetid: b0e2ad92-875f-421d-b612-f624e644aa69
ms.openlocfilehash: 93a4d4a6bc0ebef6b6af7f7f8af59dec865bcfa3
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="getting-started-with-windows-powershell"></a><span data-ttu-id="d2c8e-103">Wprowadzenie do korzystania z programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2c8e-103">Getting Started with Windows PowerShell</span></span>
<span data-ttu-id="d2c8e-104">Program Windows PowerShell jest powłoką wiersza polecenia systemu Windows, przeznaczonym zwłaszcza do administratorów systemu.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-104">Windows PowerShell is a Windows command-line shell designed especially for system administrators.</span></span> <span data-ttu-id="d2c8e-105">Program Windows PowerShell zawiera monitu interakcyjnego i środowisko obsługi skryptów, który może służyć niezależnie lub razem.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-105">Windows PowerShell includes an interactive prompt and a scripting environment that can be used independently or in combination.</span></span>

<span data-ttu-id="d2c8e-106">W przeciwieństwie do większości powłoki, które akceptują i zwracają tekst, programu Windows PowerShell jest oparty na .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) i .NET Framework, akceptuje i zwraca obiekty .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-106">Unlike most shells, which accept and return text, Windows PowerShell is built on top of the .NET Framework common language runtime (CLR) and the .NET Framework, and accepts and returns .NET Framework objects.</span></span> <span data-ttu-id="d2c8e-107">Ta zmiana podstawowe w środowisku wprowadzono całkowicie nowe narzędzia i metod do zarządzania i konfiguracji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-107">This fundamental change in the environment brings entirely new tools and methods to the management and configuration of Windows.</span></span>

<span data-ttu-id="d2c8e-108">Środowisko Windows PowerShell pojęcia związane z polecenia cmdlet (Wymowa "polecenie let"), prosty, jedną funkcję narzędzie wiersza polecenia wbudowanych w powłoce.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-108">Windows PowerShell introduces the concept of a cmdlet (pronounced "command-let"), a simple, single-function command-line tool built into the shell.</span></span> <span data-ttu-id="d2c8e-109">Każde polecenie cmdlet można używać osobno, ale ich zasilania jest zrealizowane, korzystając z tych narzędzi proste w połączeniu Aby wykonać złożone zadania.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-109">You can use each cmdlet separately, but their power is realized when you use these simple tools in combination to perform complex tasks.</span></span> <span data-ttu-id="d2c8e-110">Program Windows PowerShell zawiera ponad sto podstawowe podstawowych poleceń cmdlet środowiska i możesz zapisać własnego polecenia cmdlet i udostępniać innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-110">Windows PowerShell includes more than one hundred basic core cmdlets, and you can write your own cmdlets and share them with other users.</span></span>

<span data-ttu-id="d2c8e-111">Jak wiele powłoki programu Windows PowerShell umożliwia dostęp do systemu plików na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-111">Like many shells, Windows PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="d2c8e-112">Ponadto w programie Windows PowerShell *dostawców* umożliwiają dostęp do innych magazynów danych, takich jak rejestr i magazyny certyfikatów podpisu cyfrowego, łatwo dostęp do systemu plików.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-112">In addition, Windows PowerShell *providers* enable you to access other data stores, such as the registry and the digital signature certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="d2c8e-113">Ten Przewodnik wprowadzający zawiera wprowadzenie do programu Windows PowerShell: język, poleceń cmdlet, dostawców i obiektów.</span><span class="sxs-lookup"><span data-stu-id="d2c8e-113">This Getting Started guide provides an introduction to Windows PowerShell: the language, the cmdlets, the providers, and the use of objects.</span></span>

<span data-ttu-id="d2c8e-114">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="d2c8e-114">In this topic:</span></span>

- [<span data-ttu-id="d2c8e-115">Wymagania systemowe programu PowerShell systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d2c8e-115">Windows PowerShell System Requirements</span></span>](../setup/Windows-PowerShell-System-Requirements.md)

- [<span data-ttu-id="d2c8e-116">Instalowanie programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2c8e-116">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)

- [<span data-ttu-id="d2c8e-117">Uruchamianie środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2c8e-117">Starting Windows PowerShell</span></span>](../setup/Starting-Windows-PowerShell.md)

- [<span data-ttu-id="d2c8e-118">Przygotowania do użycia środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2c8e-118">Getting Ready to Use Windows PowerShell</span></span>](Getting-Ready-to-Use-Windows-PowerShell.md)

