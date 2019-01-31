---
title: 'Visualizzazione Funzioni: dati di campionamento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68280c4da20ce063b93b7347cc2857d4a83b9a18
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769155"
---
# <a name="functions-view---sampling-data"></a>Visualizzazione Funzioni: dati di campionamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione del rapporto Funzioni per il metodo di profilatura del campionamento elenca le funzioni che sono state campionate durante l'esecuzione della profilatura.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
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
 [Visualizzazione Funzioni - Campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
