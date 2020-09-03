---
title: Progettazione sottotipi di progetto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706451"
---
# <a name="project-subtypes-design"></a>Progettazione di sottotipi di progetto

I sottotipi di progetto consentono ai pacchetti VSPackage di estendere i progetti basati sulla Microsoft Build Engine (MSBuild). L'utilizzo dell'aggregazione consente di riutilizzare la maggior parte del sistema di progetto gestito di base implementato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ma ancora di personalizzare il comportamento per uno scenario specifico.

 Gli argomenti seguenti illustrano in dettaglio la progettazione e l'implementazione di base dei sottotipi di progetto:

- Progettazione del sottotipo di progetto.

- Aggregazione a più livelli.

- Interfacce di supporto.

## <a name="project-subtype-design"></a>Progettazione sottotipi di progetto

L'inizializzazione di un sottotipo di progetto viene eseguita aggregando gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetti e principali <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Questa aggregazione consente a un sottotipo di progetto di eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. I sottotipi di progetto ottengono la prima possibilità di gestire le proprietà usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , i comandi che usano e e la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> gestione di elementi di progetto con <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . I sottotipi di progetto possono anche estendere:

- Oggetti di configurazione del progetto.

- Oggetti dipendenti dalla configurazione.

- Oggetti browse indipendenti dalla configurazione.

- Oggetti di automazione del progetto.

- Raccolte di proprietà di automazione del progetto.

Per ulteriori informazioni sull'estendibilità per sottotipi di progetto, vedere [proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>File dei criteri

L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente fornisce un esempio di estensione del sistema di progetto di base con un sottotipo di progetto nell'implementazione dei file di criteri. Un file di criteri consente la definizione dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente gestendo caratteristiche che includono la finestra di dialogo Esplora soluzioni, **Aggiungi progetto** , finestra di dialogo **Aggiungi nuovo elemento** e la finestra di dialogo **Proprietà** . Il sottotipo di criteri esegue l'override di queste funzionalità tramite le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementazioni e.

### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione

Il meccanismo di aggregazione del sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo in questo modo l'implementazione di un sottotipo avanzato aggiungendo un progetto con Flavor. Inoltre, gli oggetti di supporto di un sottotipo di progetto, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , sono progettati per consentire più livelli di sovrapposizione. In conformità ai vincoli delle regole di aggregazione COM e COM, i sottotipi di progetto e i progetti di base devono essere programmati in modo cooperativo per consentire al sottotipo interno o al progetto di base di partecipare correttamente alla delega delle chiamate al metodo e alla gestione dei conteggi dei riferimenti. Ovvero, il progetto che sta per essere aggregato deve essere programmato per supportare l'aggregazione.

Nella figura seguente è illustrata una rappresentazione schematica di un'aggregazione di sottotipi di progetto multilivello.

