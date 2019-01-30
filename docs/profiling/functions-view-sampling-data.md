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
ms.workload:
- multiple
ms.openlocfilehash: 4bf90e28fec2c97c4dbdc5d90bb78ffed4020970
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948739"
---
# <a name="functions-view---sampling-data"></a>Visualizzazione Funzioni: dati di campionamento
La visualizzazione del rapporto Funzioni per il metodo di profilatura del campionamento elenca le funzioni che sono state campionate durante l'esecuzione della profilatura.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
|Colonna|Description|  
|------------|-----------------|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
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
 [Procedura: Personalizzare le colonne delle visualizzazioni dei report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Funzioni: campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)