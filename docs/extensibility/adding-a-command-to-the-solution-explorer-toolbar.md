---
title: Aggiunta di un comando alla barra degli strumenti di Esplora soluzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fff1187793350b52484bcac99021be7fc2845607
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717793"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Aggiungere un comando alla barra degli strumenti Esplora soluzioni
Questa procedura dettagliata viene illustrato come aggiungere un pulsante per la **Esplora soluzioni** sulla barra degli strumenti.

 Qualsiasi comando in una barra degli strumenti o menu viene chiamato un pulsante in Visual Studio. Quando si fa clic sul pulsante, viene eseguito il codice nel gestore del comando. In genere, i comandi correlati vengono raggruppati insieme per formare un gruppo. I menu o barre degli strumenti fungono da contenitori per i gruppi. La priorità determina l'ordine in cui vengono visualizzati i singoli comandi in un gruppo dal menu o sulla barra degli strumenti. È possibile impedire la visualizzazione sulla barra degli strumenti o nel menu controllando la visibilità di un pulsante. Un comando che è elencato in una `<VisibilityConstraints>` sezione del *vsct* file viene visualizzato solo nel contesto associato. La visibilità non può essere applicata ai gruppi.

 Per altre informazioni sui comandi della barra degli strumenti, menu e *vsct* i file, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
>  Utilizzare tabella comandi XML (*vsct*) file invece di configurazione della tabella dei comandi (*CTC*) i file per definire come menu e comandi vengono visualizzate in VSPackage. Per altre informazioni, vedere [Visual Studio Command Table (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu
 Creare un progetto VSIX denominato `SolutionToolbar`. Aggiungere un modello di elemento di comando di menu denominato **ToolbarButton**. Per informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Aggiungere un pulsante alla barra degli strumenti Esplora soluzioni
 In questa sezione della procedura dettagliata viene illustrato come aggiungere un pulsante per la **Esplora soluzioni** sulla barra degli strumenti. Quando si fa clic sul pulsante, viene eseguito il codice nel metodo di callback.

1.  Nel *ToolbarButtonPackage.vsct* file, andare alla `<Symbols>` sezione. Il `<GuidSymbol>` nodo contiene il gruppo di menu e comandi che è stato generato dal modello di pacchetto. Aggiungere un `<IDSymbol>` elemento per questo nodo per dichiarare il gruppo che conterrà il comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2.  Nel `<Groups>` sezione, dopo la voce di gruppo esistente, definire il nuovo gruppo di cui è stato dichiarato nel passaggio precedente.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Impostando l'elemento padre coppia GUID: ID `guidSHLMainMenu` e `IDM_VS_TOOL_PROJWIN` inserisce questo gruppo di nel **Esplora soluzioni** sulla barra degli strumenti e impostare un valore ad alta priorità vengono suddivisi, dopo che gli altri gruppi di comandi.

3.  Nel `<Buttons>` , quindi modificare l'ID padre dell'oggetto generato `<Button>` voce in modo da riflettere il gruppo definito nel passaggio precedente. Modificato `<Button>` elemento dovrebbe essere simile al seguente:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

     Il **Esplora soluzioni** sulla barra degli strumenti deve visualizzare il nuovo pulsante di comando a destra dei pulsanti esistenti. L'icona del pulsante è barratura.

5.  Fare clic sul pulsante nuovo.

     Una finestra di dialogo con il messaggio **ToolbarButtonPackage all'interno di SolutionToolbar.ToolbarButton.MenuItemCallback()** deve essere visualizzato.

## <a name="control-the-visibility-of-a-button"></a>Controllare la visibilità di un pulsante
 In questa sezione della procedura dettagliata viene illustrato come controllare la visibilità di un pulsante sulla barra degli strumenti. Impostando un contesto per uno o più progetti nel `<VisibilityConstraints>` sezione il *SolutionToolbar.vsct* file, si limita un pulsante che verrà visualizzato solo quando uno o più progetti sono aperti.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Per visualizzare un pulsante quando uno o più progetti sono aperti

1. Nel `<Buttons>` sezione del *ToolbarButtonPackage.vsct*, aggiungere due flag dei comandi esistente `<Button>` elemento, tra il `<Strings>` e `<Icons>` tag.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Il `DefaultInvisible` e `DynamicVisibility` flag devono essere impostati pertanto che le voci di `<VisibilityConstraints>` sezione per rendere effettive.

2. Creare un `<VisibilityConstraints>` sezione che dispone di due `<VisibilityItem>` voci. Inserire la nuova sezione subito dopo la chiusura `</Commands>` tag.

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

    Ogni elemento visibilità rappresenta una condizione in cui viene visualizzato il pulsante specificato. Per applicare più condizioni, è necessario creare più voci per lo stesso pulsante.

3. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    Il **Esplora soluzioni** sulla barra degli strumenti non contiene il pulsante barrato.

4. Aprire qualsiasi soluzione che contiene un progetto.

    Pulsante Barrato viene visualizzato sulla barra degli strumenti a destra dei pulsanti esistenti.

5. Nel **File** menu, fare clic su **Chiudi soluzione**. Il pulsante viene rimosso dalla barra degli strumenti.

   La visibilità del pulsante è controllata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fino a quando non viene caricato il pacchetto VSPackage. Dopo che il VSPackage viene caricato, la visibilità del pulsante è controllata dal pacchetto VSPackage.  Per altre informazioni, vedere [vs confronto tra oggetti MenuCommand. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).

## <a name="see-also"></a>Vedere anche
- [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)