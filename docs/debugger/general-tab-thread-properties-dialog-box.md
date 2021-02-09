---
title: Scheda generale, finestra di dialogo Proprietà thread | Microsoft Docs
description: Visualizzare la finestra di dialogo Proprietà thread per informazioni su un thread, inclusi nome del modulo, ID thread, ID processo, stato thread, motivo attesa e tempo CPU.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02ba7d14dad8e4755170ffca7853aa9cc6c85a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870545"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà thread
Usare questa finestra di dialogo per trovare altre informazioni su un thread specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo in una finestra [visualizzazione thread](../debugger/threads-view.md) oppure aprire [visualizzazione messaggi](../debugger/messages-view.md) ed espandere un messaggio. Selezionare un nodo thread nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 La finestra di dialogo **Proprietà thread** contiene un riquadro, ovvero la scheda **generale** . Sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Nome del modulo**|Nome del modulo.|
|**ID thread**|ID univoco del thread. Si noti che i numeri ID del thread vengono riutilizzati. identificano un thread solo per la durata del thread.|
|**ID processo**|ID univoco del processo. I numeri ID processo vengono riutilizzati in modo da identificare un processo solo per la durata di tale processo. Il tipo di oggetto processo viene creato durante l'esecuzione di un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati. Scegliere questo valore per visualizzare le proprietà dell'ID del processo.|
|**Stato thread**|Stato corrente del thread. Un thread in esecuzione usa un processore; un thread standby sta per utilizzarne uno. Un thread pronto è in attesa di utilizzare un processore perché uno non è disponibile. Un thread in transizione è in attesa dell'esecuzione di una risorsa, ad esempio in attesa di paging del relativo stack di esecuzione in dal disco. Un thread in attesa non necessita del processore perché è in attesa del completamento di un'operazione di periferica o una risorsa diventa disponibile.|
|**Motivo attesa**|Questa condizione è applicabile solo quando il thread è nello stato di attesa. Le coppie di eventi vengono usate per comunicare con i sottosistemi protetti.|
|**Tempo CPU**|Tempo totale di CPU dedicato a questo processo e ai relativi thread. Uguale all'ora utente + ora privilegiata.|
|**Tempo utente**|Tempo totale trascorso dal thread per l'esecuzione del codice in modalità utente. Le applicazioni vengono eseguite in modalità utente, come i sottosistemi come gestione finestre e il motore di grafica.|
|**Tempo privilegiato**|Tempo totale trascorso utilizzato da questo thread per l'esecuzione di codice in modalità privilegiata. Quando viene chiamato un servizio di sistema Windows, il servizio viene spesso eseguito in modalità privilegiata per accedere ai dati privati del sistema. Tali dati vengono protetti dall'accesso da thread in esecuzione in modalità utente. Le chiamate al sistema possono essere esplicite o implicite, ad esempio quando si verifica un errore di pagina o un interrupt.|
|**Tempo trascorso**|Tempo totale trascorso (in secondi) in cui il thread è stato eseguito.|
|**Priorità corrente**|Priorità dinamica corrente del thread. I thread all'interno di un processo possono aumentare e ridurre la propria priorità di base rispetto alla priorità di base del processo.|
|**Priorità di base**|Priorità di base corrente del thread.|
|**Indirizzo iniziale**|Indirizzo virtuale iniziale per il thread.|
|**PC utente**|Il contatore del programma utente per il thread.|
|**Cambi di contesto**|Numero di opzioni da un thread a un altro. I commutatori di thread possono essere eseguiti all'interno di un singolo processo o tra più processi. Un thread può essere causato da un thread che ne richiede altre per informazioni o da un thread che viene interrotto quando un thread con priorità più alta diventa pronto per l'esecuzione.|