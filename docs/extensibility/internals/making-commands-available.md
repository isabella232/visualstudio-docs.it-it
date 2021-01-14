---
title: Rendere disponibili i comandi | Microsoft Docs
description: Informazioni su come controllare la disponibilità dei comandi aggiunti all'IDE di Visual Studio nei pacchetti VSPackage, usando il caricamento ritardato, il contesto e la visibilità.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d17fd0b63438183b10b1ecb0e5eb6abb9f5d7f46
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204540"
---
# <a name="making-commands-available"></a>Rendere disponibili i comandi

Quando si aggiungono più VSPackage a Visual Studio, è possibile che l'interfaccia utente (UI) venga sovraccaricata con i comandi. È possibile programmare il pacchetto per ridurre questo problema, come indicato di seguito:

- Programmare il pacchetto in modo che venga caricato solo quando richiesto dall'utente.

- Programmare il pacchetto in modo che i relativi comandi vengano visualizzati solo quando possono essere richiesti nel contesto dello stato corrente del Integrated Development Environment (IDE).

## <a name="delayed-loading"></a>Caricamento ritardato

Il modo più comune per abilitare il caricamento ritardato consiste nel progettare il pacchetto VSPackage in modo che i relativi comandi vengano visualizzati nell'interfaccia utente, ma il pacchetto non viene caricato fino a quando un utente non fa clic su uno dei comandi. A tale scopo, nel file con estensione vsct creare comandi senza flag di comando.

Nell'esempio seguente viene illustrata la definizione di un comando di menu da un file con estensione vsct. Si tratta del comando generato dal modello di pacchetto di Visual Studio quando si seleziona l'opzione del **comando di menu** nel modello.

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

Nell'esempio, se il gruppo padre, `MyMenuGroup` , è un elemento figlio di un menu di primo livello, ad esempio il menu **strumenti** , il comando sarà visibile nel menu, ma il pacchetto che esegue il comando non verrà caricato fino a quando non si fa clic sul comando da parte di un utente. Tuttavia, tramite la programmazione del comando per implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, è possibile abilitare il caricamento del pacchetto quando il menu che contiene il comando viene espanso per la prima volta.

Si noti che il caricamento ritardato può migliorare anche le prestazioni di avvio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contesto corrente e visibilità dei comandi

È possibile programmare i comandi VSPackage in modo che siano visibili o nascosti, a seconda dello stato corrente dei dati VSPackage o delle azioni attualmente pertinenti. È possibile abilitare il pacchetto VSPackage per impostare lo stato dei comandi, in genere usando un'implementazione del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo dall' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, ma è necessario caricare il pacchetto VSPackage prima di poter eseguire il codice. È invece consigliabile abilitare l'IDE per gestire la visibilità dei comandi senza caricare il pacchetto. A tale scopo, nel file. vsct associare i comandi a uno o più contesti dell'interfaccia utente speciali. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come *GUID del contesto del comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitora le modifiche risultanti da azioni utente, ad esempio il caricamento di un progetto o la modifica alla compilazione. Quando si verificano modifiche, l'aspetto dell'IDE viene modificato automaticamente. Nella tabella seguente sono illustrati quattro contesti principali di modifica IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitorati da.

| Tipo di contesto | Descrizione |
|-------------------------| - |
| Tipo di progetto attivo | Per la maggior parte dei tipi di progetto, questo `GUID` valore corrisponde al GUID del pacchetto VSPackage che implementa il progetto. Tuttavia, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i progetti utilizzano il tipo `GUID` di progetto come valore. |
| Finestra attiva | In genere, si tratta dell'ultima finestra del documento attiva che stabilisce il contesto dell'interfaccia utente corrente per le combinazioni di tasti. Tuttavia, potrebbe anche essere una finestra degli strumenti con una tabella di associazione di chiavi simile alla Web browser interna. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un contesto di comando diverso `GUID` . |
| Servizio di linguaggio attivo | Il servizio di linguaggio associato al file attualmente visualizzato in un editor di testo. |
| Finestra degli strumenti attiva | Finestra degli strumenti aperta con lo stato attivo. |

Una quinta area del contesto principale è lo stato dell'interfaccia utente dell'IDE. I contesti dell'interfaccia utente sono identificati dal contesto del comando attivo `GUID` , come indicato di seguito:

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

È possibile visualizzare o nascondere un comando del pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file. vsct del pacchetto usando i `DefaultDisabled` flag di comando, `DefaultInvisible` e `DynamicVisibility` e aggiungendo uno o più elementi [VisibilityItem](../../extensibility/visibilityitem-element.md) alla sezione [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Quando un contesto del comando specificato `GUID` diventa attivo, il comando viene visualizzato senza caricare il pacchetto.

### <a name="custom-context-guids"></a>GUID di contesto personalizzati

Se non è già stato definito un GUID del contesto del comando appropriato, è possibile definirne uno nel pacchetto VSPackage e quindi programmarlo come attivo o inattivo come richiesto per controllare la visibilità dei comandi. Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio per:

- Registrare GUID di contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo).

- Ottenere lo stato di un contesto `GUID` (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo).

- Attivare e disattivare i contesti `GUID` (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo).

    > [!CAUTION]
    > Verificare che il pacchetto VSPackage non influisca sullo stato di un GUID del contesto esistente perché altri pacchetti VSPackage possono dipendere da essi.

## <a name="example"></a>Esempio

Nell'esempio seguente di un comando VSPackage viene illustrata la visibilità dinamica di un comando gestito da contesti di comando senza caricare il pacchetto VSPackage.

Il comando è impostato per essere abilitato e visualizzato quando esiste una soluzione. ovvero, ogni volta che uno dei seguenti GUID del contesto del comando è attivo:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Nell'esempio si noti che ogni flag di comando è un elemento separato del [flag di comando](../../extensibility/command-flag-element.md) .

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

Si noti anche che ogni contesto dell'interfaccia utente deve essere specificato in un `VisibilityItem` elemento separato, come indicato di seguito.

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

- [Aggiungere un comando alla barra degli strumenti Esplora soluzioni](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Aggiunta dinamica di voci di menu](../../extensibility/dynamically-adding-menu-items.md)
