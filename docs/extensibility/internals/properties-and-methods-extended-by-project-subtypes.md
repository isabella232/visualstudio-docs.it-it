---
title: Proprietà e metodi estesi dai sottotipi di progetto | Microsoft Docs
description: Informazioni sulle funzionalità che i sottotipi di progetto possono migliorare o modificare, consentendo di personalizzare il comportamento dei sistemi di progetto di Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cff332d7b573bb2fdff886b4206ea1267c091c48
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878040"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi dai sottotipi di progetto
Un sottotipo di progetto ha numerose potenzialità per influenzare il comportamento del progetto perché viene costruito come aggregatore di un progetto di base. Questa sezione riepiloga alcune delle funzionalità che possono essere migliorate o modificate dai sottotipi di progetto.

## <a name="features-gained-by-aggregation"></a>Funzionalità acquisite dall'aggregazione
 La tabella seguente riepiloga molti dei metodi in base ai quali l'aggregazione consente l'override dei sottotipi di progetto nei progetti di base.

|Metodi sottoposti a override dall'aggregazione|Sottotipo di progetto|
|---------------------------------------|---------------------|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Abilita un sottotipo di progetto<br /><br /> -Modificare la didascalia e l'icona del nodo del progetto.<br />-Esegue l'override completo dell' `Browse` oggetto progetto.<br />-Controlla se il progetto può essere rinominato.<br />-Ordinamento del controllo.<br />-Controlla il contesto utente per la Guida dinamica.|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto di controllare quali servizi contestuali sono disponibili per le finestre di progettazione e gli editor.|
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Abilita un sottotipo di progetto<br /><br /> -Partecipare al routing dei comandi per i comandi di progetto.<br />-Aggiungere, rimuovere o disabilitare i comandi di ambiente del progetto e Esplora soluzioni comandi attivi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Consente al sottotipo di progetto di filtrare le informazioni visualizzate dall'utente nella finestra di dialogo **Aggiungi nuovo elemento** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Abilita un sottotipo di progetto<br /><br /> -Determinare il generatore predefinito in base a un'estensione di file.<br />-Eseguire il mapping di un nome di generatore leggibile a un oggetto COM.|

## <a name="properties-used-by-project-subtypes"></a>Proprietà utilizzate dai sottotipi di progetto
 L'ambiente e il sistema del progetto di base possono utilizzare le proprietà di <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> ed <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumerazioni descritte in dettaglio nella tabella seguente per consentire a un sottotipo di progetto di controllare varie funzionalità del sistema del progetto.

|Proprietà VSHPROPID|Sottotipo di progetto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Consente a un sottotipo di progetto di controllare il contenuto della finestra di dialogo **Aggiungi elemento** . Il sottotipo di progetto può fornire una nuova specifica delle directory dei modelli, aggiungere nuovi tipi di elementi, rimuovere gli elementi esistenti e riorganizzare un subset degli elementi nella finestra di dialogo **Aggiungi elemento** del progetto di base.|
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà indipendenti dalla configurazione.|
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà dipendenti dalla configurazione.|
|`ExtObjectCATID`|Consente a un sottotipo di progetto di fornire un Extender di automazione per gli oggetti progetto o elemento progetto conoscendo il CATId dell'estensione. Un sottotipo di progetto, ad esempio, può fornire un `Project.Extender("<subtype>")` oggetto personalizzato.|
|`BrowseObjectCATID`|Consente a un sottotipo di progetto di fornire un Extender di automazione per l' `Browse` oggetto conoscendo il CATID di Extender. Un sottotipo di progetto, ad esempio, può aggiungere proprietà aggiuntive alla <xref:EnvDTE.Project.Properties%2A> raccolta.|
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto di fornire un Extender di automazione per l'oggetto browse della configurazione del progetto. Un sottotipo di progetto, ad esempio, può aggiungere proprietà aggiuntive alla <xref:EnvDTE.Configuration.Properties%2A> raccolta.|
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto di fornire un Extender di automazione per l'oggetto di configurazione.|
|`DefaultPlatformName`|Consente a un sottotipo di progetto di determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|

 Il progetto di base fornisce un'implementazione predefinita delle proprietà precedenti. Il progetto di base ottiene questi `QueryInterface` tipi chiamando per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sul sottotipo di progetto più esterno, consentendo così al sottotipo di progetto di eseguire l'override dell'implementazione delle proprietà.

## <a name="see-also"></a>Vedi anche
- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)
