---
title: Scheda generale, finestra di dialogo Proprietà processo | Microsoft Docs
description: Visualizzare la scheda generale per informazioni su un processo, inclusi nome del modulo, ID processo, priorità di base, conteggio thread, tempo CPU, tempo utente e tempo trascorso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4980437c63348050db1a007e8f541e9af9e186cc
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862737"
---
# <a name="general-tab-process-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà processo
Utilizzare la scheda **generale** per ottenere ulteriori informazioni su un processo specifico. Per visualizzare la finestra di [dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo in una finestra [visualizzazione processi](../debugger/processes-view.md) . Selezionare un nodo di processo nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **generale** sono disponibili le impostazioni seguenti:

|Voce|Description|
|-----------|-----------------|
|**Nome del modulo**|Nome del modulo.|
|**ID processo**|ID univoco del processo. I numeri ID processo vengono riutilizzati in modo da identificare un processo solo per la durata di tale processo. Il tipo di oggetto processo viene creato durante l'esecuzione di un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati.|
|**Priorità di base**|Priorità di base corrente del processo. I thread all'interno di un processo possono aumentare e ridurre la propria priorità di base rispetto alla priorità di base del processo.|
|**Thread**|Il numero di thread attualmente attivi nel processo corrente.|
|**Tempo CPU**|Tempo totale di CPU dedicato a questo processo e ai relativi thread. Uguale all'ora utente più il tempo privilegiato.|
|**Tempo utente**|Tempo cumulativo trascorso per il quale i thread del processo hanno impiegato l'esecuzione di codice in modalità utente nei thread non inattivi. Le applicazioni vengono eseguite in modalità utente, come i sottosistemi, ad esempio Gestione finestre e il motore di grafica.|
|**Tempo privilegiato**|Tempo totale trascorso in cui il processo è stato eseguito in modalità privilegiata nei thread non inattivi. Il livello di servizio, le routine esecutive e il kernel vengono eseguiti in modalità privilegiata. I driver di dispositivo per la maggior parte dei dispositivi diversi dalle schede grafiche e dalle stampanti vengono eseguiti anche in modalità privilegiata. Alcune operazioni eseguite da Windows per l'applicazione possono essere visualizzate in altri processi di sottosistema oltre al tempo privilegiato.|
|**Tempo trascorso**|Tempo totale trascorso per l'esecuzione del processo.|