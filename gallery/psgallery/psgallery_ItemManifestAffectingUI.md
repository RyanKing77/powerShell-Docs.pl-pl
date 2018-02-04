# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Element manifestu wartości, które mają wpływ na Interfejsie galerii programu PowerShell

Ten temat zawiera wydawców z podsumowanie informacji na temat sposobu zmodyfikuj manifest ich publikacji galerii programu PowerShell, tak aby będzie mieć wpływ na funkcje PowerShellGet poleceń cmdlet i interfejsu użytkownika z galerii programu PowerShell. Ta zawartość jest zorganizowana według której zmiana pojawi się w górnej części, a następnie w obszarze nawigacyjnym po lewej stronie, począwszy. Brak sekcji szczegółów tagi obejmujący określający ważne tagi, jak również niektórych najczęściej używanych tagów. Istnieją dwa tematy, które zawierają przykłady manifestu: 

* Dla modułów, zobacz [manifestu modułu aktualizacji](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/psget_update-modulemanifest)
* Skryptów, zobacz [Tworzenie pliku skryptu za pomocą metadanych](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Kontrolowane przez Manifest elementy funkcji galerii programu PowerShell

Poniższa tabela zawiera elementy interfejsu użytkownika strony elementu galerii programu PowerShell, które są kontrolowane przez wydawcę.
Każdy element wskazuje, czy mogą być kontrolowane przez manifest modułu lub skryptu.

| Element interfejsu użytkownika | Opis | Moduł | Skrypt | 
| --- | --- | --- | --- |
| **Tytuł** | Jest to nazwa elementu, który jest opublikowany w galerii  | Nie | Nie |
| **Wersja** | Wersja wyświetlana jest ciąg wersji w metadanych, a jeśli wstępnej określono. Część podstawowej wersji w manifeście modułu jest ModuleVersion. Aby uzyskać skrypt jest identyfikowane jako. Wersja. Jeśli zostanie określony ciąg wersji wstępnej, te będą być dołączany do ModuleVersion dla modułów lub określony jako część. Wersja skryptów. Brak dokumentacji służący do określania wersji wstępnej ciągów w [modułów](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule)i w [skryptów](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Tak | Tak |
| **Opis** | Jest to opis w manifeście modułu, a w manifeście pliku skryptu jest. OPIS ELEMENTU | Tak | Tak |
| **Wymagaj akceptacji licencji** | Moduł może wymagać, że użytkownik akceptuje licencji, modyfikując manifestu modułu RequireLicenseAcceptance = $true, podając LicenseURI i dostarczanie pliku license.txt w katalogu głównym folderu modułu. Dodatkowe informacje są dostępne w [akceptacji licencji wymaga](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance) tematu. | Tak | Nie |
| **Informacje o wersji** | Dla modułów te informacje jest pobierana z sekcji ReleaseNotes w obszarze PSData\PrivateData. W manifestach skryptu jest. RELEASENOTES element. | Tak | Tak |
| **Właściciele** | Właściciele są listy użytkowników w galerii programu PowerShell, który można aktualizować elementu. Na liście właściciela nie jest uwzględniony w manifeście elementu. Dodatkowe dokumentacji opisano sposób [Zarządzaj właścicielami elementu](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Nie | Nie |
| **Autor** | To jest uwzględniane w manifeście modułu autor oraz w manifeście skryptu jako. AUTORA. Pole Author często służy do określania, firma lub organizacja skojarzony z elementem. | Tak | Tak |
| **Copyright** | To jest pole praw autorskich w manifeście modułu i. COPYRIGHT w manifeście skryptu. | Tak | Tak |
| **FileList** | Lista plików jest przenoszony z pakietu, gdy zostanie opublikowany w galerii programu PowerShell. Nie jest kontrolowane przez manifestu informacji. Uwaga: jest plik .nuspec dodatkowe na liście z każdego elementu w galerii programu PowerShell, która nie występuje po zainstalowaniu elementu w systemie. Jest to plik manifestu pakietu Nuget dla elementu i można zignorować. | Nie | Nie |
| **Tagi** | Dla modułów tagi są objęte PSData\PrivateData. W przypadku skryptów sekcja jest oznaczona. TAGI. Należy pamiętać, że tagi nie może zawierać spacji, nawet wtedy, gdy są one w cudzysłowy. Znaczniki mają dodatkowe wymagania i znaczenie, które są opisane w dalszej części tego tematu w sekcji szczegółów znacznika. | Tak | Tak |
| **Polecenia cmdlet** | Odbywa się przy użyciu CmdletsToExport modułu. Należy pamiętać, że najlepszym rozwiązaniem jest jawnie listę elementów, a nie za pomocą symbolu wieloznacznego "*", ponieważ moduł ładowania przyspieszyć dla użytkowników. | Tak | Nie |
| **Funkcje** | Odbywa się przy użyciu FunctionsToExport modułu. Należy pamiętać, że najlepszym rozwiązaniem jest jawnie listę elementów, a nie za pomocą symbolu wieloznacznego "*", ponieważ moduł ładowania przyspieszyć dla użytkowników. | Tak | Nie |
| **Zasoby usługi Konfiguracja DSC** | Dla modułów, które będą używane w środowisku PowerShell w wersji 5.0 lub nowszym odbywa się przy użyciu DscResourcesToExport. Jeśli moduł jest do użycia w programie PowerShell 4, DSCResourcesToExport powinien nie można użyć jako nie jest obsługiwane kluczem manifestu. (DSC nie był dostępny przed programu PowerShell 4). | Tak | Nie |
| **Przepływy pracy** | Przepływy pracy są publikowane w galerii programu PowerShell jako skrypty i zidentyfikowane jako przepływy pracy (zobacz [Connect AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) przykład) w kodzie. Nie jest to kontrolowane przez plik manifestu. | Nie | Nie |
| **Możliwości roli** | To będzie wyświetlane, gdy moduł opublikowany w galerii programu PowerShell zawiera jeden lub więcej liczbą plików możliwości (.psrc) roli, które są używane przez JEA. Można znaleźć w dokumentacji JEA, aby uzyskać więcej informacji na [możliwości roli](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Tak | Nie |
| **Wersje programu PowerShell** | Jest to wymienione w manifeście skryptu lub module. Dla modułów przeznaczone do użycia z programu PowerShell 5.0 a poniżej, jest kontrolowany przy użyciu tagów. Na pulpicie znacznika PSEdition_Desktop i podstawowych, użyj tagu PSEdition_Core. Dla modułów, które będą używane tylko w środowisku PowerShell w wersji 5.1 i nowszych istnieje klucz CompatiblePSEditions w manifeście głównego. Dodatkowe szczegóły, zapoznaj się z funkcji wersji PS w [w dokumentacji programu PowerShell Get](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Tak | Tak |
| **Zależności** | Zależności są moduły w galerii programu PowerShell, które są zadeklarowane w module jako RequiredModules lub w manifeście skryptu jako #Requires — moduł (nazwa). | Tak | Tak |
| **Minimalna wersja programu Powershell** | Można to wymienione w manifeście modułu jako PowerShellVersion | Tak | Nie |
| **Historia wersji** | Historia wersji odzwierciedla aktualizacjach do modułu w galerii programu PowerShell. Jeśli wersja elementu jest ukryty, za pomocą funkcji usuwania, będzie nie być wyświetlany w Historia wersji z wyjątkiem właścicieli elementu. | Nie | Nie |
| **Witryny projektu** | Witryny projektu jest dostępna dla modułów w sekcji Privatedata\PSData w manifeście modułu, określając ProjectURI. W manifeście skryptu jest kontrolowana przez określenie. PROJECTURI. | Tak | Tak |
| **Licencji** | Łącze licencji jest dostępna dla modułów w sekcji Privatedata\PSData w manifeście modułu, określając LicenseURI. W manifeście skryptu jest kontrolowana przez określenie. LICENSEURI. Należy zauważyć, że jeśli nie podano licencję za pośrednictwem LicenseURI lub następnie do modułu, warunki użytkowania galerii programu PowerShell Określ warunki użytkowania dla elementu. Zapoznaj się z warunkami użytkowania, aby uzyskać szczegółowe informacje. | Tak | Tak |

## <a name="editing-item-details"></a>Edytowanie szczegółów elementu

Strona elementu edytować galerii programu PowerShell zezwala na wydawcy zmienić kilka pól wyświetlanych dla elementu, w szczególności:

* Tytuł
* Opis
* Podsumowanie
* Adres URL ikony
* Adres URL strony głównej projektu
* Autorzy
* Prawa autorskie
* Tagi
* Informacje o wersji
* Wymaga licencji

Ta metoda nie jest zwykle zalecane, z wyjątkiem przypadków, gdy konieczne jest Popraw wyświetlanych dla starszej wersji modułu. Użytkownicy, którzy nabyli moduł będzie znaleźć metadanych jest niezgodny wyświetlanych w galerii programu PowerShell, który powoduje problemy dotyczące pozycji. Spowoduje to często zapytania, przechodząc do właścicieli element, aby potwierdzić zmianę. Zdecydowanie zaleca się, że zawsze, gdy ta metoda jest używana, nowa wersja elementu powinien zostać opublikowany, takie same zmiany. 

## <a name="tag-details"></a>Szczegóły tagu

Tagi to proste ciągi konsumentów użycia można znaleźć elementów. Tagi są najbardziej przydatna, gdy są one używane spójnie przez wiele elementów związanych z tym samym tematem. Wiele wersji tego samego word (na przykład bazy danych i baz danych, lub testowym i testowania) zwykle zapewnia korzyści mały. Znaczniki są jednowyrazowej ciągów bez uwzględniania wielkości liter i nie może zawierać spacji. Jeśli istnieje wyrażenie, które uważasz, że użytkownicy będą wyszukiwać, dodać go do opisu elementu i zostaną znalezione w wynikach wyszukiwania. Jeśli chcesz zwiększyć czytelność, należy użyć Pascal wielkości liter, łącznik, podkreślenie lub okres. Należy zachować ostrożność tworzenie tagi długich, złożonych i nietypowych, jak często są one błędna. 

Tagi, które są należy pamiętać, w galerii programu PowerShell i PowerShellGet poleceń cmdlet je traktować unikatowo. PSEdition_Desktop PSEdition_Core są szczegółowe przykłady i opisanych powyżej. 

Jak wspomniano powyżej, tagi Podaj wartość większość, jeśli są one określone i używany spójnie przez wiele elementów. Jako wydawca próby zlokalizowania najlepsze tagi do użycia Najprostszym sposobem jest wyszukiwanie galerii programu PowerShell tagów, które zamierzasz. W idealnym przypadku będzie wiele elementów zwróconych i opisy elementów są wyrównane z korzystania z tego słowa kluczowego. 

Odwołania poniżej przedstawiono niektóre tagi najczęściej używane na 12/14/2017 r. W niektórych przypadkach istnieją podobne, ale mniej idealne opcje wymienione obok tagu.
Jest najlepszym rozwiązaniem do użycia jako Tag preferowane powoduje mniej szumu i lepsze wyniki wyszukiwania dla konsumentów. 


| **Preferowany tag** | **Alternatywy i uwagi** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration jest mniej pożądana, jest zbyt długa |
| **ResourceManager** | ARM jest używany do opisu grupy procesorów i nie powinna być używana dla usługi Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automatyzacja** |  |
| **REST** |  |
| **ActiveDirectory** | Usługi AD nie jest obecnie używany przez samego siebie  |
| **SQLServer** |  |
| **DBA** |  |
| **Bezpieczeństwo** | Obrony jest mniej dokładne |
| **Bazy danych** | Bazy danych (w liczbie mnogiej) jest mniej pożądana |
| **Opracowywania oprogramowania** |  |
| **Windows** |  |
| **Kompilacji** |  |
| **Wdrożenia** | Wdrażanie jest nieco rzadziej używane |
| **Chmury** |  |
| **GIT** |  |
| **Test** | Testowanie jest mniej pożądana |
| **VersionControl** | Wersja jest mniej dokładne, chociaż często używane  |
| **Logging** | Użyj preferowanych rejestrowania akcji |
| **Dziennik** | Użyj preferowanych dziennika jako element |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Sieci** | Sieć jest podobny, rzadziej używane |
| **SharePoint** |  |
| **Raportowanie** | Zgłoszenie jest akcją, raport należy |
| **Raport** | Raport jest operacją |
| **WinRM** |  |
| **Monitorowanie** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Kolor** |  |
| **DNS** |  |
| **Office365** | Preferowane jest pisownia limit pakietu Office. Usługa Office 365 jest rzadko używane, mimo że krótszą | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Funkcja Hyper-V** | Funkcji Hyper-v jest mniej typowych jako tag |
| **Konfiguracja** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Zapory** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Zazwyczaj używany do modułów AzureRM |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |


