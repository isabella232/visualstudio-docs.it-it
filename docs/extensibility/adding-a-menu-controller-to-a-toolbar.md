---
title: Aggiunta di un controller di menu a una barra degli strumenti | Microsoft Docs
description: Informazioni su come creare un controller di menu e aggiungerlo a una barra degli strumenti della finestra degli strumenti in Visual Studio, quindi implementare i comandi del controller di menu e testarlo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ce14999913a3928cbe25d9f034c8288651629a3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597821"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Aggiungere un controller di menu a una barra degli strumenti
Questa procedura dettagliata si basa sulla procedura dettagliata [aggiungere una barra degli strumenti a una finestra](../extensibility/adding-a-toolbar-to-a-tool-window.md) degli strumenti e Mostra come aggiungere un controller di menu alla barra degli strumenti della finestra degli strumenti. I passaggi illustrati di seguito possono essere applicati anche alla barra degli strumenti creata nella procedura dettagliata per l' [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md) .

Un controller di menu è un controllo Split. Il lato sinistro del controller di menu Mostra l'ultimo comando utilizzato ed è possibile eseguirlo facendo clic su di esso. Il lato destro del controller di menu è una freccia che, quando viene selezionato, apre un elenco di comandi aggiuntivi. Quando si fa clic su un comando nell'elenco, il comando viene eseguito e sostituisce il comando sul lato sinistro del controller di menu. In questo modo, il controller di menu funziona come un pulsante di comando che Mostra sempre l'ultimo comando utilizzato da un elenco.

I controller di menu possono essere visualizzati nei menu, ma vengono spesso usati nelle barre degli strumenti.

## <a name="prerequisites"></a>Prerequisiti
A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Creare un controller di menu

1. Seguire le procedure descritte in [aggiungere una barra degli strumenti a una finestra](../extensibility/adding-a-toolbar-to-a-tool-window.md) degli strumenti per creare una finestra degli strumenti con una barra degli strumenti.

2. In *TWTestCommandPackage. vsct* passare alla sezione simboli. Nell'elemento GuidSymbol denominato **guidTWTestCommandPackageCmdSet**, dichiarare il controller di menu, il gruppo di controller di menu e tre voci di menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Nella sezione menu, dopo l'ultima voce di menu, definire il controller di menu come menu.

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

    `TextChanges` `TextIsAnchorCommand` Per consentire al controller di menu di riflettere l'ultimo comando selezionato, è necessario includere i flag e.

4. Nella sezione gruppi, dopo l'ultima voce di gruppo, aggiungere il gruppo di controller di menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Impostando il controller di menu come elemento padre, tutti i comandi inseriti in questo gruppo vengono visualizzati nel controller di menu. L' `priority` attributo viene omesso, che lo imposta sul valore predefinito 0, perché è l'unico gruppo del controller di menu.

5. Nella sezione pulsanti, dopo la voce dell'ultimo pulsante, aggiungere un elemento Button per ognuna delle voci di menu.

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

   1. Nel menu **Visualizza/altre finestre** aprire **test ToolWindow**.

   2. Il controller di menu viene visualizzato sulla barra degli strumenti della finestra degli strumenti.

   3. Fare clic sulla freccia sul lato destro del controller menu per visualizzare i tre comandi possibili.

      Si noti che quando si fa clic su un comando, il titolo del controller di menu cambia per visualizzare quel comando. Nella sezione successiva verrà aggiunto il codice per attivare questi comandi.

## <a name="implement-the-menu-controller-commands"></a>Implementare i comandi del controller di menu

1. In *TWTestCommandPackageGuids.cs* aggiungere gli ID comando per le tre voci di menu dopo gli ID comando esistenti.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. In *TWTestCommand.cs* aggiungere il codice seguente nella parte superiore della `TWTestCommand` classe.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Nel costruttore TWTestCommand, dopo l'ultima chiamata al `AddCommand` metodo, aggiungere il codice per indirizzare gli eventi per ogni comando attraverso gli stessi gestori.

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

4. Aggiungere un gestore eventi alla classe **TWTestCommand** per contrassegnare il comando selezionato come selezionato.

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

5. Aggiungere un gestore eventi che visualizza un MessageBox quando l'utente seleziona un comando sul controller di menu:

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

2. Aprire il **ToolWindow di test** nel menu **Visualizza/altre finestre** .

    Il controller di menu viene visualizzato nella barra degli strumenti della finestra degli strumenti e visualizza **MC Item 1**.

3. Fare clic sul pulsante del controller di menu a sinistra della freccia.

    Verranno visualizzati tre elementi, il primo dei quali è selezionato e con una casella di evidenziazione intorno alla relativa icona. Fare clic su **MC Item 3**.

    Verrà visualizzata una finestra di dialogo con il messaggio **selezionato controller di menu elemento 3**. Si noti che il messaggio corrisponde al testo del pulsante del controller di menu. Il pulsante del controller di menu ora Visualizza **MC Item 3**.

## <a name="see-also"></a>Vedere anche
- [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)