![Rappresentazione grafica dei progetti multilivello Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Un'aggregazione di sottotipi di progetto multilivello è costituita da tre livelli, un progetto di base, aggregato da un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo di progetto avanzato. La figura è incentrata su alcune delle interfacce di supporto fornite come parte dell'architettura del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottotipo di progetto.

### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione

Tra molte delle funzionalità di base del sistema di progetto migliorate da un sottotipo di progetto sono disponibili meccanismi di distribuzione. Un sottotipo di progetto influisce sui meccanismi di distribuzione implementando interfacce di configurazione (ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ) che vengono recuperate chiamando QueryInterface su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . In uno scenario in cui il sottotipo di progetto e il sottotipo di progetto avanzato aggiungono implementazioni di configurazione diverse, il progetto di base chiama `QueryInterface` per l'oggetto del sottotipo di progetto avanzato `IUnknown` . Se il sottotipo di progetto interno contiene l'implementazione della configurazione richiesta dal progetto di base, il sottotipo di progetto avanzato delega l'implementazione fornita dal sottotipo del progetto interno. Come meccanismo per rendere permanente lo stato da un livello di aggregazione a un altro, tutti i livelli dei sottotipi di progetto implementano <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per rendere permanente i dati XML non correlati alla compilazione nei file di progetto. Per altre informazioni, vedere [salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> viene implementato come meccanismo per recuperare i dispositivi Extender di automazione dai sottotipi di progetto.

L'illustrazione seguente è incentrata sull'implementazione dell'estensione di automazione, l'oggetto browse della configurazione del progetto in particolare, usato dai sottotipi di progetto per estendere il sistema del progetto di base.

![Rappresentazione dell'Extender automatico delle caratteristiche dei progetti VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

I sottotipi di progetto possono estendere ulteriormente il sistema del progetto di base estendendo il modello a oggetti di automazione. Questi vengono definiti come parte dell'oggetto di automazione DTE e vengono usati per estendere l'oggetto del progetto, l' `ProjectItem` oggetto e l' `Configuration` oggetto. Per ulteriori informazioni, vedere [estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Aggregazione a più livelli

Un'implementazione del sottotipo di progetto che esegue il wrapping di un sottotipo di progetto di livello inferiore deve essere programmata in modo cooperativo per consentire il corretto funzionamento del sottotipo del progetto interno. Un elenco di responsabilità di programmazione include:

- L' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementazione del sottotipo di progetto che sta eseguendo il wrapping del sottotipo interno deve delegare all' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementazione del sottotipo di progetto interno per entrambi i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metodi e.

- L' <xref:EnvDTE80.IInternalExtenderProvider> implementazione del sottotipo di progetto wrapper deve delegare a quella del sottotipo di progetto interno. In particolare, l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> deve ottenere la stringa di nomi dal sottotipo di progetto interno e quindi concatenare le stringhe che si desidera aggiungere come Extender.

- L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implementazione di un sottotipo di progetto wrapper deve creare un'istanza dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> oggetto del sottotipo di progetto interno e tenerlo come delegato privato, perché solo l'oggetto di configurazione del progetto del progetto di base sa direttamente che l'oggetto di configurazione del sottotipo del progetto wrapper esiste. Il sottotipo di progetto esterno può inizialmente scegliere le interfacce di configurazione che desidera gestire direttamente e quindi delegare il resto all'implementazione del sottotipo di progetto interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfacce di supporto

Il progetto di base delega le chiamate a interfacce di supporto aggiunte da un sottotipo di progetto per estendere i vari aspetti della relativa implementazione. Sono incluse l'estensione degli oggetti di configurazione del progetto e di vari oggetti visualizzatore proprietà. Queste interfacce vengono recuperate chiamando `QueryInterface` on `punkOuter` (un puntatore a `IUnknown` ) dell'aggregatore del sottotipo di progetto più esterno.

|Interfaccia|Sottotipo di progetto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente al sottotipo di progetto di:<br /><br /> -Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />-Controllare l'avvio del debugger consentendo al sottotipo di progetto di fornire la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-Disabilitare la valutazione delle espressioni in fase di progettazione gestendo in modo appropriato il `DBGLAUNCH_DesignTimeExprEval` case nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente al sottotipo di progetto di:<br /><br /> -Estendere l'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> del progetto per aggiungere o rimuovere le proprietà indipendenti dalla configurazione del progetto.<br />-Estendere l'oggetto di automazione del progetto ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) del progetto.<br /><br /> I valori delle proprietà precedenti vengono ricavati dall' <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumerazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente di eseguire il mapping del sottotipo di progetto all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto in base all'oggetto browse della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente di eseguire il mapping del sottotipo di progetto all'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o `VSITEMID` , in base all'oggetto browse della configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto di salvare in modo permanente i dati strutturati XML arbitrari nel file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili a MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente al sottotipo di progetto di:<br /><br /> -Aggiungere nuove proprietà MSBuild da salvare in modo permanente.<br />-Rimuovere le proprietà non necessarie da MSBuild.<br />-Query per un valore corrente di una proprietà di MSBuild.<br />: Modificare il valore corrente di una proprietà di MSBuild.|

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
