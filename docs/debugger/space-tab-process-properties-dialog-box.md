---
title: Scheda Spazio, finestra di dialogo Proprietà processo | Microsoft Docs
description: Informazioni su come visualizzare la finestra di dialogo Proprietà processo in Spy++ durante il debug. Esaminare le impostazioni disponibili nella scheda Spazio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce7db03ee93ef0f45f99827d3be27b0ae7df2287
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636603"
---
# <a name="space-tab-process-properties-dialog-box"></a>Scheda Spazio, finestra di dialogo Proprietà processo
Usare la **scheda Spazio** per esaminare lo spazio indirizzi di un processo. Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione](../debugger/processes-view.md) processi. Selezionare un nodo di processo nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Spazio sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Mostra per lo spazio di memoria di tipo**|Usare questa casella di riepilogo per selezionare la categoria di spazio (immagine, mappata, riservata o non assegnata).|
|**Byte eseguibili**|Per la categoria selezionata, la somma di tutto lo spazio indirizzi utilizzato da questo processo. La memoria eseguibile è una memoria che può essere eseguita dai programmi, ma non può essere letta o scritta.|
|**Byte eseguibili sola lettura**|Per la categoria selezionata, la somma di tutto lo spazio indirizzi in uso con le proprietà di sola lettura utilizzate da questo processo. Exec-read-only memory è una memoria che può essere eseguita e letta.|
|**Byte eseguibili lettura/scrittura**|Per la categoria selezionata, la somma di tutto lo spazio indirizzi in uso con le proprietà di lettura/scrittura usate da questo processo. Exec-read-write memory è una memoria che può essere eseguita dai programmi, nonché letta e modificata.|
|**Exec-Write Copy Bytes**|Per la categoria selezionata, la somma di tutto lo spazio indirizzi che può essere eseguito dai programmi, nonché letto e scritto. Questo tipo di protezione viene usato quando la memoria deve essere condivisa tra processi. Se i processi di condivisione leggono solo la memoria, useranno tutti la stessa memoria. Se un processo di condivisione desidera l'accesso in scrittura, verrà creata una copia di questa memoria per il processo.|
|**Byte senza accesso**|Per la categoria selezionata, la somma di tutto lo spazio indirizzi che impedisce a un processo di usarlo. Se si tenta di scrivere o leggere, viene generata una violazione di accesso.|
|**Byte sola lettura**|Per la categoria selezionata, somma di tutto lo spazio indirizzi che può essere eseguito e letto.|
|**Byte di lettura/scrittura**|Per la categoria selezionata, somma di tutto lo spazio indirizzi che consente la lettura e la scrittura.|
|**Byte copia/scrittura**|Per la categoria selezionata, somma di tutto lo spazio indirizzi che consente la condivisione della memoria per la lettura ma non per la scrittura. Quando i processi leggono questa memoria, possono condividere la stessa memoria. Tuttavia, quando un processo di condivisione vuole avere accesso in lettura/scrittura a questa memoria condivisa, viene creata una copia di tale memoria per la scrittura.|