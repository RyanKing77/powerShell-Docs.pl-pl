---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Pola list z możliwością wielokrotnego wyboru
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: a762145dc197ec7e1424b2fbdcef5e7380d13803
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404945"
---
# <a name="multiple-selection-list-boxes"></a>Pola listy wielokrotnego wyboru

Użyj programu Windows PowerShell 3.0 i nowszych wersji, aby utworzyć formant pola listy wielokrotnego wyboru w niestandardowym formularzu Windows.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Utwórz listę formantów okna, które zezwala na wiele zaznaczeń

Skopiuj i następnie wklej poniższą zawartość do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).

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

Skrypt rozpoczyna się od ładowania dwóch klas .NET Framework: **System.Drawing** i **System.Windows.Forms**. Następnie uruchom nowe wystąpienie klasy .NET Framework **System.Windows.Forms.Form**; zapewniający pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Po utworzeniu wystąpienia klasy formularza, należy przypisać wartości do trzech właściwości tej klasy.

- **Tekst.** Staje się on tytuł okna.

- **Rozmiar.** Jest to rozmiar formularza, w pikselach. Powyższy skrypt tworzy formularz, który jest 300 pikseli szerokości i wysokości 200 pikseli.

- **Pozycjapoczątkowa.** Tej opcjonalnej właściwości jest równa **CenterScreen** w poprzednim skrypcie. Jeśli nie dodasz tę właściwość, Windows wybiera lokalizację, gdy formularz jest otwarty. Ustawiając **Pozycjapoczątkowa** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu każdorazowo ładuje.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Następnie należy utworzyć **OK** przycisk dla formularza użytkownika. Określ rozmiar i zachowanie **OK** przycisku. W tym przykładzie położenie przycisku jest 120 pikseli od górnej krawędzi formularza i 75 pikseli od lewej krawędzi. Wysokość przycisku jest 23 pikseli, podczas gdy długość przycisk wynosi 75 pikseli. Skrypt używa wstępnie zdefiniowanych typów Windows Forms do określenia zachowania przycisku.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Podobnie można utworzyć **anulować** przycisku. **Anulować** przycisk jest 120 pikseli od górnej, ale 150 pikseli od lewej krawędzi okna.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Następnie należy podać tekst etykiety na okno, w tym artykule opisano informacje, które mają być zapewniają użytkownikom.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Dodawanie kontrolki (w tym przypadku pole listy), która umożliwia użytkownikom, podaj informacje, które zostały opisane w tekście etykiet. Istnieje wiele formantów, które można zastosować, oprócz pól tekstowych; Aby uzyskać więcej kontrolek, zobacz [Namespace System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) w witrynie MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Oto, jak określić chcesz zezwolić użytkownikom na wybór wielu wartości z listy.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

W następnej sekcji należy określić wartości, które mają pola listy, które mają być wyświetlane użytkownikom.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

Określ maksymalną wysokość kontrolki pola listy.

```powershell
$listBox.Height = 70
```

Dodawanie kontrolki pola listy do formularza i poinformuj Windows, aby otworzyć formularz na jego podstawie inne okna i okna dialogowe, gdy zostanie otwarta.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.

```powershell
$result = $form.ShowDialog()
```

Na koniec kod wewnątrz **Jeśli** bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników, wybierz co najmniej jedną opcję z listy rozwijanej, a następnie kliknij **OK** przycisk lub naciśnij klawisz **Enter**  klucza.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Zobacz też

- [Witaj twórco skryptów:  Dlaczego nie działają te przykłady programu PowerShell graficznego interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell porada tygodnia:  Pola listy wyboru wielokrotnego — i nie tylko!](https://technet.microsoft.com/library/ff730950.aspx)