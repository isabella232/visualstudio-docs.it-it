---
title: Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)
titleSuffix: ''
description: Informazioni sulle interfacce correlate a VSPackage per il controllo del codice sorgente in Visual Studio SDK. Il pacchetto implementa alcune interfacce e ne utilizza altre per il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af5c971b804e1c288bf710f6627c0e769e790ee1
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876350"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)

Questa sezione elenca tutte le interfacce correlate a VSPackage del controllo del codice sorgente in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Il pacchetto VSPackage del controllo del codice sorgente implementa alcune di queste interfacce e usa altre per eseguire le attività di controllo del codice sorgente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per i pacchetti VSPackage del controllo del codice sorgente

 Le interfacce seguenti sono descritte in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] e il pacchetto VSPackage del controllo del codice sorgente implementa un subset di tali interfacce a seconda del set di funzionalità desiderato. Alcune interfacce sono contrassegnate come obbligatorie e devono essere implementate da ogni VSPackage del controllo del codice sorgente.

 Per le interfacce non implementate da un pacchetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettata per il caso in cui non viene registrato alcun pacchetto VSPackage e non è controllato alcun progetto. Un VSPackage del controllo del codice sorgente scritto correttamente implementa tutte le interfacce necessarie anziché lasciarlo all'implementazione predefinita di tali interfacce.

 Un pacchetto VSPackage del controllo del codice sorgente deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.

 Le interfacce sono:

- Obbligatorio: l'entità appropriata (VSPackage del controllo del codice sorgente, stub del controllo del codice sorgente, progetto) deve implementare l'interfaccia.

- Consigliato: l'entità deve implementare questa interfaccia; in caso contrario, la funzionalità del controllo del codice sorgente può essere limitata.

- Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più completo.

| Interfaccia | Scopo | Implementato da | Implementare? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Gli editor chiamano questa interfaccia prima di modificare o salvare un file. Il pacchetto VSPackage del controllo del codice sorgente può estrarre il file o negare l'operazione se l'estrazione ha esito negativo. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Questa interfaccia fornisce la funzionalità di base del controllo del codice sorgente per i progetti, ad esempio la registrazione e l'annullamento della registrazione di progetti con il controllo del codice sorgente e il supporto per i glifi di controllo del codice sorgente | VSPackage del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Questa interfaccia viene ottenuta dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto utilizzando la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funzione o semplicemente eseguendo il cast dell'oggetto `IVsHierarchy` che implementa a `IVsSccProject2` . Viene usato per ottenere i file nel controllo del codice sorgente in un progetto o per informare il progetto dello stato o del percorso del controllo del codice sorgente corrente. | Progetto | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Il modulo di integrazione usa questa interfaccia per impostare il pacchetto VSPackage attivo corrente. | VSPackage del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi pacchetto VSPackage può segnalare che desidera ricevere gli eventi del documento ed essere informati dalla shell sugli eventi che stanno per verificarsi. Viene implementato e gestito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , che a sua volta passa gli eventi che implementano al `IVsTrackProjectDocumentsEvents2` pacchetto VSPackage. | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Questa interfaccia fornisce l'elaborazione batch, le operazioni di lettura/scrittura sincronizzate e un `OnQueryAddFiles` metodo avanzato. | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Esplora soluzioni** e i progetti chiamano questa interfaccia quando i nuovi file vengono aggiunti ai progetti o quando i file e le cartelle vengono rinominati o eliminati da progetti. Il pacchetto VSPackage del controllo del codice sorgente può estrarre il file di progetto o annullare l'operazione. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Esplora soluzioni** e i progetti chiamano questa interfaccia in risposta alle chiamate effettuate ai metodi dell'interfaccia IVstrackProjectDocuments3. Il pacchetto VSPackage del controllo del codice sorgente può tenere traccia delle operazioni in batch, le operazioni di lettura/scrittura sincronizzate e usare un metodo più avanzato `OnQueryAddFiles` . | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Questa interfaccia fornisce supporto per la gestione dell'integrazione per i progetti Web. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Questa interfaccia viene utilizzata per recuperare le descrizioni comandi per i file inclusi nel controllo del codice sorgente nei progetti. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Questa interfaccia fornisce il supporto dell'estensione dello spazio dei nomi. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Il pacchetto VSPackage usa questa interfaccia per integrare un'estensione dello spazio dei nomi nelle finestre di dialogo **nuovo**, **Apri** o **Salva** . Di conseguenza, i progetti possono essere aggiunti automaticamente al controllo del codice sorgente durante la creazione o aggiunti al controllo del codice sorgente quando è attiva un'operazione di salvataggio. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Il pacchetto VSPackage usa questa interfaccia per definire glifi aggiuntivi come glifi del controllo del codice sorgente per i nodi in **Esplora soluzioni**. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Questa interfaccia viene utilizzata dalla finestra di dialogo **Aggiungi** per i progetti Web. Fornisce metodi per l'esplorazione di un percorso del controllo del codice sorgente e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo del codice sorgente in quel percorso. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Questa interfaccia fornisce il supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Questa interfaccia consente ai progetti di controllare lo stato di avanzamento del caricamento asincrono avviato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Progetto | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Questa interfaccia consente all'IDE di eseguire una query sul VSPackage del controllo del codice sorgente attivo. L'IDE esegue una query sul valore delle impostazioni di controllo del codice sorgente che hanno un significato anche quando non è stato registrato alcun VSPackage del controllo del codice sorgente attivo. Questa interfaccia viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Questa interfaccia viene utilizzata per la registrazione del pacchetto VSPackage del controllo del codice sorgente. | Stub del controllo del codice sorgente | Necessario |
| <xref:EnvDTE.SourceControl> | Questa interfaccia viene usata in automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare alcuna interfaccia utente. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Questa interfaccia viene utilizzata per salvare le impostazioni del controllo del codice sorgente nel file di soluzione (con estensione sln). Le impostazioni includono il percorso del controllo del codice sorgente e i flag di stato del controllo del codice sorgente. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Questa interfaccia viene utilizzata per salvare le impostazioni del controllo del codice sorgente nel file delle opzioni di soluzione (con estensione suo). Questo può includere impostazioni di controllo del codice sorgente specifiche dell'utente, ad esempio il percorso di integrazione dell'utente corrente. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Questa interfaccia viene utilizzata per monitorare gli eventi in modo da eseguire operazioni quali l'archiviazione dei file di progetto prima di chiudere le soluzioni o il recupero di nuovi file dal controllo del codice sorgente all'apertura di un progetto. | VSPackage del controllo del codice sorgente | Consigliato |

## <a name="see-also"></a>Vedi anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
