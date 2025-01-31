---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Program PowerShell
title: Wartości manifestu pakietu, które mają wpływ na interfejs użytkownika galerii programu PowerShell
ms.openlocfilehash: cedf81df8de29c54ef559a800d654305029491ec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084712"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Wartości manifestu pakietu, które mają wpływ na interfejs użytkownika galerii programu PowerShell

Ten temat zawiera wydawców podsumowanie informacji na temat sposobu zmodyfikować manifest w swoich publikacjach galerii programu PowerShell, dzięki czemu będzie mieć wpływ na funkcje polecenia cmdlet PowerShellGet i interfejs użytkownika galerii programu PowerShell. Ta zawartość jest posortowana według której zmiana zostanie zastosowana, zaczynając od w górnej części, a następnie w obszarze nawigacyjnym po lewej stronie. Ma sekcji szczegółów obejmujący znaczników, który identyfikuje istotne, tagi, a także niektórych najczęściej używanych tagów. Istnieją dwa tematy, które zawierają przykłady manifestu:

- Dla modułów, zobacz [manifestu modułu aktualizacji](/powershell/module/powershellget/Update-ModuleManifest)
- W przypadku skryptów, zobacz [Tworzenie pliku skryptu z metadanymi](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Galeria programu PowerShell funkcji elementy kontrolowane przez w manifeście

W poniższej tabeli przedstawiono elementy strony pakietu galerii programu PowerShell, interfejsu użytkownika, które są kontrolowane przez wydawcę. Każdy element wskazuje, czy może kontrolowane przez w manifeście modułu lub skryptu.

| Element interfejsu użytkownika | Opis | Moduł | Skrypt |
| --- | --- | --- | --- |
| **Tytuł** | Jest to nazwa pakietu, który jest opublikowany w galerii  | Nie | Nie |
| **Wersja** | Wyświetlana jest wersja ciąg wersji metadanych i wstępnej Jeśli jest określony. Część podstawowej wersji w manifeście modułu jest ModuleVersion. Aby uzyskać skrypt jest identyfikowany jako. Wersja. Jeśli zostanie określony ciąg wersji wstępnej, on dołączany do ModuleVersion dla modułów, lub określony jako część. WERSJA dla skryptów. Brak dokumentacji do określania ciągów wersji wstępnej w [modułów](module-prerelease-support.md), a następnie w [skryptów](script-prerelease-support.md) | Tak | Tak |
| **Opis** | Jest to opis w manifeście modułu, a w manifest pliku skryptu. OPIS ELEMENTU | Tak | Tak |
| **Wymaganie akceptacji licencji** | Moduł może wymagać, że użytkownik akceptuje licencji, modyfikując manifestu modułu RequireLicenseAcceptance = $true, podając LicenseURI i podając pliku license.txt w katalogu głównym folderu modułu. Dodatkowe informacje są dostępne w [wymaga zaakceptowania licencji](../how-to/working-with-packages/packages-that-require-license-acceptance.md) tematu. | Tak | Nie |
| **Informacje o wersji** | Dla modułów te informacje są pobierane z sekcji ReleaseNotes w obszarze PSData\PrivateData. W manifestach skryptu jest. RELEASENOTES element. | Tak | Tak |
| **Właściciele** | Właściciele są listy użytkowników w galerii programu PowerShell, który może zaktualizować pakiet. Listy właścicieli jest niedostępna w manifeście pakietu. Dodatkowa dokumentacja zawiera opis sposobu [Zarządzanie właścicielami elementów](../how-to/publishing-packages/managing-package-owners.md). | Nie | Nie |
| **Autor** | Jest to zawarte w manifeście modułu autor oraz w manifeście jako skrypt. AUTOR. Pola Autor jest często używany do określenia firmy lub organizacji skojarzony z pakietem. | Tak | Tak |
| **Copyright** | Jest to w polu Copyright w manifeście modułu i. COPYRIGHT w manifeście skryptu. | Tak | Tak |
| **FileList** | Lista plików jest rysowana od pakietu, gdy zostanie opublikowany w galerii programu PowerShell. Nie jest kontrolowane przez informacje manifestu. Uwaga: jest plik dodatkowe .nuspec z każdego pakietu w galerii programu PowerShell, który nie jest obecny, po zainstalowaniu pakietu w systemie. To jest manifest pakietu Nuget dla pakietu i mogą być ignorowane. | Nie | Nie |
| **Tagi** | Dla modułów tagi znajdują się w obszarze PSData\PrivateData. W przypadku skryptów jest oznaczona sekcji. TAGI. Należy pamiętać, że tagi nie może zawierać spacji, nawet wtedy, gdy są one w cudzysłowie. Tagi mają dodatkowe wymagania i znaczenie, które są opisane w dalszej części tego tematu w sekcji szczegółów tagu. | Tak | Tak |
| **Polecenia cmdlet** | To jest dostępna w manifeście modułu przy użyciu CmdletsToExport. Należy pamiętać, że najlepszym rozwiązaniem jest jawnie listę elementów, a nie za pomocą symbolu wieloznacznego "*", ponieważ moduł ładowania usprawnić dla użytkowników. | Tak | Nie |
| **Funkcje** | To jest dostępna w manifeście modułu przy użyciu FunctionsToExport. Należy pamiętać, że najlepszym rozwiązaniem jest jawnie listę elementów, a nie za pomocą symbolu wieloznacznego "*", ponieważ moduł ładowania usprawnić dla użytkowników. | Tak | Nie |
| **Zasoby DSC** | Dla modułów, które będą używane w programie PowerShell w wersji 5.0 lub nowszym to jest podawany jako manifest za pomocą DscResourcesToExport. Jeśli moduł jest ma być używany w programie PowerShell 4, DSCResourcesToExport nie należy użyć, ponieważ nie jest obsługiwane klucza manifestu. (DSC nie była dostępna przed 4 programu PowerShell). | Tak | Nie |
| **Przepływy pracy** | Przepływy pracy są publikowane w galerii programu PowerShell jako skrypty i zidentyfikowane jako przepływy pracy (zobacz [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) przykład) w kodzie. To nie są kontrolowane przez manifestu. | Nie | Nie |
| **Możliwości roli** | To będzie wyświetlane, gdy moduł, który został opublikowany w galerii programu PowerShell plikami przynajmniej jednej roli możliwości (.psrc), które są używane przez usługi JEA. Znajdują się w dokumentacji usługi JEA, aby uzyskać więcej informacji na [możliwości roli](/powershell/jea/role-capabilities). | Tak | Nie |
| **Wersje programu PowerShell** | To jest określona w manifeście skryptu lub modułu. Dla modułów, przeznaczony do użycia przy użyciu programu PowerShell w wersji 5.0, a poniżej, jest kontrolowany przy użyciu tagów. Dla komputerów Użyj tagu PSEdition_Desktop i core, można użyć w tagu PSEdition_Core. Dla modułów, które będą używane tylko w programie PowerShell 5.1 i nowszych istnieje klucz CompatiblePSEditions w manifeście głównego. Aby uzyskać dodatkowe szczegóły, zapoznaj się z funkcji wersji PS w [dokumentacji programu PowerShell Get](module-psedition-support.md). | Tak | Tak |
| **Zależności** | Zależności są moduły w galerii programu PowerShell, które są zadeklarowane w module jako RequiredModules lub w manifeście skryptu jako #Requires — moduł (nazwa). | Tak | Tak |
| **Minimalna wersja programu PowerShell** | To może być określona w manifeście modułu jako PowerShellVersion | Tak | Nie |
| **Historia wersji** | Historia wersji odzwierciedla aktualizacje wprowadzone w module w galerii programu PowerShell. Jeśli wersja pakietu jest ukryty za pomocą funkcji usuwania, go nie pojawi się w historii wersji, z wyjątkiem do właścicieli pakietu. | Nie | Nie |
| **Project Site** | Moduły w sekcji Privatedata\PSData manifestu modułu umowy witryny projektu, określając ProjectURI. W manifeście skryptu jest kontrolowana przez określenie. PROJECTURI. | Tak | Tak |
| **Licencja** | Link licencji umowy modułów w sekcji Privatedata\PSData manifestu modułu, określając LicenseURI. W manifeście skryptu jest kontrolowana przez określenie. LICENSEURI. Należy zauważyć, że jeśli licencji nie jest oferowana w ramach LicenseURI lub w module warunków użytkowania dla galerii programu PowerShell Określ warunki użytkowania dla pakietu. Zobacz warunki użytkowania, aby uzyskać szczegółowe informacje. | Tak | Tak |
| **Ikona** | Ikona można określić dla dowolnego pakietu w galerii programu PowerShell, podając wartość IconURI Flaga w manifeście skryptów lub w sekcji Privatedata PSData manifestu modułu. Wartość IconURI powinien wskazywać obraz 32 x 32, przezroczystość tła. Identyfikator URI **musi** być adresem URL obrazu bezpośrednie i **nie** przejdź do strony sieci web zawierającej obraz lub plików w pakiecie galerii programu PowerShell. | Tak | Tak |


## <a name="editing-package-details"></a>Edytowanie szczegółów pakietu

Strona pakietu edytować galerii programu PowerShell umożliwia wydawcy zmienić kilka pól wyświetlanych dla pakietu, w szczególności:

- Title
- Opis
- Podsumowanie
- Adres URL ikony
- Adres URL strony głównej projektu
- Autorzy
- Prawa autorskie
- Znaczniki
- Informacje o wersji
- Wymaga licencji

To podejście jest zwykle niezalecane, z wyjątkiem sytuacji, gdy konieczne Popraw wyświetlanych dla starszej wersji modułu. Użytkownicy, którzy zakupili moduł zobaczą metadanych nie być zgodny z wyświetlanych w galerii programu PowerShell, który wywołuje wątpliwości dotyczące pakietu. Spowoduje to często zapytania, przechodząc do właścicieli pakietu, aby potwierdzić zmiany. Zdecydowanie zaleca się, że każdym razem, gdy ta metoda jest stosowana, nową wersję pakietu powinny być publikowane z tej samej zmiany.

## <a name="tag-details"></a>Szczegóły tagu

Tagi są zwykłe ciągi odbiorcy Użyj, aby wyszukiwać pakiety. Tagi są najbardziej przydatne, gdy są stosowane konsekwentnie w wielu pakietach związane z tym samym temacie. Za pomocą wiele wersji tego samego programu word (na przykład bazy danych i baz danych, lub testów i testowania) zwykle zapewnia niewielkie korzyści. Tagi są jednowyrazowej ciągów bez uwzględniania wielkości liter i nie może zawierać spacji. W przypadku frazy, które uważasz, że użytkownicy będą wyszukiwać, dodaj ją do opisu pakietu i będzie można znaleźć w wynikach wyszukiwania. Użyj Pascal wielkość liter w wyrazie, łącznik, podkreślenie lub okres, jeśli próbujesz w celu poprawienia czytelności.
Należy zachować ostrożność w przypadku tworzenia tagów długie, złożone i nietypowe, ponieważ są one często błędna.

Istnieją znaczniki, które są pamiętać, galerii programu PowerShell oraz PowerShellGet poleceń cmdlet je traktować unikatowo. PSEdition_Desktop PSEdition_Core są konkretne przykłady i opisanych powyżej.

Jak wspomniano powyżej, tagi zapewniają najbardziej wartości, gdy są określone i używany konsekwentnie w wielu pakietach. Jako wydawca próbuje zlokalizować najlepsze tagów do użycia to najłatwiejsza metoda jest wyszukiwanie w galerii programu PowerShell dla tagów, które zamierzasz. W idealnym przypadku będzie istnieć wiele pakietów zwracane i opisy pakietu zostaną wyrównane z użyciem tego słowa kluczowego.

Odwołanie poniżej przedstawiono niektóre najczęściej używanych tagi, począwszy od 12/14/2017. W niektórych przypadkach są podobne, ale może być mniej idealne opcje wymienione na liście obok znacznikiem. Jest najlepszym rozwiązaniem jest używany Tag preferowane jako skutkować mniejszą hałasu i lepsze wyniki wyszukiwania dla konsumentów.

| Preferowany tagu | Alternatywy i uwagi |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration jest mniej pożądana, jest za długa |
| ResourceManager | Służy do opisywania grupy procesorów ARM i nie powinny być używane dla usługi Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatyzacja |  |
| REST |  |
| Polecenie cmdlet | Usługi AD nie jest obecnie używany przez siebie  |
| SQLServer |  |
| DBA |  |
| Bezpieczeństwo | Ochrona jest mniej dokładny |
| Baza danych | Bazy danych (liczba mnoga) jest mniej pożądana |
| DevOps |  |
| Windows |  |
| Kompilacja |  |
| Wdrażanie | Wdrażanie jest nieco mniej często używane |
| Chmura |  |
| GIT |  |
| Test | Testowanie jest mniej pożądana |
| VersionControl | Wersja jest mniej dokładne, mimo że częściej używane  |
| Rejestrowanie | Użyj preferowanych rejestrowania akcji |
| Log | Preferowany korzystanie z dziennika jako rzeczy |
| Kopia zapasowa |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Magazyn |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Sieć | Sieć jest podobny, rzadziej używane |
| Program SharePoint |  |
| Raportowanie | Raportowanie jest akcja, jest to raport |
| Raport | Jest to raport |
| WinRM |  |
| Monitorowanie |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Kolor |  |
| DNS |  |
| Office365 | Preferowane jest pisownia się pakietu Office. Usługi Office 365 jest rzadko używane, ale krótszy |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Funkcja Hyper-V | Funkcji Hyper-v jest mniej typowe jako tag |
| Konfiguracja |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Zapora |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Zazwyczaj używany do modułów AzureRM |
| ZIP |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
