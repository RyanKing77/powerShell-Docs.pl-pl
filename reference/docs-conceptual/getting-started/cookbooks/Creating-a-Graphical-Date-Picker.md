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
# <a name="creating-a-graphical-date-picker"></a>Tworzenie graficznego obiektu wyboru daty

Umożliwia tworzenie formularza za pomocą graficznego, formantu Styl kalendarza, która umożliwia użytkownikom wybór dnia miesiąca w środowisku Windows PowerShell 3.0 i nowszych wersjach.

## <a name="create-a-graphical-date-picker-control"></a>Utwórz formant wyboru daty graficznego

Skopiuj i następnie wklej następujący kod do programu Windows PowerShell ISE, a następnie zapisz go jako skrypt programu Windows PowerShell (ps1).

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

Skrypt, który rozpoczyna się od ładowania dwie klasy .NET Framework: **System.Drawing** i **System.Windows.Forms**. Następnie należy uruchomić nowe wystąpienie klasy .NET Framework **Windows.Forms.Form**; zapewnia pustego formularza lub okna, do którego można rozpocząć dodawanie kontrolki.

```powershell
$form = New-Object Windows.Forms.Form
```

Po utworzeniu wystąpienia klasy formularza należy przypisać wartości do trzech właściwości tej klasy.

- **tekst.** To jest tytuł okna.

- **Rozmiar.** Jest to rozmiar w postaci, w pikselach. Powyższy skrypt tworzy formularz, który jest 243 pikseli szerokości i wysokości 230 pikseli.

- **StartingPosition.** Ta opcjonalna właściwość jest ustawiona na **CenterScreen** w powyższy skrypt. Jeśli nie dodasz tej właściwości, system Windows wybiera lokalizację po otwarciu formularza. Przez ustawienie **StartingPosition** do **CenterScreen**, automatycznie wyświetlasz formularza w środku ekranu zawsze ładuje.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Następnie utwórz, a następnie dodaj formant kalendarza w formularzu. W tym przykładzie bieżącego dnia nie jest wyróżniony lub zaznaczona kółkiem. Użytkownicy mogą wybrać w tym samym czasie tylko jeden dzień w kalendarzu.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Następnie należy utworzyć **OK** przycisk w formularzu. Określ rozmiar i zachowanie **OK** przycisku. W tym przykładzie położenie przycisku jest 165 pikseli od górnej krawędzi formularza i 38 pikseli od lewej krawędzi. Wysokość przycisku jest 23 pikseli, gdy długość przycisk 75 pikseli. Skrypt używa wstępnie zdefiniowanych typów formularzy systemu Windows w celu określenia zachowania przycisku.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Podobnie można utworzyć **anulować** przycisku. **Anulować** znajduje się przycisk 165 pikseli od góry, ale 113 pikseli od lewej krawędzi okna.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ustaw **Topmost** właściwości **$true** wymusić okno, aby otworzyć nad innych okien i oknach dialogowych.

```powershell
$form.Topmost = $true
```

Dodaj następujący wiersz kodu do wyświetlania formularza w systemie Windows.

```powershell
$result = $form.ShowDialog()
```

Na koniec kodu wewnątrz **Jeśli** bloku instruuje system Windows, co należy zrobić z formularza po użytkowników wybierz dzień w kalendarzu, a następnie kliknij przycisk **OK** przycisk lub naciśnij przycisk **Enter** klucz. Środowisko Windows PowerShell Wyświetla wybraną datą użytkownikom.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zobacz też

- [Witaj skryptów Guy: Dlaczego te przykłady graficznego interfejsu użytkownika programu PowerShell nie działają?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell porada tygodnia: tworzenie formant wyboru daty graficznego](http://technet.microsoft.com/library/ff730942.aspx)