---
title: Visualizzazione Durata oggetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d4ea486930d0ea9f266b4ee57b69a50f7c570651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772624"
---
# <a name="object-lifetime-view"></a>Visualizzazione Durata oggetti
La visualizzazione Durata oggetti è disponibile quando anche raccogliere i dati sulla durata degli **oggetti .NET** viene controllato nelle pagine delle proprietà **sessione di prestazioni.**

 Il Garbage Collector di .NET Framework gestisce l'allocazione e il rilascio di memoria per l'applicazione. Per ottimizzare le prestazioni del Garbage Collector, l'heap gestito è diviso in tre generazioni: 0, 1 e 2. Il Garbage Collector del runtime archivia i nuovi oggetti nella generazione 0. Gli oggetti non raccolti vengono promossi e archiviati nelle generazioni 1 e 2.

 Il Garbage Collector recupera memoria tramite la deallocazione di un'intera generazione di oggetti. Per gli oggetti creati dall'applicazione sottoposta a profilatura, la visualizzazione Durata oggetti mostra il numero e le dimensioni degli oggetti e la generazione in cui vengono recuperati.

## <a name="general"></a>Generale

|Colonna|Descrizione|
|------------|-----------------|
|**Nome della classe**|Nome della classe del tipo allocato.|
|**ID di processo**|ID di processo dell'esecuzione della profilatura.|
|**Process Name**|Nome del processo.|
|**Nome del modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|

## <a name="instance-data"></a>Dati dell'istanza
 Questi dati indicano il numero di oggetti del tipo creati durante l'esecuzione della profilatura e la generazione in cui gli oggetti sono stati deallocati dal Garbage Collector.

|Colonna|Descrizione|
|------------|-----------------|
|**Istanze**|Numero di allocazioni di oggetti di questo tipo.|
|**% istanze totali**|Percentuale del numero totale di allocazioni effettuate durante l'esecuzione della profilatura.|
|**Istanze di generazione 0 raccolte**|Numero di istanze del tipo deallocate nella generazione 0 dell'algoritmo di Garbage Collection.|
|**Istanze di generazione 1 raccolte**|Numero di istanze del tipo deallocate nella generazione 1 dell'algoritmo di Garbage Collection.|
|**Istanze di generazione 2 raccolte**|Numero di istanze del tipo deallocate nella generazione 2 dell'algoritmo di Garbage Collection.|
|**Istanze attive alla fine**|Numero di istanze del tipo che non sono state deallocate fino alla fine dell'esecuzione della profilatura.|

## <a name="size-byte-data"></a>Dati per le dimensioni (byte)
 Questi dati indicano le dimensioni degli oggetti del tipo creati durante l'esecuzione della profilatura e la quantità di memoria recuperata in ogni generazione in cui gli oggetti sono stati deallocati.

|Colonna|Descrizione|
|------------|-----------------|
|**Totale byte allocati**|Numero totale di byte per tutte le istanze del tipo.|
|**% byte totali**|Percentuale del numero totale di byte allocati nell'esecuzione della profilatura per le istanze di questo tipo.|
|**Byte di generazione 0 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 0 dell'algoritmo di Garbage Collection.|
|**Byte di generazione 1 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 1 dell'algoritmo di Garbage Collection.|
|**Byte di generazione 2 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 2 dell'algoritmo di Garbage Collection.|

## <a name="large-object-heap-data"></a>Dati per l'heap degli oggetti grandi
 L'allocatore di memoria .NET gestisce gli oggetti molto grandi in una posizione separata dall'heap gestito standard. I dati per l'heap degli oggetti grandi indicano il numero e le dimensioni degli oggetti del tipo che sono stati gestiti in questa posizione.

|Colonna|Descrizione|
|------------|-----------------|
|**Istanze di heap oggetti grandi raccolte**|Numero di istanze di questo tipo posizionate nell'heap degli oggetti grandi e raccolte durante l'esecuzione della profilatura.|
|**Byte di heap oggetti grandi raccolti**|Dimensioni in byte delle istanze di questo tipo posizionate nell'heap degli oggetti grandi e raccolte durante l'esecuzione della profilatura.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
