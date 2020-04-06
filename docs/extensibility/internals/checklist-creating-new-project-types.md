---
title: 'Elenco di controllo: creazione di nuovi tipi di progetto Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709744"
---
# <a name="checklist-create-new-project-types"></a>Elenco di controllo: creare nuovi tipi di progettoChecklist: Create new project types
È necessario completare diverse attività per creare un nuovo tipo di progetto. L'elenco di controllo seguente fornisce una guida a tali attività:The following checklist provides a guide to those tasks:

1. Progettare la funzionalità per il nuovo tipo di progetto. Per ulteriori informazioni, consultate [Decisioni relative alla progettazione dei tipi](../../extensibility/internals/project-type-design-decisions.md)di progetto.

2. Determinare quali editor vengono utilizzati per il codice e altri elementi del progetto. È possibile utilizzare gli editor principali o standard oppure creare e utilizzare editor specifici del progetto. Per ulteriori informazioni, consultate Creare editor e finestre di [progettazione personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [Procedura: aprire editor specifici](../../extensibility/how-to-open-project-specific-editors.md)del progetto.

3. Determinare il livello di partecipazione degli elementi di progetto in **Visualizzazione classi** e **nel Visualizzatore oggetti**. Per ulteriori informazioni, consultate Strumenti di [esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)di supporto.

4. Derivare nuove classi in base alle decisioni di progettazione prese in precedenza per il progetto e gli elementi di progetto.

5. Scrivere il codice per i seguenti componenti del tipo di progetto:

    - Factory di progetto, per gestire la creazione di nuovi progetti e l'apertura di progetti esistenti. Per altre informazioni, vedere [Creare istanze](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)di progetto utilizzando factory di progetto .

    - Gerarchia del progetto e gestione dei comandi. Per ulteriori informazioni, vedere Utilizzo delle classi di [progetto HierUtil7 per implementare un tipo di progetto (C, )](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), Elementi di un modello di progetto , Componenti principali del [modello](../../extensibility/internals/project-model-core-components.md)di [progetto](../../extensibility/internals/elements-of-a-project-model.md)e [MenuCommands e OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Gestione degli elementi di progetto, inclusa l'aggiunta del progetto alla finestra di dialogo **Nuovo progetto.** Per ulteriori informazioni, consultate Aggiungere modelli di [progetto e di elemento](../../extensibility/internals/adding-project-and-project-item-templates.md) di progetto e [Registrare modelli](../../extensibility/internals/registering-project-and-item-templates.md)di progetto e di elemento .

    - Persistenza dello stato del progetto e dei singoli elementi. Per ulteriori informazioni, consultate [Aprire e salvare elementi di progetto.](../../extensibility/internals/opening-and-saving-project-items.md) Per la persistenza delle informazioni sulla soluzione, vedere [Soluzioni](../../extensibility/internals/solutions-overview.md).

    - Proprietà indipendenti dalla configurazione da visualizzare nella finestra Proprietà.Configuration-independent properties to display in the Properties window. Per ulteriori informazioni, consultate [Estendere le proprietà.](../../extensibility/internals/extending-properties.md)

    - Proprietà di configurazione del progetto implementate nelle pagine delle proprietà per mostrare le proprietà dipendenti dalla configurazione. Per ulteriori informazioni, consultate Gestire le opzioni di [configurazione.](../../extensibility/internals/managing-configuration-options.md)

    - Enumerazione degli output per la distribuzione. Per ulteriori informazioni, consultate [Configurazione del progetto per l'output.](../../extensibility/internals/project-configuration-for-output.md)

    - Servizi di avvio del progetto. Per ulteriori informazioni, consultate Elementi di un modello di progetto e [Componenti di base del modello](../../extensibility/internals/project-model-core-components.md)di [progetto.](../../extensibility/internals/elements-of-a-project-model.md)

    - Oggetti o classi `IDispatch`derivate da , disponibili per l'automazione.

    - File della tabella dei comandi XML (*con estensione vsct*). Per ulteriori informazioni, vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Eseguire il debug e avviare il tipo di progetto.

7. Visualizzare il progetto nella scheda **Progetto** della finestra di dialogo **Aggiungi riferimento** impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage`. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Creare il file di Microsoft Installer (*MSI*) per l'installazione dei package VS. Per ulteriori informazioni, vedere [Installare pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrare un tipo](../../extensibility/internals/registering-a-project-type.md)di progetto e [VSPackage](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Vedere anche
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quando creare i tipi di progettoWhen to create project types](../../extensibility/internals/when-to-create-project-types.md)
- [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)
