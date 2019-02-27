---
title: Dodawanie programu Windows PowerShell działań do przybornika programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852108"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Dodawanie działań programu Windows PowerShell do przybornika programu Visual Studio

Przed utworzeniem przepływu pracy programu PowerShell za pomocą projektanta przepływów pracy, należy najpierw dodać działania programu PowerShell do przybornika w przepływ pracy programu Visual Studio projekt aplikacji konsoli. Poniższa procedura pokazuje, jak dodać działania z zestawu Microsoft.PowerShell.Core.Activities do przybornika Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Dodawanie programu Windows PowerShell działań do przybornika

1. Utwórz nowy projekt aplikacji konsoli przepływu pracy w programie Visual Studio.

2. Na **widoku** menu, kliknij przycisk **przybornika**.

3. Dodaj nową kartę w przyborniku kliknij prawym przyciskiem myszy w przyborniku, a następnie klikając polecenie **Dodaj zakładkę**i nazwij nową kartę takich jak "Działania programu PowerShell".

   Dodawanie karty pozwala grupować oddzielnie od innych narzędzi w przyborniku działań programu PowerShell.

4. Na nowej karcie przybornika, kliknij przycisk **wybierz elementy...** . **Wybierz elementy przybornika** zostanie wyświetlone okno dialogowe.

5. W **wybierz elementy przybornika** okno dialogowe, kliknij przycisk **System.Activities** kartę.

6. Kliknij przycisk **Przeglądaj**.

7. Przejdź do folderu %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, a następnie kliknij dwukrotnie Microsoft.PowerShell.Core.Activities.dll.

8. Kliknij przycisk **OK**. Działania zdefiniowane przez zestaw Microsoft.PowerShell.Core.Activities są teraz dostępne w przyborniku.

## <a name="see-also"></a>Zobacz też

[Pisanie przepływu pracy środowiska Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Tworzenie przepływu pracy za pomocą programu Windows PowerShell działań](./creating-a-workflow-with-windows-powershell-activities.md)