---
title: Scheda Generale, finestra di dialogo proprietà Thread | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26eed1eb9d40fe78de34512f9e560ca59c19df12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307703"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare questa finestra di dialogo per ottenere ulteriori informazioni su un thread specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo a un [visualizzazione thread](../debugger/threads-view.md) finestra, oppure aprire [visualizzazione messaggi](../debugger/messages-view.md) ed espandere un messaggio. Selezionare qualsiasi nodo di thread nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Il **Thread Properties** finestra di dialogo contiene un riquadro, il **generali** scheda. Sono disponibili le seguenti impostazioni:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome modulo**|Nome del modulo.|  
|**ID thread**|ID univoco di questo thread. Si noti che i numeri di ID thread vengono riutilizzati; consentono di identificare un thread solo per la durata del thread in questione.|  
|**ID processo**|ID univoco di questo processo. Numeri di ID di processo vengono riutilizzati e identificano un processo solo per la durata del processo stesso. Il tipo di oggetto processo viene creato quando viene eseguito un programma. Tutti i thread in un processo di condividono lo stesso spazio degli indirizzi e abbiano accesso agli stessi dati. Scegliere questo valore per visualizzare le proprietà dell'ID del processo.|  
|**Lo stato del thread**|Lo stato corrente del thread. Un thread in esecuzione con un processore; un thread di Standby è circa di usarne uno. È in attesa di un Thread pronto per utilizzare un processore in quanto non è disponibile. Un thread in fase di transizione è in attesa di una risorsa da eseguire, ad esempio in attesa dello stack di esecuzione venga paginato dal disco. Un thread in attesa, il processore non è necessario perché è in attesa di completare un'operazione esterna o una risorsa venga resa disponibile.|  
|**Motivo attesa**|Questa opzione è disponibile solo quando il thread è nello stato di attesa. Coppie di eventi vengono utilizzate per comunicare con i sottosistemi protetti.|  
|**Tempo di CPU**|Tempo CPU totale impiegato per il processo e thread. Uguale all'utente ora + tempo privilegiato.|  
|**Tempo utente**|Tempo trascorso totale che questo thread ha impiegato nell'esecuzione del codice in modalità utente. Le applicazioni vengono eseguiti in modalità utente, i sottosistemi, ad esempio la gestione finestre e il motore della grafica.|  
|**Tempo privilegiato**|Tempo trascorso totale che questo thread ha impiegato nell'esecuzione del codice in modalità privilegiata. Quando viene chiamato un servizio di sistema di Windows, il servizio verrà eseguito spesso in modalità privilegiata per accedere ai dati privati di sistema. Tali dati sono protetti dall'accesso dal thread in esecuzione in modalità utente. Chiamate al sistema possono essere esplicite o implicite, ad esempio quando si verifica un errore di pagina o un interrupt.|  
|**Tempo trascorso**|Il tempo totale trascorso, in secondi, il thread è in esecuzione.|  
|**Priorità corrente**|La priorità dinamica corrente di questo thread. Thread all'interno di un processo può aumentare e ridurre le proprie priorità di base rispetto alla priorità di base del processo.|  
|**Priorità di base**|La priorità di base corrente di questo thread.|  
|**Indirizzo iniziale**|Indirizzo virtuale iniziale per questo thread.|  
|**PC utente**|Il contatore di programma utente per il thread.|  
|**Cambi di contesto**|Il numero di opzioni da un thread a altro. Switch di thread può verificarsi all'interno di un singolo processo o tra processi. Un commutatore di thread potrebbe essere causato da un thread di richiesta di informazioni o da un thread quando un thread con priorità maggiore diventa pronto per l'esecuzione.|



