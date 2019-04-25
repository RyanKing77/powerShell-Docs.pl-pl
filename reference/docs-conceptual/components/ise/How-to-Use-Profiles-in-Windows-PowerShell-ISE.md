---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać profilów w środowisku Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057540"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="4a507-103">Jak używać profilów w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4a507-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="4a507-104">W tym temacie wyjaśniono, jak używać profilów w Windows PowerShell® zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="4a507-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="4a507-105">Zaleca się, że przed przystąpieniem do wykonywania zadań w tej sekcji, możesz przejrzeć [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), lub w okienku konsoli typu `Get-Help about_Profiles` i naciśnij klawisz **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="4a507-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="4a507-106">Profil jest skrypt programu Windows PowerShell ISE, który jest uruchamiany automatycznie po uruchomieniu nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="4a507-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="4a507-107">Można utworzyć co najmniej jeden profil programu Windows PowerShell dla programu Windows PowerShell ISE i ich używać do dodawania Konfigurowanie środowiska programu Windows PowerShell lub programu Windows PowerShell ISE przygotowania go do swojego użytku, za pomocą zmiennych, aliasy, funkcje i kolorów i czcionek Preferencje, które mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="4a507-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="4a507-108">Profil, który ma wpływ na każdą sesję środowiska Windows PowerShell ISE, rozpoczęcie.</span><span class="sxs-lookup"><span data-stu-id="4a507-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="4a507-109">Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i Załaduj profil.</span><span class="sxs-lookup"><span data-stu-id="4a507-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="4a507-110">Domyślne zasady wykonywania "Restricted" uniemożliwia wszystkie skrypty uruchamiania, w tym profile.</span><span class="sxs-lookup"><span data-stu-id="4a507-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="4a507-111">Jeśli używasz zasad "Restricted", nie można załadować profilu.</span><span class="sxs-lookup"><span data-stu-id="4a507-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="4a507-112">Aby uzyskać więcej informacji na temat zasad wykonywania, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="4a507-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="4a507-113">Wybieranie profilu do użycia w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4a507-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="4a507-114">Windows PowerShell ISE obsługuje profile dla bieżącego użytkownika i dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4a507-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="4a507-115">Obsługuje ona również Profile programu Windows PowerShell, które są stosowane do wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="4a507-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="4a507-116">Profil, którego używasz zależy od sposobu korzystania z programu Windows PowerShell i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4a507-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="4a507-117">Jeśli używasz tylko Windows PowerShell ISE, aby uruchomić program Windows PowerShell, Zapisz wszystkie elementy w jeden z profilów specyficzne dla środowiska ISE, takich jak profilu CurrentUserCurrentHost w środowisku Windows PowerShell ISE lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4a507-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="4a507-118">Jeśli używasz wielu programów hosta do uruchamiania środowiska Windows PowerShell, Zapisz funkcje, aliasy, zmienne i poleceń w profilu, który ma wpływ na wszystkie programy hosta, takie jak CurrentUserAllHosts lub AllUsersAllHosts, a następnie zapisz funkcjami specyficznymi dla środowiska ISE, takich jak kolory i czcionki dostosowania w profilu CurrentUserCurrentHost dla środowiska Windows PowerShell ISE profilu lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4a507-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="4a507-119">Dostępne są następujące profile, które mogą być tworzone i używane w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4a507-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="4a507-120">Każdy profil są zapisywane w jego własnej określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4a507-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="4a507-121">Typ profilu</span><span class="sxs-lookup"><span data-stu-id="4a507-121">Profile Type</span></span> | <span data-ttu-id="4a507-122">Ścieżka profilu</span><span class="sxs-lookup"><span data-stu-id="4a507-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="4a507-123">**Bieżący użytkownik, program PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="4a507-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="4a507-124">`$PROFILE.CurrentUserCurrentHost`, lub `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="4a507-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="4a507-125">**Wszyscy użytkownicy, program PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="4a507-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="4a507-126">**Bieżący użytkownik, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="4a507-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="4a507-127">**Wszyscy użytkownicy, wszystkie hosty**</span><span class="sxs-lookup"><span data-stu-id="4a507-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="4a507-128">Aby utworzyć nowy profil</span><span class="sxs-lookup"><span data-stu-id="4a507-128">To create a new profile</span></span>

<span data-ttu-id="4a507-129">Aby utworzyć nowe "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4a507-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="4a507-130">Aby utworzyć nowy "Wszyscy użytkownicy, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4a507-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="4a507-131">Aby utworzyć nowy profil "bieżącego użytkownika, wszystkie hosty", uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4a507-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="4a507-132">Aby utworzyć nowy profil "wszystkich użytkowników i wszystkie hosty", wpisz:</span><span class="sxs-lookup"><span data-stu-id="4a507-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="4a507-133">Aby dokonać edycji profilu</span><span class="sxs-lookup"><span data-stu-id="4a507-133">To edit a profile</span></span>

1. <span data-ttu-id="4a507-134">Aby otworzyć profil, należy uruchomić psedit polecenia ze zmienną, która określa profil, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="4a507-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="4a507-135">Na przykład, aby otworzyć "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, wpisz: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="4a507-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="4a507-136">Dodaj kilka elementów do Twojego profilu.</span><span class="sxs-lookup"><span data-stu-id="4a507-136">Add some items to your profile.</span></span> <span data-ttu-id="4a507-137">Poniżej przedstawiono kilka przykładów, które ułatwią Ci rozpoczęcie pracy:</span><span class="sxs-lookup"><span data-stu-id="4a507-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="4a507-138">Aby zmienić domyślny kolor tła w okienku konsoli na niebieski w typ pliku profilu: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="4a507-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="4a507-139">Aby uzyskać więcej informacji na temat zmiennej $psISE zobacz [dokumentacja modelu obiektów programu Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="4a507-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="4a507-140">Aby zmienić rozmiar czcionki do 20 plików typu profilu: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="4a507-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="4a507-141">Można zapisać w pliku profilu, **pliku** menu, kliknij przycisk **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="4a507-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="4a507-142">Gdy następnym razem otworzysz środowiska Windows PowerShell ISE dostosowania są stosowane.</span><span class="sxs-lookup"><span data-stu-id="4a507-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a507-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a507-143">See Also</span></span>

- [<span data-ttu-id="4a507-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="4a507-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="4a507-145">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4a507-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)