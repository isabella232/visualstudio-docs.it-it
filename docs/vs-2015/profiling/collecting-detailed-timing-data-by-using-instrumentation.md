---
title: Raccolta di dati di intervallo dettagliati tramite la strumentazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c129ddf016e02fe6c29d5cf63fe57ba07fbd4e95
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087976"
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>Raccolta di dati di intervallo dettagliati tramite la strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il metodo di strumentazione degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inserisce codice di profilatura in una copia di un modulo. Il codice registra ogni voce, uscita e chiamata di funzione delle funzioni nel modulo durante un'esecuzione di profilatura. Il metodo di strumentazione è utile per raccogliere informazioni dettagliate sugli intervalli relative a una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione.  
  
 È possibile specificare il metodo di strumentazione tramite una delle procedure seguenti:  
  
- Nella prima pagina della procedura guidata di profilatura selezionare **Strumentazione**.  
  
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Strumentazione**.  
  
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni selezionare **Strumentazione**.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:  
  
- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.  
  
  Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** quando si esegue la profilatura con il metodo di strumentazione.  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|Nella pagina **Generale** aggiungere dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Nella pagina **Avvio** specificare l'applicazione da avviare e l'ordine di avvio se si hanno più progetti EXE nella soluzione.|-   [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)|  
|Nella pagina **Binari** specificare un percorso per le copie instrumentate dei moduli. Per impostazione predefinita, i file binari originali vengono spostati in una cartella di backup.|-   [Procedura: Rilocare file binari instrumentati](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Strumentazione** escludere le funzioni piccole dalla profilatura per ridurre il sovraccarico di profilatura, eseguire la profilatura del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire a un prompt dei comandi prima e dopo il processo di strumentazione.|-   [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Procedura: Profilare codice JavaScript nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Procedura: Specificare comandi pre- e post-strumentazione](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Nella pagina **Contatori CPU** specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilatura.|-   [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|Nella pagina **Eventi di Windows** selezionare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|-   [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate** specificare le opzioni aggiuntive da passare al programma di strumentazione VSInstr, ad esempio le opzioni per includere o escludere funzioni specifiche.|-   [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Procedura: Limitare la strumentazione a specifiche funzioni](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
