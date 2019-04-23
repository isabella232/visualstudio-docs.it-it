---
title: "Procedura: Esaminare il codice di sistema dopo un'eccezione | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c34b2fdf2b6400ffe88f9e9ff08cbe6e4b41daa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092786"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Procedura: Esaminare il codice di sistema dopo un'eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si verifica un'eccezione, potrebbe essere necessario esaminare il codice di una chiamata al sistema per determinare la causa dell'eccezione. Nella procedura riportata di seguito viene illustrato come determinare la causa se non sono disponibili simboli caricati per il codice di sistema o se Just My Code è attivato.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Per esaminare il codice di sistema dopo un'eccezione  
  
1. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse e quindi fare clic su **Mostra codice esterno**.  
  
     Se Just My Code non è attivato, questa opzione non è disponibile nel menu di scelta rapida e il codice di sistema viene visualizzato per impostazione predefinita.  
  
2. Fare clic con il pulsante destro del mouse sui frame di codice esterni presenti nella finestra **Stack di chiamate**.  
  
3. Selezionare **Carica simboli da** e quindi fare clic su **Server dei simboli Microsoft**.  
  
    1. Se Just My Code è attivato, viene visualizzata una finestra di dialogo indicante che Just My Code è stato disabilitato. Tale operazione è necessaria per eseguire le chiamate di sistema.  
  
    2. Viene visualizzata la finestra di dialogo **Download dei simboli pubblici**. La finestra viene chiusa al termine del download.  
  
4. È ora possibile esaminare il codice di sistema nella finestra **Stack di chiamate** e in altre finestre. Ad esempio, è possibile fare doppio clic su un frame dello stack di chiamate per visualizzare il codice nella finestra **Disassembly** o nella finestra origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)
