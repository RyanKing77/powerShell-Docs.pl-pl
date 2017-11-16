---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Wielokrotne zaznaczenie pola listy
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 122014888bc5cf93c1c709b9d534d572037f5ffe
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="multiple-selection-list-boxes"></a>Pola listy wielokrotnego wyboru
Umożliwia utworzenie pole listy wielokrotnego wyboru w niestandardowym formularzu systemu Windows w środowisku Windows PowerShell 3.0 i nowszych wersjach.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Utwórz listę formantów pól, które umożliwiają wielokrotny
Skopiuj i następnie wklej następujący kod do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

Skrypt, który rozpoczyna się od ładowania dwie klasy .NET Framework: **System.Drawing** i **System.Windows.Forms**. Następnie należy uruchomić nowe wystąpienie klasy .NET Framework **klasie System.Windows.Forms.Form**; zapewnia pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.

```
$form = New-Object System.Windows.Forms.Form
```

Po utworzeniu wystąpienia klasy formularza należy przypisać wartości do trzech właściwości tej klasy.

- **Tekst.** To jest tytuł okna.

- **Rozmiar.** Jest to rozmiar w postaci, w pikselach. Powyższy skrypt tworzy formularz, który jest 300 pikseli szerokości i wysokości 200 pikseli.

- **StartingPosition.** Ta opcjonalna właściwość jest ustawiona na **CenterScreen** w powyższy skrypt. Jeśli nie dodasz tej właściwości, system Windows wybiera lokalizację po otwarciu formularza. Przez ustawienie **StartingPosition** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu zawsze ładuje.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Następnie należy utworzyć **OK** przycisk w formularzu. Określ rozmiar i zachowanie **OK** przycisku. W tym przykładzie położenie przycisku jest 120 pikseli od górnej krawędzi formularza i 75 pikseli od lewej krawędzi. Wysokość przycisku jest 23 pikseli, gdy długość przycisk 75 pikseli. Skrypt używa wstępnie zdefiniowanych typów formularzy systemu Windows w celu określenia zachowania przycisku.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Podobnie można utworzyć **anulować** przycisku. **Anulować** przycisk jest 120 pikseli od góry, ale 150 pikseli od lewej krawędzi okna.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Następnie zawierają tekst etykiety opisujący informacje, które chcesz użytkowników w celu zapewnienia okna.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

Dodawanie formantu (w tym przypadku pole listy), który umożliwia użytkownikom, podaj informacje, które zostały opisane w tekście etykiety. Istnieje wiele formantów, które można zastosować poza pól tekstowych. Aby uzyskać więcej opcji, zobacz [Namespace elementu System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) w witrynie MSDN.

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```


Oto, jak określić czy chcesz zezwolić użytkownikom na wybranie wielu wartości z listy.

```
$listBox.SelectionMode = "MultiExtended"
```

W następnej sekcji można określić wartości ma pole listy do wyświetlenia użytkownikom.

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

Określ maksymalną wysokość formantu pola listy.

```
$listBox.Height = 70
```

Dodawanie do formularza pole listy oraz poinstruuj systemu Windows, aby otworzyć formularz nad innych oknach i oknach dialogowych, gdy zostanie otwarta.

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

Dodaj następujący wiersz kodu do wyświetlania formularza w systemie Windows.

```
$result = $form.ShowDialog()
```

Na koniec kodu wewnątrz **Jeśli** bloku instruuje system Windows, co należy zrobić z formularza po użytkowników wybierz jedną lub więcej opcji na liście, a następnie kliknij przycisk **OK** przycisk lub naciśnij przycisk **Enter**  klucza.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Zobacz też
- [Witaj skryptów Guy: Dlaczego te przykłady graficznego interfejsu użytkownika programu PowerShell nie działają?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell porada tygodnia: wielokrotnego wyboru listy, pola — i nie tylko!](http://technet.microsoft.com/library/ff730950.aspx)

