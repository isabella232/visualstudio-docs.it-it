---
title: 'Visualizzazione Funzioni: dati di campionamento di memoria .NET | Microsoft Docs'
description: Ottenere informazioni sulla visualizzazione Funzioni dei dati di profilatura dell'allocazione di memoria .NET raccolti tramite il metodo di campionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6b4503f2287030158e7790e4def8843ee3c29e0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033786"
---
# <a name="functions-view---net-memory-sampling-data"></a>Visualizzazione Funzioni: dati di campionamento di memoria .NET
La visualizzazione Funzioni dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di campionamento elenca le funzioni che hanno allocato memoria durante l'esecuzione della profilatura e indica le dimensione e il numero delle allocazioni.

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
|**Allocazioni inclusive**|Numero totale di oggetti allocati in questa funzione e funzioni figlio corrispondenti.|
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Allocazioni esclusive**|Numero di oggetti creati durante l'esecuzione diretta della funzione nella parte superiore dello stack di chiamate. Questo numero non include gli oggetti creati nelle funzioni figlio.|
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|
|**Byte inclusivi**|Numero di byte di memoria allocati da questa funzione e dalle funzioni figlio corrispondenti.|
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi di questa funzione.|
|**Byte esclusivi**|Numero di byte di memoria allocati da questa funzione ma non dalle funzioni figlio corrispondenti.|
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte esclusivi di questa funzione.|

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
