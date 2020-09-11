---
title: Aggiunta di un comando alla barra degli strumenti Esplora soluzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08513ef67dfdffbf70b5ce2ff449a9ceb4250c37
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012295"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Aggiungere un comando alla barra degli strumenti Esplora soluzioni
In questa procedura dettagliata viene illustrato come aggiungere un pulsante alla barra degli strumenti **Esplora soluzioni** .

 Qualsiasi comando su una barra degli strumenti o un menu è denominato pulsante in Visual Studio. Quando si fa clic sul pulsante, viene eseguito il codice nel gestore del comando. In genere, i comandi correlati sono raggruppati per formare un gruppo. Menu o barre degli strumenti fungono da contenitori per i gruppi. La priorità determina l'ordine in cui i singoli comandi di un gruppo vengono visualizzati nel menu o sulla barra degli strumenti. È possibile impedire la visualizzazione di un pulsante sulla barra degli strumenti o nel menu controllando la relativa visibilità. Un comando elencato in una `<VisibilityConstraints>` sezione del file con *estensione vsct* viene visualizzato solo nel contesto associato. Non è possibile applicare la visibilità ai gruppi.

 Per ulteriori informazioni sui menu, i comandi della barra degli strumenti e i file con *estensione vsct* , vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Usare i file della tabella dei comandi XML (con*estensione vsct*) anziché i file di configurazione della tabella dei comandi (con*estensione CTC*) per definire la modalità di visualizzazione dei menu e dei comandi nei pacchetti VSPackage. Per ulteriori informazioni, vedere la [tabella dei comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu
 Creare un progetto VSIX denominato `SolutionToolbar` . Aggiungere un modello di elemento del comando di menu denominato **ToolBarButton**. Per informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Aggiungere un pulsante alla barra degli strumenti Esplora soluzioni
 In questa sezione della procedura dettagliata viene illustrato come aggiungere un pulsante alla barra degli strumenti **Esplora soluzioni** . Quando si fa clic sul pulsante, viene eseguito il codice nel metodo di callback.

1. Nel file *ToolbarButtonPackage. vsct* passare alla  `<Symbols>` sezione. Il `<GuidSymbol>`  nodo contiene il gruppo di menu e il comando generati dal modello di pacchetto. Aggiungere un `<IDSymbol>` elemento a questo nodo per dichiarare il gruppo che conterrà il comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Nella `<Groups>` sezione, dopo la voce di gruppo esistente, definire il nuovo gruppo dichiarato nel passaggio precedente.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Impostando la coppia GUID: ID padre su, il `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` gruppo viene inserito sulla barra degli strumenti **Esplora soluzioni** e l'impostazione di un valore con priorità alta la inserisce dopo gli altri gruppi di comandi.

3. Nella `<Buttons>` sezione modificare l'ID padre della voce generata in `<Button>` modo che corrisponda al gruppo definito nel passaggio precedente. L' `<Button>` elemento modificato dovrebbe essere simile al seguente:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

     Nella barra degli strumenti **Esplora soluzioni** dovrebbe essere visualizzato il nuovo pulsante di comando a destra dei pulsanti esistenti. L'icona del pulsante è la barrata.

5. Fare clic sul pulsante nuovo.

     Dovrebbe essere visualizzata una finestra di dialogo contenente il messaggio **ToolbarButtonPackage all'interno di SolutionToolbar. ToolBarButton. MenuItemCallback ()** .

## <a name="control-the-visibility-of-a-button"></a>Controllare la visibilità di un pulsante
 In questa sezione della procedura dettagliata viene illustrato come controllare la visibilità di un pulsante su una barra degli strumenti. Impostando un contesto su uno o più progetti nella `<VisibilityConstraints>` sezione del file *SolutionToolbar. vsct* , si limita un pulsante affinché venga visualizzato solo quando un progetto o progetti sono aperti.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Per visualizzare un pulsante quando uno o più progetti sono aperti

1. Nella `<Buttons>` sezione di *ToolbarButtonPackage. vsct*aggiungere due flag di comando all' `<Button>` elemento esistente tra i `<Strings>` `<Icons>` tag e.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    I `DefaultInvisible` `DynamicVisibility` flag e devono essere impostati in modo da `<VisibilityConstraints>` rendere effettive le voci nella sezione.

2. Creare una `<VisibilityConstraints>` sezione con due `<VisibilityItem>` voci. Inserire la nuova sezione subito dopo il tag di chiusura `</Commands>` .

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Ogni elemento Visibility rappresenta una condizione in cui viene visualizzato il pulsante specificato. Per applicare più condizioni, è necessario creare più voci per lo stesso pulsante.

3. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    La barra degli strumenti **Esplora soluzioni** non contiene il pulsante barrato.

4. Aprire qualsiasi soluzione contenente un progetto.

    Il pulsante barrato viene visualizzato sulla barra degli strumenti a destra dei pulsanti esistenti.

5. Scegliere **Chiudi soluzione** dal menu **File**. Il pulsante scompare dalla barra degli strumenti.

   La visibilità del pulsante viene controllata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finché il pacchetto VSPackage non viene caricato. Una volta caricato il pacchetto VSPackage, la visibilità del pulsante viene controllata dal pacchetto VSPackage.  Per ulteriori informazioni, vedere [oggetti MenuCommand e OleMenuCommands](../vs-2015/misc/menucommands-vs-olemenucommands.md?view=vs-2015).

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)