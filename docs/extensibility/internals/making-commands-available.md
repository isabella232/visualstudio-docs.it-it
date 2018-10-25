---
title: Rendere disponibili i comandi | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1292dc3879effa53f3b4a41b87374a3a5f46ff0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857133"
---
# <a name="making-commands-available"></a>Miglioramento della disponibilità dei comandi
Quando vengono aggiunti più pacchetti VSPackage in Visual Studio, l'interfaccia utente (UI) possa diventare saturi con i comandi. È possibile programmare il pacchetto per contribuire a ridurre questo problema, come indicato di seguito:

-   Il pacchetto di programma in modo che venga caricato solo quando un utente ne richiede.

-   Il pacchetto del programma in modo che i relativi comandi vengono visualizzati solo quando potrebbero essere necessari nel contesto dello stato corrente dell'ambiente di sviluppo integrato (IDE).

## <a name="delayed-loading"></a>Il caricamento ritardato
 Il modo consueto per abilitare il caricamento ritardato è progettare il pacchetto VSPackage in modo che i relativi comandi vengono visualizzati nell'interfaccia utente, ma non è possibile caricare il pacchetto stesso fino a quando un utente fa clic su uno dei comandi. A tale scopo, nel file vsct, creare i comandi non con alcun flag dei comandi.

 Nell'esempio seguente illustra la definizione di un comando di menu da un file con estensione vsct. Questo è il comando che viene generato dal modello di pacchetto Visual Studio quando la **comando di Menu** scelto nel modello.

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

Nell'esempio, se il gruppo padre, `MyMenuGroup`, è un figlio di un menu di primo livello, ad esempio il **strumenti** menu sarà visibile in tale menu il comando, ma il pacchetto che esegue il comando non verrà caricato finché non si seleziona il comando da un utente. Tuttavia, programmando il comando per implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, è possibile abilitare il pacchetto da caricare quando il menu che contiene il comando viene espanso.

Si noti che il caricamento ritardato può anche migliorare le prestazioni all'avvio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contesto corrente e la visibilità dei comandi
 È possibile programmare comandi package VS di essere visibile o nascosto, a seconda dello stato corrente dei dati VSPackage o le azioni che sono attualmente pertinenti. È possibile abilitare il pacchetto VSPackage impostare lo stato dei comandi, in genere tramite un'implementazione del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, ma questa operazione richiede il pacchetto VSPackage deve essere caricato prima di poter eseguire il codice. In alternativa, è consigliabile abilitare l'IDE gestire la visibilità dei comandi senza il caricamento del pacchetto. A tale scopo, nel file vsct, associare i comandi con uno o più contesti dell'interfaccia utente speciali. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come un *GUID di contesto comando*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Consente di monitorare le modifiche risultanti da azioni dell'utente, ad esempio il caricamento di un progetto o il passaggio di modifica alla compilazione. Quando si verificano modifiche, viene automaticamente modificato l'aspetto dell'IDE. La tabella seguente mostra quattro contesti principali dell'IDE di modifica che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoraggi.


| Tipo di contesto | Descrizione |
|-------------------------| - |
| Tipo di progetto attivo | Per la maggior parte dei tipi di progetto, questo `GUID` valore corrisponde al GUID del pacchetto VSPackage che implementa il progetto. Tuttavia [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti usano il tipo di progetto `GUID` come valore. |
| Finestra attiva | In genere, questo è l'ultima finestra di documento attivo che definisce il contesto dell'interfaccia utente corrente di tasti di scelta rapida. Tuttavia, potrebbe essere anche una finestra degli strumenti con una tabella di tasti di scelta rapida che è simile al Web browser interno. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un contesto di comandi diverso `GUID`. |
| Servizio di linguaggio Active | Il servizio di linguaggio che è associato il file che è attualmente visualizzato in un editor di testo. |
| Finestra degli strumenti attiva | Una finestra degli strumenti che è aperto e ha lo stato attivo. |

 Un'area principale contesto quinta è lo stato dell'interfaccia utente dell'IDE. Contesti dell'interfaccia utente sono identificati dal contesto del comando attivo `GUID`s, come indicato di seguito:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Questi GUID sono contrassegnati come attiva o inattiva, a seconda dello stato corrente dell'IDE. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Per nascondere e visualizzare i comandi in base al contesto
 È possibile visualizzare o nascondere un comando del pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file con estensione vsct del pacchetto usando il `DefaultDisabled`, `DefaultInvisible`, e `DynamicVisibility` comando flag e aggiungere uno o più [VisibilityItem](../../extensibility/visibilityitem-element.md) elementi di [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione. Quando un contesto del comando specificato `GUID` diventa attivo, il comando viene visualizzato senza il caricamento del pacchetto.

### <a name="custom-context-guids"></a>GUID di contesto personalizzato
 Se un contesto di comandi appropriata che GUID non è già definito, è possibile definire uno nel pacchetto VSPackage e programmarlo per essere attivi o inattivi in base alle esigenze per controllare la visibilità dei comandi. Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio:

-   Registra i GUID di contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (metodo)).

-   Ottenere lo stato di un contesto `GUID` (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (metodo)).

-   Contesto di attivazione `GUID`s e disattivare (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (metodo)).

    > [!CAUTION]
    > Assicurarsi che il pacchetto VSPackage non influiscono sullo stato di qualsiasi GUID di contesto esistenti perché altri pacchetti VSPackage potrebbero dipendono da essi.

## <a name="example"></a>Esempio
 L'esempio seguente di un comando VSPackage illustra la visibilità dinamica di un comando che è gestito da contesti dei comandi senza caricare il pacchetto VSPackage.

 Il comando è impostato per essere abilitato e visualizzata ogni volta che esiste una soluzione; vale a dire, ogni volta che uno del contesto del comando seguente GUID è attivo:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Nell'esempio, si noti che ogni flag di comando è un oggetto separato [Flag di comando](../../extensibility/command-flag-element.md) elemento.

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

Si noti anche che ogni contesto dell'interfaccia utente deve essere specificato in un oggetto separato `VisibilityItem` elemento, come indicato di seguito.

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

## <a name="see-also"></a>Vedere anche

- [Confronto tra oggetti MenuCommand e OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Aggiunta dinamica di voci di menu](../../extensibility/dynamically-adding-menu-items.md)
