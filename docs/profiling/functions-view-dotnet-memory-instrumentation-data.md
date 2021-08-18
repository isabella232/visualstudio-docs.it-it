---
title: 'Visualizzazione Funzioni: dati di strumentazione di memoria .NET | Microsoft Docs'
description: Ottenere informazioni sulla visualizzazione Funzioni dei dati di profilatura dell'allocazione di memoria .NET raccolti tramite il metodo di strumentazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ffac8904b22280e8dccc2e0aae96da780ff1b86e05b1b4ae10a9b504fe486cc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426963"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Visualizzazione Funzioni: dati di strumentazione di memoria .NET
La visualizzazione Funzioni dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di strumentazione elenca le funzioni che hanno allocato memoria durante l'esecuzione della profilatura. La riga di una funzione indica le dimensioni e il numero di allocazioni, nonché i dati di intervallo per la funzione.

## <a name="general"></a>Generale

|Colonna|Descrizione|
|------------|-----------------|
|**Nome della funzione**|Nome della funzione.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Numero di chiamate**|Numero totale di chiamate effettuate a questa funzione.|
|**File di origine**|File di origine che contiene la definizione di questa funzione.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i valori di tempo esclusivo.|
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|

## <a name="net-memory-values"></a>Valori di memoria .NET
 I valori di memoria .NET inclusivi di una funzione indicano il numero (allocazioni) e le dimensioni (byte) di oggetti creati dalla funzione e dalle relative funzioni figlio.

 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dalla funzione, ma non dalle relative funzioni figlio.

|Colonna|Descrizione|
|------------|-----------------|
|**Allocazioni inclusive**|Numero totale di oggetti creati in questa funzione e in funzioni chiamate da questa funzione.|
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Allocazioni esclusive**|Numero totale di oggetti creati durante l'esecuzione di codice nel corpo della funzione. Questo numero non include gli oggetti creati nelle funzioni chiamate da questa funzione.|
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|
|**Byte inclusivi**|Numero totale di byte di memoria allocati in questa funzione e in funzioni chiamate da questa funzione.|
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi di questa funzione.|
|**Byte esclusivi**|Numero totale di byte di memoria allocati da questa funzione ma non da funzioni chiamate da questa funzione.|
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte esclusivi di questa funzione.|

## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo inclusivo trascorso**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione.|
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo trascorso di questa funzione.|
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione.|
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione.|
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione.|

## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso
 I valori relativi al tempo esclusivo trascorso indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma non include il tempo trascorso nelle funzioni figlio.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo esclusivo trascorso**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione.|
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questa funzione.|
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione.|
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione.|
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione.|

## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma include il tempo trascorso nelle funzioni figlio.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo inclusivo applicazione**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione.|
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione totale di questa funzione.|
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione.|
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione.|
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione.|

## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione
 I valori relativi al tempo esclusivo applicazione indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, né il tempo trascorso nelle funzioni figlio.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo esclusivo applicazione**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione.|
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione totale di questa funzione.|
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione.|
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione.|
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Funzioni: campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)
