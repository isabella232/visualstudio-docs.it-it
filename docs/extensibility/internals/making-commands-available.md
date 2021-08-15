---
title: Rendere disponibili i comandi | Microsoft Docs
description: Informazioni su come controllare la disponibilità dei comandi aggiunti all'IDE di Visual Studio nei pacchetti VSPackage usando il caricamento ritardato, il contesto e la visibilità.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f845644650c3ed87d0a62543da5a8155dcf806b02b8cb65db30e5297350ee185
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305555"
---
# <a name="making-commands-available"></a>Rendere disponibili i comandi

Quando vengono aggiunti più pacchetti VSPackage Visual Studio, l'interfaccia utente può diventare sovraffollata da comandi. È possibile programmare il pacchetto per ridurre questo problema, come indicato di seguito:

- Programmare il pacchetto in modo che sia caricato solo quando richiesto da un utente.

- Programmare il pacchetto in modo che i relativi comandi siano visualizzati solo quando potrebbero essere necessari nel contesto dello stato corrente dell'ambiente di sviluppo integrato (IDE).

## <a name="delayed-loading"></a>Caricamento ritardato

Il modo tipico per abilitare il caricamento ritardato è progettare il PACCHETTO VSPackage in modo che i relativi comandi siano visualizzati nell'interfaccia utente, ma il pacchetto stesso non viene caricato fino a quando un utente non fa clic su uno dei comandi. A tale scopo, nel file con estensione vsct creare comandi senza flag di comando.

L'esempio seguente illustra la definizione di un comando di menu da un file con estensione vsct. Si tratta del comando generato dal modello di Visual Studio quando è selezionata l'opzione **Comando** di menu nel modello.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

Nell'esempio, se il gruppo padre, , è figlio di un menu di primo livello, ad esempio il menu Strumenti , il comando sarà visibile in tale menu, ma il pacchetto che esegue il comando non verrà caricato fino a quando un utente non fa clic sul `MyMenuGroup` comando.  Tuttavia, programmando il comando per implementare l'interfaccia , è possibile abilitare il caricamento del pacchetto quando il menu che contiene il comando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> viene espanso per la prima volta.

Si noti che il caricamento ritardato può anche migliorare le prestazioni di avvio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contesto corrente e visibilità dei comandi

È possibile programmare i comandi VSPackage in modo che siano visibili o nascosti, a seconda dello stato corrente dei dati VSPackage o delle azioni attualmente rilevanti. È possibile abilitare il pacchetto VSPackage per impostare lo stato dei relativi comandi, in genere usando un'implementazione del metodo dall'interfaccia , ma ciò richiede che il VSPackage venga caricato prima di poter eseguire il <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> codice. È invece consigliabile abilitare l'IDE per gestire la visibilità dei comandi senza caricare il pacchetto. A tale scopo, nel file con estensione vsct associare i comandi a uno o più contesti speciali dell'interfaccia utente. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come *GUID del contesto di comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitora le modifiche risultanti da azioni dell'utente, ad esempio il caricamento di un progetto o il processo di modifica o compilazione. Quando si verificano modifiche, l'aspetto dell'IDE viene modificato automaticamente. La tabella seguente illustra quattro contesti principali della modifica dell'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitorata.

| Tipo di contesto | Descrizione |
|-------------------------| - |
| Tipo Project attivo | Per la maggior parte dei tipi di progetto, questo valore `GUID` corrisponde al GUID del pacchetto VSPackage che implementa il progetto. Tuttavia, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i progetti usano Project type come `GUID` valore. |
| Finestra attiva | In genere, questa è l'ultima finestra del documento attiva che stabilisce il contesto dell'interfaccia utente corrente per i tasti di scelta rapida. Tuttavia, potrebbe anche essere una finestra degli strumenti con una tabella di associazione di tasti simile alla tabella Web browser. Per le finestre dei documenti a schede diverse, ad esempio l'editor HTML, ogni scheda ha un contesto di comando `GUID` diverso. |
| Active Language Service | Servizio di linguaggio associato al file attualmente visualizzato in un editor di testo. |
| Finestra degli strumenti attiva | Finestra degli strumenti aperta con lo stato attivo. |

Una quinta area di contesto principale è lo stato dell'interfaccia utente dell'IDE. I contesti dell'interfaccia utente sono identificati dai contesti di `GUID` comando attivi, come indicato di seguito:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Questi GUID sono contrassegnati come attivi o inattivi, a seconda dello stato corrente dell'IDE. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

### <a name="hide-and-display-commands-based-on-context"></a>Nascondere e visualizzare i comandi in base al contesto

È possibile visualizzare o nascondere un comando di pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file con estensione vsct del pacchetto usando i flag di comando , e e aggiungendo uno o più elementi VisibilityItem alla `DefaultDisabled` `DefaultInvisible` sezione `DynamicVisibility` [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) [](../../extensibility/visibilityitem-element.md) Quando un contesto di comando `GUID` specificato diventa attivo, il comando viene visualizzato senza caricare il pacchetto.

### <a name="custom-context-guids"></a>GUID di contesto personalizzati

Se non è già stato definito un GUID del contesto di comando appropriato, è possibile definirne uno nel vspackage e programmarlo in modo che sia attivo o inattivo in base alle esigenze per controllare la visibilità dei comandi. Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio per:

- Registrare i GUID di contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo ).

- Ottenere lo stato di un `GUID` contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo ).

- Attivare e `GUID` disattivare il contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo ).

    > [!CAUTION]
    > Assicurarsi che il pacchetto VSPackage non influisca sullo stato di qualsiasi GUID di contesto esistente perché altri PACCHETTI VSPackage possono dipendere da essi.

## <a name="example"></a>Esempio

L'esempio seguente di un comando VSPackage illustra la visibilità dinamica di un comando gestito da contesti di comando senza caricare il pacchetto VSPackage.

Il comando è impostato per essere abilitato e visualizzato ogni volta che esiste una soluzione. ciò significa che ogni volta che è attivo uno dei GUID del contesto di comando seguenti:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Nell'esempio si noti che ogni flag di comando è un [elemento Flag di comando](../../extensibility/command-flag-element.md) separato.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Si noti anche che ogni contesto dell'interfaccia utente deve essere specificato in un elemento `VisibilityItem` separato, come indicato di seguito.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedi anche

- [Aggiungere un comando alla barra degli strumenti Esplora soluzioni comandi](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Aggiunta dinamica di voci di menu](../../extensibility/dynamically-adding-menu-items.md)
