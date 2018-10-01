---
title: "Procedura: esaminare il codice di sistema dopo un'eccezione | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c66e77a2e5cc7596bb8473678b84f962453df41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517543"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Procedura: esaminare il codice di sistema dopo un'eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: esaminare codice dopo un'eccezione di sistema](https://docs.microsoft.com/visualstudio/debugger/how-to-examine-system-code-after-an-exception).  
  
Quando si verifica un'eccezione, potrebbe essere necessario esaminare il codice di una chiamata al sistema per determinare la causa dell'eccezione. Nella procedura riportata di seguito viene illustrato come determinare la causa se non sono disponibili simboli caricati per il codice di sistema o se Just My Code è attivato.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Per esaminare il codice di sistema dopo un'eccezione  
  
1.  Nel **Stack di chiamate** finestra destro del mouse e quindi fare clic su **Mostra codice esterno**.  
  
     Se Just My Code non è attivato, questa opzione non è disponibile nel menu di scelta rapida e il codice di sistema viene visualizzato per impostazione predefinita.  
  
2.  Fare doppio clic su frame di codice esterni presenti nella **Stack di chiamate** finestra.  
  
3.  Puntare **Carica simboli da** e quindi fare clic su **server dei simboli Microsoft**.  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo indicante che Just My Code è stato disabilitato. Tale operazione è necessaria per eseguire le chiamate di sistema.  
  
    2.  Il **download dei simboli pubblici** verrà visualizzata la finestra di dialogo. La finestra viene chiusa al termine del download.  
  
4.  È ora possibile esaminare il codice di sistema nel **Stack di chiamate** finestra e altre finestre. Ad esempio, è possibile fare doppio clic su un frame di stack di chiamate per visualizzare il codice in un'origine o **Disassembly** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)





