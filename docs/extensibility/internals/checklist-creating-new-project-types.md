---
title: 'Elenco di controllo: creazione di nuovi tipi di progetto | Microsoft Docs'
description: Informazioni sulle attività che è necessario completare per creare e visualizzare un nuovo tipo di progetto in Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 20579422e8253b2c0cff7961a91395b5e44137ab
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189966"
---
# <a name="checklist-create-new-project-types"></a>Elenco di controllo: creare nuovi tipi di progetto
Per creare un nuovo tipo di progetto, è necessario completare diverse attività. Nell'elenco di controllo seguente viene fornita una guida a tali attività:

1. Progettare le funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere [decisioni di progettazione dei tipi di progetto](../../extensibility/internals/project-type-design-decisions.md).

2. Determinare quali editor vengono utilizzati per il codice e altri elementi del progetto. È possibile utilizzare gli editor standard o di base oppure è possibile creare e utilizzare editor specifici del progetto. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di editor e finestre di progettazione personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [procedura: aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).

3. Determinare il livello di partecipazione che gli elementi del progetto avranno nel **Visualizzazione classi** e il **Visualizzatore oggetti**. Per altre informazioni, vedere [supporto per gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Derivare nuove classi in base alle decisioni di progettazione effettuate in precedenza per gli elementi del progetto e del progetto.

5. Scrivere il codice per i componenti dei tipi di progetto seguenti:

    - Project Factory, per gestire la creazione di nuovi progetti e l'apertura di progetti esistenti. Per altre informazioni, vedere [creare istanze di progetto tramite Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Gerarchia del progetto e gestione dei comandi. Per altre informazioni, vedere [usare le classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](/previous-versions/bb166212(v=vs.100)), [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)e oggetti MenuCommand e [OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

    - Gestione degli elementi di progetto, inclusa l'aggiunta del progetto alla finestra di dialogo **nuovo progetto** . Per altre informazioni, vedere [aggiungere modelli](../../extensibility/internals/adding-project-and-project-item-templates.md) di progetti e di elementi di progetto e [registrare i modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistenza dello stato del progetto e dei singoli elementi. Per altre informazioni, vedere [aprire e salvare gli elementi del progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per la persistenza delle informazioni sulla soluzione, vedere [soluzioni](../../extensibility/internals/solutions-overview.md).

    - Proprietà indipendenti dalla configurazione da visualizzare nel Finestra Proprietà. Per altre informazioni, vedere [Estendi proprietà](../../extensibility/internals/extending-properties.md).

    - Proprietà di configurazione del progetto implementate nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per altre informazioni, vedere [gestire le opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

    - Enumerazione degli output per la distribuzione. Per altre informazioni, vedere [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

    - Servizi di avvio del progetto. Per ulteriori informazioni, vedere [elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).

    - Oggetti o classi derivate da `IDispatch` , disponibili per l'automazione.

    - File della tabella dei comandi XML (con *estensione vsct*). Per ulteriori informazioni, vedere [file della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Testare, eseguire il debug e avviare il tipo di progetto.

7. Visualizzare il progetto nella scheda **progetto** della finestra di dialogo **Aggiungi riferimento** impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage` . Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Creare il file di Microsoft Installer (*MSI*) per l'installazione dei pacchetti VSPackage. Per altre informazioni, vedere [installare VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrare un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)e [VSPackage](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Vedere anche
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quando creare i tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)
- [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)