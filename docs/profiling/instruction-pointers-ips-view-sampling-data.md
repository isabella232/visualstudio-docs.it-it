---
title: "Visualizzazione Puntatore all'istruzione: dati di campionamento | Microsoft Docs"
description: Informazioni su come la visualizzazione DEGLI INDIRIZZI IP dei dati di campionamento elenca i dati sulle prestazioni per le istruzioni dell'assembly eseguite direttamente al momento della raccolta degli esempi.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3cfc6a196d69da4fa5f5837265340b05a503d71370bb721a3f049890a991477c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121354996"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Visualizzazione dei puntatori all'istruzione: dati di campionamento
Nella visualizzazione Puntatore all'istruzione dei dati di campionamento sono elencati i dati sulle prestazioni per le istruzioni dell'assembly eseguite direttamente durante la raccolta dei campioni nell'esecuzione della profilatura.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Colonna|Descrizione|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo contenente l'istruzione.|
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|
|**File di origine**|File di origine che contiene l'istruzione.|
|**Nome della funzione**|Nome della funzione contenente l'istruzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Inizio carattere di origine**|Offset del carattere iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine carattere di origine**|Offset del carattere finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Indirizzo istruzione**|Indirizzo dell'istruzione nel file binario caricato.|
|**Campioni esclusivi**|Numero totale di campioni raccolti durante l'esecuzione dell'istruzione.|
|**% esempi esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione dell'istruzione.|

## <a name="see-also"></a>Vedi anche
- [Visualizzazione puntatori all'istruzione (IP) - campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
