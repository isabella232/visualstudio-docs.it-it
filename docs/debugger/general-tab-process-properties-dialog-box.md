---
title: Scheda Generale, finestra di dialogo Proprietà processo | Microsoft Docs
description: Visualizzare la scheda Generale per informazioni su un processo, tra cui il nome del modulo, l'ID processo, la priorità di base, il numero di thread, il tempo cpu, il tempo utente e il tempo trascorso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e50cffecb1ef12373e8a6774efebf832aebaa9b61fdc362657474028acdb7cc9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391395"
---
# <a name="general-tab-process-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà processo
Usare la **scheda** Generale per altre informazioni su un processo specifico. Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione](../debugger/processes-view.md) processi. Selezionare un nodo di processo nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Generale sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Nome modulo**|Nome del modulo.|
|**ID processo**|ID univoco di questo processo. I numeri ID processo vengono riutilizzati, quindi identificano un processo solo per la durata del processo. Il tipo di oggetto Process viene creato quando viene eseguito un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati.|
|**Priorità di base**|Priorità di base corrente di questo processo. I thread all'interno di un processo possono generare e ridurre la propria priorità di base rispetto alla priorità di base del processo.|
|**Thread**|Il numero di thread attualmente attivi nel processo corrente.|
|**Tempo CPU**|Tempo cpu totale impiegato per questo processo e i relativi thread. Uguale a User Time (Tempo utente) e Privileged Time (Tempo con privilegi).|
|**Tempo utente**|Tempo cumulativo trascorso che i thread di questo processo hanno dedicato all'esecuzione di codice in modalità utente in thread non inattivi. Le applicazioni vengono eseguite in modalità utente, così come i sottosistemi, ad esempio gestione finestre e motore di grafica.|
|**Tempo privilegiato**|Tempo totale trascorso in cui questo processo è stato eseguito in modalità privilegiata in thread non inattivi. Il livello di servizio, le routine Executive e il kernel vengono eseguiti in modalità privilegiata. I driver di dispositivo per la maggior parte dei dispositivi diversi da schede grafiche e stampanti vengono eseguiti anche in modalità privilegiata. Alcune operazioni che Windows per l'applicazione possono essere visualizzate in altri processi del sottosistema oltre a Privileged Time.|
|**Tempo trascorso**|Tempo totale trascorso durante l'esecuzione del processo.|