---
title: 'Elenco di controllo: creazione di nuovi tipi di progetto | Microsoft Docs'
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
ms.openlocfilehash: 02edc5925109a31eebfd98c90bd116fb86eef276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697233"
---
# <a name="checklist-creating-new-project-types"></a>Elenco di controllo: Creazione di nuovi tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per creare un nuovo tipo di progetto, è necessario completare diverse attività. Nell'elenco di controllo seguente viene fornita una guida a tali attività.  
  
1. Progettare le funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere [decisioni di progettazione dei tipi di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
2. Determinare quali editor vengono utilizzati per il codice e altri elementi del progetto. È possibile utilizzare gli editor standard o di base oppure è possibile creare e utilizzare editor specifici del progetto. Per ulteriori informazioni, vedere [creazione di editor e finestre di progettazione personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [procedura: aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3. Determinare il livello di partecipazione che gli elementi del progetto avranno nel **Visualizzazione classi** e il **Visualizzatore oggetti**. Per ulteriori informazioni, vedere [supporto degli strumenti](../../extensibility/internals/supporting-symbol-browsing-tools.md)per l'esplorazione dei simboli.  
  
4. Derivare nuove classi in base alle decisioni di progettazione effettuate in precedenza per gli elementi del progetto e del progetto.  
  
5. Scrivere il codice per i componenti dei tipi di progetto seguenti:  
  
    - Project Factory, per gestire la creazione di nuovi progetti e l'apertura di progetti esistenti. Per altre informazioni, vedere [creazione di istanze di progetto tramite Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    - Gerarchia del progetto e gestione dei comandi. Per altre informazioni, vedere [not in Build: uso delle classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md) e oggetti MenuCommand e [OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    - Gestione degli elementi di progetto, inclusa l'aggiunta del progetto alla finestra di dialogo **nuovo progetto** . Per altre informazioni, vedere [aggiunta di modelli](../../extensibility/internals/adding-project-and-project-item-templates.md) di progetto e di elementi di progetto e registrazione dei [modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    - Persistenza dello stato del progetto e dei singoli elementi. Per ulteriori informazioni, vedere [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per la persistenza delle informazioni sulla soluzione, vedere [soluzioni](../../extensibility/internals/solutions-overview.md).  
  
    - Proprietà indipendenti dalla configurazione da visualizzare nel Finestra Proprietà. Per ulteriori informazioni, vedere [estensione delle proprietà](../../extensibility/internals/extending-properties.md).  
  
    - Proprietà di configurazione del progetto implementate nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per ulteriori informazioni, vedere [gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
    - Enumerazione degli output per la distribuzione. Per altre informazioni, vedere [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).  
  
    - Servizi di avvio del progetto. Per ulteriori informazioni, vedere [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
    - Oggetti o classi derivate da `IDispatch` , disponibili per l'automazione.  
  
    - File della tabella dei comandi XML (con estensione vsct). Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6. Testare, eseguire il debug e avviare il tipo di progetto.  
  
7. Visualizzare il progetto nella scheda **progetto** della finestra di dialogo **Aggiungi riferimento** impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage` . Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8. Creare il file di Microsoft Installer (MSI) per l'installazione dei pacchetti VSPackage. Per altre informazioni, vedere [installazione di VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)e [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando creare i tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
