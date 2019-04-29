---
title: Progettazione i sottotipi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e7cd96324e5a2bbd6c9b0acf4125bc0450cfd06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62430542"
---
# <a name="project-subtypes-design"></a>Progettazione di sottotipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sottotipi di progetto consentono a pacchetti VSPackage di estendere i progetti basati su Microsoft Build Engine (MSBuild). L'uso di aggregazione consente di riutilizzare la maggior parte del sistema del progetto core gestite implementata in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ma comunque personalizzare il comportamento per un determinato scenario.  
  
 Gli argomenti seguenti vengono descritte la progettazione di base e l'implementazione di sottotipi di progetto:  
  
- Sottotipo di progetto.  
  
- Aggregazione a più livelli.  
  
- Supporto di interfacce.  
  
## <a name="project-subtype-design"></a>Sottotipo di progetto  
 L'inizializzazione di un sottotipo di progetto viene ottenuta mediante l'aggregazione principale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> oggetti. Questa aggregazione consente a un sottotipo di progetto eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. Sottotipi di progetto ottenere la prima opportunità di gestire le proprietà usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, usando i comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e gestione di elementi di progetto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Sottotipi di progetto possono anche essere estesi:  
  
- Gli oggetti di configurazione del progetto.  
  
- Oggetti dipendenti dalla configurazione.  
  
- Oggetti indipendenti dalla configurazione Sfoglia.  
  
- Gli oggetti di automazione del progetto.  
  
- Raccolte delle proprietà di automazione del progetto.  
  
  Per altre informazioni sull'estensibilità dai sottotipi di progetto, vedere [delle proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>File dei criteri  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente fornisce un esempio di estensione del sistema di progetto di base con un sottotipo di progetto nella propria implementazione di file dei criteri. Un file di criteri consente il data shaping della [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente gestendo le funzionalità che includono Esplora soluzioni **Aggiungi progetto** nella finestra di dialogo **Aggiungi nuovo elemento** nella finestra di dialogo e  **Proprietà** nella finestra di dialogo. Il sottotipo criteri esegue l'override e migliora tali funzionalità attraverso <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementazioni.  
  
##### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione  
 Meccanismo di aggregazione sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo in tal modo un sottotipo avanzato deve essere implementata da ulteriore flavoring un progetto caratterizzato. Inoltre, gli oggetti di supporto di un progetto di sottotipo, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sono progettati per consentire a più livelli di sovrapposizione. In linea con i vincoli di COM e COM le regole di aggregazione, sottotipi di progetto e progetti di base devono essere programmate in modo cooperativo per abilitare il sottotipo interno o al progetto di base partecipare in modo corretto delega le chiamate di metodo e la gestione di conteggi dei riferimenti . Il progetto sta per essere aggregati, ovvero deve essere programmati per supporta l'aggregazione.  
  
 La figura seguente mostra una rappresentazione schematica di un'aggregazione sottotipo di progetto a più livelli.  
  
 ![Rappresentazione grafica di Visual Studio projectflavor a più livelli](../../extensibility/internals/media/vs-multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Sottotipo di progetto più livelli  
  
 Un'aggregazione sottotipo di progetto a più livelli è costituito da tre livelli, un progetto di base, che viene aggregata da un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo di progetto avanzati. Nella figura è incentrato su alcune delle interfacce che vengono fornite come parte del supporta di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] architettura sottotipo di progetto.  
  
##### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione  
 Molte del sistema del progetto di base fra le funzionalità migliorate mediante un sottotipo di progetto sono meccanismi di distribuzione. Un sottotipo di progetto influenza meccanismi di distribuzione mediante l'implementazione di interfacce di configurazione (ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) che vengono recuperate tramite una chiamata QueryInterface sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. In uno scenario in cui il sottotipo del progetto sia il sottotipo di progetto avanzati aggiungere implementazioni diverse configurazione, chiamato al progetto di base `QueryInterface` sul sottotipo di progetto avanzati `IUnknown`. Se il sottotipo di progetto interno contiene l'implementazione di configurazione che chiede al progetto di base, il sottotipo di progetto avanzati delega per l'implementazione fornita dal sottotipo del progetto interno. Come un meccanismo per rendere persistente lo stato dal livello di uno aggregazione a altro, tutti i livelli di sottotipi di progetto implementano <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per rendere persistenti non-build correlati i dati XML nei file di progetto. Per altre informazioni, vedere [salvataggio permanente dei dati nel File di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> viene implementato come un meccanismo per recuperare dispositivi Extender di automazione dai sottotipi di progetto.  
  
 Nella figura seguente è incentrato sull'implementazione del dispositivo extender di automazione, l'oggetto di esplorazione di configurazione di progetto, in particolare, utilizzato dai sottotipi di progetto per estendere il sistema di progetto di base.  
  
 ![Rappresentazione grafica di Extender automatico delle caratteristiche progetto VS](../../extensibility/internals/media/vs-projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extender di automazione sottotipo di progetto.  
  
 Sottotipi di progetto è possono estendere ulteriormente il sistema di progetto di base estendendo il modello oggetto di automazione. Queste sono definite come parte dell'oggetto di automazione DTE e vengono utilizzate per estendere l'oggetto di progetto, il `ProjectItem` oggetto e il `Configuration` oggetto. Per altre informazioni, vedere [estendendo il modello a oggetti del progetto Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Aggregazione a più livelli  
 Un'implementazione di sottotipo di progetto che esegue il wrapping di un sottotipo di progetto di livello inferiore deve essere programmate in modo cooperativo per consentire il sottotipo di progetto interno funzionare correttamente. Un elenco di programmazione le responsabilità include:  
  
- Il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> necessario delegare l'implementazione del sottotipo di progetto che esegue il wrapping il sottotipo interno per il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementazione del sottotipo di progetto interno per entrambe <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metodi.  
  
- Il <xref:EnvDTE80.IInternalExtenderProvider> implementazione del sottotipo di progetto wrapper deve delegare a quello del relativo sottotipo del progetto interno. In particolare, l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> deve ottenere la stringa dei nomi dal sottotipo di progetto interno e quindi concatenare le stringhe che si desidera aggiungere come dispositivi Extender.  
  
- Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> deve creare un'istanza di implementazione di un sottotipo di progetto wrapper di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> oggetto del relativo interna sottotipo di progetto e tenerlo in un delegato privato, poiché solo oggetto di configurazione di progetto del progetto base direttamente è evidente che il wrapper oggetto di configurazione sottotipo di progetto esistente. Sottotipo del progetto esterno può inizialmente scegliere interfacce di configurazione che si desidera gestire in modo diretto e quindi delegare il resto all'implementazione del sottotipo di progetto interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Supporto di interfacce  
 Il progetto di base delega le chiamate al supporto di interfacce aggiunte da un sottotipo di progetto, per estendere vari aspetti della relativa implementazione. Ciò include l'estensione vari oggetti di browser di proprietà e gli oggetti di configurazione di progetto. Queste interfacce vengono recuperate chiamando `QueryInterface` sul `punkOuter` (un puntatore al `IUnknown`) di Sil aggregator sottotipo di progetto più esterno.  
  
|Interfaccia|Sottotipo di progetto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente al sottotipo di progetto per:<br /><br /> -Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Controllare l'avvio del debugger, consentendo il sottotipo di progetto fornire la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Disabilita la valutazione dell'espressione design-time gestendo in modo appropriato le `DBGLAUNCH_DesignTimeExprEval` maiuscole nella propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente al sottotipo di progetto per:<br /><br /> -Consente di estendere il <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> del progetto da aggiungere o rimuovere proprietà indipendente dalla configurazione del progetto.<br />-Estendere l'oggetto di automazione (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) del progetto.<br /><br /> I valori delle proprietà sopra vengono prelevati <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumerazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente al sottotipo di progetto eseguire il mapping al <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto dato l'oggetto di esplorazione di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente al sottotipo di progetto eseguire il mapping al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o il `VSITEMID` oggetto, dato l'oggetto di esplorazione di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto rendere persistenti i dati XML strutturati arbitrari al file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili a MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente al sottotipo di progetto per:<br /><br /> -Aggiungere nuove proprietà di MSBuild per essere resi persistenti.<br />-Rimuovere proprietà necessaria da MSBuild.<br />-Query per il valore corrente di una proprietà di MSBuild.<br />-Modificare il valore corrente di una proprietà di MSBuild.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
