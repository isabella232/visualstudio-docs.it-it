---
title: Proprietà della sessione di prestazioni | Microsoft Docs
description: Informazioni su come una sessione di prestazioni consente di configurare le impostazioni che determinano come viene profilata l'applicazione.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0fb9846958700e89ea4bc7cf12815ccf6335e39c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711527"
---
# <a name="performance-session-properties"></a>Proprietà della sessione di prestazioni

Una **sessione di prestazioni** consente di configurare le impostazioni che determinano la modalità di profilatura dell'applicazione. Include inoltre i rapporti generati per la sessione di profilatura.

È possibile creare una **sessione di prestazioni** eseguendo la **Creazione guidata sessione di prestazioni** o creando manualmente una sessione. La **sessione di prestazioni** viene visualizzata in **Esplora prestazioni** dopo che è stata creata la **sessione di prestazioni**.

Per visualizzare le proprietà della **sessione di prestazioni**, selezionare il nome della sessione in **Esplora prestazioni**, fare clic con il pulsante destro del mouse e quindi selezionare **Proprietà**.

La sessione di prestazioni presenta le pagine delle proprietà seguenti:

## <a name="general"></a>Generale

Queste impostazioni consentono di selezionare il metodo di profilatura, aggiungere dati di durata e raccolta di oggetti .NET e specificare il percorso e le convenzioni di denominazione predefiniti del rapporto.

Per altre informazioni, vedere:

[Procedura: Scegliere i metodi di raccolta](../profiling/how-to-choose-collection-methods.md)

[Raccogliere dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Procedura: Impostare le opzioni relative al nome del file di dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Launch

Queste impostazioni consentono di effettuare una selezione da un elenco di file binari e specificare il relativo ordine di avvio.

Per altre informazioni, vedere [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>campionamento

Queste impostazioni consentono di selezionare l'evento e l'intervallo di campionamento quando si usa il campionamento come metodo di profilatura. Un evento di campionamento viene usato per raccogliere i dati di profilatura secondo l'intervallo specificato. Ad esempio, se l'evento di campionamento è costituito dai cicli di clock e l'intervallo di campionamento è impostato su 10.000.000, i dati di profilatura verranno raccolti ogni 10 milioni di cicli di clock. Sono disponibili i quattro tipi di eventi di campionamento seguenti:

- Cicli di clock per i problemi legati alla CPU
- Errori di pagina per i problemi relativi alla memoria
- Chiamate di sistema per i problemi associati all'I/O
- Contatori di prestazioni per i problemi di prestazioni ridotte
- È possibile specificare eventi di campionamento aggiuntivi in base ai contatori delle prestazioni disponibili.

Per altre informazioni, vedere [Procedura: Scegliere gli eventi di campionamento](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>Binary
Queste impostazioni consentono di specificare se si desidera rilocare il file binario instrumentato in un'altra posizione. Ad esempio, se si  sta profilandoMy.DLLe si sceglie di non spostare  il file binario instrumentato, viene creata una copia di backupMy.DLLdenominata *My.Orig.DLL.* Successivamente, *My.DLL* viene modificato mediante l'inserimento di probe per raccogliere dati. Se si decide di rilocare il file binario instrumentato, il file binario originale non viene rinominato e il file binario instrumentato viene copiato nel percorso specificato in modo da essere usato durante la strumentazione.

Per altre informazioni, vedere [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Interazioni tra livelli

Per altre informazioni, vedere [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md).

## <a name="instrumentation"></a>Strumentazione

Queste impostazioni consentono di raccogliere i dati sulle prestazioni per il codice JScript nelle pagine Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e di specificare gli eventi di **pre-strumentazione** e **post-strumentazione** che devono verificarsi prima o dopo il processo di strumentazione.

Per altre informazioni, vedere:

[Procedura: Profilare il codice JavaScript nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Procedura: Specificare comandi pre- e post-strumentazione](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>Contatori CPU

Queste impostazioni consentono di raccogliere i dati sui contatori delle prestazioni della CPU quando si usa il metodo di profilatura della strumentazione. I contatori delle prestazioni portatili sono disponibili indipendentemente dal modello o dal produttore della CPU. Gli eventi piattaforma invece sono specifici del modello e del produttore della CPU. Per altre informazioni sui contatori di prestazioni relative al processore, vedere la documentazione relativa al processore specifico.

Per altre informazioni, vedere [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Eventi Windows

Durante la profilatura, è possibile raccogliere i dati dai provider di traccia eventi. I dati possono essere visualizzati usando l'opzione`/calltrace` dello strumento da riga di comando *VSPerfReport.exe*. Per altre informazioni su Event Tracing for Windows (ETW), vedere [About Event Tracing](/windows/win32/etw/about-event-tracing) (Informazioni su Event Tracing).

Per altre informazioni, vedere:

[Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Contatori Windows

Questa opzione consente di raccogliere i dati dai contatori di Windows Performance Monitor. Per raccogliere questi dati, selezionare la casella di controllo **Raccogliere contatori Windows**. L'intervallo di raccolta può essere impostato nella casella **Intervallo di raccolta**. Potrebbero essere inoltre disponibili le opzioni **Categoria contatori** e **Istanza**. Sono disponibili alcuni contatori predefiniti di Windows Performance Monitor.

 Per altre informazioni, vedere [Procedura: Raccogliere dati Windows contatore.](../profiling/how-to-collect-windows-counter-data.md)

## <a name="advanced"></a>Avanzato

Queste impostazioni consentono di aggiungere opzioni al processo di strumentazione specificando una o più opzioni dello strumento di profilatura da riga di comando [VSInstr](../profiling/vsinstr.md). È inoltre possibile specificare la versione di Common Runtime di cui eseguire la profilatura quando l'applicazione usa più di una versione.

Per altre informazioni, vedere:

[Procedura: Specificare il runtime di .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Vedi anche

[Panoramiche](../profiling/overviews-performance-tools.md) 
 [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md) 
 [Controllare la raccolta dei dati](../profiling/controlling-data-collection.md)
