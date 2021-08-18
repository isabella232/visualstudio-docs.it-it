---
title: Project Sottotipi Progettazione | Microsoft Docs
description: Informazioni su come i sottotipi di progetto consentono ai pacchetti VSPackage di estendere i progetti in Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 432fc7791fa8c2c398dd7bca2285db31a9a5e12d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102389"
---
# <a name="project-subtypes-design"></a>Progettazione di sottotipi di progetto

Project sottotipi consentono ai pacchetti VSPackage di estendere i progetti in base Microsoft Build Engine (MSBuild). L'uso dell'aggregazione consente di riutilizzare la maggior parte del sistema di progetto gestito di base implementato in ma ancora personalizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comportamento per uno scenario specifico.

 Gli argomenti seguenti illustrano in dettaglio la progettazione e l'implementazione di base dei sottotipi di progetto:

- Project Progettazione del sottotipo.

- Aggregazione a più livelli.

- Interfacce di supporto.

## <a name="project-subtype-design"></a>Project Progettazione del sottotipo

L'inizializzazione di un sottotipo di progetto viene ottenuta aggregando gli oggetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> main e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Questa aggregazione consente a un sottotipo di progetto di eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. Project sottotipi hanno la prima possibilità di gestire le proprietà usando , i comandi che usano e e la gestione <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> degli elementi di progetto usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Project sottotipi possono anche estendere:

- Project di configurazione.

- Oggetti dipendenti dalla configurazione.

- Oggetti di esplorazione indipendenti dalla configurazione.

- Project oggetti di automazione.

- Project raccolte di proprietà di automazione.

Per altre informazioni sull'estendibilità in base ai sottotipi di progetto, vedere Proprietà e [metodi estesi Project sottotipi](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>File dei criteri

L'ambiente fornisce un esempio di estensione del sistema del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto di base con un sottotipo di progetto nella relativa implementazione dei file di criteri. Un file di criteri consente di modellare l'ambiente gestendo le funzionalità che includono la finestra di dialogo Esplora soluzioni, Aggiungi Project, Aggiungi nuovo elemento e la finestra di dialogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proprietà.    Il sottotipo di criteri esegue l'override e migliora queste funzionalità tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` le implementazioni di e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione

Il meccanismo di aggregazione del sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo l'implementazione di un sottotipo avanzato con un'ulteriore descrizione di un progetto avanzato. Inoltre, gli oggetti di supporto di un sottotipo di progetto, ad esempio , sono progettati per consentire <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> più livelli di suddivisione in livelli. In base ai vincoli delle regole di aggregazione COM e COM, i sottotipi di progetto e i progetti di base devono essere programmati in modo cooperativo per consentire al sottotipo interno o al progetto di base di partecipare correttamente alla delega delle chiamate al metodo e alla gestione dei conteggi dei riferimenti. In altre informazioni, il progetto che sta per essere aggregato deve essere programmato per supportare l'aggregazione.

La figura seguente mostra una rappresentazione schematica di un'aggregazione di sottotipi di progetto a più livelli.

