---
title: Raccolta di dati di intervallo dettagliati tramite la strumentazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bfd22edc9bd672a8d82c94a705b523ce7d836169
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779623"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Raccogliere dati di intervallo dettagliati tramite la strumentazione
Il metodo di strumentazione degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inserisce il codice di profilatura in una copia di un modulo. Il codice registra ogni voce, uscita e chiamata di funzione delle funzioni nel modulo durante un'esecuzione di profilatura. Il metodo di strumentazione è utile per raccogliere informazioni dettagliate sugli intervalli relative a una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione.

 È possibile specificare il metodo di strumentazione tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura selezionare **Strumentazione**.

- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Strumentazione**.

- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni selezionare **Strumentazione**.

## <a name="common-tasks"></a>Attività comuni
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.

  Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo**Pagine delle proprietà** della sessione di _prestazioni_quando si esegue la profilata utilizzando il metodo di strumentazione.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** aggiungere dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Raccogliere dati sull'allocazione e la durata della memoria .NETCollect .NET memory allocation and lifetime data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: impostare le opzioni relative al nome del file di dati sulle prestazioniHow to: Set performance data file name options](../profiling/how-to-set-performance-data-file-name-options.md)|
|Nella pagina **Avvio** specificare l'applicazione da avviare e l'ordine di avvio se si hanno più progetti EXE nella soluzione.|-   [Procedura: specificare il file binario da avviareHow to: Specify the binary to start](../profiling/how-to-specify-the-binary-to-start.md)|
|Nella pagina **Binari** specificare un percorso per le copie instrumentate dei moduli. Per impostazione predefinita, i file binari originali vengono spostati in una cartella di backup.|-   [Procedura: riposizionare i file binari instrumentatiHow to: Relocate instrumented binaries](../profiling/how-to-relocate-instrumented-binaries.md)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Strumentazione** escludere le funzioni piccole dalla profilatura per ridurre il sovraccarico di profilatura, eseguire la profilatura del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire a un prompt dei comandi prima e dopo il processo di strumentazione.|-   [Procedura: escludere o includere funzioni brevi dalla strumentazioneHow to: Exclude or include short functions from instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Procedura: profilare il codice JavaScript nelle pagine WebHow to: Profile JavaScript code in web pages](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Procedura: specificare comandi pre e post-strumentazioneHow to: Specify pre- and post-instrument commands](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Nella pagina **Contatori CPU** specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilatura.|-   [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Nella pagina **Eventi di Windows** selezionare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|-   [Procedura: raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare le opzioni aggiuntive da passare al programma di strumentazione VSInstr, ad esempio le opzioni per includere o escludere funzioni specifiche.|-   [Procedura: specificare opzioni di strumentazione aggiuntiveHow to: Specify additional instrumentation options](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Procedura: limitare la strumentazione a funzioni specificheHow to: Limit instrumentation to specific functions](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VsInstr](../profiling/vsinstr.md)|
