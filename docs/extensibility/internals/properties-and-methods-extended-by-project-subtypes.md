---
title: Proprietà e metodi estesi dai sottotipi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706202"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi dai sottotipi di progetto
Un sottotipo di progetto ha molto potere per influenzare il comportamento del progetto perché è costruito come aggregatore di un progetto di base. In questa sezione vengono riepilogate alcune delle funzionalità che possono essere migliorate o modificate dai sottotipi di progetto.

## <a name="features-gained-by-aggregation"></a>Caratteristiche acquisite dall'aggregazione
 Nella tabella seguente vengono riepilogati molti dei metodi che l'aggregazione consente ai sottotipi di progetto di eseguire l'override nei progetti di base.

|Metodi sottoposti a override per aggregazioneMethods Overridden by Aggregation|Sottotipo di progetto|
|---------------------------------------|---------------------|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Consente a un sottotipo di progetto di<br /><br /> - Modificare la didascalia e l'icona del nodo del progetto.<br />- Eseguire `Browse` completamente l'override dell'oggetto di progetto.<br />- Controllare se il progetto può essere rinominato.<br />- Controllare l'ordinamento.<br />- Controllare il contesto utente per la guida dinamica.- Control user context for dynamic help.|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto di controllare quali servizi contestuali vengono forniti alle finestre di progettazione e agli editor.|
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Consente a un sottotipo di progetto di<br /><br /> - Partecipare al routing dei comandi per i comandi di progetto.- Participate in the command routing for project commands.<br />- Aggiungere, rimuovere o disabilitare entrambi i comandi di ambiente del progetto e i comandi attivi di Esplora soluzioni.- Add, remove, or disable both project ambient commands and Solution Explorer active commands.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Consente al sottotipo di progetto di filtrare ciò che l'utente vede nella finestra di dialogo **Aggiungi nuovo elemento.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Consente a un sottotipo di progetto di<br /><br /> - Determinare il generatore predefinito data un'estensione di file.<br />- Eseguire il mapping di un nome di generatore leggibile a un oggetto COM.- Map a human readable generator name to a COM object.|

## <a name="properties-used-by-project-subtypes"></a>Proprietà utilizzate dai sottotipi di progetto
 L'ambiente e il sistema del <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> progetto di base possono utilizzare le proprietà da e le enumerazioni descritte nella tabella seguente per consentire a un sottotipo di progetto di controllare varie funzionalità del sistema del progetto.

|VSHPROPID (proprietà)|Sottotipo di progetto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Consente a un sottotipo di progetto di controllare il contenuto della finestra di dialogo **Aggiungi elemento.** Il sottotipo di progetto può fornire una nuova specifica di directory del modello, aggiungere nuovi tipi di elementi, rimuovere elementi esistenti e riorganizzare un sottoinsieme degli elementi nella finestra di dialogo **Aggiungi elemento** del progetto di base.|
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà indipendenti dalla configurazione.|
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà dipendenti dalla configurazione.|
|`ExtObjectCATID`|Consente a un sottotipo di progetto di fornire un'estensione di automazione per gli oggetti progetto o elemento di progetto conoscendo il CATID Disestensione. Ad esempio, un sottotipo di `Project.Extender("<subtype>")` progetto può fornire un oggetto personalizzato.|
|`BrowseObjectCATID`|Consente a un sottotipo di progetto `Browse` di fornire un estensione di automazione per l'oggetto conoscendo il CATID Extender. Ad esempio, un sottotipo di progetto <xref:EnvDTE.Project.Properties%2A> può aggiungere proprietà aggiuntive alla raccolta.|
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto di fornire un'estensione di automazione per l'oggetto di visualizzazione della configurazione del progetto. Ad esempio, un sottotipo di progetto <xref:EnvDTE.Configuration.Properties%2A> può aggiungere proprietà aggiuntive alla raccolta.|
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto di fornire un'estensione di automazione per l'oggetto di configurazione.|
|`DefaultPlatformName`|Consente a un sottotipo di progetto di determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|

 Il progetto di base fornisce un'implementazione predefinita delle proprietà precedenti. Il progetto di base `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ottiene questi chiamando il sottotipo di progetto più esterno, consentendo così il sottotipo di progetto per eseguire l'override dell'implementazione delle proprietà.

## <a name="see-also"></a>Vedere anche
- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)
