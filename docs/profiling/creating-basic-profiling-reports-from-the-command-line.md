---
title: Riga di comando per la profilatura-creazione di report di base
description: Informazioni sulle opzioni di riepilogo e CallTrace di VSPerfReport.exe, che creano report con estensione CSV (valori delimitati da virgole) da un file di dati di profilatura con estensione vsp o vsps.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4d5e263d68ff2fbfbd963e9e3ee3833bd266aaba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955996"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Creare report di profilatura di base tramite la riga di comando
Questo articolo descrive i comandi VSPerfReport di base che generano report di valori separati da virgole (file con estensione *csv*) da un file di dati di profilatura con estensione *vsp* o *vsps*. Per la descrizione di tutte le opzioni del report, vedere [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Comandi del report
 Usare uno dei comandi seguenti per creare un report per il file di dati di profilatura specificato.

 **VSPerfReport** `VSPFile` **/Summary:All** Genera tutti i report disponibili per il file con estensione *vsp* o *vsps*.

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...] Genera i tipi di report specificati.

 **VSPerfReport** `VSPFile` **/CallTrace** Genera un report che elenca ogni evento di raccolta dati. Solo strumentazione.

## <a name="summary-report-type-parameters"></a>Parametri di riepilogo per tipo di report
 La tabella seguente descrive i report generati a seconda dell'opzione di tipo di report specificata Le colonne di un report variano a seconda del metodo di profilatura usato per raccogliere i dati.

|Parametro di riepilogo|Descrizione report|Riferimenti per il report|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Rappresenta le relazioni padre-figlio tra le funzioni.|-   [Campionamento dei dati](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/caller-callee-view-contention-data.md)|
|**Funzione**|Elenca i dati di profilatura per funzione.|-   [Campionamento dei dati](../profiling/functions-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/functions-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/functions-view-contention-data.md)|
|**CallTree**|Rappresenta i percorsi di esecuzione e i dati di profilatura delle funzioni nell'esecuzione della profilatura.|-   [Dati di strumentazione](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Campionamento dei dati](../profiling/call-tree-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/call-tree-view-contention-data.md)|
|**Contatore**|Elenca i contrassegni di profilo e valori del contatore delle prestazioni di Windows raccolti durante l'esecuzione della profilatura.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|
|**IP**|Elenca i dati di profilatura per istruzione.|-   [Campionamento dei dati](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dati su conflitti](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Vita**|Visualizza la durata degli oggetti allocati.|-   [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md)|
|**Linea**|Elenca i dati di profilatura per riga di codice sorgente.|-   [Campionamento dei dati](../profiling/lines-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dati sui conflitti](../profiling/lines-view-contention-data.md)|
|**Intestazione**|Informazioni di intestazione per il file di dati di profilatura.|Specifico per il file.|
|**Contrassegno**|Contrassegni di profilatura raccolti nell'esecuzione della profilatura.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|
|**Modulo**|Elenca i dati di profilatura per i moduli.|-   [Campionamento dei dati](../profiling/modules-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/modules-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/modules-view-contention-data.md)|
|**Processo**|Elenca i dati di profilatura per i processi.|-   [Visualizzazione processo](../profiling/process-view.md)<br />-   [Dati su conflitti](../profiling/process-view-contention-data.md)|
|**Thread**|Elenca i dati di profilatura per i thread.|-   [Visualizzazione processo](../profiling/process-view.md)|
|**Tipo**|Elenca i dati di profilatura dell'allocazione in base al tipo.|-   [Visualizzazione allocazioni](../profiling/dotnet-memory-allocations-view.md)|
|**Contesa**|Conflitti tra risorse.|-   [Conflitti tra risorse](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Elenca i problemi relativi alle regole di prestazioni.|Elenca il valore CheckId, la descrizione e il percorso del codice sorgente del problema relativo alla regola.|
|**ETW**|Elenca gli eventi ETW (Event Tracing for Windows) raccolti durante l'esecuzione della profilatura.|-   [Report ETW](../profiling/event-tracing-for-windows-etw-report.md)|
