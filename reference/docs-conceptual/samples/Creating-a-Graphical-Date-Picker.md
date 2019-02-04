---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie graficznego obiektu wyboru daty
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686502"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="77896-103">Tworzenie graficznego obiektu wyboru daty</span><span class="sxs-lookup"><span data-stu-id="77896-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="77896-104">Użyj programu Windows PowerShell 3.0 i nowszych wersjach, aby utworzyć formularza z formantem Styl kalendarza graficzny, pozwala użytkownikom na wybór dnia miesiąca.</span><span class="sxs-lookup"><span data-stu-id="77896-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="77896-105">Utwórz formant graficzny wyboru daty</span><span class="sxs-lookup"><span data-stu-id="77896-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="77896-106">Skopiuj i następnie wklej poniższą zawartość do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="77896-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="77896-107">Skrypt rozpoczyna się od ładowania dwóch klas .NET Framework: **System.Drawing** i **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="77896-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="77896-108">Następnie uruchom nowe wystąpienie klasy .NET Framework **Windows.Forms.Form**; zapewniający pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="77896-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="77896-109">Po utworzeniu wystąpienia klasy formularza, należy przypisać wartości do trzech właściwości tej klasy.</span><span class="sxs-lookup"><span data-stu-id="77896-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="77896-110">**Tekst.**</span><span class="sxs-lookup"><span data-stu-id="77896-110">**Text.**</span></span> <span data-ttu-id="77896-111">Staje się on tytuł okna.</span><span class="sxs-lookup"><span data-stu-id="77896-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="77896-112">**Rozmiar.**</span><span class="sxs-lookup"><span data-stu-id="77896-112">**Size.**</span></span> <span data-ttu-id="77896-113">Jest to rozmiar formularza, w pikselach.</span><span class="sxs-lookup"><span data-stu-id="77896-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="77896-114">Powyższy skrypt tworzy formularz, który jest 243 pikseli szerokości i wysokości 230 pikseli.</span><span class="sxs-lookup"><span data-stu-id="77896-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="77896-115">**Pozycjapoczątkowa.**</span><span class="sxs-lookup"><span data-stu-id="77896-115">**StartingPosition.**</span></span> <span data-ttu-id="77896-116">Tej opcjonalnej właściwości jest równa **CenterScreen** w poprzednim skrypcie.</span><span class="sxs-lookup"><span data-stu-id="77896-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="77896-117">Jeśli nie dodasz tę właściwość, Windows wybiera lokalizację, gdy formularz jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="77896-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="77896-118">Ustawiając **Pozycjapoczątkowa** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu każdorazowo ładuje.</span><span class="sxs-lookup"><span data-stu-id="77896-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="77896-119">Następnie utwórz, a następnie dodaj formant kalendarza w formularzu.</span><span class="sxs-lookup"><span data-stu-id="77896-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="77896-120">W tym przykładzie bieżący dzień jest wyróżniony lub nie kółku.</span><span class="sxs-lookup"><span data-stu-id="77896-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="77896-121">Użytkownicy mogą wybrać naraz tylko jeden dzień w kalendarzu.</span><span class="sxs-lookup"><span data-stu-id="77896-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="77896-122">Następnie należy utworzyć **OK** przycisk dla formularza użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77896-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="77896-123">Określ rozmiar i zachowanie **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="77896-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="77896-124">W tym przykładzie położenie przycisku jest 165 pikseli od górnej krawędzi formularza i 38 pikseli od lewej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="77896-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="77896-125">Wysokość przycisku jest 23 pikseli, podczas gdy długość przycisk wynosi 75 pikseli.</span><span class="sxs-lookup"><span data-stu-id="77896-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="77896-126">Skrypt używa wstępnie zdefiniowanych typów Windows Forms do określenia zachowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="77896-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="77896-127">Podobnie można utworzyć **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="77896-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="77896-128">**Anulować** znajduje się przycisk 165 pikseli od górnej, ale 113 pikseli od lewej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="77896-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="77896-129">Ustaw **Topmost** właściwości **$true** wymusić okna, aby otworzyć na jego podstawie innych okien i okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="77896-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="77896-130">Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.</span><span class="sxs-lookup"><span data-stu-id="77896-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="77896-131">Na koniec kod wewnątrz **Jeśli** bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników, wybierz dzień w kalendarzu, a następnie kliknij przycisk **OK** przycisk lub naciśnij klawisz **Enter** klucz.</span><span class="sxs-lookup"><span data-stu-id="77896-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="77896-132">Program Windows PowerShell Wyświetla wybraną datą dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="77896-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="77896-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77896-133">See Also</span></span>

- [<span data-ttu-id="77896-134">Witaj twórco skryptów:  Dlaczego nie działają te przykłady programu PowerShell graficznego interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="77896-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="77896-135">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="77896-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="77896-136">Windows PowerShell porada tygodnia:  Tworzenie graficznego obiektu wyboru daty</span><span class="sxs-lookup"><span data-stu-id="77896-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)