---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Pola list z możliwością wielokrotnego wyboru
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: a762145dc197ec7e1424b2fbdcef5e7380d13803
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320979"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="56ca5-103">Pola listy wielokrotnego wyboru</span><span class="sxs-lookup"><span data-stu-id="56ca5-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="56ca5-104">Użyj programu Windows PowerShell 3.0 i nowszych wersji, aby utworzyć formant pola listy wielokrotnego wyboru w niestandardowym formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="56ca5-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="56ca5-105">Utwórz listę formantów okna, które zezwala na wiele zaznaczeń</span><span class="sxs-lookup"><span data-stu-id="56ca5-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="56ca5-106">Skopiuj i następnie wklej poniższą zawartość do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="56ca5-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="56ca5-107">Skrypt, który rozpoczyna się od ładowania dwóch klas .NET Framework: **System.Drawing** i **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="56ca5-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="56ca5-108">Następnie uruchom nowe wystąpienie klasy .NET Framework **System.Windows.Forms.Form**; zapewniający pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="56ca5-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="56ca5-109">Po utworzeniu wystąpienia klasy formularza, należy przypisać wartości do trzech właściwości tej klasy.</span><span class="sxs-lookup"><span data-stu-id="56ca5-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="56ca5-110">**Tekst.**</span><span class="sxs-lookup"><span data-stu-id="56ca5-110">**Text.**</span></span> <span data-ttu-id="56ca5-111">Staje się on tytuł okna.</span><span class="sxs-lookup"><span data-stu-id="56ca5-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="56ca5-112">**Rozmiar.**</span><span class="sxs-lookup"><span data-stu-id="56ca5-112">**Size.**</span></span> <span data-ttu-id="56ca5-113">Jest to rozmiar formularza, w pikselach.</span><span class="sxs-lookup"><span data-stu-id="56ca5-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="56ca5-114">Powyższy skrypt tworzy formularz, który jest 300 pikseli szerokości i wysokości 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="56ca5-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="56ca5-115">**Pozycjapoczątkowa.**</span><span class="sxs-lookup"><span data-stu-id="56ca5-115">**StartingPosition.**</span></span> <span data-ttu-id="56ca5-116">Tej opcjonalnej właściwości jest równa **CenterScreen** w poprzednim skrypcie.</span><span class="sxs-lookup"><span data-stu-id="56ca5-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="56ca5-117">Jeśli nie dodasz tę właściwość, Windows wybiera lokalizację, gdy formularz jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="56ca5-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="56ca5-118">Ustawiając **Pozycjapoczątkowa** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu każdorazowo ładuje.</span><span class="sxs-lookup"><span data-stu-id="56ca5-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="56ca5-119">Następnie należy utworzyć **OK** przycisk dla formularza użytkownika.</span><span class="sxs-lookup"><span data-stu-id="56ca5-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="56ca5-120">Określ rozmiar i zachowanie **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="56ca5-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="56ca5-121">W tym przykładzie położenie przycisku jest 120 pikseli od górnej krawędzi formularza i 75 pikseli od lewej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="56ca5-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="56ca5-122">Wysokość przycisku jest 23 pikseli, podczas gdy długość przycisk wynosi 75 pikseli.</span><span class="sxs-lookup"><span data-stu-id="56ca5-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="56ca5-123">Skrypt używa wstępnie zdefiniowanych typów Windows Forms do określenia zachowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="56ca5-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="56ca5-124">Podobnie można utworzyć **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="56ca5-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="56ca5-125">**Anulować** przycisk jest 120 pikseli od górnej, ale 150 pikseli od lewej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="56ca5-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="56ca5-126">Następnie należy podać tekst etykiety na okno, w tym artykule opisano informacje, które mają być zapewniają użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="56ca5-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="56ca5-127">Dodawanie kontrolki (w tym przypadku pole listy), która umożliwia użytkownikom, podaj informacje, które zostały opisane w tekście etykiet.</span><span class="sxs-lookup"><span data-stu-id="56ca5-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="56ca5-128">Istnieje wiele formantów, które można zastosować, oprócz pól tekstowych; Aby uzyskać więcej kontrolek, zobacz [Namespace System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="56ca5-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="56ca5-129">Oto, jak określić chcesz zezwolić użytkownikom na wybór wielu wartości z listy.</span><span class="sxs-lookup"><span data-stu-id="56ca5-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="56ca5-130">W następnej sekcji należy określić wartości, które mają pola listy, które mają być wyświetlane użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="56ca5-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="56ca5-131">Określ maksymalną wysokość kontrolki pola listy.</span><span class="sxs-lookup"><span data-stu-id="56ca5-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="56ca5-132">Dodawanie kontrolki pola listy do formularza i poinformuj Windows, aby otworzyć formularz na jego podstawie inne okna i okna dialogowe, gdy zostanie otwarta.</span><span class="sxs-lookup"><span data-stu-id="56ca5-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="56ca5-133">Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.</span><span class="sxs-lookup"><span data-stu-id="56ca5-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="56ca5-134">Na koniec kod wewnątrz **Jeśli** bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników, wybierz co najmniej jedną opcję z listy rozwijanej, a następnie kliknij **OK** przycisk lub naciśnij klawisz **Enter**  klucza.</span><span class="sxs-lookup"><span data-stu-id="56ca5-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="56ca5-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56ca5-135">See Also</span></span>

- [<span data-ttu-id="56ca5-136">Witaj twórco skryptów Guy: Dlaczego te przykłady programu PowerShell graficznego interfejsu użytkownika nie działają?</span><span class="sxs-lookup"><span data-stu-id="56ca5-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="56ca5-137">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="56ca5-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="56ca5-138">Program Windows PowerShell porada tygodnia: wielokrotny wybór listy pola — i nie tylko!</span><span class="sxs-lookup"><span data-stu-id="56ca5-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](https://technet.microsoft.com/library/ff730950.aspx)