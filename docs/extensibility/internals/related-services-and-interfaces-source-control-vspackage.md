---
title: Interfacce (VSPackage di controllo di origine) e servizi correlati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00bebd0a08acb9eeab369f5aa80b94e6805277b0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598999"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)
In questa sezione elenca tutte le interfacce correlate al pacchetto VSPackage in controllo di origine al [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Il controllo del codice sorgente pacchetto VSPackage implementa alcune di queste interfacce e usato da altri utenti per eseguire attività di controllo di origine.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per pacchetti VSPackage di controllo di origine
 Le interfacce seguenti sono descritti nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], e il controllo del codice sorgente pacchetto VSPackage implementa un subset di essi a seconda del relativo set di funzionalità desiderate. Alcune interfacce sono contrassegnate come obbligatorio e deve essere implementata da ogni controllo del codice sorgente VSPackage.

 Per tali interfacce che non implementa un pacchetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettato per il caso in cui non è registrato alcun pacchetto VSPackage e nessun progetto sono controllato. Un controllo del codice sorgente scritto correttamente. pacchetto VSPackage implementa le interfacce di tutte le necessarie anziché lasciarla per l'implementazione predefinita di tali interfacce.

 Un controllo del codice sorgente VSPackage deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.

 Le interfacce sono:

-   Obbligatorie: L'entità appropriata (progetto di controllo del codice sorgente VSPackage, Stub di controllo, origine) deve implementare l'interfaccia.

-   Consigliato: L'entità deve implementare questa interfaccia. in caso contrario, controllo del codice sorgente può essere limitato.

-   Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più avanzato.

| Interfaccia | Scopo | Implementato da | Implementare? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editor di chiamare questa interfaccia prima di modificare o salvare un file. Il controllo del codice sorgente pacchetto VSPackage può estrarre il file o nega l'operazione se l'estrazione ha esito negativo. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Questa interfaccia fornisce funzionalità di controllo di origine di base per i progetti, ad esempio la registrazione e annullamento della registrazione di progetti con controllo del codice sorgente e offrire supporto per i glifi del controllo origine di base. | Controllo del codice sorgente VSPackage | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Questa interfaccia viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> usando il <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funzione, o eseguendo semplicemente il cast dell'oggetto che implementa `IVsHierarchy` a `IVsSccProject2`. Viene utilizzato per ottenere i file in controllo del codice sorgente in un progetto o per informare il progetto del percorso o lo stato corrente del controllo origine. | Progetto | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Il modulo di integrazione Usa questa interfaccia per impostare il pacchetto VSPackage attivo corrente. | Controllo del codice sorgente VSPackage | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi pacchetto VSPackage può segnalare che vuole ricevere gli eventi del documento e tenere dalla shell sugli eventi che stanno per verificarsi. Si è implementato e gestito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], che a sua volta passa gli eventi che implementa il `IVsTrackProjectDocumentsEvents2` al pacchetto VSPackage. | Stub di controllo di origine | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Questa interfaccia fornisce l'elaborazione batch, operazioni di lettura/scrittura sincronizzato e un avanzato `OnQueryAddFiles` (metodo). | Stub di controllo di origine | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Esplora soluzioni** e progetti di chiamare questa interfaccia quando vengono aggiunti nuovi file per i progetti oppure quando vengono rinominate o eliminate dai progetti di file e cartelle. Il controllo del codice sorgente VSPackage può estrarre il file di progetto o annullare l'operazione. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Esplora soluzioni** e progetti di chiamare questa interfaccia in risposta alle chiamate ai metodi dell'interfaccia IVstrackProjectDocuments3. Operazioni di lettura/scrittura, il controllo del codice sorgente VSPackage può tenere traccia delle operazioni in batch, sincronizzate e lavorare con un più avanzati `OnQueryAddFiles` (metodo). | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Questa interfaccia fornisce supporto di gestione di integrazione per i progetti Web. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Questa interfaccia viene utilizzata per recuperare le descrizioni comandi per i file di controllo del codice sorgente nei progetti. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Questa interfaccia fornisce supporto delle estensioni dello spazio dei nomi. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Il pacchetto VSPackage Usa questa interfaccia per integrare un'estensione dello spazio dei nomi nel **New**, **Open**, o **Salva** finestre di dialogo. Di conseguenza, i progetti possono essere automaticamente aggiunti al controllo del codice sorgente al momento della creazione o aggiunto al controllo del codice sorgente durante un salvataggio operazione è attiva. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Il pacchetto VSPackage Usa questa interfaccia per definire glifi aggiuntivi come glifi del controllo origine per i nodi **Esplora soluzioni**. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Il **Add** finestra di dialogo per i progetti Web Usa questa interfaccia. Fornisce metodi per la visualizzazione per un percorso di controllo di origine e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo di origine in tale posizione. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Questa interfaccia fornisce supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Questa interfaccia consente ai progetti di seguire l'avanzamento del caricamento asincrono avviato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Progetto | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Questa interfaccia consente all'IDE di query sul VSPackage di controllo di origine attiva. L'IDE di una query il valore delle impostazioni di controllo di origine che hanno un significato anche quando non esiste alcun controllo del codice sorgente attivo che VSPackage registrati. Questa interfaccia è implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Stub di controllo di origine | Obbligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Questa interfaccia viene utilizzata la registrazione di VSPackage di controllo del codice sorgente. | Stub di controllo di origine | Obbligatorio |
| <xref:EnvDTE.SourceControl> | Questa interfaccia viene utilizzata nel modello di automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare alcuna interfaccia utente. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Questa interfaccia viene utilizzata per salvare l'origine delle impostazioni di controllo nel file di soluzione (sln). Le impostazioni includono il percorso e flag di stato di controllo di origine. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Questa interfaccia viene utilizzata per salvare le impostazioni di controllo di origine nel file di opzioni (con estensione suo) della soluzione. Ciò può includere impostazioni di controllo di origine specifici dell'utente, ad esempio posizione di inserimento dell'utente corrente. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Questa interfaccia viene utilizzata per monitorare gli eventi per eseguire operazioni quali l'archiviazione dei file di progetto prima della chiusura di soluzioni, o per ottenere nuovi file dal controllo del codice sorgente quando si apre un progetto. | Controllo del codice sorgente VSPackage | Consigliato |

## <a name="see-also"></a>Vedere anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)