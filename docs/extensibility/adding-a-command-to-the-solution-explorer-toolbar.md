---
title: Aggiunta di un comando alla barra degli strumenti di Esplora soluzioni . Documenti Microsoft
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
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740342"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Aggiungere un comando alla barra degli strumenti di Esplora soluzioniAdd a command to the Solution Explorer toolbar
In questa procedura dettagliata viene illustrato come aggiungere un pulsante alla barra degli strumenti **di Esplora soluzioni.**

 Qualsiasi comando in una barra degli strumenti o un menu viene chiamato un pulsante in Visual Studio.Any command on a toolbar or menu is called a button in Visual Studio. Quando si fa clic sul pulsante, viene eseguito il codice nel gestore comandi. In genere, i comandi correlati vengono raggruppati per formare un unico gruppo. I menu o le barre degli strumenti fungono da contenitori per i gruppi. La priorità determina l'ordine in cui i singoli comandi di un gruppo vengono visualizzati nel menu o nella barra degli strumenti. È possibile impedire la visualizzazione di un pulsante sulla barra degli strumenti o sul menu controllandone la visibilità. Un comando elencato `<VisibilityConstraints>` in una sezione del file *vsct* viene visualizzato solo nel contesto associato. La visibilità non può essere applicata ai gruppi.

 Per ulteriori informazioni sui menu, i comandi della barra degli strumenti e i file *vsct,* consultate [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

> [!NOTE]
> Utilizzare i file della tabella dei comandi XML (*.vsct*) anziché i file di configurazione della tabella dei comandi (*.ctc*) per definire la modalità di visualizzazione dei menu e dei comandi nei package VS. Per altre informazioni, vedere Tabella dei comandi di Visual Studio (.For more information, see [Visual Studio Command Table (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)file .

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menuCreate an extension with a menu command
 Creare un progetto `SolutionToolbar`VSIX denominato . Aggiungere un modello di elemento di comando di menu denominato **ToolbarButton**. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu .

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Aggiungere un pulsante alla barra degli strumenti di Esplora soluzioniAdd a button to the Solution Explorer toolbar
 In questa sezione della procedura dettagliata viene illustrato come aggiungere un pulsante alla barra degli strumenti **di Esplora soluzioni.** Quando si fa clic sul pulsante, viene eseguito il codice nel metodo di callback.

1. Nel file *ToolbarButtonPackage.vsct* passare `<Symbols>` alla sezione. Il `<GuidSymbol>` nodo contiene il gruppo di menu e il comando generati dal modello di pacchetto. Aggiungere `<IDSymbol>` un elemento a questo nodo per dichiarare il gruppo che conterrà il comando.

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

     L'impostazione della coppia `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` GUID:ID padre su e inserisce questo gruppo nella barra degli strumenti di **Esplora soluzioni** e l'impostazione di un valore ad alta priorità lo inserisce dopo gli altri gruppi di comandi.

3. Nella `<Buttons>` sezione modificare l'ID padre `<Button>` della voce generata in modo che rifletta il gruppo definito nel passaggio precedente. L'elemento modificato dovrebbe essere simile al seguente:The modified `<Button>` element should look like this:

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

     La barra degli strumenti **di Esplora soluzioni** dovrebbe visualizzare il nuovo pulsante di comando a destra dei pulsanti esistenti. L'icona del pulsante è barrata.

5. Fare clic sul nuovo pulsante.

     Dovrebbe essere visualizzata una finestra di dialogo con il messaggio **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** .

## <a name="control-the-visibility-of-a-button"></a>Controllare la visibilità di un pulsante
 In questa sezione della procedura dettagliata viene illustrato come controllare la visibilità di un pulsante in una barra degli strumenti. Impostando un contesto su uno `<VisibilityConstraints>` o più progetti nella sezione del file *SolutionToolbar.vsct,* si limita la visualizzazione di un pulsante solo quando è aperto uno o più progetti.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Per visualizzare un pulsante quando uno o più progetti sono aperti

1. Nella `<Buttons>` sezione *ToolbarButtonPackage.vsct*aggiungere due flag di `<Button>` comando all'elemento esistente, tra i `<Strings>` tag e `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    I `DefaultInvisible` `DynamicVisibility` flag e devono essere impostati `<VisibilityConstraints>` in modo che le voci nella sezione abbiano effetto.

2. Creare `<VisibilityConstraints>` una sezione `<VisibilityItem>` con due voci. Inserire la nuova sezione `</Commands>` subito dopo il tag di chiusura.

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

    Ogni elemento di visibilità rappresenta una condizione in base alla quale viene visualizzato il pulsante specificato. Per applicare più condizioni, è necessario creare più voci per lo stesso pulsante.

3. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    La barra degli strumenti di **Esplora soluzioni** non contiene il pulsante barrato.

4. Aprire una soluzione contenente un progetto.

    Il pulsante barrato viene visualizzato sulla barra degli strumenti a destra dei pulsanti esistenti.

5. Scegliere **Chiudi soluzione** dal menu **File**. Il pulsante scompare dalla barra degli strumenti.

   La visibilità del pulsante è controllata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fino a quando non viene caricato il pacchetto VSPackage. Dopo il pacchetto VSPackage viene caricato, la visibilità del pulsante è controllata dal pacchetto VSPackage.  Per ulteriori informazioni, vedere [MenuCommands vs.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
