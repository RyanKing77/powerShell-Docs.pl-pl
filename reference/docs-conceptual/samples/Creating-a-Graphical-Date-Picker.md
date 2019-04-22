---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie graficznego obiektu wyboru daty
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506805"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="93d8d-103">Tworzenie graficznego obiektu wyboru daty</span><span class="sxs-lookup"><span data-stu-id="93d8d-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="93d8d-104">Użyj programu Windows PowerShell 3.0 i nowszych wersjach, aby utworzyć formularza z formantem Styl kalendarza graficzny, pozwala użytkownikom na wybór dnia miesiąca.</span><span class="sxs-lookup"><span data-stu-id="93d8d-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="93d8d-105">Utwórz formant graficzny wyboru daty</span><span class="sxs-lookup"><span data-stu-id="93d8d-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="93d8d-106">Skopiuj i następnie wklej poniższą zawartość do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="93d8d-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="93d8d-107">Skrypt rozpoczyna się od ładowania dwóch klas .NET Framework: **System.Drawing** i **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="93d8d-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="93d8d-108">Następnie uruchom nowe wystąpienie klasy .NET Framework **Windows.Forms.Form**; zapewniający pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="93d8d-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="93d8d-109">W tym przykładzie przypisuje wartości do czterech właściwości tej klasy przy użyciu **właściwość** właściwość i Tabela skrótów.</span><span class="sxs-lookup"><span data-stu-id="93d8d-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="93d8d-110">**Używana wartość StartPosition**: Jeśli nie dodasz tę właściwość, Windows wybiera lokalizację, gdy formularz jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="93d8d-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="93d8d-111">Przez ustawienie tej właściwości na **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu każdorazowo ładuje.</span><span class="sxs-lookup"><span data-stu-id="93d8d-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="93d8d-112">**Rozmiar**: Jest to rozmiar formularza, w pikselach.</span><span class="sxs-lookup"><span data-stu-id="93d8d-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="93d8d-113">Powyższy skrypt tworzy formularz, który jest 243 pikseli szerokości i wysokości 230 pikseli.</span><span class="sxs-lookup"><span data-stu-id="93d8d-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="93d8d-114">**Tekst**: Staje się on tytuł okna.</span><span class="sxs-lookup"><span data-stu-id="93d8d-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="93d8d-115">**Najwyższego poziomu**: Przez ustawienie tej właściwości na `$true`, możesz wymusić okna, aby otworzyć na jego podstawie innych okien i okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="93d8d-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="93d8d-116">Następnie utwórz, a następnie dodaj formant kalendarza w formularzu.</span><span class="sxs-lookup"><span data-stu-id="93d8d-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="93d8d-117">W tym przykładzie bieżący dzień jest wyróżniony lub nie kółku.</span><span class="sxs-lookup"><span data-stu-id="93d8d-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="93d8d-118">Użytkownicy mogą wybrać naraz tylko jeden dzień w kalendarzu.</span><span class="sxs-lookup"><span data-stu-id="93d8d-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="93d8d-119">Następnie należy utworzyć **OK** przycisk dla formularza użytkownika.</span><span class="sxs-lookup"><span data-stu-id="93d8d-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="93d8d-120">Określ rozmiar i zachowanie **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="93d8d-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="93d8d-121">W tym przykładzie położenie przycisku jest 165 pikseli od górnej krawędzi formularza i 38 pikseli od lewej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="93d8d-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="93d8d-122">Wysokość przycisku jest 23 pikseli, podczas gdy długość przycisk wynosi 75 pikseli.</span><span class="sxs-lookup"><span data-stu-id="93d8d-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="93d8d-123">Skrypt używa wstępnie zdefiniowanych typów Windows Forms do określenia zachowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="93d8d-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="93d8d-124">Podobnie można utworzyć **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="93d8d-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="93d8d-125">**Anulować** znajduje się przycisk 165 pikseli od górnej, ale 113 pikseli od lewej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="93d8d-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="93d8d-126">Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.</span><span class="sxs-lookup"><span data-stu-id="93d8d-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="93d8d-127">Na koniec kod wewnątrz `if` bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników, wybierz dzień w kalendarzu, a następnie kliknij przycisk **OK** przycisk lub naciśnij klawisz **Enter** klucza.</span><span class="sxs-lookup"><span data-stu-id="93d8d-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="93d8d-128">Program Windows PowerShell Wyświetla wybraną datą dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="93d8d-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="93d8d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93d8d-129">See Also</span></span>

- [<span data-ttu-id="93d8d-130">Witaj twórco skryptów:  Dlaczego nie działają te przykłady programu PowerShell graficznego interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="93d8d-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="93d8d-131">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="93d8d-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="93d8d-132">Windows PowerShell porada tygodnia:  Tworzenie graficznego obiektu wyboru daty</span><span class="sxs-lookup"><span data-stu-id="93d8d-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)