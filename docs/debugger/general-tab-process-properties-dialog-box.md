---
title: Scheda Generale, finestra di dialogo Proprietà processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52822d3cc503c948c7c1fdc320d850d9e1f84ec6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927048"
---
# <a name="general-tab-process-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà processo
Usare la **generale** pressione di tab per altre informazioni su un processo specifico. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **generale** scheda:  
  
|Voce|Description|  
|-----------|-----------------|  
|**Nome modulo**|Nome del modulo.|  
|**ID processo**|ID univoco di questo processo. Numeri di ID di processo vengono riutilizzati e identificano un processo solo per la durata del processo stesso. Il tipo di oggetto processo viene creato quando viene eseguito un programma. Tutti i thread in un processo di condividono lo stesso spazio degli indirizzi e abbiano accesso agli stessi dati.|  
|**Priorità di base**|La priorità di base corrente di questo processo. Thread all'interno di un processo può aumentare e ridurre le proprie priorità di base relativo alla priorità di base del processo.|  
|**Thread**|Il numero di thread attualmente attivi nel processo corrente.|  
|**Tempo CPU**|Tempo CPU totale impiegato per il processo e thread. Uguale all'ora di utenti più tempo privilegiato.|  
|**Tempo utente**|Tempo trascorso totale thread del processo hanno impiegato dal codice in esecuzione in modalità utente thread non inattivi. Le applicazioni vengono eseguiti in modalità utente, i sottosistemi, ad esempio la gestione finestre e il motore della grafica.|  
|**Tempo privilegiato**|Il tempo totale trascorso questo processo è stato in esecuzione in modalità privilegiata in thread non inattivi. Il livello di servizio, le routine e il Kernel di eseguire in modalità privilegiata. Driver di dispositivo per la maggior parte dei dispositivi diversi da schede video grafiche e le stampanti eseguire anche in modalità privilegiata. Alcune operazioni che esegue Windows per l'applicazione possono apparire in altri processi di sottosistema oltre a tempo privilegiato.|  
|**Tempo trascorso**|Il tempo totale trascorso che questo processo è in esecuzione.|