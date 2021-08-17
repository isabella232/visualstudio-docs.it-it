---
title: Project Sottotipi progettazione | Microsoft Docs
description: Informazioni su come i sottotipi di progetto consentono ai pacchetti VSPackage di estendere i progetti in base Microsoft Build Engine (MSBuild).
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
ms.openlocfilehash: 0cea3cde98ab0f35d46be1169b5f47d538e1ff8294bb251a4e4b3d358b688b18
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432320"
---
# <a name="project-subtypes-design"></a>Progettazione di sottotipi di progetto

Project sottotipi consentono ai pacchetti VSPackage di estendere i progetti in base Microsoft Build Engine (MSBuild). L'uso dell'aggregazione consente di riutilizzare la maggior parte del sistema di progetto gestito principale implementato in , personalizzando comunque il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comportamento per uno scenario specifico.

 Gli argomenti seguenti illustrano in dettaglio la progettazione e l'implementazione di base dei sottotipi di progetto:

- Project Progettazione del sottotipo.

- Aggregazione multi-livello.

- Interfacce di supporto.

## <a name="project-subtype-design"></a>Project Progettazione del sottotipo

L'inizializzazione di un sottotipo di progetto viene ottenuta aggregando gli oggetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> e principali. Questa aggregazione consente a un sottotipo di progetto di eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. Project sottotipi hanno la prima possibilità di gestire le proprietà usando , i comandi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> che usano e e la gestione degli elementi di progetto usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Project sottotipi possono anche estendere:

- Project di configurazione.

- Oggetti dipendenti dalla configurazione.

- Oggetti di esplorazione indipendenti dalla configurazione.

- Project oggetti di automazione.

- Project raccolte di proprietà di automazione.

