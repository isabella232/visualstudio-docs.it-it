---
title: Scheda Generale, finestra di dialogo Proprietà processo | Microsoft Docs
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
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5043d5250c6ce26807379d6cef25077480dbc344
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531884"
---
# <a name="general-tab-process-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [scheda Generale, finestra di dialogo Proprietà processo](https://docs.microsoft.com/visualstudio/debugger/general-tab-process-properties-dialog-box).  
  
Usare la **generale** pressione di tab per altre informazioni su un processo specifico. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **generale** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome modulo**|Nome del modulo.|  
|**ID processo**|ID univoco di questo processo. Numeri di ID di processo vengono riutilizzati e identificano un processo solo per la durata del processo stesso. Il tipo di oggetto processo viene creato quando viene eseguito un programma. Tutti i thread in un processo di condividono lo stesso spazio degli indirizzi e abbiano accesso agli stessi dati.|  
|**Priorità di Base**|La priorità di base corrente di questo processo. Thread all'interno di un processo può aumentare e ridurre le proprie priorità di base relativo alla priorità di base del processo.|  
|**Thread**|Il numero di thread attualmente attivi nel processo corrente.|  
|**Tempo di CPU**|Tempo CPU totale impiegato per il processo e thread. Uguale all'ora di utenti più tempo privilegiato.|  
|**Tempo utente**|Tempo trascorso totale thread del processo hanno impiegato dal codice in esecuzione in modalità utente thread non inattivi. Le applicazioni vengono eseguiti in modalità utente, i sottosistemi, ad esempio la gestione finestre e il motore della grafica.|  
|**Tempo privilegiato**|Il tempo totale trascorso questo processo è stato in esecuzione in modalità privilegiata in thread non inattivi. Il livello di servizio, le routine e il Kernel di eseguire in modalità privilegiata. Driver di dispositivo per la maggior parte dei dispositivi diversi da schede video grafiche e le stampanti eseguire anche in modalità privilegiata. Alcune operazioni che esegue Windows per l'applicazione possono apparire in altri processi di sottosistema oltre a tempo privilegiato.|  
|**Tempo trascorso**|Il tempo totale trascorso che questo processo è in esecuzione.|


