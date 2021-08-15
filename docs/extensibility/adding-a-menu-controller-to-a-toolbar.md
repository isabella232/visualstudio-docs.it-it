---
title: Aggiunta di un controller di menu a una barra degli strumenti | Microsoft Docs
description: Informazioni su come creare un controller di menu e aggiungerlo a una barra degli strumenti della finestra degli strumenti Visual Studio, quindi implementare i comandi del controller di menu e testarlo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3028024f6c13c8d722a565a73d64d6ec8b3de16fae2dde227efc0114f403fedd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239425"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Aggiungere un controller di menu a una barra degli strumenti
Questa procedura dettagliata si basa sulla procedura dettagliata Aggiungere una barra degli strumenti [a](../extensibility/adding-a-toolbar-to-a-tool-window.md) una finestra degli strumenti e illustra come aggiungere un controller di menu alla barra degli strumenti della finestra degli strumenti. I passaggi illustrati qui possono essere applicati anche alla barra degli strumenti creata nella procedura [dettagliata Aggiungere una barra degli](../extensibility/adding-a-toolbar.md) strumenti.

Un controller di menu è un controllo di divisione. Sul lato sinistro del controller di menu viene visualizzato l'ultimo comando usato ed è possibile eseguirlo facendo clic su di esso. Il lato destro del controller di menu è una freccia che, quando si fa clic, apre un elenco di comandi aggiuntivi. Quando si fa clic su un comando nell'elenco, il comando viene eseguito e sostituisce il comando sul lato sinistro del controller di menu. In questo modo, il controller di menu funziona come un pulsante di comando che mostra sempre l'ultimo comando usato da un elenco.

I controller di menu possono essere visualizzati nei menu, ma vengono usati più spesso sulle barre degli strumenti.

## <a name="prerequisites"></a>Prerequisiti
A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-controller"></a>Creare un controller di menu

1. Seguire le procedure descritte in [Aggiungere una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) per creare una finestra degli strumenti con una barra degli strumenti.

2. In *TWTestCommandPackage.vsct* passare alla sezione Simboli. Nell'elemento GuidSymbol denominato **guidTWTestCommandPackageCmdSet** dichiarare il controller di menu, il gruppo di controller di menu e tre voci di menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Nella sezione Menu, dopo l'ultima voce di menu, definire il controller di menu come menu.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    I `TextChanges` flag e devono essere inclusi per consentire al controller di menu di riflettere `TextIsAnchorCommand` l'ultimo comando selezionato.

4. Nella sezione Gruppi aggiungere il gruppo controller di menu dopo l'ultima voce di gruppo.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Impostando il controller di menu come padre, tutti i comandi inseriti in questo gruppo vengono visualizzati nel controller di menu. L'attributo viene omesso, che lo imposta sul valore predefinito 0, perché è `priority` l'unico gruppo nel controller di menu.

5. Nella sezione Pulsanti, dopo l'ultima voce di pulsante, aggiungere un elemento Button per ogni voce di menu.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. A questo punto, è possibile esaminare il controller di menu. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

   1. Nel menu **Visualizza/Altro Windows** aprire **Strumento di testWindow**.

   2. Il controller di menu viene visualizzato sulla barra degli strumenti nella finestra degli strumenti.

   3. Fare clic sulla freccia sul lato destro del controller di menu per visualizzare i tre comandi possibili.

      Si noti che quando si fa clic su un comando, il titolo del controller di menu cambia per visualizzare il comando. Nella sezione successiva verrà aggiunto il codice per attivare questi comandi.

## <a name="implement-the-menu-controller-commands"></a>Implementare i comandi del controller di menu

1. In *TWTestCommandPackageGuids.cs* aggiungere gli ID di comando per le tre voci di menu dopo gli ID di comando esistenti.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. In *TWTestCommand.cs* aggiungere il codice seguente all'inizio della `TWTestCommand` classe .

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Nel costruttore TWTestCommand, dopo l'ultima chiamata al metodo , aggiungere il codice per indirizzare gli eventi per ogni comando `AddCommand` tramite gli stessi gestori.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Aggiungere un gestore eventi alla **classe TWTestCommand** per contrassegnare il comando selezionato come selezionato.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Aggiungere un gestore eventi che visualizza un oggetto MessageBox quando l'utente seleziona un comando nel controller di menu:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Test del controller di menu

1. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

2. Aprire Strumento **di testFinestra** nel menu **Visualizza/Windows** comando.

    Il controller di menu viene visualizzato nella barra degli strumenti nella finestra degli strumenti e visualizza **MC Item 1.**

3. Fare clic sul pulsante del controller di menu a sinistra della freccia.

    Dovrebbero essere visualizzati tre elementi, il primo dei quali è selezionato e ha una casella di evidenziazione intorno alla relativa icona. Fare **clic su MC Item 3**.

    Verrà visualizzata una finestra di dialogo con il messaggio **È stato selezionato Voce di controller di menu 3**. Si noti che il messaggio corrisponde al testo nel pulsante del controller di menu. Il pulsante del controller di menu visualizza **ora MC Item 3.**

## <a name="see-also"></a>Vedi anche
- [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)
