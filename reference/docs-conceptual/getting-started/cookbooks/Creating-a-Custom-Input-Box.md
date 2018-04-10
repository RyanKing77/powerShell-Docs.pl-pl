---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie niestandardowego pola wejściowego
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 681a75a28a8fb03eb4442d5e20b32b25a337d540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="e1ac8-103">Tworzenie niestandardowego pola wejściowego</span><span class="sxs-lookup"><span data-stu-id="e1ac8-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="e1ac8-104">Skrypt graficznego niestandardowego pola wejściowego przy użyciu funkcji tworzenia formularzy programu Microsoft .NET Framework w środowisku Windows PowerShell 3.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="e1ac8-105">Tworzenie niestandardowych, graficznego pola wejściowego</span><span class="sxs-lookup"><span data-stu-id="e1ac8-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="e1ac8-106">Skopiuj i następnie wklej następujący kod do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="e1ac8-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="e1ac8-107">Skrypt, który rozpoczyna się od ładowania dwie klasy .NET Framework: **System.Drawing** i **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="e1ac8-108">Następnie należy uruchomić nowe wystąpienie klasy .NET Framework **klasie System.Windows.Forms.Form**; zapewnia pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="e1ac8-109">Po utworzeniu wystąpienia klasy formularza należy przypisać wartości do trzech właściwości tej klasy.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="e1ac8-110">**tekst.**</span><span class="sxs-lookup"><span data-stu-id="e1ac8-110">**Text.**</span></span> <span data-ttu-id="e1ac8-111">To jest tytuł okna.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="e1ac8-112">**Rozmiar.**</span><span class="sxs-lookup"><span data-stu-id="e1ac8-112">**Size.**</span></span> <span data-ttu-id="e1ac8-113">Jest to rozmiar w postaci, w pikselach.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="e1ac8-114">Powyższy skrypt tworzy formularz, który jest 300 pikseli szerokości i wysokości 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="e1ac8-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="e1ac8-115">**StartingPosition.**</span></span> <span data-ttu-id="e1ac8-116">Ta opcjonalna właściwość jest ustawiona na **CenterScreen** w powyższy skrypt.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="e1ac8-117">Jeśli nie dodasz tej właściwości, system Windows wybiera lokalizację po otwarciu formularza.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="e1ac8-118">Przez ustawienie **StartingPosition** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu zawsze ładuje.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="e1ac8-119">Następnie należy utworzyć **OK** przycisk w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="e1ac8-120">Określ rozmiar i zachowanie **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="e1ac8-121">W tym przykładzie położenie przycisku jest 120 pikseli od górnej krawędzi formularza i 75 pikseli od lewej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="e1ac8-122">Wysokość przycisku jest 23 pikseli, gdy długość przycisk 75 pikseli.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="e1ac8-123">Skrypt używa wstępnie zdefiniowanych typów formularzy systemu Windows w celu określenia zachowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="e1ac8-124">Podobnie można utworzyć **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="e1ac8-125">**Anulować** przycisk jest 120 pikseli od góry, ale 150 pikseli od lewej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="e1ac8-126">Następnie zawierają tekst etykiety opisujący informacje, które chcesz użytkowników w celu zapewnienia okna.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="e1ac8-127">Dodawanie formantu (w tym przypadku pole tekstowe), który umożliwia użytkownikom, podaj informacje, które zostały opisane w tekście etykiety.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="e1ac8-128">Istnieje wiele formantów, które można zastosować poza pól tekstowych. Aby uzyskać więcej opcji, zobacz [Namespace elementu System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="e1ac8-129">Ustaw **Topmost** właściwości **$true** wymusić okno, aby otworzyć nad innych okien i oknach dialogowych.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="e1ac8-130">Następnie dodaj następujący wiersz kodu formularza i ustawić fokus do pola tekstowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="e1ac8-131">Dodaj następujący wiersz kodu do wyświetlania formularza w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="e1ac8-132">Na koniec kodu wewnątrz **Jeśli** bloku instruuje system Windows, co należy zrobić z formularza po użytkowników umieścić tekst w polu tekstowym, a następnie kliknij przycisk **OK** przycisk lub naciśnij przycisk **Enter** klucz.</span><span class="sxs-lookup"><span data-stu-id="e1ac8-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="e1ac8-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1ac8-133">See Also</span></span>

- [<span data-ttu-id="e1ac8-134">Witaj skryptów Guy: Dlaczego te przykłady graficznego interfejsu użytkownika programu PowerShell nie działają?</span><span class="sxs-lookup"><span data-stu-id="e1ac8-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="e1ac8-135">GitHub: WinFormsExampleUpdates Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="e1ac8-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="e1ac8-136">Windows PowerShell porada tygodnia: Tworzenie niestandardowego pole wprowadzania</span><span class="sxs-lookup"><span data-stu-id="e1ac8-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)