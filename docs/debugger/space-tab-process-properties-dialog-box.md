---
title: Scheda spazio, finestra di dialogo Proprietà processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 563d54c39b4d9ce3bb2d76a9e531161c2c4ee5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929813"
---
# <a name="space-tab-process-properties-dialog-box"></a>Scheda Spazio, finestra di dialogo Proprietà processo
Utilizzare la scheda **spazio** per esaminare lo spazio degli indirizzi di un processo. Per visualizzare la finestra di [dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo in una finestra [visualizzazione processi](../debugger/processes-view.md) . Selezionare un nodo di processo nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **spazio** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Mostra per lo spazio di memoria di tipo**|Usare questa casella di riepilogo per selezionare la categoria di spazio (immagine, mappata, riservata o non assegnata).|
|**Byte eseguibili**|Per la categoria selezionata, somma di tutti gli spazi degli indirizzi utilizzati da questo processo. La memoria eseguibile è memoria che può essere eseguita dai programmi, ma non può essere letta o scritta.|
|**Byte eseguibili sola lettura**|Per la categoria selezionata, somma di tutto lo spazio degli indirizzi utilizzato con proprietà di sola lettura utilizzate da questo processo. Exec: la memoria di sola lettura è memoria che può essere eseguita e letta.|
|**Byte eseguibili lettura/scrittura**|Per la categoria selezionata, somma di tutti gli spazi di indirizzi usati con le proprietà di lettura/scrittura utilizzate da questo processo. La memoria Exec-Read-Write è memoria che può essere eseguita da programmi, nonché da lettura e modifica.|
|**Exec-scrittura byte copia**|Per la categoria selezionata, somma di tutto lo spazio di indirizzi che può essere eseguito da programmi, nonché da lettura e scrittura. Questo tipo di protezione viene utilizzato quando la memoria deve essere condivisa tra i processi. Se i processi di condivisione leggono solo la memoria, tutti utilizzeranno la stessa memoria. Se un processo di condivisione desidera l'accesso in scrittura, verrà creata una copia della memoria per il processo.|
|**Byte senza accesso**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi che impedisce a un processo di utilizzarla. Se si tenta di scrivere o leggere, viene generata una violazione di accesso.|
|**Byte sola lettura**|Per la categoria selezionata, somma di tutti gli spazi di indirizzi che possono essere eseguiti e letti.|
|**Byte lettura/scrittura**|Per la categoria selezionata, somma di tutto lo spazio di indirizzi che consente la lettura e la scrittura.|
|**Byte copia/scrittura**|Per la categoria selezionata, somma di tutto lo spazio di indirizzi che consente la condivisione della memoria per la lettura, ma non per la scrittura. Quando i processi leggono questa memoria, possono condividere la stessa memoria. Tuttavia, quando un processo di condivisione vuole avere accesso in lettura/scrittura a questa memoria condivisa, viene creata una copia di tale memoria per la scrittura.|