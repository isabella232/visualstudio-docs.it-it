---
title: Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)
titleSuffix: ''
description: Informazioni sulle interfacce correlate al vspackage del controllo del codice sorgente in Visual Studio SDK. Il pacchetto implementa alcune interfacce e ne usa altre per il controllo del codice sorgente.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a51c5894234aba9b0689ee5ff940720ebab4c3e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709503"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)

Questa sezione elenca tutte le interfacce correlate al pacchetto VSPackage del controllo del codice sorgente in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Il pacchetto VSPackage del controllo del codice sorgente implementa alcune di queste interfacce e ne usa altre per eseguire attività di controllo del codice sorgente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per i pacchetti VSPackage del controllo del codice sorgente

 Le interfacce seguenti sono descritte in e il pacchetto VSPackage del controllo del codice sorgente ne implementa un subset a seconda [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] del set di funzionalità desiderato. Alcune interfacce sono contrassegnate come obbligatorie e devono essere implementate da ogni VSPackage del controllo del codice sorgente.

 Per le interfacce non implementate da un pacchetto, fornisce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un'implementazione predefinita. Si noti che l'implementazione predefinita è progettata per il caso in cui non viene registrato alcun VSPackage e non viene controllato alcun progetto. Un pacchetto VSPackage del controllo del codice sorgente scritto correttamente implementa tutte le interfacce necessarie anziché lasciarlo all'implementazione predefinita di tali interfacce.

 Un VSPackage del controllo del codice sorgente deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.

 Le interfacce sono:

- Obbligatorio: l'entità appropriata (vspackage del controllo del codice sorgente, stub del controllo del codice sorgente, progetto) deve implementare l'interfaccia .

- Consigliato: l'entità deve implementare questa interfaccia. In caso contrario, la funzionalità di controllo del codice sorgente potrebbe essere limitata.

- Facoltativo: l'entità può implementare questa interfaccia per fornire un set di funzionalità più ricco.

| Interfaccia | Scopo | Implementato da | Implementare? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Gli editor chiamano questa interfaccia prima di modificare o salvare un file. Il pacchetto VSPackage del controllo del codice sorgente può estrarre il file o negare l'operazione se l'estrazione non riesce. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Questa interfaccia fornisce funzionalità di base per il controllo del codice sorgente per i progetti, ad esempio la registrazione e l'annullamento della registrazione di progetti con il controllo del codice sorgente e il supporto per i glifi di base del controllo del codice sorgente. | VsPackage del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Questa interfaccia viene ottenuta da usando la funzione o semplicemente eseguendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> cast dell'oggetto che implementa `IVsHierarchy` a `IVsSccProject2` . Viene usato per ottenere i file nel controllo del codice sorgente in un progetto o per informare il progetto dello stato o del percorso corrente del controllo del codice sorgente. | Project | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Il modulo di integrazione usa questa interfaccia per impostare il VSPackage attivo corrente. | VsPackage del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi PACCHETTO VSPackage può segnalare che vuole ricevere eventi di documenti ed essere consigliato dalla shell per gli eventi che stanno per verificarsi. Viene implementato e gestito da , che a sua volta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] passa gli eventi che `IVsTrackProjectDocumentsEvents2` implementano al VSPackage. | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Questa interfaccia fornisce l'elaborazione batch, le operazioni di lettura/scrittura sincronizzate e un metodo `OnQueryAddFiles` avanzato. | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Esplora soluzioni** e i progetti chiamano questa interfaccia quando vengono aggiunti nuovi file ai progetti o quando i file e le cartelle vengono rinominati o eliminati dai progetti. Il pacchetto VSPackage del controllo del codice sorgente può estrarre il file di progetto o annullare l'operazione. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Esplora soluzioni** progetti e chiamano questa interfaccia in risposta alle chiamate effettuate ai metodi dell'interfaccia IVstrackProjectDocuments3. Il pacchetto VSPackage del controllo del codice sorgente può tenere traccia delle operazioni in batch, delle operazioni di lettura/scrittura sincronizzate e usare un metodo più `OnQueryAddFiles` avanzato. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Questa interfaccia fornisce il supporto per la gestione dell'integrazione per i progetti Web. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Questa interfaccia viene usata per recuperare le descrizioni comandi per i file del controllo del codice sorgente nei progetti. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Questa interfaccia fornisce il supporto dell'estensione dello spazio dei nomi. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Il pacchetto VSPackage usa questa interfaccia per integrare un'estensione dello spazio dei nomi **nelle finestre di** dialogo Nuovo , Apri **o** Salva .  Di conseguenza, i progetti possono essere aggiunti automaticamente al controllo del codice sorgente al momento della creazione o al controllo del codice sorgente quando è attiva un'operazione di salvataggio. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Il VSPackage usa questa interfaccia per definire glifi aggiuntivi come glifi del controllo del codice sorgente per i nodi in **Esplora soluzioni**. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | La **finestra di** dialogo Aggiungi per i progetti Web usa questa interfaccia. Fornisce metodi per l'esplorazione di un percorso del controllo del codice sorgente e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo del codice sorgente in tale percorso. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Questa interfaccia fornisce il supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Questa interfaccia consente ai progetti di controllare lo stato di avanzamento del caricamento asincrono avviato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Questa interfaccia consente all'IDE di eseguire query sul VSPackage del controllo del codice sorgente attivo. L'IDE esegue una query sul valore delle impostazioni del controllo del codice sorgente che hanno significato anche quando non è registrato alcun VSPackage del controllo del codice sorgente attivo. Questa interfaccia viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Stub del controllo del codice sorgente | Necessario |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Questa interfaccia viene usata per registrare il pacchetto VSPackage del controllo del codice sorgente. | Stub del controllo del codice sorgente | Necessario |
| <xref:EnvDTE.SourceControl> | Questa interfaccia viene usata nell'automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare alcuna interfaccia utente. | VsPackage del controllo del codice sorgente | Facoltativo |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Questa interfaccia viene usata per salvare le impostazioni del controllo del codice sorgente nel file di soluzione (con estensione sln). Le impostazioni includono il percorso del controllo del codice sorgente e i flag di stato del controllo del codice sorgente. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Questa interfaccia viene usata per salvare le impostazioni del controllo del codice sorgente nel file di opzioni della soluzione (con estensione suo). Possono essere incluse le impostazioni del controllo del codice sorgente specifiche dell'utente, ad esempio il percorso di integrazione dell'utente corrente. | VsPackage del controllo del codice sorgente | Consigliato |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Questa interfaccia viene usata per monitorare gli eventi per eseguire operazioni quali l'archiviazione dei file di progetto prima della chiusura delle soluzioni o il recupero di nuovi file dal controllo del codice sorgente all'apertura di un progetto. | VsPackage del controllo del codice sorgente | Consigliato |

## <a name="see-also"></a>Vedi anche
- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