![Rappresentazione grafica dei progetti multilivello Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Un'aggregazione di sottotipi di progetto a più livelli è costituita da tre livelli, un progetto di base, aggregato da un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo di progetto avanzato. La figura è incentrata su alcune delle interfacce di supporto fornite come parte dell'architettura del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottotipo di progetto.

### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione

Tra molte delle funzionalità del sistema del progetto di base migliorate da un sottotipo di progetto sono i meccanismi di distribuzione. Un sottotipo di progetto influisce sui meccanismi di distribuzione implementando interfacce di configurazione (ad esempio e ) recuperate chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> QueryInterface su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . In uno scenario in cui sia il sottotipo di progetto che il sottotipo di progetto avanzato aggiungono implementazioni di configurazione diverse, il progetto di base chiama sul sottotipo di `QueryInterface` progetto avanzato `IUnknown` . Se il sottotipo di progetto interno contiene l'implementazione di configurazione richiesta dal progetto di base, il sottotipo di progetto avanzato delega l'implementazione fornita dal sottotipo di progetto interno. Come meccanismo per rendere persistenti lo stato da un livello di aggregazione a un altro, tutti i livelli di sottotipi di progetto implementano per rendere persistenti i dati XML non correlati alla compilazione <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> nei file di progetto. Per altre informazioni, vedere [Persisting Data in the MSBuild Project File](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> viene implementato come meccanismo per recuperare gli extender di automazione dai sottotipi di progetto.

La figura seguente è incentrata sull'implementazione dell'extender di automazione, in particolare l'oggetto di esplorazione della configurazione del progetto, usato dai sottotipi di progetto per estendere il sistema del progetto di base.

![Rappresentazione dell'Extender automatico delle caratteristiche dei progetti VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Project sottotipi possono estendere ulteriormente il sistema del progetto di base estendendo il modello a oggetti di automazione. Questi vengono definiti come parte dell'oggetto di automazione DTE e vengono usati per estendere l'oggetto Project, l'oggetto `ProjectItem` e `Configuration` l'oggetto . Per altre informazioni, vedere [Estensione del modello a oggetti della classe Base Project](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Aggregazione a più livelli

Un'implementazione del sottotipo di progetto che esegue il wrapping di un sottotipo di progetto di livello inferiore deve essere programmata in modo cooperativo per consentire il corretto funzionamento del sottotipo di progetto interno. Un elenco di responsabilità di programmazione include:

- L'implementazione del sottotipo di progetto che esegue il wrapping del sottotipo interno deve delegare all'implementazione del sottotipo di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> interno per entrambi i metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- <xref:EnvDTE80.IInternalExtenderProvider>L'implementazione del sottotipo di progetto wrapper deve delegare a quella del sottotipo di progetto interno. In particolare, l'implementazione di deve ottenere la stringa di nomi dal sottotipo di progetto interno e quindi concatenare le stringhe da aggiungere <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> come extender.

- L'implementazione di un sottotipo di progetto wrapper deve creare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> un'istanza dell'oggetto del sottotipo di progetto interno e contenerlo come delegato privato, poiché solo l'oggetto di configurazione del progetto di base sa direttamente che esiste l'oggetto di configurazione del sottotipo di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> wrapper. Il sottotipo di progetto esterno può inizialmente scegliere le interfacce di configurazione che vuole gestire direttamente e quindi delegare il resto all'implementazione del sottotipo di progetto interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfacce di supporto

Il progetto di base delega le chiamate alle interfacce di supporto aggiunte da un sottotipo di progetto per estendere vari aspetti della relativa implementazione. Ciò include l'estensione di oggetti di configurazione del progetto e vari oggetti del visualizzatore proprietà. Queste interfacce vengono recuperate chiamando `QueryInterface` su `punkOuter` (un puntatore a `IUnknown` ) dell'aggregatore del sottotipo di progetto più esterno.

|Interfaccia|Project Sottotipo|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente al sottotipo di progetto di:<br /><br /> - Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />- Controllare l'avvio del debugger consentendo al sottotipo di progetto di fornire la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />- Disabilitare la valutazione delle espressioni in fase di progettazione gestendo in modo appropriato il `DBGLAUNCH_DesignTimeExprEval` case nella relativa implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente al sottotipo di progetto di:<br /><br /> - Estendere il <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> del progetto per aggiungere o rimuovere proprietà indipendenti dalla configurazione del progetto.<br />- Estendere l'oggetto di automazione del progetto ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) del progetto.<br /><br /> I valori delle proprietà precedenti vengono presi <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> dall'enumerazione .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente al sottotipo di progetto di eseguire il mapping <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> all'oggetto dato l'oggetto di esplorazione della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente al sottotipo di progetto di eseguire il mapping all'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o `VSITEMID` , dato l'oggetto di esplorazione della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto di rendere persistenti i dati strutturati XML arbitrari nel file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente al sottotipo di progetto di:<br /><br /> - Aggiungere nuove MSBuild proprietà da rendere persistenti.<br />- Rimuovere le proprietà non necessarie MSBuild.<br />- Eseguire una query per un valore corrente di una MSBuild proprietà.<br />- Modificare il valore corrente di una MSBuild proprietà.|

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