Per altre informazioni sull'estendibilità in base ai sottotipi di progetto, vedere Proprietà e metodi [estesi Project sottotipi.](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>File dei criteri

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente fornisce un esempio di estensione del sistema del progetto di base con un sottotipo di progetto nell'implementazione dei file di criteri. Un file di criteri consente di definire la forma dell'ambiente gestendo le funzionalità che includono le finestre di dialogo Esplora soluzioni, Aggiungi Project, Aggiungi nuovo elemento e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proprietà.    Il sottotipo di criteri sostituisce e migliora queste funzionalità tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` le implementazioni di e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione

Il meccanismo di aggregazione del sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo così l'implementazione di un sottotipo avanzato con un ulteriore progetto di versioni. Inoltre, gli oggetti di supporto di un sottotipo di progetto, ad esempio , sono progettati per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> consentire più livelli di livelli. In linea con i vincoli delle regole di aggregazione COM e COM, i sottotipi di progetto e i progetti di base devono essere programmati in modo cooperativo per consentire al sottotipo interno o al progetto di base di partecipare correttamente alla delega delle chiamate ai metodi e alla gestione dei conteggi dei riferimenti. Ciò significa che il progetto che sta per essere aggregato deve essere programmato per supportare l'aggregazione.

La figura seguente mostra una rappresentazione schematica di un'aggregazione di sottotipi di progetto multi-livello.

![Rappresentazione grafica dei progetti multilivello Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Un'aggregazione di sottotipi di progetto multi-livello è costituita da tre livelli, un progetto di base, che viene aggregato in base a un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo di progetto avanzato. La figura è incentrata su alcune delle interfacce di supporto fornite come parte dell'architettura del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottotipo di progetto.

### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione

Tra molte delle funzionalità del sistema del progetto di base migliorate da un sottotipo di progetto sono i meccanismi di distribuzione. Un sottotipo di progetto influenza i meccanismi di distribuzione implementando interfacce di configurazione (ad esempio e ) recuperate chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> QueryInterface su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . In uno scenario in cui sia il sottotipo di progetto che il sottotipo di progetto avanzato aggiungono implementazioni di configurazione diverse, il progetto di base chiama `QueryInterface` sull'oggetto del sottotipo di progetto `IUnknown` avanzato. Se il sottotipo di progetto interno contiene l'implementazione di configurazione richiesta dal progetto di base, il sottotipo di progetto avanzato delega l'implementazione fornita dal sottotipo di progetto interno. Come meccanismo per rendere persistente lo stato da un livello di aggregazione a un altro, tutti i livelli dei sottotipi di progetto implementano per rendere persistenti i dati XML non correlati alla compilazione nei file <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> di progetto. Per altre informazioni, vedere [Persisting Data in the MSBuild Project File](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> viene implementato come meccanismo per recuperare gli extender di automazione dai sottotipi di progetto.

La figura seguente è incentrata sull'implementazione dell'estensione di automazione, in particolare l'oggetto di esplorazione della configurazione del progetto, usato dai sottotipi di progetto per estendere il sistema del progetto di base.

![Rappresentazione dell'Extender automatico delle caratteristiche dei progetti VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Project sottotipi possono estendere ulteriormente il sistema del progetto di base estendendo il modello a oggetti di automazione. Questi vengono definiti come parte dell'oggetto di automazione DTE e vengono usati per estendere l'oggetto Project, `ProjectItem` l'oggetto e `Configuration` l'oggetto . Per altre informazioni, vedere [Extending the Object Model of the Base Project](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Aggregazione multi-livello

Un'implementazione del sottotipo di progetto che esegue il wrapping di un sottotipo di progetto di livello inferiore deve essere programmata in modo cooperativo per consentire il corretto funzionamento del sottotipo di progetto interno. Un elenco di responsabilità di programmazione include:

- L'implementazione del sottotipo di progetto che esegue il wrapping del sottotipo interno deve delegare all'implementazione del sottotipo di progetto interno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per entrambi i metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- <xref:EnvDTE80.IInternalExtenderProvider>L'implementazione del sottotipo di progetto wrapper deve delegare a quella del sottotipo di progetto interno. In particolare, l'implementazione di deve ottenere la stringa di nomi dal sottotipo di progetto interno e quindi concatenare le stringhe da <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> aggiungere come extender.

- L'implementazione di un sottotipo di progetto wrapper deve creare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> un'istanza dell'oggetto del sottotipo di progetto interno e contenerlo come delegato privato, poiché solo l'oggetto di configurazione del progetto di base sa direttamente che esiste l'oggetto di configurazione del sottotipo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> progetto wrapper. Il sottotipo di progetto esterno può inizialmente scegliere le interfacce di configurazione che vuole gestire direttamente e quindi delegare il resto all'implementazione del sottotipo di progetto interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfacce di supporto

Il progetto di base delega le chiamate alle interfacce di supporto aggiunte da un sottotipo di progetto, per estendere vari aspetti della relativa implementazione. Ciò include l'estensione degli oggetti di configurazione del progetto e di vari oggetti del visualizzatore proprietà. Queste interfacce vengono recuperate chiamando su `QueryInterface` `punkOuter` (un puntatore a `IUnknown` ) dell'aggregatore del sottotipo di progetto più esterno.

|Interfaccia|Project Sottotipo|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente al sottotipo di progetto di:<br /><br /> - Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />- Controllare l'avvio del debugger consentendo al sottotipo di progetto di fornire la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />- Disabilitare la valutazione delle espressioni in fase di progettazione gestendo in modo appropriato `DBGLAUNCH_DesignTimeExprEval` la distinzione tra maiuscole e minuscole nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente al sottotipo di progetto di:<br /><br /> - Estendere il <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> del progetto per aggiungere o rimuovere proprietà indipendenti dalla configurazione del progetto.<br />- Estendere l'oggetto di automazione del progetto ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) del progetto.<br /><br /> I valori delle proprietà precedenti vengono prelevati <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> dall'enumerazione .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente al sottotipo di progetto di eseguire il mapping <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> all'oggetto dato l'oggetto di esplorazione della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente al sottotipo di progetto di eseguire il mapping all'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o , in base `VSITEMID` all'oggetto di esplorazione della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto di rendere persistenti i dati strutturati XML arbitrari nel file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili per MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente al sottotipo di progetto di:<br /><br /> - Aggiungere nuove MSBuild proprietà da rendere persistenti.<br />- Rimuovere le proprietà non necessarie MSBuild.<br />- Esegue una query per un valore corrente di una MSBuild proprietà.<br />- Modifica il valore corrente di una MSBuild proprietà.|

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
