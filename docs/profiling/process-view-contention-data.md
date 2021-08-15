---
title: 'Visualizzazione Processo: dati sui conflitti | Microsoft Docs'
description: Informazioni su come nella visualizzazione Processo vengono visualizzati i dati relativi ai processi e ai thread eseguiti durante l'esecuzione della profilatura.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 042b8834b9b3d1b4f91bef09a5a71b2bdb394da5865426f352b28446ee858811
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121246006"
---
# <a name="process-view---contention-data"></a>Visualizzazione Processo: dati sui conflitti
Nella visualizzazione Processo sono riportati i dati sui conflitti per i processi e i thread eseguiti durante l'esecuzione della profilatura.

 Quando sono disponibili i simboli, i processi vengono elencati in base al nome. Quando non sono disponibili i simboli, i processi vengono elencati in base all'indirizzo di memoria in formato esadecimale. I thread vengono elencati come elementi figlio del processo che li ha creati.

 La tabella seguente illustra i valori delle colonne nella tabella della visualizzazione Processo.

|Colonna|Descrizione|
|------------|-----------------|
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|
|**Tempo di blocco**|Tempo totale durante il quale è stata impedita l'esecuzione di funzioni del processo o del thread.|
|**% tempo blocco**|Percentuale della durata del processo o del thread in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**Conflitti**|Numero di volte in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**% conflitti**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti del processo o del thread.|
|**Ora fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|
|**ID**|Identificatore generato dal sistema per il processo o il thread.|
|**Durata**|Numero di millisecondi o di cicli del processore dall'inizio del processo o del thread alla fine del processo o del thread o alla fine della profilatura.|
|**Tipo**|Tipo di riga, ovvero processo o thread.<br /><br /> Solo nei rapporti della riga di comando di **VSReport**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|
|**Nome**|Nome del processo o del thread.|
|**ID univoco**|Identificatore generato dal profiler univoco per il processo o il thread.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Processo](../profiling/process-view.md)
