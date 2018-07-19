---
title: Aggiunta di un Controller di Menu per una barra degli strumenti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78ffb4e98ce8589f20d4a0253ce675e546f15ae4
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078729"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Aggiungere un controller di menu per una barra degli strumenti
Questa procedura dettagliata si basa sulle [aggiungere una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) procedura dettagliata e viene illustrato come aggiungere un controller di menu per la finestra degli strumenti. I passaggi illustrati in questo caso è possibile applicare anche alla barra degli strumenti che viene creato nel [aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md) procedura dettagliata.  
  
 Un controller di menu è un controllo split. Il lato sinistro del controller di menu Mostra l'ultimo comando, e sono eseguibili facendovi clic sopra. La parte destra del controller di menu è una freccia che, quando si fa clic, viene aperto un elenco di comandi aggiuntivi. Quando si fa clic su un comando nell'elenco, l'esecuzione del comando, e sostituisce il comando sul lato sinistro del controller di menu. In questo modo, il controller di menu funziona come un pulsante di comando che mostra sempre il comando ultimo usato da un elenco.  
  
 I controller di menu possono essere visualizzati nei menu, ma vengono spesso usati nelle barre degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-menu-controller"></a>Creare un controller di menu  
  
1.  Seguire le procedure descritte nel [aggiungere una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) per creare una finestra degli strumenti con una barra degli strumenti.  
  
2.  Nelle *TWTestCommandPackage.vsct*, passare alla sezione dei simboli. Nell'elemento GuidSymbol denominato **guidTWTestCommandPackageCmdSet**, dichiarare i controller di menu, gruppo di controller di menu e tre voci di menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Nella sezione i menu, dopo l'ultima voce di menu, definire il controller di menu come menu.  
  
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
  
     Il `TextChanges` e `TextIsAnchorCommand` flag devono essere inclusi per consentire al controller di menu in modo da riflettere l'ultimo comando selezionato.  
  
4.  Nei gruppi di sezione, dopo l'ultima voce di gruppo, aggiungere il gruppo di controller di menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Impostando il controller di menu come elemento padre, qualsiasi comando inserito in questo gruppo vengono visualizzati nel controller di menu. Il `priority` attributo viene omesso, che imposta il valore predefinito pari a 0, perché è l'unico gruppo sul controller di menu.  
  
5.  Nella sezione pulsanti, dopo l'ultima voce di pulsante, aggiungere un elemento Button per ognuna delle voci di menu.  
  
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
  
6.  A questo punto, è possibile esaminare il controller di menu. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
    1.  Nel **visualizzazione / Other Windows** menu, aprire **ToolWindow Test**.  
  
    2.  Il controller di menu viene visualizzato sulla barra degli strumenti nella finestra degli strumenti.  
  
    3.  Fare clic sulla freccia a destra del controller di menu per visualizzare i tre comandi possibili.  
  
     Si noti che quando si sceglie un comando, il titolo del controller di menu cambia per visualizzare tale comando. Nella sezione successiva, si aggiungerà il codice per attivare i comandi seguenti.  
  
## <a name="implement-the-menu-controller-commands"></a>Implementare i comandi di controller di menu  
  
1.  Nelle *TWTestCommandPackageGuids.cs*, aggiungere gli ID comando per le tre voci di menu dopo l'ID di comando esistenti.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Nelle *TWTestCommand.cs*, aggiungere il codice seguente all'inizio del `TWTestCommand` classe.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Nel costruttore TWTestCommand, dopo l'ultima chiamata al `AddCommand` metodo, aggiungere il codice per instradare gli eventi per ogni comando tramite i gestori di eventi stesso.  
  
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
  
4.  Aggiungere un gestore eventi per il **TWTestCommand** classe per contrassegnare il comando selezionato come selezionato.  
  
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
  
5.  Aggiungere un gestore eventi che consente di visualizzare una finestra di messaggio quando l'utente seleziona un comando nel controller di menu:  
  
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
  
## <a name="testing-the-menu-controller"></a>Il test controller di menu  
  
1.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
2.  Aprire il **ToolWindow di Test** nel **visualizzazione / Other Windows** menu.  
  
     Il controller di menu viene visualizzato nella barra degli strumenti nella finestra degli strumenti e consente di visualizzare **MC elemento 1**.  
  
3.  Fare clic sul pulsante di controller di menu a sinistra della freccia.  
  
     Verranno visualizzati tre elementi, il primo dei quali è selezionato e dispone di una casella evidenziazione intorno relativa icona. Fare clic su **MC elemento 3**.  
  
     Viene visualizzata una finestra di dialogo con il messaggio **è stato selezionato il controller di Menu 3 elemento**. Si noti che il messaggio corrisponde al testo del pulsante di controller di menu. Il pulsante di controller di menu Visualizza ora **MC elemento 3**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)