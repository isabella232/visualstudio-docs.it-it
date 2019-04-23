---
title: 'Procedura: Usare lo strumento di ricerca | Microsoft Docs'
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
ms.openlocfilehash: c14fdcc5d58c62eebf993ba336a109adac5b7106
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053767"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: Usare lo strumento di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare lo strumento di ricerca nel **Trova finestra** finestra di dialogo per visualizzare le proprietà della finestra o messaggi. Lo strumento di ricerca consente anche di individuare finestre figlio disabilitato e discernere quale finestra per evidenziare se disabilitata finestre figlio si sovrappongono.  
  
 ![Spy&#43; &#43; trovare la finestra di dialogo](../debugger/media/icon-spy-find.png "Icon_Spy + + Find")  
Strumento di ricerca nella finestra di dialogo Trova finestra  
  
 La figura precedente mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.  
  
### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà della finestra o messaggi  
  
1. Disporre le finestre in modo che sia Spy + + e la finestra di destinazione sono visibili.  
  
2. Dal **Spy** menu, scegliere **Trova finestra**.  
  
     Il [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) apre.  
  
3. Trascinare il **strumento di ricerca** nell'intervallo di destinazione.  
  
     Quando si trascina lo strumento, il **Trova finestra** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
     - oppure -  
  
     Se hai l'handle della finestra di cui si vuole esaminare (ad esempio, copiato dal debugger), digitarla nella **gestire** casella di testo.  
  
    > [!TIP]
    >  Per ridurre il disordine schermata, selezionare la **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di mantenere solo le **Trova finestra** nella finestra di dialogo visibile nella parte superiore alle altre applicazioni. La finestra principale di Spy + + è ripristinata quando si fa clic **OK** oppure **Cancel**, o quando si cancella il **Nascondi Spy + +** opzione.  
  
4. Sotto **mostrano**, selezionare **proprietà** oppure **messaggi**.  
  
5. Fare clic su **OK**.  
  
     Se è stato selezionato **delle proprietà**, il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) apre. Se è stato selezionato **messaggi**, un [visualizzazione messaggi](../debugger/messages-view.md) verrà visualizzata la finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)   
 [Uso di Spy++](../debugger/using-spy-increment.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)
