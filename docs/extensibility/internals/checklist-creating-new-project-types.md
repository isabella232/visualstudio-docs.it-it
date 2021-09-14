---
title: 'Elenco di controllo: Creazione di nuovi Project di | Microsoft Docs'
description: Informazioni sulle attività che devono essere completate per creare e visualizzare un nuovo tipo di progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e7cb031b55a83dbc2694b8532c91b013a343ffa3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627354"
---
# <a name="checklist-create-new-project-types"></a>Elenco di controllo: Creare nuovi tipi di progetto
È necessario completare diverse attività per creare un nuovo tipo di progetto. L'elenco di controllo seguente fornisce una guida a tali attività:

1. Progettare la funzionalità per il nuovo tipo di progetto. Per altre informazioni, vedere l'Project [di progettazione dei tipi.](../../extensibility/internals/project-type-design-decisions.md)

2. Determinare quali editor vengono usati per il codice e altri elementi del progetto. È possibile usare gli editor di base o standard oppure è possibile creare e usare editor specifici del progetto. Per altre informazioni, vedere [Creare editor e finestre di progettazione personalizzati](../../extensibility/creating-custom-editors-and-designers.md) e [Procedura: Aprire editor specifici del progetto.](../../extensibility/how-to-open-project-specific-editors.md)

3. Determinare il livello di partecipazione degli elementi di progetto nel Visualizzazione classi **e** nel **Visualizzatore oggetti.** Per altre informazioni, vedere Support [symbol-browsing tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Derivare nuove classi in base alle decisioni di progettazione prese in precedenza per il progetto e gli elementi del progetto.

5. Scrivere il codice per i componenti del tipo di progetto seguenti:

    - Project factory, per gestire la creazione di nuovi progetti e l'apertura di progetti esistenti. Per altre informazioni, vedere [Creare istanze di progetto usando factory di progetto.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

    - Project della gerarchia e dei comandi. Per altre informazioni, vedere Usare le classi di progetto HierUtil7 per implementare un tipo di progetto [(C++),](/previous-versions/bb166212(v=vs.100)) [Elementi](../../extensibility/internals/elements-of-a-project-model.md)di un modello di progetto, componenti principali del modello [Project](../../extensibility/internals/project-model-core-components.md)e MenuCommands e [OleMenuCommands.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

    - Project gestione degli elementi, inclusa l'aggiunta del progetto alla **finestra di dialogo Project** nuovo progetto. Per altre informazioni, vedere Aggiungere modelli [di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [Registrare modelli di progetto ed elemento.](../../extensibility/internals/registering-project-and-item-templates.md)

    - Persistenza dello stato del progetto e dei singoli elementi. Per altre informazioni, vedere [Aprire e salvare elementi di progetto.](../../extensibility/internals/opening-and-saving-project-items.md) Per la persistenza delle informazioni sulla soluzione, vedere [Soluzioni.](../../extensibility/internals/solutions-overview.md)

    - Proprietà indipendenti dalla configurazione da visualizzare nel Finestra Proprietà. Per altre informazioni, vedere [Estendere le proprietà.](../../extensibility/internals/extending-properties.md)

    - Project proprietà di configurazione implementate nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per altre informazioni, vedere Gestire [le opzioni di configurazione.](../../extensibility/internals/managing-configuration-options.md)

    - Enumerazione degli output per la distribuzione. Per altre informazioni, vedere Configurazione [Project per l'output.](../../extensibility/internals/project-configuration-for-output.md)

    - Project servizi di avvio. Per altre informazioni, vedere [Elementi di un modello di progetto e](../../extensibility/internals/elements-of-a-project-model.md) Componenti Project componenti di base del [modello.](../../extensibility/internals/project-model-core-components.md)

    - Oggetti o classi derivate da `IDispatch` , disponibili per l'automazione.

    - File di tabella dei comandi XML *(con estensione vsct).* Per altre informazioni, vedere Visual Studio file di tabella dei comandi (con estensione [vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Testare, eseguire il debug e avviare il tipo di progetto.

7. Visualizzare il progetto nella **Project** della **finestra** di dialogo Aggiungi riferimento impostando come valore `VARIANT_TRUE` per `VSHPROPID_ShowProjInSolutionPage` . Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Creare il file di Microsoft Installer (*.msi*) per installare i pacchetti VSPackage. Per altre informazioni, vedere [Install VSPackages with Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), Register a project [type](../../extensibility/internals/registering-a-project-type.md)e [VSPackages.](../../extensibility/internals/vspackages.md)

## <a name="see-also"></a>Vedi anche
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quando creare i tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)
- [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)