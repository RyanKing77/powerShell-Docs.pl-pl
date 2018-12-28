---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie graficznego obiektu wyboru daty
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404669"
---
# <a name="creating-a-graphical-date-picker"></a>Tworzenie graficznego obiektu wyboru daty

Użyj programu Windows PowerShell 3.0 i nowszych wersjach, aby utworzyć formularza z formantem Styl kalendarza graficzny, pozwala użytkownikom na wybór dnia miesiąca.

## <a name="create-a-graphical-date-picker-control"></a>Utwórz formant graficzny wyboru daty

Skopiuj i następnie wklej poniższą zawartość do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).

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

Skrypt rozpoczyna się od ładowania dwóch klas .NET Framework: **System.Drawing** i **System.Windows.Forms**. Następnie uruchom nowe wystąpienie klasy .NET Framework **Windows.Forms.Form**; zapewniający pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.

```powershell
$form = New-Object Windows.Forms.Form
```

Po utworzeniu wystąpienia klasy formularza, należy przypisać wartości do trzech właściwości tej klasy.

- **Tekst.** Staje się on tytuł okna.

- **Rozmiar.** Jest to rozmiar formularza, w pikselach. Powyższy skrypt tworzy formularz, który jest 243 pikseli szerokości i wysokości 230 pikseli.

- **Pozycjapoczątkowa.** Tej opcjonalnej właściwości jest równa **CenterScreen** w poprzednim skrypcie. Jeśli nie dodasz tę właściwość, Windows wybiera lokalizację, gdy formularz jest otwarty. Ustawiając **Pozycjapoczątkowa** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu każdorazowo ładuje.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Następnie utwórz, a następnie dodaj formant kalendarza w formularzu. W tym przykładzie bieżący dzień jest wyróżniony lub nie kółku. Użytkownicy mogą wybrać naraz tylko jeden dzień w kalendarzu.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Następnie należy utworzyć **OK** przycisk dla formularza użytkownika. Określ rozmiar i zachowanie **OK** przycisku. W tym przykładzie położenie przycisku jest 165 pikseli od górnej krawędzi formularza i 38 pikseli od lewej krawędzi. Wysokość przycisku jest 23 pikseli, podczas gdy długość przycisk wynosi 75 pikseli. Skrypt używa wstępnie zdefiniowanych typów Windows Forms do określenia zachowania przycisku.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Podobnie można utworzyć **anulować** przycisku. **Anulować** znajduje się przycisk 165 pikseli od górnej, ale 113 pikseli od lewej krawędzi okna.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ustaw **Topmost** właściwości **$true** wymusić okna, aby otworzyć na jego podstawie innych okien i okien dialogowych.

```powershell
$form.Topmost = $true
```

Dodaj następujący wiersz kodu w celu wyświetlenia formularza w Windows.

```powershell
$result = $form.ShowDialog()
```

Na koniec kod wewnątrz **Jeśli** bloku powoduje, że Windows co należy zrobić z formularzem, po użytkowników, wybierz dzień w kalendarzu, a następnie kliknij przycisk **OK** przycisk lub naciśnij klawisz **Enter** klucz. Program Windows PowerShell Wyświetla wybraną datą dla użytkowników.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zobacz też

- [Witaj twórco skryptów:  Dlaczego nie działają te przykłady programu PowerShell graficznego interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell porada tygodnia:  Tworzenie graficznego obiektu wyboru daty](https://technet.microsoft.com/library/ff730942.aspx)