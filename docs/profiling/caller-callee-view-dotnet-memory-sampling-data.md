---
title: 'Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET | Microsoft Docs'
description: Informazioni su come la visualizzazione Chiamante/chiamato visualizza i dati di campionamento della memoria .NET per una funzione selezionata e le relative funzioni padre e figlio in Esplora prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 0e024bf05e2b49ff98ec8c6821d9303844296039
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108096"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Visualizzazione Chiamante-chiamato: dati di campionamento di memoria .NET
La visualizzazione Chiamante/chiamato consente di visualizzare i dati di profilatura della memoria .NET per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie.

 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura della memoria relative alla funzione selezionata. Sono incluse tutte le chiamate campionate alla funzione.

 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza la quantità del valore della funzione selezionata (corrente) generato da chiamate da parte della funzione chiamante (padre).

 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza dati di profilatura di memoria per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.

 Fare doppio clic su una riga della funzione chiamante o chiamata per rendere quella riga la funzione corrente.

|Colonna|Descrizione|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|
|**Nome della funzione**|Nome completo della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Tipo**|Il contesto della funzione:<br /><br /> **0**: la funzione corrente<br /><br /> **1**: una funzione che chiama la funzione corrente<br /><br /> **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|
|**Level**|Profondità della funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|
|**Allocazioni inclusive**|- Per la funzione corrente, il numero di oggetti allocati dalla funzione nell'esecuzione della profilatura. Il numero include gli oggetti creati nelle funzioni chiamate.<br />- Per una funzione chiamante, il numero delle allocazioni inclusive della funzione corrente generate da chiamate da questa funzione.<br />- Per una funzione chiamata, il numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione corrente. Il numero include le allocazioni effettuate dalle funzioni chiamate dalla funzione chiamata.|
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Allocazioni esclusive**|- Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice del corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Il numero non include gli oggetti creati nelle funzioni chiamate dalla funzione.<br />- Per una funzione chiamante, il numero delle allocazioni esclusive della funzione corrente generate da chiamate da questa funzione.<br />- Per una funzione chiamata, il numero di oggetti creati dalle istanze di questa funzione chiamate dalla funzione corrente. Il numero non include gli oggetti creati dalle funzioni chiamate dalla funzione chiamata.|
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Byte inclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Il numero include la memoria allocata nelle funzioni chiamate da questa funzione.<br />- Per una funzione chiamante, il numero dei byte inclusivi della funzione corrente generati da chiamate dalla funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze di questa funzione generati da chiamate dalla funzione corrente. Il numero include i byte allocati dalle funzioni chiamate dalla funzione chiamata.|
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Byte esclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Questo numero non include la memoria allocata dalle funzioni chiamate dalla funzione corrente.<br />- Per una funzione chiamante, il numero dei byte esclusivi della funzione corrente generati da chiamate dalla funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze della funzione generati da chiamate dalla funzione corrente. Il numero non include i byte allocati dalle funzioni chiamate dalla funzione chiamata.|
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione chiamante/chiamato : dati di strumentazione della memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)
- [Visualizzazione chiamante/chiamato : dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)
