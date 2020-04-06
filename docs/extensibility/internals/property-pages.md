---
title: Pagine delle proprietà Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706062"
---
# <a name="property-pages"></a>Pagine delle proprietà
Gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione del progetto e le proprietà indipendenti dalla configurazione del progetto utilizzando le pagine delle proprietà. Un pulsante **Pagine delle proprietà** è abilitato nella finestra **Proprietà** o nella barra degli strumenti Esplora soluzioni per gli oggetti che forniscono una visualizzazione della pagina delle proprietà dell'oggetto selezionato. Le pagine delle proprietà vengono create dall'ambiente e sono disponibili per soluzioni e progetti. Possono, tuttavia, anche essere resi disponibili per gli elementi di progetto che utilizzano proprietà dipendenti dalla configurazione. Questa funzionalità può essere utilizzata quando i file all'interno di un progetto richiedono diverse impostazioni dello switch del compilatore per compilare correttamente.

## <a name="using-property-pages"></a>Utilizzo delle pagine delle proprietàUsing Property Pages
 Se una pagina delle proprietà è già visualizzata e la selezione cambia (ad esempio, da una soluzione a un progetto), le informazioni visualizzate nelle pagine cambiano per visualizzare le proprietà per la nuova selezione. Se non sono presenti proprietà nell'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.

 Se sono selezionati più oggetti, nella pagina delle proprietà viene visualizzata l'intersezione delle proprietà per tutti gli elementi selezionati. Se l'elemento selezionato non contiene proprietà dipendenti dalla configurazione e viene fatto clic sul pulsante **Pagine delle proprietà** nella barra degli strumenti di Esplora soluzioni, lo stato attivo passa alla finestra Proprietà.If the selected item does not contain configuration-dependent properties and the Property Pages button on the Solution Explorer toolbar is clicked, lo stato attivo passa alla finestra Proprietà. Per ulteriori informazioni relative alla finestra Proprietà e alla selezione, vedere [Estensione delle proprietà](../../extensibility/internals/extending-properties.md).

 Se le proprietà vengono visualizzate per più oggetti e si modifica un valore in una pagina delle proprietà, tutti i valori per gli oggetti vengono impostati sul nuovo valore anche se inizialmente erano diversi e la pagina era vuota quando le proprietà di un singolo oggetto sono state visualizzate.

 In . **ProjectProperty Pages** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nel primo, per i progetti Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzate utilizzando un formato di campo, come illustrato nella schermata seguente. In the second, shown later in this section, the property page hosts a properties grid similar to that found in the Properties Window.

 ![Pagine delle proprietà di Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "VsVBPropPages vsVBPropPages") Finestra di dialogo Pagine delle proprietà del progetto con il formato del campo e la struttura ad albero

 La struttura ad albero nella finestra di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>dialogo Pagine delle proprietà non viene compilata utilizzando . L'ambiente, in base al nome <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> livello passato dalle interfacce e .

 Nelle pagine delle proprietà sono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] disponibili solo due categorie di primo livello:There are only two top-level categories available on Property pages:

- Proprietà comuni, che visualizza informazioni indipendenti dalla configurazione per l'oggetto o gli oggetti selezionati. Di conseguenza, quando viene selezionata una delle sottocategorie Proprietà comuni, le opzioni Configurazione, Piattaforma e Configuration Manager nella parte superiore della finestra di dialogo non sono disponibili.

- Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri debugging, Optimization e Build per la soluzione o il progetto.

  Non è possibile creare altre categorie di primo livello, ma è possibile `IVsPropertyPage`scegliere di non visualizzare l'una o l'altra nell'implementazione di . Se, ad esempio, non si dispone di proprietà indipendenti dalla configurazione da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria Proprietà comuni. Le proprietà comuni `ISpecifyPropertyPages` vengono visualizzate se vengono implementate dall'oggetto `ISpecifyPropertyPages` sfoglia dell'elemento e `IVsCfg` `IVsProjectCfg`dalle proprietà Configuration durante l'implementazione nell'oggetto di configurazione (l'oggetto che implementa , e le interfacce correlate).

  Ogni categoria visualizzata in una categoria di primo livello rappresenta una pagina delle proprietà separata. Le voci di categoria e sottocategoria disponibili nella `ISpecifyPropertyPages` finestra `IVsPropertyPage`di dialogo sono determinate dall'implementazione di e .

  `IDispatch`Gli oggetti per gli elementi nel contenitore di selezione `ISpecifyPropertyPages` che dispongono di proprietà da visualizzare nelle pagine delle proprietà implementano per enumerare un elenco di ID di classe. Gli ID di classe vengono `ISpecifyPropertyPages` passati come variabili e vengono utilizzati per creare un'istanza delle pagine delle proprietà. L'elenco degli ID di classe `IVsPropertyPage` viene passato anche per creare la struttura ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà passano quindi le informazioni all'oggetto `IDispatch` che implementa `ISpecifyPropertyPages` e inserisce le informazioni per ogni pagina.

  Le proprietà dell'oggetto Sfoglia `IDispatch` vengono recuperate utilizzando per ogni oggetto nel contenitore di selezione.

  Implementazione nel pacchetto VSPackage fornisce la funzionalità per il pulsante Guida.Implementing `Help::DisplayTopicFromF1Keyword` in your VSPackage provides the functionality for the Help button.

  Per ulteriori informazioni, vedere `IDispatch` e `ISpecifyPropertyPages`in MSDN Library.

  Il secondo tipo di pagine delle proprietà visualizzate negli esempi ospita una forma della griglia delle proprietà, come illustrato nella schermata seguente.

  ![Pagine delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "VsVCPropPages (informazioni in base alle pagine vcVCPropPages") Finestra di dialogo Pagine delle proprietà con griglia delle proprietà

  Le `IVSMDPropertyBrowser` interfacce `IVSMDPropertyGrid` e (dichiarate in vsmanaged.h) vengono utilizzate per creare e popolare la griglia delle proprietà all'interno di una finestra di dialogo o di una finestra.

  L'architettura dei progetti è cambiata considerevolmente rispetto alle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In particolare, la nozione di quale progetto è attivo è cambiata. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], non esiste alcun concetto di progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo era il progetto su cui i comandi di compilazione e distribuzione sarebbero stati predefiniti indipendentemente dal contesto. A questo punto, i controlli della soluzione e gli arbitri dei comandi di compilazione e distribuzione si applicano a quali progetti.

  Quello che in precedenza era un progetto attivo ora viene acquisito in uno dei tre modi seguenti:

- Il progetto Startup

   È possibile specificare uno o più progetti dalla pagina delle proprietà della soluzione che verrà avviata quando l'utente preme F5 o seleziona Esegui dal menu Compila. Questo funziona in modo simile al vecchio progetto attivo nel senso che il suo nome viene visualizzato in Esplora soluzioni con carattere grassetto.

   È possibile recuperare il progetto di avvio `DTE.Solution.SolutionBuild.StartupProjects`come proprietà nel modello di automazione chiamando . In un pacchetto VSPackage, chiamare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metodi o . `IVsSolutionBuildManager`è disponibile come `QueryService` servizio su SID_SVsSolutionBuildManager. Per ulteriori informazioni, vedere Oggetto di [configurazione del progetto](../../extensibility/internals/project-configuration-object.md) e Configurazione [soluzione](../../extensibility/internals/solution-configuration.md).

- Configurazione della build della soluzione attiva

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ha una configurazione di soluzione attiva, `DTE.Solution.SolutionBuild.ActiveConfiguration`disponibile nel modello di automazione implementando . Una configurazione di soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può avere più configurazioni, su più piattaforme, con nomi diversi). Per ulteriori informazioni relative alle pagine delle proprietà della soluzione, vedere [Configurazione soluzione](../../extensibility/internals/solution-configuration.md).

- Progetto attualmente selezionato

   Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> il metodo per recuperare la gerarchia del progetto e l'elemento di progetto o gli elementi selezionati. Da DTE, è `SelectedItems.SelectedItem.Project` necessario `SelectedItems.SelectedItem.ProjectItem` utilizzare i metodi e . C'è codice di esempio sotto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le intestazioni nei documenti principali.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione soluzione](../../extensibility/internals/solution-configuration.md)
