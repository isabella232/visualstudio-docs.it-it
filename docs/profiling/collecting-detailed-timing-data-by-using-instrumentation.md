---
title: Raccogliere dati di intervallo dettagliati tramite la strumentazione
description: Usare il Strumenti di profilatura di strumentazione per informazioni dettagliate sugli intervalli relativi a una sezione del codice e per comprendere l'impatto delle operazioni di I/O.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc7f3596175c2259a3f1c8054f1bacd4e3be0513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107940"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Raccogliere dati di intervallo dettagliati tramite la strumentazione
Il metodo di strumentazione degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inserisce il codice di profilatura in una copia di un modulo. Il codice registra ogni voce, uscita e chiamata di funzione delle funzioni nel modulo durante un'esecuzione di profilatura. Il metodo di strumentazione è utile per raccogliere informazioni dettagliate sugli intervalli relative a una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione.

 È possibile specificare il metodo di strumentazione tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura selezionare **Strumentazione**.

- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Strumentazione**.

- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni selezionare **Strumentazione**.

## <a name="common-tasks"></a>Attività comuni
 È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi **scegliere Proprietà.**

  Le attività nella tabella seguente descrivono le  opzioni che è possibile specificare nella finestra di dialogo Pagine delle proprietà della sessione di prestazioni quando si esegue la profilatura usando il metodo di strumentazione.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** aggiungere dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Raccogliere dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: Impostare le opzioni relative al nome del file di dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|
|Nella pagina **Avvio** specificare l'applicazione da avviare e l'ordine di avvio se si hanno più progetti EXE nella soluzione.|-   [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)|
|Nella pagina **Binari** specificare un percorso per le copie instrumentate dei moduli. Per impostazione predefinita, i file binari originali vengono spostati in una cartella di backup.|-   [Procedura: Rilocare file binari instrumentati](../profiling/how-to-relocate-instrumented-binaries.md)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Strumentazione** escludere le funzioni piccole dalla profilatura per ridurre il sovraccarico di profilatura, eseguire la profilatura del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire a un prompt dei comandi prima e dopo il processo di strumentazione.|-   [Procedura: Escludere o includere funzioni brevi dalla strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Procedura: Profilare il codice JavaScript nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Procedura: Specificare comandi pre-strumentazione e post-strumentazione](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Nella pagina **Contatori CPU** specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilatura.|-   [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Nella pagina **Eventi di Windows** selezionare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|-   [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare le opzioni aggiuntive da passare al programma di strumentazione VSInstr, ad esempio le opzioni per includere o escludere funzioni specifiche.|-   [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Procedura: Limitare la strumentazione a funzioni specifiche](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
