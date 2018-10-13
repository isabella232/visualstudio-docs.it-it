---
title: Pagine delle proprietà | Microsoft Docs
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
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f68dc7cc470e4244616c6e9a3cb41bdeb8f9103
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181065"
---
# <a name="property-pages"></a>Pagine delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli utenti possono visualizzare e modificare proprietà dipendenti dalla configurazione e - indipendente usando le pagine delle proprietà del progetto. Oggetto **pagine delle proprietà** pulsante è abilitato nel **proprietà** finestra o nella barra degli strumenti Esplora soluzioni per gli oggetti che forniscono una visualizzazione di pagina di proprietà dell'oggetto selezionato. Pagine delle proprietà vengono creati dall'ambiente e sono disponibili per i progetti e soluzioni. Possono, tuttavia, anche essere resi disponibili per gli elementi di progetto che fanno usano di proprietà dipendenti dalla configurazione. Questa funzionalità può essere usata quando i file all'interno di un progetto richiedono le impostazioni dell'opzione del compilatore diverse compilare correttamente.  
  
## <a name="using-property-pages"></a>Usando le pagine delle proprietà  
 Se è già visualizzata una pagina delle proprietà e la selezione viene modificata (ad esempio, da una soluzione a un progetto), le informazioni visualizzate nelle pagine delle modifiche per visualizzare le proprietà per la nuova selezione. Se non esistono proprietà sull'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.  
  
 Se sono selezionati più oggetti, la pagina delle proprietà Visualizza l'intersezione di proprietà per tutti gli elementi selezionati. Se l'elemento selezionato non contiene le proprietà dipendenti dalla configurazione e il **pagine delle proprietà** si fa clic sul pulsante sulla barra degli strumenti Esplora soluzioni, lo stato attivo passa alla finestra Proprietà. Per altre informazioni relative alla finestra delle proprietà e alla selezione, vedere [estensione di proprietà](../../extensibility/internals/extending-properties.md).  
  
 Se vengono visualizzate le proprietà per più oggetti e si modifica un valore in una pagina delle proprietà, tutti i valori per gli oggetti vengono impostati sul nuovo valore anche se sono stati inizialmente diversi e la pagina è vuota quando sono state visualizzate le proprietà di un singolo oggetto.  
  
 Esistono due tipi generali di **pagine ProjectProperty** delle finestre di dialogo disponibili in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Nel primo, per i progetti Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzati utilizzando un formato del campo, come illustrato nello screenshot seguente. Nella seconda, illustrato più avanti in questa sezione, la proprietà host pagina una griglia delle proprietà analoga a quella presente nella finestra Proprietà.  
  
 ![Pagine delle proprietà di Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Finestra di dialogo Pagine delle proprietà di progetto con la struttura di campo di formato e struttura ad albero  
  
 La struttura ad albero nella finestra di dialogo Pagine delle proprietà non è stata creata usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. L'ambiente, basato sul nome del livello passato dal <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfacce, la compila.  
  
 Sono disponibili solo due categorie di livello superiore in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pagine delle proprietà:  
  
-   Proprietà comuni, che consente di visualizzare informazioni indipendenti dalla configurazione per gli oggetti selezionati. Di conseguenza, quando viene selezionata una delle sottocategorie proprietà comuni, le opzioni di configurazione, piattaforma e Configuration Manager nella parte superiore della finestra di dialogo non sono disponibili.  
  
-   Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri di compilazione, debug e ottimizzazione per la soluzione o progetto.  
  
 Non è possibile creare le eventuali altre categorie di livello superiore, ma è possibile scegliere di non visualizzare una o l'altra nell'implementazione di `IVsPropertyPage`. Se, ad esempio, non è qualsiasi proprietà indipendenti dalla configurazione da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria di proprietà comuni. Per visualizzare le proprietà comuni se `ISpecifyPropertyPages` viene implementata dalla proprietà di configurazione e l'oggetto di visualizzazione dell'elemento quando si implementano `ISpecifyPropertyPages` nell'oggetto di configurazione (l'oggetto che implementa `IVsCfg`, `IVsProjectCfg`ed elementi correlati interfacce).  
  
 Ogni categoria visualizzata in una categoria principale rappresenta una pagina delle proprietà separate. Voci di categoria e sottocategoria disponibili nella finestra di dialogo sono determinate dall'implementazione della `ISpecifyPropertyPages` e `IVsPropertyPage`.  
  
 `IDispatch` gli oggetti per gli elementi nel contenitore di selezione che dispongono di proprietà da visualizzare nella proprietà pagine implementare `ISpecifyPropertyPages` per enumerare un elenco di ID di classe. Gli ID di classe vengono passati come variabili a `ISpecifyPropertyPages` e vengono usati per creare un'istanza di pagine delle proprietà. L'elenco di ID di classe viene anche passato a `IVsPropertyPage` per creare la struttura ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà, quindi passare informazioni eseguire il backup per il `IDispatch` oggetto che implementa `ISpecifyPropertyPages` e inserisce le informazioni per ogni pagina.  
  
 Le proprietà dell'oggetto di visualizzazione vengono recuperate usando `IDispatch` per ogni oggetto nel contenitore di selezione.  
  
 Implementazione `Help::DisplayTopicFromF1Keyword` nel pacchetto VSPackage fornisce la funzionalità per il pulsante?.  
  
 Per altre informazioni, vedere `IDispatch` e `ISpecifyPropertyPages`in MSDN library.  
  
 Il secondo tipo di pagine delle proprietà visualizzati negli host esempi una forma di griglia delle proprietà, come illustrato nello screenshot seguente.  
  
 ![Pagine delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Finestra di dialogo Pagine delle proprietà con la griglia delle proprietà  
  
 Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (dichiarato in vsmanaged.h) vengono usati per creare e popolare la griglia delle proprietà all'interno di una finestra di dialogo o una finestra.  
  
 L'architettura dei progetti è stato notevolmente modificato dalle versioni precedenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. In particolare, è attiva la nozione di quale progetto è stato modificato. In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], non vi è alcun concetto di un progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo è stato il progetto che crea e Distribuisci i comandi sarebbe per impostazione predefinita indipendentemente dal contesto. A questo punto, la soluzione controlla ed esegue l'arbitraggio che crea e Distribuisci i comandi si applicano a progetti.  
  
 Qual era in precedenza un progetto attivo ora viene acquisito in uno dei tre modi diversi:  
  
-   Il progetto di avvio  
  
     È possibile specificare uno o più progetti dalla pagina delle proprietà della soluzione che viene avviato quando l'utente preme F5 o si sceglie di eseguire dal menu Compila. Questo funziona in modo analogo per il progetto attivo precedente nel senso che il relativo nome viene visualizzato in Esplora soluzioni con tipo di carattere grassetto.  
  
     È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects`. In un pacchetto VSPackage, si chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metodi. `IVsSolutionBuildManager` è disponibile come servizio da `QueryService` su SID_SVsSolutionBuildManager. Per altre informazioni, vedere [oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md) e [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   Configurazione di compilazione della soluzione attiva  
  
     [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contiene una configurazione soluzione attiva, disponibile nel modello di automazione implementando `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configurazione di soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può avere più configurazioni su più piattaforme, con nomi diversi). Per altre informazioni relative alle pagine delle proprietà della soluzione, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   Progetto attualmente selezionato  
  
     Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodo per recuperare la gerarchia del progetto e l'elemento del progetto o gli elementi selezionati. Da DTE, si utilizzerebbe il `SelectedItems.SelectedItem.Project` e `SelectedItems.SelectedItem.ProjectItem` metodi. Codice di esempio in tali intestazioni nel nucleo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documenti.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)

