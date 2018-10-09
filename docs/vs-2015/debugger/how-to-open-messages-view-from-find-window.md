---
title: 'Procedura: aprire la visualizzazione messaggi dalla finestra Trova | Microsoft Docs'
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
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b847124ff6be20f91827d2ec3fc311d5cd48ece2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528759"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedura: aprire la visualizzazione messaggi dalla finestra Trova
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: aprire la visualizzazione messaggi dalla finestra Trova](https://docs.microsoft.com/visualstudio/debugger/how-to-open-messages-view-from-find-window).  
  
Può risultare comodo usare la **Trova finestra** finestra di dialogo per selezionare una finestra di destinazione e quindi aprire una visualizzazione di messaggi di tale finestra.  
  
### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Per aprire una finestra di visualizzazione dei messaggi tramite la finestra di dialogo Trova finestra  
  
1.  Disporre le finestre in modo che sia Spy + + e la finestra di destinazione sono visibili.  
  
2.  Dal **Spy** menu, scegliere **Trova finestra**.  
  
     Il [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) apre.  
  
3.  Dal **Windows** scheda, trascinare le **strumento di ricerca** nell'intervallo di destinazione. Quando si trascina lo strumento, il **Trova finestra** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
     - oppure -  
  
     Se hai l'handle della finestra di cui si vuole esaminare (ad esempio, copiato dal debugger), è possibile digitare nel **gestire** casella di testo.  
  
4.  Sotto **mostrare**, selezionare **messaggi**.  
  
5.  Premere **OK**.  
  
     Uno spazio vuoto [visualizzazione messaggi](../debugger/messages-view.md) viene visualizzata una finestra e un **messaggi** menu viene aggiunto alla barra degli strumenti di Spy + +.  
  
6.  Dal **messaggi** menu, scegliere **opzioni di registrazione**.  
  
     Il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) apre.  
  
7.  Selezionare le opzioni per i messaggi che si desidera visualizzare.  
  
8.  Premere **OK** per avviare la registrazione messaggi.  
  
     A seconda delle opzioni selezionate, i messaggi di avviare lo streaming nella finestra di visualizzazione di messaggi attiva.  
  
9. Quando si dispone di messaggi sufficiente, scegliere **Arresta registrazione** dalle **messaggi** menu.


