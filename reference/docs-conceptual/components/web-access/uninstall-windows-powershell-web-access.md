---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Odinstalowywanie programu windows powershell web access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405455"
---
# <a name="uninstall-windows-powershell-web-access"></a>Odinstalowywanie programu Windows PowerShell Web Access

Zaktualizowano: 24 czerwca 2013 r.

Dotyczy: Windows Server 2012 R2, Windows Server 2012

Kroki opisane w tym temacie Usuń witrynę sieci Web programu Windows PowerShell Web Access i odpowiadającej jej aplikacji z serwera bramy, w którym jest zainstalowany.

## <a name="notify-users"></a>Powiadom użytkowników

Przed rozpoczęciem należy powiadomić użytkowników konsoli internetowej o usunięciu witryny internetowej.

Odinstalowywanie programu Windows PowerShell Web Access nie powoduje odinstalowania usług IIS lub inne funkcje, które zostały zainstalowane automatycznie, ponieważ wymaga programu Windows PowerShell Web Access, ich uruchomienie.
Proces odinstalowywania pozostawia zainstalowane funkcje, na których był zależny; Windows PowerShell Web Access Funkcje te można odinstalować oddzielnie, jeśli to konieczne.

## <a name="recommended-quick-uninstallation"></a>Zalecana (szybka) dezinstalacja

Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno:

- Aplikacja sieci web programu Windows PowerShell Web Access, a
- Funkcja Windows PowerShell Web Access

za pomocą poleceń cmdlet programu Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Krok 1. Usuwanie aplikacji sieci web przy użyciu poleceń cmdlet

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

    -   Na pulpicie Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.

    -   Na Windows **Start** ekranu, kliknij przycisk **programu Windows PowerShell**.

2. Typ `Uninstall-PswaWebApplication`, a następnie naciśnij klawisz **Enter**.
   1. Jeśli masz określoną własną, niestandardową nazwę witryny internetowej, możesz dodać do polecenia parametr `-WebsiteName` i określić nazwę witryny internetowej.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Jeśli używasz niestandardowej aplikacji sieci web (innej niż aplikacja domyślna, **pswa**, Dodaj `-WebApplicationName` parametru do polecenia i określ nazwę aplikacji sieci web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Jeśli używasz certyfikatu testowego, dodaj parametr `DeleteTestCertificate` do polecenia cmdlet, jak pokazano w następującym przykładzie.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Krok 2. Odinstalowywanie za pomocą poleceń cmdlet program Windows PowerShell Web Access

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika. Jeśli sesja jest już otwarta, przejdź do następnego kroku.

    -   Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.

    -   Na Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

1. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *nazwa_komputera* reprezentuje serwer zdalny, z którego chcesz usunąć program Windows PowerShell Web Access. Parametr `-Restart` powoduje automatyczne ponowne uruchomienie serwerów docelowych, jeśli jest to wymagane w związku z usunięciem składnika.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Aby usunąć role i funkcje z dysku VHD trybu offline, należy dodać zarówno parametr `-ComputerName`, jak i parametr `-VHD`. Parametr `-ComputerName` zawiera nazwę serwera, na którym należy zainstalować dysk VHD, a parametr `-VHD` zawiera ścieżkę do pliku dysku VHD na określonym serwerze.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Po zakończeniu operacji usunięcia, sprawdź, czy usunięte z programu Windows PowerShell Web Access, otwierając **wszystkie serwery** strony w Menedżerze serwera, wybierając serwer, z którego usunięto funkcję i wyświetlając **ról i Funkcje** kafelków na stronie wybranego serwera.

    Można również uruchomić `Get-WindowsFeature` polecenia cmdlet ukierunkowanych na wybrany serwer (Get-WindowsFeature - ComputerName &lt; *nazwa_komputera*&gt;) aby wyświetlić listę ról i funkcji, które są zainstalowane na serwerze.

## <a name="custom-uninstallation"></a>Dezinstalacja niestandardowa

Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno aplikacji sieci web programu Windows PowerShell Web Access, jak i funkcji programu Windows PowerShell Web Access przy użyciu Usuń role i funkcje kreatora w Menedżerze serwera i konsoli Menedżera usług IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Krok 1. Usuwanie aplikacji sieci web za pomocą Menedżera usług IIS


1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności. Jeśli jest on już otwarty, przejdź do następnego kroku.

    -   Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.

    -   Na Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót, gdy jest on wyświetlany w **aplikacje** wyników.

1. W okienku drzewa Menedżera usług IIS wybierz witrynę sieci Web, który uruchomił aplikację sieci web programu Windows PowerShell Web Access.

1. W **akcje** okienku w obszarze **Zarządzaj witryną internetową**, kliknij przycisk **zatrzymać**.

1. W okienku drzewa kliknij prawym przyciskiem myszy aplikację sieci web w witrynie sieci Web, na którym działa aplikacja sieci web programu Windows PowerShell Web Access, a następnie kliknij przycisk **Usuń**.

1. W okienku drzewa wybierz **pul aplikacji**, wybierz folder puli aplikacji programu Windows PowerShell Web Access, kliknij przycisk **zatrzymać** w **akcje** okienka, a następnie kliknij przycisk  **Usuń** w okienku zawartości.

1. Zamknij Menedżera usług IIS.

> ![Ostrzeżenie Uwaga](images/SecurityNote.jpeg)**Uwaga**:
>
> Certyfikat nie jest usuwany podczas dezinstalacji.
>
> Jeśli chcesz usunąć utworzony przez Ciebie certyfikat z podpisem własnym lub używany certyfikat testowy, zrób to w Menedżerze usług IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Krok 2. Odinstalowywanie za pomocą funkcji Kreator usuwania ról i program Windows PowerShell Web Access

1. Jeśli Menedżer serwera jest już otwarty, przejdź do następnego kroku. Jeśli Menedżer serwera nie jest już otwarty, otwórz go, wykonując jedną z następujących czynności.

    -   Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.

    -   Na Windows **Start** ekranu, kliknij przycisk **Menedżera serwera**.

1. Na **Zarządzaj** menu, kliknij przycisk **Usuń role i funkcje**.

1. Na **serwer docelowy wybierz** stronie, wybierz serwer lub dysk VHD trybu offline, z którego chcesz usunąć tę funkcję. Aby wybrać dysk VHD trybu offline, najpierw wybierz serwer, na którym należy zainstalować dysk VHD, a następnie wybierz plik dysku VHD. Po wybraniu serwera docelowego kliknij **Dalej**.

1. Kliknij przycisk **dalej** ponownie, aby przejść do **usuwanie funkcji** strony.

1. Usuń zaznaczenie pola wyboru dla **programu Windows PowerShell Web Access**, a następnie kliknij przycisk **dalej**.

1. Na **Potwierdzenie opcji usuwania** kliknij **Usuń**.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i używanie programu Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md)
- [Pomoc Menedżera 7.0 usług IIS](https://technet.microsoft.com/library/cc732664.aspx)