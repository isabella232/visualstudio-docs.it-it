---
title: Proprietà e metodi estesi Project sottotipi | Microsoft Docs
description: Informazioni sulle funzionalità che i sottotipi di progetto possono migliorare o modificare, che consentono di personalizzare il comportamento dei sistemi di progetto di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0744b8669e3ab5d2fe7a3e936157172c5b0e0ef2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117670"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi dai sottotipi di progetto
Un sottotipo di progetto ha molte capacità per influenzare il comportamento del progetto perché viene costruito come aggregatore di un progetto di base. Questa sezione riepiloga alcune delle funzionalità che possono essere migliorate o modificate dai sottotipi di progetto.

## <a name="features-gained-by-aggregation"></a>Funzionalità ottenute dall'aggregazione
 La tabella seguente riepiloga molti dei metodi che l'aggregazione consente ai sottotipi di progetto di eseguire l'override nei progetti di base.

|Metodi sottoposti a override dall'aggregazione|Project Sottotipo|
|---------------------------------------|---------------------|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Consente a un sottotipo di progetto di<br /><br /> - Modificare la didascalia e l'icona del nodo del progetto.<br />- Eseguire l'override completo dell'oggetto `Browse` progetto.<br />- Controllare se il progetto può essere rinominato.<br />- Controllare l'ordinamento.<br />- Controllare il contesto utente per la Guida dinamica.|
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto di controllare quali servizi contestuali vengono forniti a finestre di progettazione ed editor.|
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Consente a un sottotipo di progetto di<br /><br /> - Partecipare al routing dei comandi per i comandi di progetto.<br />- Aggiungere, rimuovere o disabilitare entrambi i comandi di ambiente del progetto e Esplora soluzioni comandi attivi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Consente al sottotipo di progetto di filtrare ciò che l'utente visualizza nella **finestra di** dialogo Aggiungi nuovo elemento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Consente a un sottotipo di progetto di<br /><br /> - Determinare il generatore predefinito in base a un'estensione di file.<br />- Eseguire il mapping di un nome di generatore leggibile a un oggetto COM.|

## <a name="properties-used-by-project-subtypes"></a>Proprietà usate dai sottotipi Project
 L'ambiente e il sistema del progetto di base possono usare le proprietà di ed enumerazioni riportate in dettaglio nella tabella seguente per consentire a un sottotipo di progetto di controllare varie funzionalità <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> del sistema del progetto.

|VSHPROPID - proprietà|Project Sottotipo|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Consente a un sottotipo di progetto di controllare il contenuto della **finestra di dialogo** Aggiungi elemento. Il sottotipo di progetto può fornire una nuova specifica di directory modello, aggiungere nuovi tipi di elementi, rimuovere elementi esistenti e riorganizzare un subset degli elementi nella finestra di dialogo Aggiungi **elemento** del progetto di base.|
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà indipendenti dalla configurazione.|
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto di aggiungere o rimuovere pagine delle proprietà dipendenti dalla configurazione.|
|`ExtObjectCATID`|Consente a un sottotipo di progetto di fornire un extender di automazione per gli oggetti progetto o elemento di progetto conoscendo il CATID di Extender. Ad esempio, un sottotipo di progetto può fornire un oggetto `Project.Extender("<subtype>")` personalizzato.|
|`BrowseObjectCATID`|Consente a un sottotipo di progetto di fornire un extender di automazione per l'oggetto `Browse` conoscendo il CATID di Extender. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive alla <xref:EnvDTE.Project.Properties%2A> raccolta.|
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto di fornire un extender di automazione per l'oggetto di esplorazione della configurazione del progetto. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive alla <xref:EnvDTE.Configuration.Properties%2A> raccolta.|
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto di fornire un extender di automazione per l'oggetto di configurazione.|
|`DefaultPlatformName`|Consente a un sottotipo di progetto di determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|

 Il progetto di base fornisce un'implementazione predefinita delle proprietà precedenti. Il progetto di base ottiene questi elementi chiamando per sul sottotipo di progetto più esterno, consentendo così al sottotipo di progetto di `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> eseguire l'override dell'implementazione delle proprietà.

## <a name="see-also"></a>Vedi anche
- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)
