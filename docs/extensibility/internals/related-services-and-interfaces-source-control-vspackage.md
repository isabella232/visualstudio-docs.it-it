---
title: Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)
titleSuffix: ''
description: Informazioni sulle interfacce correlate al pacchetto VSPackage del controllo del codice sorgente in Visual Studio SDK. Il pacchetto implementa alcune interfacce e ne usa altre per il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6385307c91541204d58228b489160888f79dec85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903333"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)

Questa sezione elenca tutte le interfacce correlate al pacchetto VSPackage del controllo del codice sorgente in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Il controllo del codice sorgente VSPackage implementa alcune di queste interfacce e ne usa altre per eseguire attività di controllo del codice sorgente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per vspackage del controllo del codice sorgente

 Le interfacce seguenti sono descritte in e il controllo del codice sorgente VSPackage implementa un subset di queste interfacce a seconda del [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] set di funzionalità desiderato. Alcune interfacce sono contrassegnate come obbligatorie e devono essere implementate da ogni VSPackage del controllo del codice sorgente.

 Per le interfacce non implementate da un pacchetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettata per il caso in cui non viene registrato alcun VSPackage e non viene controllato alcun progetto. Un pacchetto VSPackage del controllo del codice sorgente scritto correttamente implementa tutte le interfacce necessarie anziché lasciarlo all'implementazione predefinita di tali interfacce.

 Un VSPackage del controllo del codice sorgente deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.

 Le interfacce sono:

- Obbligatorio: l'entità appropriata (vspackage del controllo del codice sorgente, stub del controllo del codice sorgente, progetto) deve implementare l'interfaccia .

- Consigliato: l'entità deve implementare questa interfaccia. In caso contrario, la funzionalità del controllo del codice sorgente potrebbe essere limitata.

- Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più ricco.

| Interfaccia | Scopo | Implementato da | Implementare? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Gli editor chiamano questa interfaccia prima di modificare o salvare un file. Il pacchetto VSPackage del controllo del codice sorgente può estrarre il file o negare l'operazione se l'estrazione ha esito negativo. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Questa interfaccia fornisce funzionalità di base per il controllo del codice sorgente per i progetti, ad esempio la registrazione e l'annullamento della registrazione dei progetti con il controllo del codice sorgente e il supporto per i glifi di base del controllo del codice sorgente. | VSPackage del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Questa interfaccia viene ottenuta da utilizzando la funzione o semplicemente eseguendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> cast dell'oggetto che implementa a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> `IVsHierarchy` `IVsSccProject2` . Viene usato per ottenere i file nel controllo del codice sorgente in un progetto o per informare il progetto dello stato o del percorso corrente del controllo del codice sorgente. | Project | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Il modulo di integrazione usa questa interfaccia per impostare il VSPackage attivo corrente. | VSPackage del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi VSPackage può segnalare che vuole ricevere eventi del documento ed essere avvisato dalla shell sugli eventi che stanno per verificarsi. Viene implementato e gestito da , che a sua volta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] passa gli eventi che `IVsTrackProjectDocumentsEvents2` implementano al pacchetto VSPackage. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Questa interfaccia fornisce l'elaborazione batch, le operazioni di lettura/scrittura sincronizzate e un metodo `OnQueryAddFiles` avanzato. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Esplora soluzioni** e i progetti chiamano questa interfaccia quando vengono aggiunti nuovi file ai progetti o quando i file e le cartelle vengono rinominati o eliminati dai progetti. Il controllo del codice sorgente VSPackage può estrarre il file di progetto o annullare l'operazione. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Esplora soluzioni** e i progetti chiamano questa interfaccia in risposta alle chiamate effettuate ai metodi dell'interfaccia IVstrackProjectDocuments3. Il pacchetto VSPackage del controllo del codice sorgente può tenere traccia delle operazioni in batch, delle operazioni di lettura/scrittura sincronizzate e usare un metodo più `OnQueryAddFiles` avanzato. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Questa interfaccia fornisce il supporto per la gestione dell'integrazione per i progetti Web. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Questa interfaccia viene usata per recuperare le descrizioni comandi per i file controllati dal codice sorgente nei progetti. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Questa interfaccia fornisce il supporto dell'estensione dello spazio dei nomi. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Il pacchetto VSPackage usa questa interfaccia per integrare un'estensione dello spazio dei nomi nelle **finestre di** dialogo Nuovo **,** Apri **o** Salva . Di conseguenza, i progetti possono essere aggiunti automaticamente al controllo del codice sorgente al momento della creazione o al controllo del codice sorgente quando è attiva un'operazione di salvataggio. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Il pacchetto VSPackage usa questa interfaccia per definire glifi aggiuntivi come glifi del controllo del codice sorgente per i nodi in **Esplora soluzioni**. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | La **finestra di** dialogo Aggiungi per i progetti Web usa questa interfaccia. Fornisce metodi per l'esplorazione di un percorso del controllo del codice sorgente e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo del codice sorgente in tale percorso. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Questa interfaccia fornisce il supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Questa interfaccia consente ai progetti di controllare lo stato di avanzamento del caricamento asincrono avviato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Questa interfaccia consente all'IDE di eseguire query sul pacchetto VSPackage del controllo del codice sorgente attivo. L'IDE esegue una query sul valore delle impostazioni del controllo del codice sorgente che hanno significato anche quando non è registrato alcun VSPackage del controllo del codice sorgente attivo. Questa interfaccia viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Questa interfaccia viene usata nella registrazione del pacchetto VSPackage del controllo del codice sorgente. | Stub del controllo del codice sorgente | Obbligatoria |
| <xref:EnvDTE.SourceControl> | Questa interfaccia viene usata nell'automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare alcuna interfaccia utente. | VSPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Questa interfaccia viene usata per salvare le impostazioni del controllo del codice sorgente nel file di soluzione (sln). Le impostazioni includono il percorso del controllo del codice sorgente e i flag di stato del controllo del codice sorgente. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Questa interfaccia viene usata per salvare le impostazioni del controllo del codice sorgente nel file delle opzioni della soluzione (con estensione suo). Può includere impostazioni di controllo del codice sorgente specifiche dell'utente, ad esempio il percorso di integrazione dell'utente corrente. | VSPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Questa interfaccia viene usata per monitorare gli eventi per eseguire operazioni quali l'archiviazione dei file di progetto prima della chiusura delle soluzioni o il recupero di nuovi file dal controllo del codice sorgente all'apertura di un progetto. | VSPackage del controllo del codice sorgente | Consigliato |

## <a name="see-also"></a>Vedere anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
