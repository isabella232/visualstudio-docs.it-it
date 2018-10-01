---
title: Scheda messaggi, finestra di dialogo Opzioni messaggio | Microsoft Docs
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
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8048c63ed9b9f049ed171002dfcc612fc9361569
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528515"
---
# <a name="messages-tab-message-options-dialog-box"></a>Scheda Messaggi, Finestra di dialogo Opzioni messaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [scheda dei messaggi, finestra di dialogo Opzioni messaggio](https://docs.microsoft.com/visualstudio/debugger/messages-tab-message-options-dialog-box).  
  
Usare la **messaggi** pressione di tab per selezionare quali tipi di elenco nel messaggio [visualizzazione messaggi](../debugger/messages-view.md)e per specificare i criteri di ricerca di messaggi. Per visualizzare il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **i messaggi di Log** dal **Spy** menu.  
  
 In genere, si seleziona innanzitutto **gruppi di messaggi**e quindi ottimizzare la selezione selezionando singoli **dei messaggi alla visualizzazione**. Il **tutte** pulsante Seleziona tutti i tipi di messaggio e il **None** pulsante Cancella tutti i tipi.  
  
 Le impostazioni seguenti sono disponibili sul **messaggi** scheda:  
  
 **Messaggi alla visualizzazione**  
 Selezionare i messaggi specifici per la visualizzazione. Quando si crea una nuova finestra dei messaggi, è possibile visualizzare tutti i messaggi. Quando si filtrano i messaggi dal **messaggi** scheda, tale filtro si applica solo ai nuovi messaggi, non a quelli che sono già stati visualizzati nella visualizzazione di Windows.  
  
 **Gruppi di messaggi**  
 Selezionare i gruppi di messaggi per la visualizzazione. Gruppi disponibili includono:  
  
-   WM_USER: con un codice maggiore di o uguale a WM_USER  
  
-   Registrato: registrato con il **RegisterWindowMessage** chiamare  
  
-   Sconosciuto: messaggi sconosciuti nell'intervallo da 0 a (WM_USER – 1)  
  
 Si noti che questi **gruppi di messaggi** non eseguono il mapping alle voci specifiche sotto **messaggi da visualizzare**. Quando si seleziona un gruppo, la selezione viene applicata direttamente al flusso di messaggi.  
  
 All'interno di una casella di controllo disabilitata **gruppi di messaggi** indica che il **messaggi da visualizzare** casella di riepilogo è stata modificata per i messaggi in tale gruppo; non tutti i tipi di messaggio in tale gruppo vengono selezionati.  
  
 **Salvare le impostazioni come predefinito**  
 Salvare le impostazioni correnti per un utilizzo successivo come le opzioni di ricerca di messaggi. Queste impostazioni vengono salvate anche quando si esce da Spy + +.



