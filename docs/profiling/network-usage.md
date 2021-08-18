---
title: Analizzare l'utilizzo della rete nelle app UWP
description: Informazioni su come lo Visual Studio di diagnostica di rete raccoglie i dati sulle operazioni di rete eseguite usando il Windows. API Web.Http.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed223022d9d9d8033f854247815f44cb3531df83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141649"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analizzare l'utilizzo della rete nelle app UWP
Lo strumento di diagnostica **Rete** di Visual Studio consente di raccogliere dati sulle operazioni di rete eseguite con l'[API Windows.Web.Http](/uwp/api/windows.web.http). L'analisi dei dati può essere utile nella risoluzione di problemi di accesso e autenticazione, di uso errato della cache, nonché in caso di problemi di prestazioni relativi a visualizzazione e download.

 Lo strumento Rete supporta solo le app UWP. Altre piattaforme non sono attualmente supportate.

> [!NOTE]
> Per una descrizione più completa dello strumento Rete, vedere [Introducing Visual Studio's network tool (Introduzione](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/)dello strumento di rete di Visual Studio).

## <a name="collect-network-tool-data"></a>Raccogliere i dati dello strumento di rete
 È consigliabile eseguire lo strumento **Rete** con un progetto di Visual Studio aperto nel computer di Visual Studio.

1. Aprire il progetto in Visual Studio.

2. Nel menu fare clic su **Debug/Profiler prestazioni**. Scegliere **Rete** e quindi **Avvia**.

3. Lo strumento di rete inizia a raccogliere il traffico di rete HTTP dell'app.

    Quando si esegue l'app, la visualizzazione di riepilogo nel riquadro sinistro visualizza automaticamente un elenco di operazioni HTTP acquisite. Selezionare un elemento nella visualizzazione di riepilogo per visualizzare ulteriori informazioni nel pannello dei dettagli nel riquadro di destra.

4. Scegliere **Arresta** per chiudere l'app.

   La finestra di report dovrebbe essere analoga alla seguente:

   ![Finestra Rete](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analizzare i dati
 È possibile analizzare il traffico HTTP acquisito mentre l'applicazione è in esecuzione o anche dopo che l'applicazione è stata chiusa, selezionando una delle operazioni di rete visualizzate nella visualizzazione di riepilogo.

 Nella visualizzazione di riepilogo dello strumento **Rete** sono visualizzati i dati relativi alle singole operazioni di rete che si sono verificate durante l'esecuzione dell'app. Scegliere un'intestazione di colonna per ordinare l'elenco oppure scegliere i tipi di contenuto da visualizzare nella visualizzazione del filtro **Tipo di contenuto**.

 Scegliere **Salva come HAR** per creare un file JSON utilizzabile da strumenti di terze parti come Fiddler.

 Nelle visualizzazioni dei dettagli dello strumento **Rete** sono visualizzate maggiori informazioni su un'operazione di rete presente nella visualizzazione di riepilogo.

 ![Riquadro dei dettagli dello strumento di rete](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|Nome|Descrizione|
|-|-|
|**Intestazioni**|Informazioni sulle intestazioni della richiesta dell'evento.|
|**Corpo**|Dati relativi ai payload di richiesta e risposta.|
|**Parametri**|Nomi e valori dei parametri delle stringhe di query.|
|**Biscotti**|Dati relativi ai cookie di richiesta e risposta.|
|**Timings**|Grafico delle fasi di acquisizione delle risorse selezionate.|

 La barra di **riepilogo** dello strumento Rete indica il numero di operazioni di rete visualizzate in un determinato momento, la quantità di dati trasferita, il tempo impiegato per il download e il numero di errori (richieste con risposte 4xx o 5xx) visibili.

### <a name="analysis-tips"></a>Suggerimenti sull’analisi 
 Questo strumento evidenzia determinate aree che possono essere utili quando si esegue l'analisi correlata alla rete:

1. Le richieste gestite completamente dalla cache vengono visualizzate come **(dalla cache)** nella colonna **Ricevute**. Ciò consente di determinare se si sta utilizzando la cache in modo efficace per risparmiare la larghezza di banda dell’utente o se si stanno erroneamente memorizzando nella cache risposte fornendo agli utenti finali dell'applicazione dati obsoleti.

2. Le risposte di errore (4xx o 5xx) vengono visualizzate nella colonna **Risultati** con il codice di stato rosso e vengono evidenziate anche nella barra di riepilogo. In tal modo è facile individuare gli errori tra le numerose potenziali richieste nell'applicazione.

3. Il pulsante di riformattazione della risposta (all'interno della scheda corpo) consente di analizzare i payload di risposta JSON, XML, HTML, CSS, JavaScript e TypeScript aumentando la leggibilità del contenuto.

## <a name="see-also"></a>Vedi anche

- [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio blog: Introducing Visual Studio's network inspector](https://devblogs.microsoft.com/visualstudio/)
- [Video di Channel 9: Strumenti di diagnostica di Visual Studio - nuovo profiler di rete](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)