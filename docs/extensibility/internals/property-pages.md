---
title: Pagine delle proprietà | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725051"
---
# <a name="property-pages"></a>Pagine delle proprietà
Gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione di progetto con le pagine delle proprietà. Un pulsante **pagine delle proprietà** è abilitato nella finestra **Proprietà** o nella barra degli strumenti Esplora soluzioni per gli oggetti che forniscono una visualizzazione della pagina delle proprietà dell'oggetto selezionato. Le pagine delle proprietà vengono create dall'ambiente e sono disponibili per soluzioni e progetti. Tuttavia, possono essere rese disponibili anche per gli elementi di progetto che usano le proprietà dipendenti dalla configurazione. Questa funzionalità può essere usata quando i file all'interno di un progetto richiedono impostazioni del compilatore diverse per la compilazione corretta.

## <a name="using-property-pages"></a>Utilizzo delle pagine delle proprietà
 Se una pagina delle proprietà è già visualizzata e la selezione viene modificata, ad esempio da una soluzione a un progetto, le informazioni visualizzate nelle pagine cambiano per visualizzare le proprietà per la nuova selezione. Se non sono presenti proprietà nell'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.

 Se sono selezionati più oggetti, nella pagina delle proprietà viene visualizzata l'intersezione delle proprietà di tutti gli elementi selezionati. Se l'elemento selezionato non contiene proprietà dipendenti dalla configurazione e viene fatto clic sul pulsante **pagine delle proprietà** sulla barra degli strumenti Esplora soluzioni, lo stato attivo cambierà in base alla finestra Proprietà. Per ulteriori informazioni relative all'Finestra Proprietà e alla selezione, vedere [estensione delle proprietà](../../extensibility/internals/extending-properties.md).

 Se le proprietà vengono visualizzate per più oggetti e si modifica un valore in una pagina delle proprietà, tutti i valori per gli oggetti vengono impostati sul nuovo valore anche se inizialmente erano diversi e la pagina era vuota quando venivano visualizzate le proprietà di un singolo oggetto.

 Sono disponibili due tipi generali di finestre di dialogo per le **pagine ProjectProperty** in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nel primo, per i progetti Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzate usando un formato di campo, come illustrato nello screenshot seguente. Nel secondo, illustrato più avanti in questa sezione, la pagina delle proprietà ospita una griglia delle proprietà simile a quella presente nella finestra Proprietà.

 ![Pagine delle proprietà Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Finestra di dialogo Pagine delle proprietà del progetto con formato di campo e struttura ad albero

 La struttura ad albero nella finestra di dialogo Pagine delle proprietà non viene compilata utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. L'ambiente, basato sul nome del livello passato dal <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e dalle interfacce <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>, lo compila.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pagine delle proprietà sono disponibili solo due categorie di primo livello:

- Proprietà comuni, che visualizza informazioni indipendenti dalla configurazione per l'oggetto o gli oggetti selezionati. Di conseguenza, quando si seleziona una delle sottocategorie delle proprietà comuni, le opzioni configurazione, piattaforma e Configuration Manager nella parte superiore della finestra di dialogo non sono disponibili.

- Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri di debug, ottimizzazione e compilazione per la soluzione o il progetto.

  Non è possibile creare altre categorie di primo livello, ma è possibile scegliere di non visualizzare una o l'altra nell'implementazione di `IVsPropertyPage`. Se, ad esempio, non si dispone di alcuna proprietà indipendente dalla configurazione da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria Proprietà comuni. È possibile visualizzare le proprietà comuni se `ISpecifyPropertyPages` viene implementato dall'oggetto Browse e dalle proprietà di configurazione dell'elemento quando si implementano `ISpecifyPropertyPages` nell'oggetto di configurazione (l'oggetto che implementa `IVsCfg`, `IVsProjectCfg` e le interfacce correlate).

  Ogni categoria visualizzata sotto una categoria di primo livello rappresenta una pagina delle proprietà separata. Le voci di categoria e sottocategoria disponibili nella finestra di dialogo sono determinate dall'implementazione di `ISpecifyPropertyPages` e `IVsPropertyPage`.

  `IDispatch` oggetti per gli elementi del contenitore di selezione che dispongono di proprietà da visualizzare nelle pagine delle proprietà implementano `ISpecifyPropertyPages` per enumerare un elenco di ID di classe. Gli ID di classe vengono passati come variabili a `ISpecifyPropertyPages` e vengono usati per creare un'istanza delle pagine delle proprietà. L'elenco degli ID di classe viene inoltre passato a `IVsPropertyPage` per creare la struttura ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà passano quindi le informazioni all'oggetto `IDispatch` che implementa `ISpecifyPropertyPages` e compila le informazioni per ogni pagina.

  Le proprietà dell'oggetto browse vengono recuperate usando `IDispatch` per ogni oggetto nel contenitore di selezione.

  L'implementazione di `Help::DisplayTopicFromF1Keyword` nel pacchetto VSPackage fornisce la funzionalità per il pulsante della guida.

  Per ulteriori informazioni, vedere `IDispatch` e `ISpecifyPropertyPages`in MSDN Library.

  Il secondo tipo di pagine delle proprietà visualizzato negli esempi ospita un modulo della griglia delle proprietà, come illustrato nello screenshot seguente.

  ![Pagine delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Finestra di dialogo Pagine delle proprietà con griglia Proprietà

  Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (dichiarate in vsmanaged. h) vengono utilizzate per creare e popolare la griglia delle proprietà all'interno di una finestra di dialogo o di una finestra.

  L'architettura dei progetti è cambiata notevolmente rispetto alle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In particolare, la nozione di quale progetto è attivo è cambiata. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non esiste alcun concetto di progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo era il progetto per il quale i comandi di compilazione e distribuzione sarebbero predefiniti, indipendentemente dal contesto. A questo punto, i controlli della soluzione e arbitraggio i comandi di compilazione e distribuzione si applicano ai progetti.

  Ciò che in precedenza era un progetto attivo è ora acquisito in uno dei tre modi seguenti:

- Progetto di avvio

   È possibile specificare un progetto o progetti dalla pagina delle proprietà della soluzione che verrà avviata quando l'utente preme F5 o seleziona Esegui dal menu Compila. Funziona in modo simile al vecchio progetto attivo, nel senso che il nome viene visualizzato in Esplora soluzioni con il tipo di carattere grassetto.

   È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects`. In un VSPackage è possibile chiamare i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>. `IVsSolutionBuildManager` è disponibile come servizio per `QueryService` in SID_SVsSolutionBuildManager. Per altre informazioni, vedere Configurazione di un oggetto e una [configurazione](../../extensibility/internals/solution-configuration.md)di [progetto](../../extensibility/internals/project-configuration-object.md) .

- Configurazione della build della soluzione attiva

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispone di una configurazione della soluzione attiva, disponibile nel modello di automazione, implementando `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configurazione della soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può avere più configurazioni, su più piattaforme, con nomi diversi). Per altre informazioni relative alle pagine delle proprietà della soluzione, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

- Progetto attualmente selezionato

   Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> per recuperare la gerarchia del progetto e l'elemento del progetto o gli elementi selezionati. Da DTE si useranno i metodi `SelectedItems.SelectedItem.Project` e `SelectedItems.SelectedItem.ProjectItem`. È disponibile codice di esempio sotto le intestazioni dei documenti principali [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)