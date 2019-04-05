---
title: 'Elenco di controllo: Creazione di nuovi tipi di progetto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3a6a091e5574721b93cbff23f873fe1a845ef6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001739"
---
# <a name="checklist-creating-new-project-types"></a>Elenco di controllo: Creazione di nuovi tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È necessario completare diverse attività per creare un nuovo tipo di progetto. Elenco di controllo seguente fornisce una Guida alle attività.  
  
1.  Progettare la funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determinare quale editor vengono utilizzati per codice e altri elementi del progetto. È possibile usare l'editor standard o core oppure è possibile creare e usare gli editor specifici del progetto. Per altre informazioni, vedere [finestre di progettazione e creazione di editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [come: Aprire Editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinare il livello di partecipazione avranno gli elementi del progetto nel **Visualizzazione classi** e il **Visualizzatore oggetti**. Per altre informazioni, vedere [strumenti di esplorazione che supportano simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivare nuove classi di base alle decisioni di progettazione effettuate in precedenza per il progetto e gli elementi del progetto.  
  
5.  Scrivere il codice per i componenti di tipo di progetto seguenti:  
  
    -   Factory del progetto, per gestire la creazione di nuovi progetti e aprire progetti esistenti. Per altre informazioni, vedere [creazione di istanze da usando progetto le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Gerarchia del progetto e la gestione dei comandi. Per altre informazioni, vedere [non incluso nella Build: Uso delle classi progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md) e [Vs confronto tra oggetti MenuCommand. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Gestione elementi di progetto, inclusa l'aggiunta del progetto per la **nuovo progetto** nella finestra di dialogo. Per altre informazioni, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [registrazione di Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistenza dello stato di progetto e singoli elementi. Per altre informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per il salvataggio permanente di informazioni sulla soluzione, vedere [soluzioni](../../extensibility/internals/solutions-overview.md).  
  
    -   Proprietà indipendenti di configurazione da visualizzare nella finestra Proprietà. Per altre informazioni, vedere [estensione di proprietà](../../extensibility/internals/extending-properties.md).  
  
    -   Proprietà di configurazione del progetto come implementato nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per altre informazioni, vedere [opzioni di configurazione Gestione](../../extensibility/internals/managing-configuration-options.md).  
  
    -   L'enumerazione di output per la distribuzione. Per altre informazioni, vedere [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servizi di avvio del progetto. Per altre informazioni, vedere [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
    -   Gli oggetti o classi derivate da `IDispatch`, disponibile per l'automazione.  
  
    -   File XML comando Table (vsct). Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Test, eseguire il debug e avviare il tipo di progetto.  
  
7.  Visualizzare il progetto nel **progetto** scheda della finestra di **Aggiungi riferimento** finestra di dialogo impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage`. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Creare il file di Microsoft Installer (MSI) per l'installazione di VSPackage. Per altre informazioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md), e [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
