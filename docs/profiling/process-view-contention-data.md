---
title: 'Visualizzazione Processo: dati sui conflitti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 30c938088538bcecc71e3a7e37d5ae403dd476e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778401"
---
# <a name="process-view---contention-data"></a>Visualizzazione Processo: dati sui conflitti
Nella visualizzazione Processo sono riportati i dati sui conflitti per i processi e i thread eseguiti durante l'esecuzione della profilatura.

 Quando sono disponibili i simboli, i processi vengono elencati in base al nome. Quando non sono disponibili i simboli, i processi vengono elencati in base all'indirizzo di memoria in formato esadecimale. I thread vengono elencati come elementi figlio del processo che li ha creati.

 La tabella seguente illustra i valori delle colonne nella tabella della visualizzazione Processo.

|Colonna|Descrizione|
|------------|-----------------|
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|
|**Ora bloccata**|Tempo totale durante il quale è stata impedita l'esecuzione di funzioni del processo o del thread.|
|**% tempo blocco**|Percentuale della durata del processo o del thread in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**Conflitti**|Numero di volte in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**% conflitti**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti del processo o del thread.|
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|
|**Id**|Identificatore generato dal sistema per il processo o il thread.|
|**Durata**|Numero di millisecondi o di cicli del processore dall'inizio del processo o del thread alla fine del processo o del thread o alla fine della profilatura.|
|**Tipo**|Tipo di riga, ovvero processo o thread.<br /><br /> Solo nei rapporti della riga di comando di **VSReport**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|
|**Nome**|Nome del processo o del thread.|
|**ID univoco**|Identificatore generato dal profiler univoco per il processo o il thread.|

## <a name="see-also"></a>Vedere anche
- [Procedura: personalizzare le colonne della visualizzazione reportHow to: Customize Report View columns](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Processo](../profiling/process-view.md)
