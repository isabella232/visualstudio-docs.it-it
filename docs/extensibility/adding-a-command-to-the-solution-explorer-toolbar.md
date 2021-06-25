---
title: Aggiunta di un comando alla barra degli strumenti Esplora soluzioni | Microsoft Docs
description: Informazioni su come aggiungere un pulsante che esegue un comando alla barra degli strumenti Esplora soluzioni in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900239"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Aggiungere un comando alla barra degli strumenti Esplora soluzioni comandi
Questa procedura dettagliata illustra come aggiungere un pulsante alla barra Esplora soluzioni barra **degli** strumenti.

 Qualsiasi comando su una barra degli strumenti o un menu viene chiamato pulsante in Visual Studio. Quando si fa clic sul pulsante, viene eseguito il codice nel gestore dei comandi. In genere, i comandi correlati vengono raggruppati per formare un gruppo. I menu o le barre degli strumenti fungono da contenitori per i gruppi. La priorità determina l'ordine in cui i singoli comandi di un gruppo vengono visualizzati nel menu o sulla barra degli strumenti. È possibile impedire la visualizzazione di un pulsante sulla barra degli strumenti o sul menu controllandone la visibilità. Un comando elencato in una `<VisibilityConstraints>` sezione del file *vsct* viene visualizzato solo nel contesto associato. La visibilità non può essere applicata ai gruppi.

 Per altre informazioni su menu, comandi della barra degli strumenti e file *vsct,* vedere [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Usare i file della tabella dei comandi XML *(vsct)* anziché i file di configurazione della tabella dei comandi ( con estensione *ctc*) per definire la modalità di visualizzazione di menu e comandi nei pacchetti VSPackage. Per altre informazioni, vedere Visual Studio [command table (. Vsct) file](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu
 Creare un progetto VSIX denominato `SolutionToolbar` . Aggiungere un modello di voce di comando di menu denominato **ToolbarButton**. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Aggiungere un pulsante alla barra degli strumenti Esplora soluzioni comandi
 Questa sezione della procedura dettagliata illustra come aggiungere un pulsante alla barra Esplora soluzioni barra **degli** strumenti. Quando si fa clic sul pulsante, viene eseguito il codice nel metodo di callback.

1. Nel file *ToolbarButtonPackage.vsct* passare alla  `<Symbols>` sezione . Il `<GuidSymbol>`  nodo contiene il gruppo di menu e il comando generati dal modello di pacchetto. Aggiungere un `<IDSymbol>` elemento a questo nodo per dichiarare il gruppo che contenerà il comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Nella sezione , dopo la voce di gruppo esistente, definire `<Groups>` il nuovo gruppo dichiarato nel passaggio precedente.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     L'impostazione della coppia PADRE GUID:ID su e inserisce questo gruppo sulla barra degli strumenti Esplora soluzioni e l'impostazione di un valore con priorità alta lo inserisce dopo gli `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` altri gruppi di comandi. 

3. Nella sezione modificare l'ID padre della voce generata in modo da riflettere il gruppo `<Buttons>` `<Button>` definito nel passaggio precedente. `<Button>`L'elemento modificato dovrebbe essere simile al seguente:

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

     La **Esplora soluzioni** barra degli strumenti dovrebbe visualizzare il nuovo pulsante di comando a destra dei pulsanti esistenti. L'icona del pulsante è barrato.

5. Fare clic sul nuovo pulsante.

     Verrà visualizzata una finestra di dialogo con il messaggio **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback().**

## <a name="control-the-visibility-of-a-button"></a>Controllare la visibilità di un pulsante
 Questa sezione della procedura dettagliata illustra come controllare la visibilità di un pulsante su una barra degli strumenti. Impostando un contesto su uno o più progetti nella sezione del `<VisibilityConstraints>` file *SolutionToolbar.vsct,* si limita la visualizzazione di un pulsante solo quando uno o più progetti sono aperti.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Per visualizzare un pulsante quando uno o più progetti sono aperti

1. Nella sezione `<Buttons>` di *ToolbarButtonPackage.vsct* aggiungere due flag di comando all'elemento `<Button>` esistente, tra i `<Strings>` tag e `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    I `DefaultInvisible` flag e devono essere impostati in modo che le voci nella sezione possano essere `DynamicVisibility` `<VisibilityConstraints>` applicate.

2. Creare una `<VisibilityConstraints>` sezione con `<VisibilityItem>` due voci. Inserire la nuova sezione subito dopo il tag di `</Commands>` chiusura.

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

    Ogni elemento di visibilità rappresenta una condizione in cui viene visualizzato il pulsante specificato. Per applicare più condizioni, è necessario creare più voci per lo stesso pulsante.

3. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    La **Esplora soluzioni** barra degli strumenti non contiene il pulsante barrato.

4. Aprire una soluzione contenente un progetto.

    Il pulsante barrato viene visualizzato sulla barra degli strumenti a destra dei pulsanti esistenti.

5. Scegliere **Chiudi soluzione** dal menu **File**. Il pulsante scompare dalla barra degli strumenti.

   La visibilità del pulsante viene controllata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fino al caricamento del pacchetto VSPackage. Dopo il caricamento del pacchetto VSPackage, la visibilità del pulsante viene controllata dal pacchetto VSPackage.  Per altre informazioni, vedere [MenuCommands e OleMenuCommands.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)