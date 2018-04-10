---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie graficznego obiektu wyboru daty
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="f05b6-103">Tworzenie graficznego obiektu wyboru daty</span><span class="sxs-lookup"><span data-stu-id="f05b6-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="f05b6-104">Umożliwia tworzenie formularza za pomocą graficznego, formantu Styl kalendarza, która umożliwia użytkownikom wybór dnia miesiąca w środowisku Windows PowerShell 3.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="f05b6-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="f05b6-105">Utwórz formant wyboru daty graficznego</span><span class="sxs-lookup"><span data-stu-id="f05b6-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="f05b6-106">Skopiuj i następnie wklej następujący kod do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="f05b6-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="f05b6-107">Skrypt, który rozpoczyna się od ładowania dwie klasy .NET Framework: **System.Drawing** i **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="f05b6-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="f05b6-108">Następnie należy uruchomić nowe wystąpienie klasy .NET Framework **Windows.Forms.Form**; zapewnia pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f05b6-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="f05b6-109">Po utworzeniu wystąpienia klasy formularza należy przypisać wartości do trzech właściwości tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f05b6-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="f05b6-110">**tekst.**</span><span class="sxs-lookup"><span data-stu-id="f05b6-110">**Text.**</span></span> <span data-ttu-id="f05b6-111">To jest tytuł okna.</span><span class="sxs-lookup"><span data-stu-id="f05b6-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="f05b6-112">**Rozmiar.**</span><span class="sxs-lookup"><span data-stu-id="f05b6-112">**Size.**</span></span> <span data-ttu-id="f05b6-113">Jest to rozmiar w postaci, w pikselach.</span><span class="sxs-lookup"><span data-stu-id="f05b6-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="f05b6-114">Powyższy skrypt tworzy formularz, który jest 243 pikseli szerokości i wysokości 230 pikseli.</span><span class="sxs-lookup"><span data-stu-id="f05b6-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="f05b6-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="f05b6-115">**StartingPosition.**</span></span> <span data-ttu-id="f05b6-116">Ta opcjonalna właściwość jest ustawiona na **CenterScreen** w powyższy skrypt.</span><span class="sxs-lookup"><span data-stu-id="f05b6-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="f05b6-117">Jeśli nie dodasz tej właściwości, system Windows wybiera lokalizację po otwarciu formularza.</span><span class="sxs-lookup"><span data-stu-id="f05b6-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="f05b6-118">Przez ustawienie **StartingPosition** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu zawsze ładuje.</span><span class="sxs-lookup"><span data-stu-id="f05b6-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="f05b6-119">Następnie utwórz, a następnie dodaj formant kalendarza w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f05b6-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="f05b6-120">W tym przykładzie bieżącego dnia nie jest wyróżniony lub zaznaczona kółkiem.</span><span class="sxs-lookup"><span data-stu-id="f05b6-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="f05b6-121">Użytkownicy mogą wybrać w tym samym czasie tylko jeden dzień w kalendarzu.</span><span class="sxs-lookup"><span data-stu-id="f05b6-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="f05b6-122">Następnie należy utworzyć **OK** przycisk w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f05b6-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="f05b6-123">Określ rozmiar i zachowanie **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f05b6-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="f05b6-124">W tym przykładzie położenie przycisku jest 165 pikseli od górnej krawędzi formularza i 38 pikseli od lewej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="f05b6-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="f05b6-125">Wysokość przycisku jest 23 pikseli, gdy długość przycisk 75 pikseli.</span><span class="sxs-lookup"><span data-stu-id="f05b6-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="f05b6-126">Skrypt używa wstępnie zdefiniowanych typów formularzy systemu Windows w celu określenia zachowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="f05b6-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="f05b6-127">Podobnie można utworzyć **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f05b6-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="f05b6-128">**Anulować** znajduje się przycisk 165 pikseli od góry, ale 113 pikseli od lewej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="f05b6-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="f05b6-129">Ustaw **Topmost** właściwości **$true** wymusić okno, aby otworzyć nad innych okien i oknach dialogowych.</span><span class="sxs-lookup"><span data-stu-id="f05b6-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="f05b6-130">Dodaj następujący wiersz kodu do wyświetlania formularza w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f05b6-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="f05b6-131">Na koniec kodu wewnątrz **Jeśli** bloku instruuje system Windows, co należy zrobić z formularza po użytkowników wybierz dzień w kalendarzu, a następnie kliknij przycisk **OK** przycisk lub naciśnij przycisk **Enter** klucz.</span><span class="sxs-lookup"><span data-stu-id="f05b6-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="f05b6-132">Środowisko Windows PowerShell Wyświetla wybraną datą użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="f05b6-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="f05b6-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f05b6-133">See Also</span></span>

- [<span data-ttu-id="f05b6-134">Witaj skryptów Guy: Dlaczego te przykłady graficznego interfejsu użytkownika programu PowerShell nie działają?</span><span class="sxs-lookup"><span data-stu-id="f05b6-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="f05b6-135">GitHub: WinFormsExampleUpdates Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="f05b6-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="f05b6-136">Windows PowerShell porada tygodnia: tworzenie formant wyboru daty graficznego</span><span class="sxs-lookup"><span data-stu-id="f05b6-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)