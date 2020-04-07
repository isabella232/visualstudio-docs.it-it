---
title: Aggiunta di un elenco di elementi usati più di recente a un sottomenu . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740293"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Aggiungere un elenco usato più di recente a un sottomenu
In questa procedura dettagliata vengono illustrate nelle procedure dimostrative in [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)e viene illustrato come aggiungere un elenco dinamico a un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco MRU (Most Recently Used).

Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene visualizzato il menu, l'ambiente di sviluppo integrato (IDE) di Visual Studio richiede il pacchetto VSPackage per tutti i comandi che devono essere visualizzati in corrispondenza del segnaposto. Un elenco dinamico può essere presente in qualsiasi punto di un menu. Tuttavia, gli elenchi dinamici vengono in genere memorizzati e visualizzati da soli nei sottomenu o nella parte inferiore dei menu. Utilizzando questi modelli di progettazione, si abilita l'elenco dinamico dei comandi per espandere e contrarre senza influire sulla posizione di altri comandi nel menu. In questa procedura dettagliata, l'elenco MRU dinamico viene visualizzato nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.

Tecnicamente, un elenco dinamico può essere applicato anche a una barra degli strumenti. Tuttavia, si sconsiglia l'utilizzo perché una barra degli strumenti deve rimanere invariato a meno che l'utente non esegue passaggi specifici per modificarlo.

In questa procedura dettagliata viene creato un elenco MRU di quattro elementi che modificano l'ordine ogni volta che viene selezionato uno di essi (l'elemento selezionato si sposta all'inizio dell'elenco).

Per ulteriori informazioni sui menu e sui file *vsct,* consultate [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="prerequisites"></a>Prerequisiti
Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Creare un'estensione

- Seguire le procedure descritte in [Aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu modificato nelle procedure seguenti.

  Le procedure descritte in questa procedura dettagliata `TopLevelMenu`presuppongono che il nome del pacchetto VSPackage sia , ovvero il nome utilizzato in [Aggiungi un menu alla barra dei menu](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)di Visual Studio .

## <a name="create-a-dynamic-item-list-command"></a>Creare un comando di elenco di elementi dinamiciCreate a dynamic item list command

1. Aprire *TestCommandPackage.vsct*.

2. Nel `Symbols` `GuidSymbol` nodo denominato guidTestCommandPackageCmdSet della sezione aggiungere il `MRUListGroup` simbolo `cmdidMRUList` per il gruppo e il comando, come indicato di seguito.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Nella `Groups` sezione aggiungere il gruppo dichiarato dopo le voci di gruppo esistenti.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. Nella `Buttons` sezione aggiungere un nodo per rappresentare il comando appena dichiarato, dopo le voci del pulsante esistenti.

    ```csharp
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    Il `DynamicItemStart` flag consente la generazione dinamica del comando.

5. Compilare il progetto e avviare il debug per testare la visualizzazione del nuovo comando.

    Scegliere il nuovo sottomenu **SubMenu**dal menu **TestMenu** per visualizzare il nuovo comando **Segnaposto MRU**. Dopo l'implementazione di un elenco di comandi MRU dinamico nella procedura successiva, questa etichetta di comando verrà sostituita da tale elenco ogni volta che viene aperto il sottomenu.

## <a name="filling-the-mru-list"></a>Riempimento dell'elenco MRU

1. In *TestCommandPackageGuids.cs*, aggiungere le righe seguenti dopo `TestCommandPackageGuids` gli ID di comando esistenti nella definizione della classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. In *TestCommand.cs* aggiungere l'istruzione using seguente.

    ```csharp
    using System.Collections;
    ```

3. Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata AddCommand.Add the following code in the TestCommand constructor after the last AddCommand call. Il `InitMRUMenu` sarà definito in seguito

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Aggiungere il codice seguente nella classe TestCommand.Add the following code in the TestCommand class. Questo codice inizializza l'elenco di stringhe che rappresentano gli elementi da visualizzare nell'elenco MRU.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. Dopo `InitializeMRUList` il metodo, `InitMRUMenu` aggiungere il metodo. In questo modo vengono inizializzati i comandi di menu dell'elenco MRU.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    È necessario creare un oggetto comando di menu per ogni elemento possibile nell'elenco MRU. L'IDE `OnMRUQueryStatus` chiama il metodo per ogni elemento nell'elenco MRU fino a quando non sono presenti altri elementi. Nel codice gestito, l'unico modo per l'IDE sapere che non sono presenti altri elementi consiste nel creare prima tutti i possibili elementi. Se lo si desidera, è possibile contrassegnare `mc.Visible = false;` gli elementi aggiuntivi come non visibili in un primo momento utilizzando dopo la creazione del comando di menu. Questi elementi possono quindi essere `mc.Visible = true;` resi `OnMRUQueryStatus` visibili in un secondo momento utilizzando il metodo .

6. Dopo `InitMRUMenu` il metodo, `OnMRUQueryStatus` aggiungere il metodo seguente. Questo è il gestore che imposta il testo per ogni elemento MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Dopo `OnMRUQueryStatus` il metodo, `OnMRUExec` aggiungere il metodo seguente. Questo è il gestore per la selezione di un elemento MRU. Questo metodo sposta l'elemento selezionato all'inizio dell'elenco e quindi visualizza l'elemento selezionato in una finestra di messaggio.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }

    ```

## <a name="testing-the-mru-list"></a>Test dell'elenco MRU

1. Compilare il progetto e avviare il debug.

2. Scegliere **Richiama TestCommand**dal menu **TestMenu** . In questo modo viene visualizzata una finestra di messaggio che indica che il comando è stato selezionato.

    > [!NOTE]
    > Questo passaggio è necessario per forzare il pacchetto VSPackage per caricare e visualizzare correttamente l'elenco MRU. Se si ignora questo passaggio, l'elenco MRU non viene visualizzato.

3. Scegliere **Sottomenu**dal menu **Test** . Un elenco di quattro voci viene visualizzato alla fine del sottomenu, sotto un separatore. Quando si fa clic su **Elemento 3**, verrà visualizzata una finestra di messaggio con il testo Elemento **selezionato 3**. Se l'elenco di quattro elementi non viene visualizzato, assicurarsi di aver seguito le istruzioni nel passaggio precedente.

4. Aprire nuovamente il sottomenu. Si noti che **l'elemento 3** è ora all'inizio dell'elenco e gli altri elementi sono stati spinti verso il basso di una posizione. Fare di nuovo clic **sull'elemento 3** e notare che nella finestra di messaggio viene ancora visualizzato **l'elemento selezionato 3**, che indica che il testo è stato spostato correttamente nella nuova posizione insieme all'etichetta del comando.

## <a name="see-also"></a>Vedere anche
- [Aggiunta dinamica di voci di menu](../extensibility/dynamically-adding-menu-items.md)
