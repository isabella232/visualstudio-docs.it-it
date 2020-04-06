---
title: Servizi correlati e interfacce (controllo del codice sorgente VSPackage) . Documenti Microsoft
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
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705633"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)
In questa sezione sono elencate tutte le interfacce [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]correlate al controllo del codice sorgente VSPackage nel file . Il controllo del codice sorgente VSPackage implementa alcune di queste interfacce e utilizza altri per eseguire attività di controllo del codice sorgente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per i package VS del controllo del codice sorgenteInterfaces Implemented by and for Source Control VSPackages
 Le interfacce seguenti sono [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]descritte in , e il controllo del codice sorgente VSPackage implementa un sottoinsieme di essi a seconda del set di funzionalità desiderato. Alcune interfacce sono contrassegnate come obbligatorie e devono essere implementate da ogni controllo del codice sorgente VSPackage.Some interfaces are marked as required and must be implemented by every source control VSPackage.

 Per le interfacce non implementate [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da un pacchetto, fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettata per il caso in cui non viene registrato alcun VSPackage e non è controllato alcun progetto. Un controllo del codice sorgente scritto correttamente VSPackage implementa tutte le interfacce necessarie anziché lasciarlo all'implementazione predefinita di tali interfacce.

 Un controllo del codice sorgente VSPackage deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.

 Le interfacce sono:

- Obbligatorio: l'entità appropriata (controllo del codice sorgente VSPackage, Stub controllo del codice sorgente, progetto) deve implementare l'interfaccia.

- Consigliato: l'entità deve implementare questa interfaccia. in caso contrario, la funzionalità del controllo del codice sorgente potrebbe essere limitata.

- Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più completo.

| Interfaccia | Scopo | Implementato da | Implementare? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Gli editor chiamano questa interfaccia prima di modificare o salvare un file. Il controllo del codice sorgente VSPackage può estrarre il file o negare l'operazione se l'estrazione non riesce. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Questa interfaccia fornisce funzionalità di base del controllo del codice sorgente per i progetti, ad esempio la registrazione e l'annullamento della registrazione di progetti con il controllo del codice sorgente e fornisce il supporto per i glifi del controllo del codice sorgente di base. | Controllo del codice sorgente VSPackage | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Questa interfaccia viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ottenuta <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dall'oggetto using la `IVsHierarchy` funzione `IVsSccProject2`o semplicemente eseguendo il cast dell'oggetto implementato in . Viene utilizzato per ottenere i file nel controllo del codice sorgente in un progetto o per informare il progetto dello stato o del percorso del controllo del codice sorgente corrente. | Project | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Il modulo di integrazione utilizza questa interfaccia per impostare il pacchetto VSPackage attivo corrente. | Controllo del codice sorgente VSPackage | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi VSPackage può segnalare che si desidera ricevere gli eventi del documento ed essere consigliato dalla shell sugli eventi che stanno per verificarsi. Viene implementato e gestito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]da , che a `IVsTrackProjectDocumentsEvents2` sua volta passa gli eventi che implementano il al pacchetto VSPackage. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Questa interfaccia fornisce l'elaborazione batch, le `OnQueryAddFiles` operazioni di lettura/scrittura sincronizzate e un metodo avanzato. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Esplora soluzioni** e i progetti chiamano questa interfaccia quando vengono aggiunti nuovi file ai progetti o quando file e cartelle vengono rinominati o eliminati dai progetti. Il controllo del codice sorgente VSPackage può estrarre il file di progetto o annullare l'operazione. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Esplora soluzioni** e progetti chiamano questa interfaccia in risposta alle chiamate effettuate ai metodi del IVstrackProjectDocuments3 interfaccia. Il controllo del codice sorgente VSPackage può tenere traccia delle operazioni in `OnQueryAddFiles` batch, sincronizzate operazioni di lettura/scrittura e utilizzare un metodo più avanzato. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Questa interfaccia fornisce il supporto della gestione dell'elenco per i progetti Web.This interface provides enlistment management support for Web projects. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Questa interfaccia viene utilizzata per recuperare le descrizioni comandi per i file controllati dal codice sorgente nei progetti. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Questa interfaccia fornisce il supporto dell'estensione dello spazio dei nomi. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Il pacchetto VSPackage utilizza questa interfaccia per integrare un'estensione dello spazio dei nomi nelle finestre di dialogo **Nuovo**, **Apri**o **Salva** . Di conseguenza, i progetti possono essere aggiunti automaticamente al controllo del codice sorgente al momento della creazione o aggiunti al controllo del codice sorgente quando è attiva un'operazione di salvataggio. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Il pacchetto VSPackage utilizza questa interfaccia per definire glifi aggiuntivi come glifi del controllo del codice sorgente per i nodi in **Esplora soluzioni.** | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | La finestra di dialogo **Aggiungi** per i progetti Web utilizza questa interfaccia. Fornisce metodi per l'esplorazione di un percorso del controllo del codice sorgente e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo del codice sorgente in tale percorso. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Questa interfaccia fornisce il supporto per il caricamento asincrono (in background) di progetti dal controllo del codice sorgente. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Questa interfaccia consente ai progetti di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>controllare lo stato di avanzamento del caricamento asincrono avviato da . | Project | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Questa interfaccia consente all'IDE di eseguire una query sul controllo del codice sorgente attivo VSPackage.This interface allows the IDE to query the active source control VSPackage. L'IDE esegue una query sul valore delle impostazioni del controllo del codice sorgente che hanno significato anche quando non è registrato alcun controllo del codice sorgente attivo VSPackage.The IDE queries the value of source control settings that have meaning even when there is no active source control VSPackage registered. Questa interfaccia viene implementata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]e gestita da . | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Questa interfaccia viene utilizzata nella registrazione del controllo del codice sorgente VSPackage.This interface is used in registering the source control VSPackage. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:EnvDTE.SourceControl> | Questa interfaccia viene utilizzata nell'automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare alcuna interfaccia utente. | Controllo del codice sorgente VSPackage | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Questa interfaccia viene utilizzata per salvare le impostazioni del controllo del codice sorgente nel file di soluzione (sln). Le impostazioni includono il percorso del controllo del codice sorgente e i flag di stato del controllo del codice sorgente. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Questa interfaccia viene utilizzata per salvare le impostazioni del controllo del codice sorgente nel file delle opzioni della soluzione (con estensione suo). Ciò può includere le impostazioni del controllo del codice sorgente specifiche dell'utente, ad esempio la posizione di elenco dell'utente corrente. | Controllo del codice sorgente VSPackage | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Questa interfaccia viene utilizzata per monitorare gli eventi per eseguire operazioni quali l'archiviazione dei file di progetto prima di chiudere le soluzioni o ottenere nuovi file dal controllo del codice sorgente all'apertura di un progetto. | Controllo del codice sorgente VSPackage | Consigliato |

## <a name="see-also"></a>Vedere anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
