---
title: Scheda Generale, finestra di dialogo Proprietà thread | Microsoft Docs
description: Visualizzare la finestra di dialogo Proprietà thread per informazioni su un thread, tra cui il nome del modulo, l'ID thread, l'ID processo, lo stato del thread, il motivo di attesa e il tempo cpu.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 30f5fce8a18ec91419c6c81d8c78527e32fd2cc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090824"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà thread
Usare questa finestra di dialogo per altre informazioni su un thread specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo in una [finestra](../debugger/threads-view.md) Visualizzazione thread oppure aprire [Visualizzazione messaggi](../debugger/messages-view.md) ed espandere un messaggio. Selezionare un nodo di thread nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 La **finestra di dialogo** Proprietà thread contiene un riquadro, la **scheda** Generale. Sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Nome modulo**|Nome del modulo.|
|**Thread ID**|ID univoco di questo thread. Si noti che i numeri ID thread vengono riutilizzati. identificano un thread solo per la durata del thread.|
|**ID processo**|ID univoco di questo processo. I numeri ID processo vengono riutilizzati, quindi identificano un processo solo per la durata del processo. Il tipo di oggetto Process viene creato quando viene eseguito un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati. Scegliere questo valore per visualizzare le proprietà dell'ID processo.|
|**Stato thread**|Stato corrente del thread. Un thread in esecuzione usa un processore. un thread di standby sta per usarne uno. Un thread pronto è in attesa di usare un processore perché non è disponibile. Un thread in Transition è in attesa dell'esecuzione di una risorsa, ad esempio in attesa del paged dello stack di esecuzione dal disco. Un thread in attesa non richiede il processore perché è in attesa del completamento di un'operazione periferica o della disponibilità di una risorsa.|
|**Motivo attesa**|Questa opzione è applicabile solo quando il thread si trova nello stato Wait. Le coppie di eventi vengono usate per comunicare con i sottosistemi protetti.|
|**Tempo CPU**|Tempo cpu totale impiegato per questo processo e i relativi thread. Uguale a Tempo utente + Tempo con privilegi.|
|**Tempo utente**|Tempo totale trascorso dal thread durante l'esecuzione del codice in modalità utente. Le applicazioni vengono eseguite in modalità utente, così come i sottosistemi come gestione finestre e il motore di grafica.|
|**Tempo privilegiato**|Tempo totale trascorso dal thread per l'esecuzione del codice in modalità privilegiata. Quando viene Windows un servizio di sistema, il servizio viene spesso eseguito in modalità privilegiata per ottenere l'accesso ai dati privati del sistema. Tali dati sono protetti dall'accesso da thread in esecuzione in modalità utente. Le chiamate al sistema possono essere esplicite o implicite, ad esempio quando si verifica un errore di pagina o un interrupt.|
|**Tempo trascorso**|Tempo totale trascorso (in secondi) in cui il thread è in esecuzione.|
|**Priorità corrente**|Priorità dinamica corrente di questo thread. I thread all'interno di un processo possono generare e ridurre la propria priorità di base rispetto alla priorità di base del processo.|
|**Priorità di base**|Priorità di base corrente di questo thread.|
|**Indirizzo iniziale**|Indirizzo virtuale iniziale per questo thread.|
|**PC utente**|Contatore del programma utente per il thread.|
|**Cambi di contesto**|Numero di commutatori da un thread a un altro. I commutatori di thread possono verificarsi all'interno di un singolo processo o tra processi. Un cambio di thread può essere causato da un thread che richiede informazioni a un altro thread o da un thread che viene preempted quando un thread con priorità più alta diventa pronto per l'esecuzione.|