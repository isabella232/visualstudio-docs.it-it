---
title: 'Visualizzazione Funzioni: dati sui conflitti | Microsoft Docs'
description: Ottenere informazioni dettagliate sulla visualizzazione del report Funzioni dei dati relativi ai contenuti in cui sono elencate le funzioni nell'esecuzione della profilatura che sono state bloccate dall'esecuzione durante l'esecuzione della profilatura.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ebc7fa07b9f7d8ad2694a6decba0db50b93dbdb6b7093fd4e2f81913d3514a91
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368604"
---
# <a name="functions-view---contention-data"></a>Visualizzazione Funzioni: dati sui conflitti
La visualizzazione report Funzioni dei dati sui conflitti elenca le funzioni nell'esecuzione della profilatura la cui esecuzione è stata bloccata durante l'esecuzione della profilatura stessa.

 La tabella seguente descrive i valori presenti nella visualizzazione Funzioni di un file di dati di profilatura raccolti tramite il metodo di concorrenza.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo blocco esclusivo**|La quantità di tempo durante la quale è stata impedita l'esecuzione di codice nel corpo della funzione. È escluso il tempo di blocco nelle funzioni chiamate dalla funzione.|
|**% tempo blocco esclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per questa funzione.|
|**Conflitti esclusivi**|Il numero di volte che è stata impedita l'esecuzione di codice nel corpo della funzione. Non sono inclusi i conflitti in funzioni chiamate dalla funzione.|
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti esclusivi di questa funzione.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Nome della funzione**|Nome completo della funzione.|
|**Tempo blocco inclusivo**|Ora in cui l'esecuzione di questa funzione o di una funzione chiamata da questa è stata bloccata.|
|**% tempo blocco inclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per questa funzione o per questo modulo.|
|**Conflitti inclusivi**|Numero di volte in cui l'esecuzione di questa funzione o di una funzione chiamata da questa è stata bloccata.|
|**% conflitti inclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti inclusivi di questa funzione o di questo modulo.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**ID processo**|ID del processo (PID) del processo in cui era in esecuzione la funzione.|
|**Nome processo**|Nome del processo.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Funzioni](../profiling/functions-view.md)
- [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Funzioni: campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)
