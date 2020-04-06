---
title: Rendere disponibili i comandi Documenti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707327"
---
# <a name="making-commands-available"></a>Rendere disponibili i comandi

Quando più VSPackage vengono aggiunti a Visual Studio, l'interfaccia utente (UI) può diventare sovraffollato con i comandi. È possibile programmare il pacchetto per ridurre questo problema, come indicato di seguito:You can program your package to help reduce this problem, as follows:

- Programmare il pacchetto in modo che venga caricato solo quando un utente lo richiede.

- Programmare il pacchetto in modo che i relativi comandi vengano visualizzati solo quando potrebbero essere necessari nel contesto dello stato corrente dell'ambiente di sviluppo integrato (IDE).

## <a name="delayed-loading"></a>Caricamento ritardato

Il modo tipico per abilitare il caricamento ritardato consiste nel progettare il pacchetto VSPackage in modo che i relativi comandi vengono visualizzati nell'interfaccia utente, ma il pacchetto stesso non viene caricato fino a quando un utente fa clic su uno dei comandi. A tale scopo, nel file vsct, creare comandi che non dispongono di flag di comando.

Nell'esempio seguente viene illustrata la definizione di un comando di menu da un file con estensione vsct. Si tratta del comando generato dal modello di pacchetto di Visual Studio quando viene selezionata l'opzione Comando di **menu** nel modello.

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

Nell'esempio, se il `MyMenuGroup`gruppo padre, , è un elemento figlio di un menu di primo livello, ad esempio il menu **Strumenti,** il comando sarà visibile in tale menu, ma il pacchetto che esegue il comando non verrà caricato fino a quando un utente non farà clic sul comando. Tuttavia, programmando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comando per implementare l'interfaccia, è possibile abilitare il pacchetto da caricare quando il menu che contiene il comando viene espanso per la prima volta.

Si noti che il caricamento ritardato può anche migliorare le prestazioni di avvio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contesto corrente e visibilità dei comandi

È possibile programmare i comandi VSPackage per essere visibile o nascosto, a seconda dello stato corrente dei dati VSPackage o le azioni attualmente rilevanti. È possibile abilitare il pacchetto VSPackage per impostare lo <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> stato dei <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> relativi comandi, in genere utilizzando un'implementazione del metodo dall'interfaccia, ma ciò richiede il pacchetto VSPackage da caricare prima di poter eseguire il codice. Al contrario, è consigliabile abilitare l'IDE per gestire la visibilità dei comandi senza caricare il pacchetto. A tale scopo, nel file vsct, associare i comandi a uno o più contesti speciali dell'interfaccia utente. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come GUID di *contesto del comando.*

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitora le modifiche risultanti da azioni dell'utente, ad esempio il caricamento di un progetto o la modifica alla creazione. Quando si verificano modifiche, l'aspetto dell'IDE viene modificato automaticamente. Nella tabella seguente vengono illustrati quattro contesti principali della modifica dell'IDE che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitora.

| Tipo di contesto | Descrizione |
|-------------------------| - |
| Tipo di progetto attivo | Per la maggior `GUID` parte dei tipi di progetto, questo valore è uguale al GUID del pacchetto VSPackage che implementa il progetto. Tuttavia, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i progetti `GUID` utilizzano il tipo di progetto come valore. |
| Finestra attiva | In genere, si tratta dell'ultima finestra del documento attivo che stabilisce il contesto dell'interfaccia utente corrente per le associazioni di tasti. Tuttavia, potrebbe anche essere una finestra degli strumenti che dispone di una tabella di associazione di tasti simile al browser Web interno. Per le finestre di documento a più schede, ad esempio `GUID`l'editor HTML, ogni scheda ha un contesto di comando diverso. |
| Servizio lingue attivo | Servizio di linguaggio associato al file attualmente visualizzato in un editor di testo. |
| Finestra degli strumenti attiva | Finestra degli strumenti aperta e con lo stato attivo. |

Una quinta area di contesto principale è lo stato dell'interfaccia utente dell'IDE. I contesti dell'interfaccia `GUID`utente sono identificati dal contesto del comando attivo s, come indicato di seguito:UI contexts are identified by active command context s, as follows:

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

È possibile visualizzare o nascondere un comando del pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file vsct `DefaultDisabled` `DefaultInvisible`del `DynamicVisibility` pacchetto utilizzando i flag di comando , e e aggiungendo uno o più elementi [VisibilityItem](../../extensibility/visibilityitem-element.md) alla sezione [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Quando un contesto `GUID` di comando specificato diventa attivo, il comando viene visualizzato senza caricare il pacchetto.

### <a name="custom-context-guids"></a>GUI di contesto personalizzato

Se un contesto di comando appropriato GUID non è già definito, è possibile definirne uno nel pacchetto VSPackage e quindi programmarlo per essere attivo o inattivo come richiesto per controllare la visibilità dei comandi. Utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> il servizio per:

- Registrare i GUID di <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> contesto (chiamando il metodo ).

- Ottenere lo stato `GUID` di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> contesto (chiamando il metodo ).

- Attivare `GUID`e disattivare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> contesto s (chiamando il metodo ).

    > [!CAUTION]
    > Assicurarsi che il pacchetto VSPackage non influisce sullo stato di qualsiasi GUID di contesto esistente perché altri VSPackage possono dipendere da essi.

## <a name="example"></a>Esempio

The following example of a VSPackage command demonstrates the dynamic visibility of a command that is managed by command contexts without loading the VSPackage.

Il comando è impostato per essere abilitato e visualizzato ogni volta che esiste una soluzione; vale a dire, ogni volta che è attivo uno dei seguenti GUID di contesto di comando:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Nell'esempio, si noti che ogni flag di comando è un elemento [Command Flag](../../extensibility/command-flag-element.md) separato.

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

Si noti inoltre che ogni contesto dell'interfaccia utente deve essere specificato in un elemento separato, `VisibilityItem` come indicato di seguito.

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

- [Aggiungere un comando alla barra degli strumenti di Esplora soluzioniAdd a command to the Solution Explorer toolbar](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Aggiunta dinamica di voci di menu](../../extensibility/dynamically-adding-menu-items.md)
