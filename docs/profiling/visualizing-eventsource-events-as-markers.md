---
title: Visualizzazione di eventi EventSource come marcatori | Microsoft Docs
description: Informazioni sul fatto che il visualizzatore di concorrenza può visualizzare gli eventi EventSource come marcatori ed è possibile controllare la modalità di visualizzazione dei marcatori.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b29215a6e1d3896b47e98d8447121768d0a7ed484d0701a82fc94da2574c8cb0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230924"
---
# <a name="visualize-eventsource-events-as-markers"></a>Visualizzare eventi EventSource come marcatori
Il visualizzatore di concorrenza consente di visualizzare gli eventi EventSource come marcatori ed è possibile controllare la modalità di visualizzazione dei marcatori. Per visualizzare i marcatori EventSource, registrare il GUID del provider ETW mediante la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). Il visualizzatore di concorrenza usa convenzioni predefinite per rappresentare gli eventi EventSource come [marcatori di flag](../profiling/flag-markers.md), [marcatori di span](../profiling/span-markers.md) e [marcatori di messaggi](../profiling/message-markers.md). È possibile personalizzare la modalità di visualizzazione degli eventi EventSource aggiungendo campi personalizzati agli eventi. Per altre informazioni sui marcatori, vedere [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md). Per altre informazioni sugli eventi EventSource, vedere <xref:System.Diagnostics.Tracing>.

## <a name="default-visualization-of-eventsource-events"></a>Visualizzazione predefinita degli eventi EventSource
 Per impostazione predefinita, il visualizzatore di concorrenza usa le convenzioni seguenti per rappresentare gli eventi EventSource.

### <a name="marker-type"></a>Tipo di marcatore

1. Gli eventi con [codice operativo](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start o win:Stop vengono considerati come l'inizio o la fine di una sezione span, rispettivamente.  Le sezioni span annidate o sovrapposte non possono essere visualizzate. Le coppie di eventi che iniziano in un thread di inizio e finiscono in un altro non possono essere visualizzate.

2. Un evento il cui codice operativo non è win:Start né win:Stop viene considerato come un flag di marcatore, a meno che il relativo [livello](/windows/desktop/WES/defining-severity-levels) (campo di EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR) non sia win:Verbose o superiore.

3. In tutti gli altri casi, l'evento viene considerato un messaggio.

### <a name="importance"></a>Importanza
 La tabella seguente illustra il mapping tra il livello di evento e l'importanza del marcatore.

|Livello ETW|Importanza del visualizzatore di concorrenza|
|---------------|---------------------------------------|
|win:LogAlways|Normale|
|win:Critical|Critico|
|win:Error|Critico|
|win:Warning|Alto|
|win:Informational|Normale|
|win:Verbose|Basso|
|Superiore a win:verbose|Basso|

### <a name="series-name"></a>Nome della serie
 Il nome dell'attività dell'evento viene usato per il nome della serie. Il nome della serie è vuoto se è non stata definita alcuna attività per l'evento.

### <a name="category"></a>Category
 Se il livello è win:Critical o win:Error, la categoria è Avviso (-1). In caso contrario, la categoria è quella predefinita (0).

### <a name="text"></a>Testo
 Se è stato definito un messaggio di testo formattato come printf-type per l'evento, viene visualizzato come descrizione del marcatore. In caso contrario, la descrizione è il nome dell'evento e il valore di ogni campo Payload.

## <a name="customize-visualization-of-eventsource-events"></a>Personalizzare la visualizzazione degli eventi EventSource
 È possibile personalizzare la modalità di visualizzazione degli eventi EventSource aggiungendo i campi appropriati all'evento, come descritto nelle sezioni seguenti.

### <a name="marker-type"></a>Tipo di marcatore
 Usare il campo `cvType`, un byte, per controllare il tipo di marcatore usato per rappresentare l'evento. Di seguito sono riportati i valori disponibili per cvType:

|Valore cvType|Tipo di marcatore risultante|
|------------------|---------------------------|
|0|Message|
|1|Inizio sezione span|
|2|Fine sezione span|
|3|Contrassegno|
|Tutti gli altri valori|Message|

### <a name="importance"></a>Importanza
 È possibile usare il campo `cvImportance`, un byte, per controllare l'impostazione dell'importanza per un evento EventSource. È tuttavia consigliabile controllare l'importanza visualizzata di un evento usando il relativo livello.

|Valore cvImportance|Importanza del visualizzatore di concorrenza|
|------------------------|---------------------------------------|
|0|Normale|
|1|Critico|
|2|Alto|
|3|Alto|
|4|Normale|
|5|Basso|
|Tutti gli altri valori|Basso|

### <a name="series-name"></a>Nome della serie
 Usare il campo evento `cvSeries`, una stringa, per controllare il nome della serie assegnato dal visualizzatore di concorrenza a un evento EventSource.

### <a name="category"></a>Category
 Usare il campo `cvCategory`, un byte, per controllare la categoria assegnata dal visualizzatore di concorrenza a un evento EventSource.

### <a name="text"></a>Testo
 Usare il campo `cvTextW`, una stringa, per controllare la descrizione assegnata dal visualizzatore di concorrenza a un evento EventSource.

### <a name="spanid"></a>SpanID
 Usare il campo cvSpanId, un valore int, per associare coppie di eventi. Il valore per ogni coppia di eventi di inizio/fine che rappresentano una sezione span deve essere univoco. In genere, per il codice simultaneo è necessario usare a questo scopo primitive di sincronizzazione, come <xref:System.Threading.Interlocked.Exchange%2A>, per garantire che la chiave (il valore usato per CvSpanID) sia corretta.

> [!NOTE]
> L'uso di SpanID per annidare sezioni span, consentirne la parziale sovrapposizione nello stesso thread o consentirne l'inizio in un thread e la fine in un altro non è supportato.

## <a name="see-also"></a>Vedi anche
- [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)