---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie niestandardowego pola wejściowego
ms.openlocfilehash: 9c1c3c72482157e849c0259e7d2e25ed969a4aab
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030228"
---
# <a name="creating-a-custom-input-box"></a>Tworzenie niestandardowego pola wejściowego

Skrypt graficzny niestandardowego pola wejściowego, korzystając z funkcji tworzenia formularzy programu Microsoft .NET Framework w programie Windows PowerShell 3.0 i nowszych wersjach.

## <a name="create-a-custom-graphical-input-box"></a>Tworzenie niestandardowych, graficzne pola wejściowego

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
$OKButton.Location = New-Object System.Drawing.Point(75,120)
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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Dodawanie kontrolki (w tym przypadku pole tekstowe), która umożliwia użytkownikom, podaj informacje, które zostały opisane w tekście etykiet. Istnieje wiele formantów, które można zastosować, oprócz pól tekstowych; Aby uzyskać więcej kontrolek, zobacz [Namespace System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) w witrynie MSDN.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Ustaw **Topmost** właściwości **$true** wymusić okna, aby otworzyć na jego podstawie innych okien i okien dialogowych.

```powershell
$form.Topmost = $true
```

Następnie dodaj następujący wiersz kodu, aby aktywować formularza i ustawić fokus do pola tekstowego, który został utworzony.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.

```powershell
$result = $form.ShowDialog()
```

Na koniec kod wewnątrz **Jeśli** bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników w polu tekstowym, a następnie kliknij przycisk **OK** przycisk lub naciśnij klawisz **Enter** klucz.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Zobacz też

- [Witaj twórco skryptów:  Dlaczego nie działają te przykłady programu PowerShell graficznego interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell porada tygodnia:  Tworzenie niestandardowego pola wejściowego](https://technet.microsoft.com/library/ff730941.aspx)
