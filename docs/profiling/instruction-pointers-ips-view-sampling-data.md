---
title: "Visualizzazione Puntatore all'istruzione: dati di campionamento | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77d15b606269121a1c580aae13000c6d6dc3e13e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619563"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Visualizzazione dei puntatori all'istruzione: dati di campionamento
Nella visualizzazione Puntatore all'istruzione dei dati di campionamento sono elencati i dati sulle prestazioni per le istruzioni dell'assembly eseguite direttamente durante la raccolta dei campioni nell'esecuzione della profilatura.

> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

|Colonna|Description|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo contenente l'istruzione.|
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|
|**File di origine**|File di origine che contiene l'istruzione.|
|**Nome funzione**|Nome della funzione contenente l'istruzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Inizio carattere di origine**|Offset del carattere iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine carattere di origine**|Offset del carattere finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Indirizzo istruzione**|Indirizzo dell'istruzione nel file binario caricato.|
|**Esempi esclusivi**|Numero totale di campioni raccolti durante l'esecuzione dell'istruzione.|
|**% esempi esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione dell'istruzione.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione dei puntatori all'istruzione: campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)