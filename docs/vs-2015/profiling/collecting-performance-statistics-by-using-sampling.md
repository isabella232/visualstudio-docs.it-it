---
title: Raccolta di statistiche sulle prestazioni tramite il campionamento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b84674eafde85528e04157ab213913e57d27e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840144"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Raccolta di statistiche sulle prestazioni tramite il campionamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, il metodo di campionamento degli strumenti di profilatura di [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] raccoglie informazioni di profilatura ogni 10.000.000 di cicli del processore, ovvero ogni centesimo di secondo circa in un computer da 1 GHz. Il metodo di campionamento è utile per individuare problemi relativi all'uso del processore e rappresenta il metodo consigliato nella maggior parte dei casi per iniziare l'analisi delle prestazioni.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 È possibile specificare il metodo di campionamento tramite una delle procedure seguenti:  
  
- Nella prima pagina della procedura guidata di profilatura fare clic su **Campionamento CPU (consigliato)**.  
  
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Campionamento**.  
  
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Campionamento**.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:  
  
- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.  
  
  Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si esegue la profilatura con il metodo di campionamento.  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|Nella pagina **Generale** aggiungere la raccolta dei dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: impostare le opzioni relative ai nomi file dei dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Nella pagina **Campionamento** modificare la frequenza di campionamento, scegliere come evento di campionamento un altro contatore delle prestazioni del processore anziché i cicli di clock o modificare entrambe le impostazioni.|-   [Procedura: scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)|  
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare e l'ordine di avvio.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Interazioni tra livelli** aggiungere le informazioni sulle chiamate ADO.NET ai dati raccolti con l'esecuzione della profilatura.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Eventi di Windows** specificare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|-   [Procedura: raccogliere dati di Event Tracing for Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [Procedura: raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|-   [Procedura: specificare il runtime di .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
