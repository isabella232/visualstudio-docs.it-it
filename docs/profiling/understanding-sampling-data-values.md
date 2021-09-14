---
title: Informazioni sui valori dei dati di campionamento | Microsoft Docs
description: Informazioni su come il metodo di profilatura di campionamento Visual Studio Strumenti di profilatura interrompe il processore del computer a intervalli impostati e raccoglie lo stack di chiamate di funzione.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 04ff212cce0de1faa07cd31e115346de98e44f0e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710173"
---
# <a name="understand-sampling-data-values"></a>Informazioni sui valori dei dati di campionamento

Il metodo di profilatura di *campionamento* degli strumenti di profilatura di Visual Studio interrompe il processore del computer a intervalli prestabiliti e raccoglie lo stack di chiamate della funzione. Lo *stack di chiamate* è una struttura dinamica che archivia informazioni sulle funzioni in esecuzione nel processore.

L'analisi del profiler determina se il processore esegue codice nel processo di destinazione. Se il processore non esegue codice nel processo di destinazione, il campione viene ignorato.

Se il processore esegue il codice di destinazione, il profiler incrementa i conteggi dei campioni per ogni funzione nello stack di chiamate. Nel momento in cui viene acquisito il campione, una sola funzione nello stack di chiamate esegue codice. Le altre funzioni nello stack sono elementi padre nella gerarchia delle chiamate di funzioni che sono in attesa dei valori restituiti dalle relative funzioni figlio.

Per l'evento di campionamento, il profiler incrementa il conteggio dei campioni *esclusivi* della funzione che sta attualmente eseguendo le proprie istruzioni. Dato che un campione esclusivo fa anche parte del totale (*inclusivo*) dei campioni della funzione, viene incrementato anche il conteggio dei campioni inclusivi della funzione attiva.

 Il profiler incrementa il numero di campioni inclusivi di tutte le altre funzioni nello stack di chiamate.

## <a name="inclusive-samples"></a>Campioni inclusivi

Numero totale di campioni raccolti durante l'esecuzione della funzione di destinazione.

Sono inclusi campioni raccolti durante l'esecuzione diretta del codice della funzione e campioni raccolti durante l'esecuzione delle funzioni figlio chiamate dalla funzione di destinazione.

## <a name="exclusive-samples"></a>Campioni esclusivi

Numero di campioni raccolti durante l'esecuzione diretta delle istruzioni della funzione di destinazione.

Nei campioni esclusivi non sono compresi i campioni raccolti durante l'esecuzione delle funzioni chiamate dalla funzione di destinazione.

## <a name="inclusive-percent"></a>% inclusivi

Percentuale del numero totale di campioni inclusivi nell'esecuzione della profilatura che sono campioni inclusivi della funzione o dell'intervallo di dati.

## <a name="exclusive-percent"></a>% esclusivi

Percentuale del numero totale di campioni esclusivi nell'esecuzione della profilatura che sono campioni esclusivi della funzione o dell'intervallo di dati.

## <a name="see-also"></a>Vedi anche

[Procedura: Scegliere i metodi di raccolta](../profiling/how-to-choose-collection-methods.md) 
 [Analizzare i dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
