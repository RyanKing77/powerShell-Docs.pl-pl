---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać profilów w środowisku Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405168"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="addde-103">Jak używać profilów w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="addde-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="addde-104">W tym temacie wyjaśniono, jak używać profilów w Windows PowerShell® zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="addde-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="addde-105">Zaleca się, że przed przystąpieniem do wykonywania zadań w tej sekcji, możesz przejrzeć [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), lub w okienku konsoli typu `Get-Help about_Profiles` i naciśnij klawisz **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="addde-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="addde-106">Profil jest skrypt programu Windows PowerShell ISE, który jest uruchamiany automatycznie po uruchomieniu nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="addde-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="addde-107">Można utworzyć co najmniej jeden profil programu Windows PowerShell dla programu Windows PowerShell ISE i ich używać do dodawania Konfigurowanie środowiska programu Windows PowerShell lub programu Windows PowerShell ISE przygotowania go do swojego użytku, za pomocą zmiennych, aliasy, funkcje i kolorów i czcionek Preferencje, które mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="addde-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="addde-108">Profil, który ma wpływ na każdą sesję środowiska Windows PowerShell ISE, rozpoczęcie.</span><span class="sxs-lookup"><span data-stu-id="addde-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="addde-109">Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i Załaduj profil.</span><span class="sxs-lookup"><span data-stu-id="addde-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="addde-110">Domyślne zasady wykonywania "Restricted" uniemożliwia wszystkie skrypty uruchamiania, w tym profile.</span><span class="sxs-lookup"><span data-stu-id="addde-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="addde-111">Jeśli używasz zasad "Restricted", nie można załadować profilu.</span><span class="sxs-lookup"><span data-stu-id="addde-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="addde-112">Aby uzyskać więcej informacji na temat zasad wykonywania, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="addde-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="addde-113">Wybieranie profilu do użycia w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="addde-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="addde-114">Windows PowerShell ISE obsługuje profile dla bieżącego użytkownika i dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="addde-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="addde-115">Obsługuje ona również Profile programu Windows PowerShell, które są stosowane do wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="addde-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="addde-116">Profil, którego używasz zależy od sposobu korzystania z programu Windows PowerShell i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="addde-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="addde-117">Jeśli używasz tylko Windows PowerShell ISE, aby uruchomić program Windows PowerShell, Zapisz wszystkie elementy w jeden z profilów specyficzne dla środowiska ISE, takich jak profilu CurrentUserCurrentHost w środowisku Windows PowerShell ISE lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="addde-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="addde-118">Jeśli używasz wielu programów hosta do uruchamiania środowiska Windows PowerShell, Zapisz funkcje, aliasy, zmienne i poleceń w profilu, który ma wpływ na wszystkie programy hosta, takie jak CurrentUserAllHosts lub AllUsersAllHosts, a następnie zapisz funkcjami specyficznymi dla środowiska ISE, takich jak kolory i czcionki dostosowania w profilu CurrentUserCurrentHost dla środowiska Windows PowerShell ISE profilu lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="addde-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="addde-119">Dostępne są następujące profile, które mogą być tworzone i używane w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="addde-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="addde-120">Każdy profil są zapisywane w jego własnej określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="addde-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="addde-121">Typ profilu</span><span class="sxs-lookup"><span data-stu-id="addde-121">Profile Type</span></span> | <span data-ttu-id="addde-122">Ścieżka profilu</span><span class="sxs-lookup"><span data-stu-id="addde-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="addde-123">**Bieżący użytkownik, program PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="addde-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="addde-124">`$PROFILE.CurrentUserCurrentHost`, lub `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="addde-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="addde-125">**Wszyscy użytkownicy, program PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="addde-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="addde-126">**Bieżący użytkownik, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="addde-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="addde-127">**Wszyscy użytkownicy, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="addde-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="addde-128">Aby utworzyć nowy profil</span><span class="sxs-lookup"><span data-stu-id="addde-128">To create a new profile</span></span>

<span data-ttu-id="addde-129">Aby utworzyć nowe "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="addde-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="addde-130">Aby utworzyć nowy "Wszyscy użytkownicy, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="addde-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="addde-131">Aby utworzyć nowy profil "bieżącego użytkownika, wszystkie hosty", uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="addde-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="addde-132">Aby utworzyć nowy profil "wszystkich użytkowników i wszystkie hosty", wpisz:</span><span class="sxs-lookup"><span data-stu-id="addde-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="addde-133">Aby dokonać edycji profilu</span><span class="sxs-lookup"><span data-stu-id="addde-133">To edit a profile</span></span>

1. <span data-ttu-id="addde-134">Aby otworzyć profil, należy uruchomić psedit polecenia ze zmienną, która określa profil, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="addde-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="addde-135">Na przykład, aby otworzyć "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, wpisz: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="addde-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="addde-136">Dodaj kilka elementów do Twojego profilu.</span><span class="sxs-lookup"><span data-stu-id="addde-136">Add some items to your profile.</span></span> <span data-ttu-id="addde-137">Poniżej przedstawiono kilka przykładów, które ułatwią Ci rozpoczęcie pracy:</span><span class="sxs-lookup"><span data-stu-id="addde-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="addde-138">Aby zmienić domyślny kolor tła w okienku konsoli na niebieski w typ pliku profilu: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="addde-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="addde-139">Aby uzyskać więcej informacji na temat zmiennej $psISE zobacz [dokumentacja modelu obiektów programu Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="addde-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="addde-140">Aby zmienić rozmiar czcionki do 20 plików typu profilu: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="addde-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="addde-141">Można zapisać w pliku profilu, **pliku** menu, kliknij przycisk **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="addde-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="addde-142">Gdy następnym razem otworzysz środowiska Windows PowerShell ISE dostosowania są stosowane.</span><span class="sxs-lookup"><span data-stu-id="addde-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="addde-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="addde-143">See Also</span></span>

- [<span data-ttu-id="addde-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="addde-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="addde-145">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="addde-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)