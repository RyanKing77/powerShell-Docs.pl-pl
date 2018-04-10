---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Odinstalowywanie programu windows powershell web access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-windows-powershell-web-access"></a>Odinstalowywanie programu Windows PowerShell Web Access

Zaktualizowano: 24 czerwca 2013

Dotyczy: Windows Server 2012 R2, Windows Server 2012

Kroki opisane w tym temacie Usuń witrynę sieci Web Windows PowerShell Web Access i odpowiednią aplikację z serwera bramy, w którym jest zainstalowany.

## <a name="notify-users"></a>Powiadom użytkowników

Przed rozpoczęciem należy powiadomić użytkowników konsoli internetowej o usunięciu witryny internetowej.

Odinstalowywanie programu Windows PowerShell Web Access nie powoduje odinstalowania usług IIS lub innych funkcji, które zostały zainstalowane automatycznie, ponieważ program Windows PowerShell Web Access wymagane do uruchomienia.
Proces odinstalowywania pozostawia zainstalowane funkcje, na których był zależny; Windows PowerShell Web Access Funkcje te można odinstalować oddzielnie, jeśli to konieczne.

## <a name="recommended-quick-uninstallation"></a>Zalecana (szybka) dezinstalacja

Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno:

- Aplikacja sieci web programu Windows PowerShell Web Access, i
- Funkcja Windows PowerShell Web Access

za pomocą poleceń cmdlet programu Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Krok 1: Usuwanie aplikacji sieci web przy użyciu poleceń cmdlet

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

    -   Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.

    -   W systemie Windows **Start** kliknij **programu Windows PowerShell**.

2. Typ `Uninstall-PswaWebApplication`, a następnie naciśnij klawisz **Enter**.
   1. Jeśli masz określoną własną, niestandardową nazwę witryny internetowej, możesz dodać do polecenia parametr `-WebsiteName` i określić nazwę witryny internetowej.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Jeśli używasz niestandardowej aplikacji sieci web (innej niż aplikacja domyślna, **pswa**, Dodaj `-WebApplicationName` parametru polecenia i określ nazwę aplikacji sieci web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Jeśli używasz certyfikatu testowego, dodaj parametr `DeleteTestCertificate` do polecenia cmdlet, jak pokazano w następującym przykładzie.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Krok 2: Odinstalowywanie za pomocą poleceń cmdlet programu Windows PowerShell Web Access

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika. Jeśli sesja jest już otwarta, przejdź do następnego kroku.

    -   Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.

    -   W systemie Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

1. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *nazwa_komputera* reprezentuje serwer zdalny, z którego chcesz usunąć Windows PowerShell Web Access. Parametr `-Restart` powoduje automatyczne ponowne uruchomienie serwerów docelowych, jeśli jest to wymagane w związku z usunięciem składnika.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Aby usunąć role i funkcje z dysku VHD trybu offline, należy dodać zarówno parametr `-ComputerName`, jak i parametr `-VHD`. Parametr `-ComputerName` zawiera nazwę serwera, na którym należy zainstalować dysk VHD, a parametr `-VHD` zawiera ścieżkę do pliku dysku VHD na określonym serwerze.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Po zakończeniu operacji usunięcia Sprawdź, czy Windows PowerShell Web Access jest usunięte, otwierając **wszystkie serwery** strony w Menedżerze serwera, wybierając serwer, z którego usunięto funkcję i wyświetlając **ról i Funkcje** kafelka na stronie wybranego serwera.

    Można również uruchomić `Get-WindowsFeature` polecenia cmdlet docelowym będzie wybrany serwer (Get-WindowsFeature - ComputerName &lt; *nazwa_komputera*&gt;), aby wyświetlić listę ról i funkcji, które są zainstalowane na serwerze.

## <a name="custom-uninstallation"></a>Dezinstalacja niestandardowa

Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno aplikacji sieci web programu Windows PowerShell Web Access i funkcji systemu Windows PowerShell Web Access za pomocą Usuń role i funkcje kreatora w Menedżerze serwera i konsoli Menedżera usług IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Krok 1: Usuwanie aplikacji sieci web przy użyciu Menedżera usług IIS


1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności. Jeśli jest on już otwarty, przejdź do następnego kroku.

    -   Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.

    -   W systemie Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót jest wyświetlany w **aplikacji** wyników.

1. W okienku drzewa Menedżera usług IIS wybierz witrynę internetową, która działa aplikacja sieci web programu Windows PowerShell Web Access.

1. W **akcje** okienku w obszarze **Zarządzaj witryną internetową**, kliknij przycisk **zatrzymać**.

1. W okienku drzewa kliknij prawym przyciskiem myszy aplikację sieci web w witrynie sieci Web, na którym działa aplikacja sieci web programu Windows PowerShell Web Access, a następnie kliknij przycisk **Usuń**.

1. W okienku drzewa wybierz **pul aplikacji**, wybierz folder puli aplikacji programu Windows PowerShell Web Access, kliknij przycisk **zatrzymać** w **akcje** okienka, a następnie kliknij przycisk  **Usuń** w okienku zawartości.

1. Zamknij Menedżera usług IIS.

> ![Uwaga ostrzeżenie](images/SecurityNote.jpeg)**Uwaga**:
>
> Certyfikat nie jest usuwany podczas dezinstalacji.
>
> Jeśli chcesz usunąć utworzony przez Ciebie certyfikat z podpisem własnym lub używany certyfikat testowy, zrób to w Menedżerze usług IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Krok 2: Odinstalowywanie programu Windows PowerShell Web Access za pomocą usuwania ról i funkcji — Kreator

1. Jeśli Menedżer serwera jest już otwarty, przejdź do następnego kroku. Jeśli Menedżer serwera nie jest już otwarty, otwórz go, wykonując jedną z następujących czynności.

    -   Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.

    -   W systemie Windows **Start** kliknij **Menedżera serwera**.

1. Na **Zarządzaj** menu, kliknij przycisk **Usuń role i funkcje**.

1. Na **serwera docelowego wybierz** wybierz serwer lub dysku VHD trybu offline, z którego chcesz usunąć funkcję. Aby wybrać dysk VHD trybu offline, najpierw wybierz serwer, na którym należy zainstalować dysk VHD, a następnie wybierz plik dysku VHD. Po wybraniu serwera docelowego kliknij **Dalej**.

1. Kliknij przycisk **dalej** ponownie, aby przejść do **usuwanie funkcji** strony.

1. Usuń zaznaczenie pola wyboru dla **programu Windows PowerShell Web Access**, a następnie kliknij przycisk **dalej**.

1. Na **Potwierdzenie opcji usuwania** kliknij przycisk **Usuń**.

## <a name="see-also"></a>Zobacz też

- [Zainstalować i używać programu Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md)
- [Pomoc Menedżera 7.0 usług IIS](https://technet.microsoft.com/library/cc732664.aspx)