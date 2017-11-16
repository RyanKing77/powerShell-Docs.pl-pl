---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a>Raporty dotyczące JEA
Aby zgłosić stanu konfiguracji JEA, można użyć:
1.  **Get-PSSessionConfiguration** zwraca listę wszystkich zarejestrowanych punktów końcowych na danym komputerze.
2.  **Get-PSSessionCapability** raport ma dotyczyć możliwości danego użytkownika ma w określonym punkcie końcowym.

Oto przykład **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Raport ma dotyczyć _akcje_ trwało użytkowników podczas sesji JEA, możesz:
1. Włącz zapisy "over ramię" dla tego punktu końcowego JEA i poszukaj katalogu wykaz pełny dziennik czynności wykonywanych przez użytkownika
2. Włączanie logowania modułu programu PowerShell i sprawdź dzienniki zdarzeń programu PowerShell.

