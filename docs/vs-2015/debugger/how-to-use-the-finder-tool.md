---
title: 'Procedura: usare lo strumento di ricerca | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 748ca2cf70e69aa786e8ec02f0d6bee9f6d9d485
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519417"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: utilizzare lo strumento di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: usare lo strumento di ricerca](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-finder-tool).  
  
È possibile usare lo strumento di ricerca nel **Trova finestra** finestra di dialogo per visualizzare le proprietà della finestra o messaggi. Lo strumento di ricerca consente anche di individuare finestre figlio disabilitato e discernere quale finestra per evidenziare se disabilitata finestre figlio si sovrappongono.  
  
 ![Spy&#43; &#43; trovare la finestra di dialogo](../debugger/media/icon-spy-find.png "Icon_Spy + + Find")  
Strumento di ricerca nella finestra di dialogo Trova finestra  
  
 La figura precedente mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.  
  
### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà della finestra o messaggi  
  
1.  Disporre le finestre in modo che sia Spy + + e la finestra di destinazione sono visibili.  
  
2.  Dal **Spy** menu, scegliere **Trova finestra**.  
  
     Il [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) apre.  
  
3.  Trascinare il **strumento di ricerca** nell'intervallo di destinazione.  
  
     Quando si trascina lo strumento, il **Trova finestra** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
     - oppure -  
  
     Se hai l'handle della finestra di cui si vuole esaminare (ad esempio, copiato dal debugger), digitarla nella **gestire** casella di testo.  
  
    > [!TIP]
    >  Per ridurre il disordine schermata, selezionare la **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di mantenere solo le **Trova finestra** nella finestra di dialogo visibile nella parte superiore alle altre applicazioni. La finestra principale di Spy + + è ripristinata quando si fa clic **OK** oppure **Cancel**, o quando si cancella il **Nascondi Spy + +** opzione.  
  
4.  Sotto **mostrano**, selezionare **proprietà** oppure **messaggi**.  
  
5.  Premere **OK**.  
  
     Se è stato selezionato **delle proprietà**, il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) apre. Se è stato selezionato **messaggi**, un [visualizzazione messaggi](../debugger/messages-view.md) verrà visualizzata la finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md)   
 [Utilizzo di Spy + +](../debugger/using-spy-increment.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)



