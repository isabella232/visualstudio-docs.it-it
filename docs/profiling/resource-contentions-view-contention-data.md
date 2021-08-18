---
title: 'Visualizzazione dei conflitti di risorse: dati sui conflitti | Microsoft Docs'
description: Informazioni sul modo in cui la visualizzazione Dei contenuti delle risorse elenca i dati sui contenuti per le risorse che sono state l'origine di eventi di contention.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2dabd080bfbd2463ed13f1b0f12a5521ab26b647
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131196"
---
# <a name="resource-contentions-view---contention-data"></a>Visualizzazione dei conflitti di risorse: dati sui conflitti
Nella visualizzazione dei conflitti tra le risorse sono elencati i dati sui conflitti relativi alle risorse che hanno causato gli eventi di conflitto. Un evento di conflitto si verifica quando una funzione in un thread deve attendere l'accesso alla risorsa perché una funzione in un altro thread ne ha acquisito l'accesso esclusivo. Ogni risorsa è il nodo radice di un albero delle chiamate in cui vengono visualizzati i percorsi di esecuzione delle funzioni che hanno generato gli eventi di conflitto.

## <a name="data-values"></a>Valori dei dati

### <a name="resource-values"></a>Valori della risorsa
 I dati contenuti in una riga di risorsa indicano il tempo totale durante il quale l'accesso alla risorsa è rimasto bloccato nei dati di profilatura e il numero totale di eventi di conflitto che si sono verificati a causa del conflitto di accesso a questa risorsa. I valori inclusivi ed esclusivi per una risorsa sono sempre gli stessi.

### <a name="function-values"></a>Valori della funzione
 I valori della funzione sono basati sulle istanze della funzione che si sono verificate nel percorso di esecuzione rappresentato nell'albero delle chiamate.

- I valori esclusivi sono basati sugli eventi che si sono verificati durante l'esecuzione delle istruzioni da parte della funzione nel corpo della funzione stessa. Non sono inclusi nei valori esclusivi gli eventi che si sono verificati in funzioni chiamate dalla funzione.

- I valori inclusivi sono basati sugli eventi che si sono verificati durante l'esecuzione della funzione o di una funzione chiamata dalla funzione stessa.

### <a name="percentage-values"></a>Valori percentuali
 I valori percentuali sono basati sul tempo totale o sugli eventi di conflitto nei dati di profilatura. Se si filtra il rapporto o la visualizzazione dell'esecuzione della profilatura, verranno usati come valore totale solo i conflitti e il tempo di blocco nei dati filtrati.

## <a name="navigating-the-resource-allocation-view"></a>Esplorazione della visualizzazione Assegnazione risorse

|Colonna|Descrizione|
|------------|-----------------|
|**Nome**|Nome della risorsa o della funzione.|
|**Tempo blocco esclusivo**|- Per una risorsa, il tempo totale per cui è stato bloccato l'accesso alla risorsa con conseguente attesa di un thread.<br />- Per una funzione, il tempo per cui è stato bloccato l'accesso alla risorsa padre a queste istanze della funzione durante l'esecuzione di codice nel corpo della funzione. È escluso il tempo di blocco nelle funzioni chiamate dalla funzione.|
|**% tempo blocco esclusivo**|- Per una risorsa, la percentuale del tempo totale di blocco nei dati di profilatura corrispondente al tempo di blocco di questa risorsa<br />- Per una funzione, la percentuale del tempo totale di blocco nei dati di profilatura corrispondente al tempo di blocco esclusivo di queste istanze della funzione.|
|**Conflitti esclusivi**|- Per una risorsa, il numero totale di volte in cui è stato bloccato l'accesso alla risorsa con conseguente attesa di un thread.<br />- Per una funzione, il numero di volte in cui è stato bloccato l'accesso alla risorsa padre a queste istanze della funzione durante l'esecuzione di codice nel corpo della funzione. Non sono inclusi gli eventi di blocco in funzioni chiamate dalla funzione.|
|**% conflitti esclusivi**|- Per una risorsa, la percentuale di tutti gli eventi di conflitto nei dati di profilatura che rappresentano eventi di conflitto per l'accesso a questa risorsa.<br />- Per una funzione, la percentuale di tutti gli eventi di conflitto nei dati di profilatura che rappresentano eventi di conflitto esclusivi di queste istanze della funzione per la risorsa padre.|
|**Tempo blocco inclusivo**|- Per una risorsa, il tempo totale per cui è stato bloccato l'accesso alla risorsa con conseguente attesa di un thread.<br />- Per una funzione, il tempo per cui è stato bloccato l'accesso alla risorsa padre a queste istanze della funzione o a qualsiasi funzione chiamata dalle istanze durante l'esecuzione di codice nel corpo della funzione.|
|**% tempo blocco inclusivo**|- Per una risorsa, la percentuale del tempo totale di blocco nei dati di profilatura corrispondente al tempo di blocco di questa risorsa<br />- Per una funzione, la percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo di queste istanze della funzione.|
|**Conflitti inclusivi**|- Per una risorsa, il numero totale di volte in cui è stato bloccato l'accesso alla risorsa con conseguente attesa di un thread.<br />- Per una funzione, la percentuale di tutti gli eventi di conflitto nell'esecuzione della profilatura che rappresentano eventi di conflitto inclusivi di queste istanze della funzione per la risorsa padre.|
|**% conflitti inclusivi**|- Per una risorsa, la percentuale di tutti gli eventi di conflitto nell'esecuzione della profilatura che rappresentano eventi di conflitto per l'accesso a questa risorsa.<br />- Per una funzione, il numero di volte in cui è stato bloccato l'accesso alla risorsa padre a queste istanze della funzione durante l'esecuzione di codice nel corpo della funzione. Non sono inclusi gli eventi di blocco in funzioni chiamate dalla funzione.|
|**Level**|Profondità di questa funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**ID processo**|ID del processo (PID) del processo in cui era in esecuzione la funzione.|
|**Nome processo**|Nome del processo.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|
