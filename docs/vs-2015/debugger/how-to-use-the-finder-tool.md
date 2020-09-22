---
title: 'Procedura: utilizzare lo strumento di ricerca | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00535fd336f504afcebdd24a4d009a10f7f6ff33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839856"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: utilizzare lo strumento di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare lo strumento di ricerca nella **finestra di dialogo Trova finestra** per visualizzare le proprietà o i messaggi della finestra. Lo strumento di ricerca può anche individuare le finestre figlio disabilitate e distinguere la finestra da evidenziare se le finestre figlio disabilitate si sovrappongono.  
  
 ![Spy&#43;&#43; trova finestra di dialogo](../debugger/media/icon-spy-find.png "Icon_Spy + + _Find")  
Strumento di ricerca nella finestra di dialogo Trova finestra  
  
 La figura precedente Mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.  
  
### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà o i messaggi della finestra  
  
1. Disporre le finestre in modo che siano visibili sia Spy + + che la finestra di destinazione.  
  
2. Scegliere **Trova finestra**dal menu **Spy** .  
  
     Verrà visualizzata la [finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) .  
  
3. Trascinare lo **strumento di ricerca** sulla finestra di destinazione.  
  
     Quando si trascina lo strumento, nella finestra di dialogo **Trova finestra** vengono visualizzati i dettagli della finestra selezionata.  
  
     - oppure -  
  
     Se si dispone dell'handle della finestra che si desidera esaminare (ad esempio, copiato dal debugger), digitarlo nella casella di testo **handle** .  
  
    > [!TIP]
    > Per ridurre il disordine dello schermo, selezionare l'opzione **Nascondi Spy** . Questa opzione consente di nascondere la finestra principale di Spy + +, lasciando visibile solo la finestra di dialogo **Trova finestra** nella parte superiore delle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic su **OK** o **Annulla**oppure quando si deseleziona l'opzione **Nascondi Spy + +** .  
  
4. In **Mostra**selezionare **Proprietà** o **messaggi**.  
  
5. Fare clic su **OK**.  
  
     Se si seleziona **Proprietà**, viene visualizzata la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) . Se sono stati selezionati **messaggi**, viene visualizzata una finestra [visualizzazione messaggi](../debugger/messages-view.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di Spy + +](../debugger/spy-increment-views.md)   
 [Uso di Spy + +](../debugger/using-spy-increment.md)   
 [Riferimenti per Spy++](../debugger/spy-increment-reference.md)
