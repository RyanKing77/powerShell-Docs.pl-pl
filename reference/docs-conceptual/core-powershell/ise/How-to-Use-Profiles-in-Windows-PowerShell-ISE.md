---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać profilów w środowisku Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 8789d6283457f790fdea27657abb2612304e10a1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951226"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="eb317-103">Jak używać profilów w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eb317-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="eb317-104">W tym temacie wyjaśniono, jak używać profili w Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="eb317-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="eb317-105">Firma Microsoft zaleca się przed wykonaniem zadań w tej sekcji, przejrzenie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), lub w okienku konsoli typu `Get-Help about_Profiles` i naciśnij klawisz **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="eb317-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="eb317-106">Profil jest skrypt programu Windows PowerShell ISE, który jest uruchamiany automatycznie podczas uruchamiania nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="eb317-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="eb317-107">Można utworzyć co najmniej jeden profil programu Windows PowerShell dla programu Windows PowerShell ISE i używać ich do dodawania konfiguracji środowiska Windows PowerShell lub programu Windows PowerShell ISE przygotowania go do użycia, zmienne, aliasy, funkcje i kolorów i czcionek Preferencje, które mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="eb317-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="eb317-108">Profil ma wpływ na każdej sesji programu Windows PowerShell ISE, który można uruchomić.</span><span class="sxs-lookup"><span data-stu-id="eb317-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="eb317-109">Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i ładowanie profilu.</span><span class="sxs-lookup"><span data-stu-id="eb317-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="eb317-110">Domyślne zasady wykonywania "Restricted" uniemożliwia wszystkie skrypty uruchomiona, w tym profili.</span><span class="sxs-lookup"><span data-stu-id="eb317-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="eb317-111">Jeśli używasz zasad "Restricted", nie można załadować profilu.</span><span class="sxs-lookup"><span data-stu-id="eb317-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="eb317-112">Aby uzyskać więcej informacji na temat zasad wykonywania, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="eb317-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="eb317-113">Wybieranie profilu do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eb317-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="eb317-114">Windows PowerShell ISE obsługuje profile dla bieżącego użytkownika i dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="eb317-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="eb317-115">Obsługuje ona również Profile programu Windows PowerShell, które są stosowane do wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="eb317-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="eb317-116">Profil, którego używasz, jest określana przez sposobie korzystania z programu Windows PowerShell i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eb317-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="eb317-117">Jeśli używasz tylko programu Windows PowerShell ISE uruchamianie środowiska Windows PowerShell, Zapisz wszystkie elementy w jeden z profilów specyficzne dla platformy ISE, takich jak profilu CurrentUserCurrentHost dla programu Windows PowerShell ISE lub AllUsersCurrentHost dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eb317-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="eb317-118">Użycie wielu hostowanie programów do uruchomienia programu Windows PowerShell, Zapisz funkcje, aliasy, zmienne i polecenia w profilu, który ma wpływ na wszystkie programy hosta, takich jak CurrentUserAllHosts lub AllUsersAllHosts i zapisać funkcji specyficznych dla platformy ISE, takich jak kolorów i czcionek dostosowania w profilu CurrentUserCurrentHost dla programu Windows PowerShell ISE profilu lub AllUsersCurrentHost dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eb317-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="eb317-119">Poniżej przedstawiono profilów, które mogą być tworzone i używane w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eb317-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="eb317-120">Każdy profil jest zapisywany w jego własnej określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="eb317-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="eb317-121">Typ profilu</span><span class="sxs-lookup"><span data-stu-id="eb317-121">Profile Type</span></span> | <span data-ttu-id="eb317-122">Ścieżka profilu</span><span class="sxs-lookup"><span data-stu-id="eb317-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="eb317-123">**Bieżący użytkownik, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="eb317-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="eb317-124">`$PROFILE.CurrentUserCurrentHost`, lub `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="eb317-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="eb317-125">**Wszyscy użytkownicy, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="eb317-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="eb317-126">**Bieżący użytkownik, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="eb317-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="eb317-127">**Wszyscy użytkownicy, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="eb317-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="eb317-128">Aby utworzyć nowy profil</span><span class="sxs-lookup"><span data-stu-id="eb317-128">To create a new profile</span></span>

<span data-ttu-id="eb317-129">Aby utworzyć nowe "bieżącego użytkownika, programu Windows PowerShell ISE" profil, uruchom to polecenie:</span><span class="sxs-lookup"><span data-stu-id="eb317-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="eb317-130">Aby utworzyć nową "Wszyscy użytkownicy, programu Windows PowerShell ISE" profil, uruchom to polecenie:</span><span class="sxs-lookup"><span data-stu-id="eb317-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="eb317-131">Aby utworzyć nowy profil "bieżącego użytkownika, wszystkie hosty", uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="eb317-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="eb317-132">Aby utworzyć nowy profil "wszyscy użytkownicy, wszystkie hosty", wpisz:</span><span class="sxs-lookup"><span data-stu-id="eb317-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="eb317-133">Aby edytować profilu</span><span class="sxs-lookup"><span data-stu-id="eb317-133">To edit a profile</span></span>

1. <span data-ttu-id="eb317-134">Aby otworzyć profilu, uruchom psedit polecenia ze zmienną, która określa profil, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="eb317-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="eb317-135">Na przykład, aby otworzyć "bieżącego użytkownika, programu Windows PowerShell ISE" profilu, wpisz: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="eb317-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="eb317-136">Niektóre elementy należy dodać do profilu.</span><span class="sxs-lookup"><span data-stu-id="eb317-136">Add some items to your profile.</span></span> <span data-ttu-id="eb317-137">Poniżej przedstawiono kilka przykładów ułatwiających rozpoczęcie pracy:</span><span class="sxs-lookup"><span data-stu-id="eb317-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="eb317-138">Aby zmienić domyślny kolor tła okienka konsoli na niebieski w typ pliku profilu: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="eb317-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="eb317-139">Aby uzyskać więcej informacji na temat zmiennej $psISE, zobacz [odwołanie modelu obiektu Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="eb317-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="eb317-140">Aby zmienić rozmiar czcionki do 20 w profilu typ pliku: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="eb317-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="eb317-141">Aby zapisać plik profilu na **pliku** menu, kliknij przycisk **zapisać**.</span><span class="sxs-lookup"><span data-stu-id="eb317-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="eb317-142">Następnym otwarciu programu Windows PowerShell ISE dostosowania są stosowane.</span><span class="sxs-lookup"><span data-stu-id="eb317-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb317-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb317-143">See Also</span></span>

- [<span data-ttu-id="eb317-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="eb317-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="eb317-145">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eb317-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)