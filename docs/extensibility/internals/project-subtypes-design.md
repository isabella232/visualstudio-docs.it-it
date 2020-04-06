---
title: Progettazione di sottotipi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706451"
---
# <a name="project-subtypes-design"></a>Progettazione di sottotipi di progetto

I sottotipi di progetto consentono a VSPackage di estendere i progetti basati sul motore di compilazione Microsoft (MSBuild). L'uso dell'aggregazione consente di riutilizzare la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] maggior parte del sistema di progetto gestito di base implementato in ma ancora personalizzare il comportamento per un particolare scenario.

 Negli argomenti seguenti vengono descritte in dettaglio la progettazione e l'implementazione di base dei sottotipi di progetto:

- Progettazione sottotipo di progetto.

- Aggregazione multilivello.

- Interfacce di supporto.

## <a name="project-subtype-design"></a>Progettazione di sottotipi di progetto

L'inizializzazione di un sottotipo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> viene ottenuta aggregando gli oggetti main e objects. Questa aggregazione consente a un sottotipo di progetto di eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. I sottotipi di progetto hanno <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>la prima <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>possibilità di gestire <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>le proprietà utilizzando , i comandi utilizzando e la gestione degli elementi di progetto mediante . I sottotipi di progetto possono anche estendere:

- Oggetti di configurazione del progetto.

- Oggetti dipendenti dalla configurazione.

- Oggetti sfoglia indipendenti dalla configurazione.

- Oggetti di automazione del progetto.

- Raccolte di proprietà di automazione del progetto.

Per ulteriori informazioni sull'estensibilità in base ai sottotipi di progetto, vedere [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>File dei criteri

L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un esempio di estensione del sistema di progetto di base con un sottotipo di progetto nell'implementazione dei file di criteri. Un file di criteri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente la modellazione dell'ambiente gestendo le funzionalità che includono Esplora soluzioni, finestra di dialogo **Aggiungi progetto,** **Aggiungi nuovo elemento** e **proprietà** della finestra di dialogo Proprietà. Il sottotipo di criteri esegue l'override e migliora queste funzionalità tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementazioni.

### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione

Il meccanismo di aggregazione del sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo così l'implementazione di un sottotipo avanzato insaporindo ulteriormente un progetto aromatizzato. Inoltre, gli oggetti di supporto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>un sottotipo di progetto, ad esempio , sono progettati per consentire più livelli di stratificazione. In linea con i vincoli delle regole di aggregazione COM e COM, i sottotipi di progetto e i progetti di base devono essere programmati in modo cooperativo per consentire al sottotipo interno o al progetto di base di partecipare correttamente alla delega delle chiamate al metodo e alla gestione dei conteggi dei riferimenti. Ovvero, il progetto che sta per essere aggregato deve essere programmato per supportare l'aggregazione.

Nella figura seguente viene illustrata una rappresentazione schematica di un'aggregazione di sottotipi di progetto a più livelli.

