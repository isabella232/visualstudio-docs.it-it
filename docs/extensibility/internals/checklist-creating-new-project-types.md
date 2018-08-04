---
title: 'Elenco di controllo: Creazione di nuovi tipi di progetto | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69eaf52f9864b61cfc5045da9dbaf0ca6b4410b9
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511665"
---
# <a name="checklist-create-new-project-types"></a>Elenco di controllo: Creare nuovi tipi di progetto
È necessario completare diverse attività per creare un nuovo tipo di progetto. Elenco di controllo seguente offre una Guida alle attività:  
  
1.  Progettare la funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determinare quale editor vengono utilizzati per codice e altri elementi del progetto. È possibile usare l'editor standard o core oppure è possibile creare e usare gli editor specifici del progetto. Per altre informazioni, vedere [creare editor personalizzati e finestre di progettazione](../../extensibility/creating-custom-editors-and-designers.md) e [procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinare il livello di partecipazione avranno gli elementi del progetto nel **Visualizzazione classi** e il **Visualizzatore oggetti**. Per altre informazioni, vedere [supporta gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivare nuove classi di base alle decisioni di progettazione effettuate in precedenza per il progetto e gli elementi del progetto.  
  
5.  Scrivere il codice per i componenti di tipo di progetto seguenti:  
  
    -   Factory del progetto, per gestire la creazione di nuovi progetti e aprire progetti esistenti. Per altre informazioni, vedere [creare le istanze del progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Gerarchia del progetto e la gestione dei comandi. Per altre informazioni, vedere [HierUtil7 Usa le classi di progetto per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)e [ Confronto tra oggetti MenuCommand Visual Studio. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Gestione elementi di progetto, inclusa l'aggiunta del progetto per la **nuovo progetto** nella finestra di dialogo. Per altre informazioni, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistenza dello stato di progetto e singoli elementi. Per altre informazioni, vedere [aperte e salvare elementi del progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per il salvataggio permanente di informazioni sulla soluzione, vedere [soluzioni](../../extensibility/internals/solutions.md).  
  
    -   Proprietà indipendenti dalla configurazione da visualizzare nella finestra Proprietà. Per altre informazioni, vedere [estendere proprietà](../../extensibility/internals/extending-properties.md).  
  
    -   Proprietà di configurazione del progetto come implementato nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per altre informazioni, vedere [gestire le opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
    -   L'enumerazione di output per la distribuzione. Per altre informazioni, vedere [configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servizi di avvio del progetto. Per altre informazioni, vedere [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
    -   Gli oggetti o classi derivate da `IDispatch`, disponibile per l'automazione.  
  
    -   Tabella comandi XML (*vsct*) file. Per altre informazioni, vedere [file table (vsct) di Visual Studio comando](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Test, eseguire il debug e avviare il tipo di progetto.  
  
7.  Visualizzare il progetto nel **progetto** scheda della finestra di **Aggiungi riferimento** finestra di dialogo impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage`. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Creazione di Microsoft Installer (*file con estensione msi*) file per l'installazione di VSPackage. Per altre informazioni, vedere [installa i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrare un tipo di progetto](../../extensibility/internals/registering-a-project-type.md), e [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)