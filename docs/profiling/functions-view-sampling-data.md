---
title: 'Visualizzazione Funzioni: dati di campionamento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 70fda712a29ff07ee34a4ac76a06198cb5ead8a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780026"
---
# <a name="functions-view---sampling-data"></a>Visualizzazione Funzioni: dati di campionamento
La visualizzazione del rapporto Funzioni per il metodo di profilatura del campionamento elenca le funzioni che sono state campionate durante l'esecuzione della profilatura.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Colonna|Descrizione|
|------------|-----------------|
|**ID di processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Process Name**|Nome del processo.|
|**Nome del modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|
|**Nome funzione**|Nome completo della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Esempi inclusivi**|Numero totale di campioni raccolti durante l'esecuzione di questa funzione, vale a dire il numero di campioni raccolti quando questa funzione si trovava nello stack di chiamate. Sono inclusi i campioni raccolti durante l'esecuzione delle funzioni chiamate da questa funzione.|
|**% campioni inclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che costituivano esempi inclusivi di questa funzione.|
|**Campioni esclusivi**|Numero totale di campioni raccolti durante l'esecuzione di codice nel corpo di questa funzione, vale a dire quando questa funzione si trovava in cima allo stack di chiamate. Non sono inclusi i campioni raccolti nelle funzioni chiamate da questa funzione.|
|**% esempi esclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che costituivano esempi esclusivi di questa funzione.|

## <a name="see-also"></a>Vedere anche
- [Procedura: personalizzare le colonne della visualizzazione reportHow to: Customize Report View columns](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Funzioni: campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
