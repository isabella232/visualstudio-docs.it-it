---
title: Proprietà e metodi estesi dai sottotipi di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74f1f4a88fb01e09b30e7987f1bcec1d450571a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765119"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi dai sottotipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sottotipo di progetto contiene una grande quantità di potenza per influenzare il comportamento del progetto perché viene creata come un aggregatore di un progetto di base. Questa sezione riepiloga alcune delle funzionalità che può essere migliorata o modificata dai sottotipi di progetto.  
  
## <a name="features-gained-by-aggregation"></a>Funzionalità ottenute dall'aggregazione  
 La tabella seguente riepiloga molti dei metodi di aggregazione consente di sottotipi di progetto eseguire l'override nei progetti di base.  
  
|Metodi di override da parte di aggregazione|Sottotipo di progetto|  
|---------------------------------------|---------------------|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Consente a un sottotipo di progetto per<br /><br /> -Modifica didascalia e l'icona del nodo del progetto.<br />-Override completo progetto `Browse` oggetto.<br />-Controllare se il progetto può essere rinominato.<br />-Controllo di ordinamento.<br />-Contesto utente control per la Guida dinamica.|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto controllare quali servizi contestuali vengono forniti a editor e finestre di progettazione.|  
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Consente a un sottotipo di progetto per<br /><br /> -Partecipare il routing dei comandi per i comandi di progetto.<br />-Aggiungere, rimuovere o disabilitare i comandi di ambiente di progetto e i comandi attivi di Esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Abilita il sottotipo di progetto filtrare gli elementi visualizzati dall'utente nel **Aggiungi nuovo elemento** nella finestra di dialogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Consente a un sottotipo di progetto per<br /><br /> -Determinare il generatore predefinito ha un'estensione di file.<br />-Mapping di un nome di risorse umane e leggibile del generatore a un oggetto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Proprietà utilizzate dai sottotipi di progetto  
 Il sistema di progetto di base e di ambiente può usare le proprietà dal <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumerazioni dettagliate nella tabella seguente per abilitare un sottotipo di progetto controllare diverse funzionalità del sistema del progetto.  
  
|Proprietà VSHPROPID|Sottotipo di progetto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Consente di controllare il contenuto di un sottotipo di progetto di **Aggiungi elemento** nella finestra di dialogo. Il sottotipo di progetto può fornire una nuova specifica di directory di modello, aggiungere nuovi tipi di elementi, rimuovere gli elementi esistenti e riorganizzare un subset degli elementi in al progetto di base **Aggiungi elemento** nella finestra di dialogo.|  
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere le pagine delle proprietà indipendenti dalla configurazione.|  
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere le pagine delle proprietà dipendenti dalla configurazione.|  
|`ExtObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per il progetto o un progetto di oggetti elemento se si conosce il CATID dell'oggetto Extender. Ad esempio, un sottotipo di progetto può fornire una classe personalizzata `Project.Extender("<subtype>")` oggetto.|  
|`BrowseObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per il `Browse` oggetto sapendo il CATID dell'oggetto Extender. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive per il <xref:EnvDTE.Project.Properties%2A> raccolta.|  
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per l'oggetto di esplorazione di configurazione di progetto. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive per il <xref:EnvDTE.Configuration.Properties%2A> raccolta.|  
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per l'oggetto di configurazione.|  
|`DefaultPlatformName`|Consente a un sottotipo di progetto determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|  
  
 Il progetto di base fornisce un'implementazione predefinita di queste proprietà. Il progetto di base ottiene queste informazioni chiamando `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nel sottotipo di progetto più esterno, consentendo in tal modo il sottotipo di progetto per l'override dell'implementazione delle proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)