![Rappresentazione grafica dei progetti multilivello Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Un'aggregazione di sottotipi di progetto a più livelli è costituita da tre livelli, un progetto di base, che viene aggregato da un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo di progetto avanzato. La figura è incentrata su alcune delle interfacce di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporto fornite come parte dell'architettura del sottotipo di progetto.

### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione

Tra molte delle funzionalità del sistema di progetto di base migliorate da un sottotipo di progetto sono i meccanismi di distribuzione. Un sottotipo di progetto influenza i meccanismi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>distribuzione implementando le interfacce <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>di configurazione (ad esempio e ) recuperate chiamando QueryInterface su . In uno scenario in cui sia il sottotipo di progetto che il `QueryInterface` sottotipo di progetto avanzato aggiungono implementazioni di configurazione diverse, il progetto di base chiama il sottotipo di progetto avanzato. `IUnknown` Se il sottotipo di progetto interno contiene l'implementazione di configurazione richiesta dal progetto di base, il sottotipo di progetto avanzato delega all'implementazione fornita dal sottotipo di progetto interno. Come meccanismo per mantenere lo stato da un livello di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> aggregazione a un altro, tutti i livelli di sottotipi di progetto implementano per rendere persistenti i dati XML non correlati alla compilazione nei file di progetto. Per altre informazioni, vedere [Persistenza dei dati nel file](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)di progetto MSBuild . <xref:EnvDTE80.IInternalExtenderProvider>viene implementato come meccanismo per recuperare gli estensori di automazione dai sottotipi di progetto.

La figura seguente è incentrata sull'implementazione dell'estensione di automazione, in particolare sull'oggetto sfoglia della configurazione del progetto, utilizzato dai sottotipi di progetto per estendere il sistema del progetto di base.

![Rappresentazione dell'Extender automatico delle caratteristiche dei progetti VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

I sottotipi di progetto possono estendere ulteriormente il sistema di progetto di base estendendo il modello a oggetti di automazione. Questi vengono definiti come parte dell'oggetto di automazione DTE `ProjectItem` e vengono `Configuration` utilizzati per estendere l'oggetto Project, l'oggetto e l'oggetto. Per ulteriori informazioni, vedere [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Aggregazione multilivello

Un'implementazione di sottotipo di progetto che esegue il wrapping di un sottotipo di progetto di livello inferiore deve essere programmata in modo cooperativo per consentire il corretto funzionamento del sottotipo di progetto interno. Un elenco di responsabilità di programmazione include:

- L'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> del sottotipo di progetto che esegue <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> il wrapping del sottotipo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> interno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> deve delegare all'implementazione del sottotipo di progetto interno per entrambi i metodi e .

- L'implementazione <xref:EnvDTE80.IInternalExtenderProvider> del sottotipo di progetto wrapper deve delegare a quella del relativo sottotipo di progetto interno. In particolare, l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> deve ottenere la stringa di nomi dal sottotipo di progetto interno e quindi concatenare le stringhe che si desidera aggiungere come extender.

- L'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> di un sottotipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> di progetto wrapper deve creare un'istanza dell'oggetto del relativo sottotipo di progetto interno e conservarlo come delegato privato, poiché solo l'oggetto di configurazione del progetto di base sa direttamente che esiste l'oggetto di configurazione del sottotipo di progetto wrapper. Il sottotipo di progetto esterno può inizialmente scegliere le interfacce di configurazione che desidera gestire <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>direttamente e quindi delegare il resto all'implementazione del sottotipo di progetto interno di .

## <a name="supporting-interfaces"></a>Interfacce di supportoSupporting Interfaces

I delegati del progetto di base chiamano le interfacce di supporto aggiunte da un sottotipo di progetto, per estendere vari aspetti della relativa implementazione. Ciò include l'estensione degli oggetti di configurazione del progetto e di vari oggetti del visualizzatore proprietà. Queste interfacce vengono `QueryInterface` recuperate chiamando `punkOuter` (un puntatore a `IUnknown`) dell'aggregatore di sottotipi di sottotipo più esterno.

|Interfaccia|Sottotipo di progetto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente al sottotipo di progetto di:<br /><br /> - Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />- Controllare l'avvio del debugger consentendo al sottotipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>di progetto di fornire la propria implementazione di .<br />- Disabilitare la valutazione dell'espressione `DBGLAUNCH_DesignTimeExprEval` in fase <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>di progettazione gestendo in modo appropriato il caso nell'implementazione di .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente al sottotipo di progetto di:<br /><br /> - Estendere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> il progetto per aggiungere o rimuovere le proprietà indipendenti dalla configurazione del progetto.<br />- Estendere l'oggetto<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>di automazione del progetto ( ) del progetto.<br /><br /> I valori delle <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> proprietà sopra riportati sono tratti dall'enumerazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente al sottotipo di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> di eseguire il mapping all'oggetto in base all'oggetto sfoglia della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente al sottotipo di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> di `VSITEMID` eseguire il mapping all'oggetto o , dato l'oggetto di ricerca della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto di rendere persistenti i dati strutturati XML arbitrari nel file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili a MSBuild.This data is not visible to MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente al sottotipo di progetto di:<br /><br /> - Aggiungere nuove proprietà MSBuild da rendere persistenti.- Add new MSBuild properties to be persisted.<br />- Rimuovere le proprietà non necessarie da MSBuild.- Remove unnecessary properties from MSBuild.<br />- Eseguire una query per un valore corrente di una proprietà MSBuild.- Query for a current value of an MSBuild property.<br />- Modificare il valore corrente di una proprietà MSBuild.|

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
