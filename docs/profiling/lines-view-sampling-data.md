---
title: 'Visualizzazione Righe: dati di campionamento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff4d851937111400002de531696b9b69aec20ba9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778583"
---
# <a name="lines-view---sampling-data"></a>Visualizzazione Righe: dati di campionamento
Nella visualizzazione Righe dei dati di campionamento sono elencati i dati delle prestazioni per le istruzioni eseguite durante la raccolta dei campioni nell'esecuzione della profilatura.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 In un file di origine un'istruzione può occupare più di una riga in un file di origine e una singola riga può includere più di un'istruzione. Un'istruzione viene identificata in base agli elementi seguenti:

- File di origine che contiene l'istruzione della funzione.

- Funzione che contiene l'istruzione.

- Riga di origine in cui inizia l'istruzione.

- Carattere nella riga di origine in cui inizia l'istruzione.

- Riga di origine in cui termina l'istruzione.

- Carattere nella riga di origine in cui termina l'istruzione.

  Nella colonna Nome riga è disponibile una concatenazione ordinabile dei dati dell'identificatore.

  Per definizione, un'istruzione non chiama altre funzioni. Vengono quindi elencati solo valori esclusivi.

|Colonna|Descrizione|
|------------|-----------------|
|**ID di processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Process Name**|Nome del processo.|
|**Nome del modulo**|Nome del modulo che contiene la riga della funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la riga della funzione.|
|**File di origine**|File di origine che contiene la riga della funzione.|
|**Nome funzione**|Nome della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo iniziale della funzione.|
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Inizio carattere di origine**|Offset del carattere iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Fine carattere di origine**|Offset del carattere finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|
|**Nome riga**|Un identificatore generato dal profiler della`Source File`riga con la sintassi seguente:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number End`**,**`Character End`**]**|
|**Campioni esclusivi**|Numero totale di campioni raccolti durante l'esecuzione della riga della funzione.|
|**% esempi esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione della riga della funzione.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Righe - Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)
