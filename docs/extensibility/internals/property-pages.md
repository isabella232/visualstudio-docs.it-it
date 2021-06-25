---
title: Pagine delle proprietà | Microsoft Docs
description: Informazioni sull'uso delle pagine delle proprietà per il nuovo tipo di progetto in Visual Studio SDK, che consentono agli utenti di visualizzare e modificare le proprietà del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903411"
---
# <a name="property-pages"></a>Pagine delle proprietà
Gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione e indipendenti dalla configurazione del progetto usando le pagine delle proprietà. Un **pulsante Pagine delle**  proprietà è abilitato nella finestra Proprietà o Esplora soluzioni barra degli strumenti per gli oggetti che forniscono una visualizzazione della pagina delle proprietà dell'oggetto selezionato. Le pagine delle proprietà vengono create dall'ambiente e sono disponibili per soluzioni e progetti. Possono tuttavia essere rese disponibili anche per gli elementi di progetto che usano proprietà dipendenti dalla configurazione. Questa funzionalità può essere usata quando i file all'interno di un progetto richiedono impostazioni diverse dell'opzione del compilatore per la compilazione corretta.

## <a name="using-property-pages"></a>Uso delle pagine delle proprietà
 Se una pagina delle proprietà è già visualizzata e la selezione cambia(ad esempio, da una soluzione a un progetto), le informazioni visualizzate nelle pagine cambiano per visualizzare le proprietà per la nuova selezione. Se non sono presenti proprietà nell'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.

 Se sono selezionati più oggetti, nella pagina delle proprietà viene visualizzata l'intersezione delle proprietà per tutti gli elementi selezionati. Se l'elemento selezionato non contiene proprietà  dipendenti dalla configurazione e si fa clic sul pulsante Pagine delle proprietà sulla barra degli strumenti di Esplora soluzioni, lo stato attivo cambia Finestra Proprietà. Per altre informazioni sull'Finestra Proprietà e sulla selezione, vedere [Estensione delle proprietà.](../../extensibility/internals/extending-properties.md)

 Se le proprietà vengono visualizzate per più oggetti e si modifica un valore in una pagina delle proprietà, tutti i valori per gli oggetti vengono impostati sul nuovo valore anche se inizialmente erano diversi e la pagina era vuota quando sono state visualizzate le proprietà di un singolo oggetto.

 Esistono due tipi generali di finestre **di dialogo ProjectProperty Pages** disponibili in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Nel primo caso di Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzate usando un formato di campo, come illustrato nello screenshot seguente. Nella seconda, illustrata più avanti in questa sezione, la pagina delle proprietà ospita una griglia delle proprietà simile a quella disponibile nella finestra Proprietà.

 ![Visual Basic pagine delle proprietà](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Finestra di dialogo Pagine delle proprietà del progetto con formato di campo e struttura ad albero

 La struttura ad albero nella finestra di dialogo Pagine delle proprietà non viene compilata utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L'ambiente, in base al nome del livello passato dalle interfacce e <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> , lo compila.

 Nelle pagine delle proprietà sono disponibili solo due [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] categorie di primo livello:

- Proprietà comuni, che visualizza informazioni indipendenti dalla configurazione per l'oggetto o gli oggetti selezionati. Di conseguenza, quando si seleziona una delle sottocategorie Proprietà comuni, le opzioni Configurazione, Piattaforma e Gestione configurazione nella parte superiore della finestra di dialogo non sono disponibili.

- Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri di debug, ottimizzazione e compilazione per la soluzione o il progetto.

  Non è possibile creare altre categorie di primo livello, ma è possibile scegliere di non visualizzare una o l'altra nell'implementazione di `IVsPropertyPage` . Se, ad esempio, non sono disponibili proprietà indipendenti dalla configurazione da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria Proprietà comuni . Le proprietà comuni vengono visualizzate se viene implementata dall'oggetto di esplorazione dell'elemento e le proprietà di configurazione quando si implementa nell'oggetto di configurazione (l'oggetto che implementa , e `ISpecifyPropertyPages` `ISpecifyPropertyPages` le interfacce `IVsCfg` `IVsProjectCfg` correlate).

  Ogni categoria visualizzata in una categoria di primo livello rappresenta una pagina delle proprietà separata. Le voci di categoria e sottocategoria disponibili nella finestra di dialogo sono determinate dall'implementazione di `ISpecifyPropertyPages` e `IVsPropertyPage` .

  `IDispatch` Gli oggetti per gli elementi nel contenitore di selezione che dispongono di proprietà da visualizzare nelle pagine delle proprietà implementano `ISpecifyPropertyPages` per enumerare un elenco di ID di classe. Gli ID classe vengono passati come variabili a e vengono usati per creare `ISpecifyPropertyPages` un'istanza delle pagine delle proprietà. L'elenco degli ID di classe viene anche passato a per creare la struttura `IVsPropertyPage` ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà passano quindi le informazioni `IDispatch` all'oggetto che implementa `ISpecifyPropertyPages` e inserisce le informazioni per ogni pagina.

  Le proprietà dell'oggetto browse vengono recuperate usando `IDispatch` per ogni oggetto nel contenitore di selezione.

  `Help::DisplayTopicFromF1Keyword`L'implementazione di nel pacchetto VSPackage fornisce la funzionalità per il pulsante ? .

  Per altre informazioni, vedere `IDispatch` e `ISpecifyPropertyPages` in MSDN Library.

  Il secondo tipo di pagine delle proprietà visualizzate negli esempi ospita un modulo della griglia delle proprietà, come illustrato nello screenshot seguente.

  ![Pagine delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Finestra di dialogo Pagine delle proprietà con griglia delle proprietà

  Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (dichiarate in vsmanaged.h) vengono usate per creare e popolare la griglia delle proprietà all'interno di una finestra o di una finestra di dialogo.

  L'architettura dei progetti è cambiata notevolmente rispetto alle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . In particolare, è cambiata la nozione di progetto attivo. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non esiste alcun concetto di progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo era il progetto che compilava e distribuisce i comandi per impostazione predefinita indipendentemente dal contesto. A questo punto, la soluzione controlla e arbita i comandi di compilazione e distribuzione applicabili a quali progetti.

  Quello che in precedenza era un progetto attivo ora viene acquisito in uno dei tre modi seguenti:

- Progetto di avvio

   È possibile specificare uno o più progetti dalla pagina delle proprietà della soluzione che verrà avviata quando l'utente preme F5 o sceglie Esegui dal menu Compila. Questa operazione funziona in modo simile al progetto attivo precedente, nel senso che il nome viene visualizzato in Esplora soluzioni con tipo di carattere grassetto.

   È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects` . In un VSPackage si chiamano i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metodi o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` è disponibile come servizio da `QueryService` in SID_SVsSolutionBuildManager. Per altre informazioni, vedere [Project Configuration Object e](../../extensibility/internals/project-configuration-object.md) Solution [Configuration.](../../extensibility/internals/solution-configuration.md)

- Configurazione della build della soluzione attiva

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ha una configurazione di soluzione attiva, disponibile nel modello di automazione implementando `DTE.Solution.SolutionBuild.ActiveConfiguration` . Una configurazione di soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può avere più configurazioni, su più piattaforme, con nomi diversi). Per altre informazioni relative alle pagine delle proprietà della soluzione, vedere [Configurazione della soluzione.](../../extensibility/internals/solution-configuration.md)

- Progetto attualmente selezionato

   Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodo per recuperare la gerarchia del progetto e l'elemento o gli elementi selezionati. Da DTE si userebbero i `SelectedItems.SelectedItem.Project` metodi `SelectedItems.SelectedItem.ProjectItem` e . È disponibile codice di esempio sotto queste intestazioni nei documenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] principali.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
