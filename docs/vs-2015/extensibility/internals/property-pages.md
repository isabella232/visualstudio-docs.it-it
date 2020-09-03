---
title: Pagine delle proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a45e4a98326fe829b8f87a4ecfce669118cd9d0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205748"
---
# <a name="property-pages"></a>Pagine delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione di progetto con le pagine delle proprietà. Un pulsante **pagine delle proprietà** è abilitato nella finestra **Proprietà** o nella barra degli strumenti Esplora soluzioni per gli oggetti che forniscono una visualizzazione della pagina delle proprietà dell'oggetto selezionato. Le pagine delle proprietà vengono create dall'ambiente e sono disponibili per soluzioni e progetti. Tuttavia, possono essere rese disponibili anche per gli elementi di progetto che usano le proprietà dipendenti dalla configurazione. Questa funzionalità può essere usata quando i file all'interno di un progetto richiedono impostazioni del compilatore diverse per la compilazione corretta.  
  
## <a name="using-property-pages"></a>Utilizzo delle pagine delle proprietà  
 Se una pagina delle proprietà è già visualizzata e la selezione viene modificata, ad esempio da una soluzione a un progetto, le informazioni visualizzate nelle pagine cambiano per visualizzare le proprietà per la nuova selezione. Se non sono presenti proprietà nell'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.  
  
 Se sono selezionati più oggetti, nella pagina delle proprietà viene visualizzata l'intersezione delle proprietà di tutti gli elementi selezionati. Se l'elemento selezionato non contiene proprietà dipendenti dalla configurazione e viene fatto clic sul pulsante **pagine delle proprietà** sulla barra degli strumenti Esplora soluzioni, lo stato attivo cambierà in base alla finestra Proprietà. Per ulteriori informazioni relative all'Finestra Proprietà e alla selezione, vedere [estensione delle proprietà](../../extensibility/internals/extending-properties.md).  
  
 Se le proprietà vengono visualizzate per più oggetti e si modifica un valore in una pagina delle proprietà, tutti i valori per gli oggetti vengono impostati sul nuovo valore anche se inizialmente erano diversi e la pagina era vuota quando venivano visualizzate le proprietà di un singolo oggetto.  
  
 In sono disponibili due tipi generali di finestre di dialogo per le **pagine di ProjectProperty** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Nel primo, per i progetti Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzate usando un formato di campo, come illustrato nello screenshot seguente. Nel secondo, illustrato più avanti in questa sezione, la pagina delle proprietà ospita una griglia delle proprietà simile a quella presente nella finestra Proprietà.  
  
 ![Pagina delle proprietà di Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Finestra di dialogo Pagine delle proprietà del progetto con formato di campo e struttura ad albero  
  
 La struttura ad albero nella finestra di dialogo Pagine delle proprietà non viene compilata utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L'ambiente, basato sul nome del livello passato da <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e dalle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfacce, lo compila.  
  
 Nelle pagine delle proprietà sono disponibili solo due categorie di primo livello [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
- Proprietà comuni, che visualizza informazioni indipendenti dalla configurazione per l'oggetto o gli oggetti selezionati. Di conseguenza, quando si seleziona una delle sottocategorie delle proprietà comuni, le opzioni configurazione, piattaforma e Configuration Manager nella parte superiore della finestra di dialogo non sono disponibili.  
  
- Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri di debug, ottimizzazione e compilazione per la soluzione o il progetto.  
  
  Non è possibile creare altre categorie di primo livello, ma è possibile scegliere di non visualizzare una o l'altra nell'implementazione di `IVsPropertyPage` . Se, ad esempio, non si dispone di alcuna proprietà indipendente dalla configurazione da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria Proprietà comuni. È possibile visualizzare le proprietà comuni se `ISpecifyPropertyPages` viene implementato dall'oggetto Browse dell'elemento e dalle proprietà di configurazione quando si implementa `ISpecifyPropertyPages` nell'oggetto di configurazione (l'oggetto `IVsCfg` che implementa, `IVsProjectCfg` e le interfacce correlate).  
  
  Ogni categoria visualizzata sotto una categoria di primo livello rappresenta una pagina delle proprietà separata. Le voci di categoria e sottocategoria disponibili nella finestra di dialogo sono determinate dall'implementazione di `ISpecifyPropertyPages` e `IVsPropertyPage` .  
  
  `IDispatch` gli oggetti per gli elementi del contenitore di selezione che dispongono di proprietà da visualizzare nelle pagine delle proprietà implementano `ISpecifyPropertyPages` per enumerare un elenco di ID di classe. Gli ID di classe vengono passati come variabili a `ISpecifyPropertyPages` e vengono usati per creare un'istanza delle pagine delle proprietà. L'elenco degli ID di classe viene inoltre passato a `IVsPropertyPage` per creare la struttura ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà passano quindi le informazioni all' `IDispatch` oggetto che implementa `ISpecifyPropertyPages` e compila le informazioni per ogni pagina.  
  
  Le proprietà dell'oggetto browse vengono recuperate utilizzando `IDispatch` per ogni oggetto nel contenitore di selezione.  
  
  `Help::DisplayTopicFromF1Keyword`L'implementazione di nel pacchetto VSPackage fornisce la funzionalità per il pulsante della guida.  
  
  Per ulteriori informazioni, vedere `IDispatch` e `ISpecifyPropertyPages` in MSDN Library.  
  
  Il secondo tipo di pagine delle proprietà visualizzato negli esempi ospita un modulo della griglia delle proprietà, come illustrato nello screenshot seguente.  
  
  ![Pagina delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Finestra di dialogo Pagine delle proprietà con griglia Proprietà  
  
  Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (dichiarate in vsmanaged. h) vengono utilizzate per creare e popolare la griglia delle proprietà all'interno di una finestra di dialogo o di una finestra.  
  
  L'architettura dei progetti è cambiata notevolmente rispetto alle versioni precedenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . In particolare, la nozione di quale progetto è attivo è cambiata. In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non esiste alcun concetto di progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo era il progetto per il quale i comandi di compilazione e distribuzione sarebbero predefiniti, indipendentemente dal contesto. A questo punto, i controlli della soluzione e arbitraggio i comandi di compilazione e distribuzione si applicano ai progetti.  
  
  Ciò che in precedenza era un progetto attivo è ora acquisito in uno dei tre modi seguenti:  
  
- Progetto di avvio  
  
   È possibile specificare un progetto o progetti dalla pagina delle proprietà della soluzione che verrà avviata quando l'utente preme F5 o seleziona Esegui dal menu Compila. Funziona in modo simile al vecchio progetto attivo, nel senso che il nome viene visualizzato in Esplora soluzioni con il tipo di carattere grassetto.  
  
   È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects` . In un VSPackage è possibile chiamare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metodi o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` è disponibile come servizio in `QueryService` SID_SVsSolutionBuildManager. Per altre informazioni, vedere Configurazione di un oggetto e una [configurazione](../../extensibility/internals/solution-configuration.md)di [progetto](../../extensibility/internals/project-configuration-object.md) .  
  
- Configurazione della build della soluzione attiva  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dispone di una configurazione della soluzione attiva, disponibile nel modello di automazione mediante l'implementazione di `DTE.Solution.SolutionBuild.ActiveConfiguration` . Una configurazione della soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può avere più configurazioni, su più piattaforme, con nomi diversi). Per altre informazioni relative alle pagine delle proprietà della soluzione, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).  
  
- Progetto attualmente selezionato  
  
   Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodo per recuperare la gerarchia del progetto e l'elemento del progetto o gli elementi selezionati. Da DTE si useranno i `SelectedItems.SelectedItem.Project` metodi e `SelectedItems.SelectedItem.ProjectItem` . Il codice di esempio è disponibile nelle intestazioni dei documenti principali [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Oggetto configurazione progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
