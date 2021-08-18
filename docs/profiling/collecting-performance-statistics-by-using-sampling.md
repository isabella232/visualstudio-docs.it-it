---
title: Raccolta di statistiche sulle prestazioni tramite campionamento
description: Usare il metodo Strumenti di profilatura di campionamento per individuare i problemi di utilizzo del processore. È il metodo consigliato per avviare la maggior parte delle analisi delle prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f016fb7498ec30bab30e58af4d3023be3986ab4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076815"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Raccogliere le statistiche sulle prestazioni tramite il campionamento

Per impostazione predefinita, il metodo di campionamento degli strumenti di profilatura di Visual Studio raccoglie informazioni di profilatura ogni 10.000.000 di cicli del processore, ovvero ogni centesimo di secondo circa in un computer da 1 GHz. Il metodo di campionamento è utile per individuare problemi relativi all'uso del processore e rappresenta il metodo consigliato nella maggior parte dei casi per iniziare l'analisi delle prestazioni.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

È possibile specificare il metodo di campionamento tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura fare clic su **Campionamento CPU (consigliato)**.
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Campionamento**.
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Campionamento**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi **scegliere Proprietà.**

  Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di campionamento.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** aggiungere la raccolta dei dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Procedura: Impostare le opzioni relative al nome del file di dati delle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|
|Nella pagina **Campionamento** modificare la frequenza di campionamento, scegliere come evento di campionamento un altro contatore delle prestazioni del processore anziché i cicli di clock o modificare entrambe le impostazioni.|- [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare e l'ordine di avvio.|- [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Interazione tra** livelli aggiungere le ADO.NET di chiamata ai dati raccolti nell'esecuzione della profilatura.|- [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Eventi di Windows** specificare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|- [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [Procedura: Raccogliere i dati Windows contatore](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [Procedura: Specificare il runtime .NET Framework runtime](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
