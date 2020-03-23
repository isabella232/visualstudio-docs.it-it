---
title: Raccolta di dati di durata e allocazione di memoria .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6a8c5d431b7be54c4c5bc1a1c37619deb67de751
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779584"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>Raccogliere dati di durata e allocazione di memoria .NET

Gli strumenti di profilatura di Visual Studio supportano la raccolta di dati di durata e allocazione di memoria .NET. Ciò consente di rilevare problemi nelle prestazioni dell'applicazione correlate alla memoria.

- I dati sull'allocazione di memoria .NET includono le dimensioni e il numero di oggetti di memoria .NET Framework allocati.

- I dati sulla durata degli oggetti includono le dimensioni e il numero degli oggetti di memoria .NET Framework recuperati in tre generazioni di garbage collection.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

È possibile raccogliere i dati tramite il metodo di campionamento o il metodo di profilatura della strumentazione.

- Se si usa il metodo di campionamento, il profiler tiene traccia di tutte le allocazioni e di tutti gli oggetti di memoria .NET generati dal processo avviato o a cui è connesso.

- Se si usa il metodo di strumentazione, il profiler tiene traccia solo delle allocazioni e degli oggetti di memoria .NET generati dai moduli sottoposti a strumentazione.

> [!IMPORTANT]
> Quando si raccolgono dati di memoria .NET (allocazioni, durata degli oggetti o entrambi) usando il metodo di campionamento, tutti gli eventi di campionamento specificati dall'utente vengono ignorati e per raccogliere i dati vengono usati gli eventi di allocazione di memoria appropriati.

Se si abilita la profilatura dell'allocazione di memoria .NET, si abilita anche la visualizzazione Allocazione. Se si abilita la profilatura dei dati di durata .NET,si abilita anche la visualizzazione Durata oggetti. Per altre informazioni, vedere la [visualizzazione Allocazione](../profiling/dotnet-memory-allocations-view.md) e la [visualizzazione Durata oggetti](../profiling/object-lifetime-view.md).

Per informazioni su come raccogliere dati di memoria .NET tramite gli strumenti di profilatura della riga di comando, vedere Using .NET Memory Methods to Collect Memory Allocation and Object Lifetime Data (Uso dei metodi di memoria .NET per raccogliere dati di allocazione di memoria e durata degli oggetti) in [Profiling Methods From the Command Line](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md) (Uso di metodi di profilatura dalla riga di comando).

## <a name="to-collect-net-memory-data"></a>Per raccogliere dati di memoria .NET

1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. Nella finestra di dialogo *Pagine delle proprietà della * **sessione di prestazioni** fare clic sulla scheda **Generale** e selezionare la casella di controllo **Raccogliere le informazioni sull'allocazione dell'oggetto .NET**.

3. Per raccogliere dati sulla durata degli oggetti .NET, selezionare la casella di controllo **Raccogliere anche le informazioni sulla durata dell'oggetto .NET**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo _Pagine delle proprietà_**Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.

Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo _Pagine delle proprietà_ della **sessione di prestazioni** quando si raccolgono dati di memoria .NET.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [Raccogliere dati sull'allocazione e la durata della memoria .NETCollect .NET memory allocation and lifetime data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Procedura: impostare le opzioni relative al nome del file di dati sulle prestazioniHow to: Set performance data file name options](../profiling/how-to-set-performance-data-file-name-options.md)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** scegliere l'applicazione da avviare.|- [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|- [Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Eventi di Windows** specificare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|- [Procedura: raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [Procedura: specificare il runtime di .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Attività di strumentazione

Le attività nella tabella seguente sono opzioni della finestra di dialogo **Pagine delle proprietà** specifiche della profilatura con il metodo di strumentazione.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Binari** specificare un percorso per le copie instrumentate dei moduli. Per impostazione predefinita, i file binari originali vengono spostati in una cartella di backup.|- [Procedura: riposizionare i binari instrumentatiHow to: Relocate Instrumented Binaries](../profiling/how-to-relocate-instrumented-binaries.md)|
|Nella pagina **Strumentazione** escludere le funzioni piccole dalla profilatura per ridurre il sovraccarico di profilatura, eseguire la profilatura del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire a un prompt dei comandi prima e dopo il processo di strumentazione.|- [Procedura: escludere o includere funzioni brevi dalla strumentazioneHow to: Exclude or include short functions from instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [How to: Profile JavaScript Code in Web Pages](../profiling/how-to-profile-javascript-code-in-web-pages.md) (Procedura: Profilare codice JavaScript nelle pagine Web)<br />- [Procedura: specificare comandi pre e post-strumentazioneHow to: Specify Pre- and Post-Instrument Commands](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Nella pagina **Contatori CPU** specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilatura.|- [Procedura: raccogliere i dati del contatore della CPUHow to: Collect CPU Counter Data](../profiling/how-to-collect-cpu-counter-data.md)|
|Nella pagina **Avanzate** specificare eventuali opzioni di VSInstr.exe aggiuntive, ad esempio le opzioni per includere o escludere funzioni specifiche. Per altre informazioni sulle opzioni di VSInstr, vedere [VSInstr](../profiling/vsinstr.md)|- [Procedura: specificare opzioni di strumentazione aggiuntiveHow to: Specify additional instrumentation options](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Procedura: limitare la strumentazione a funzioni specificheHow to: Limit instrumentation to specific functions](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
Procedura: scegliere i metodi di raccolta Proprietà della sessione[di prestazioniConfigure](../profiling/performance-session-properties.md) performance sessions[How to: Choose collection methods](../profiling/how-to-choose-collection-methods.md)
Performance session properties
