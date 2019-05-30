---
title: Aggiunta di un elenco a un sottomenu ultima usata | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6eb32f81947f7359f5912e8a558e8df5002a0b80
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352404"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Aggiungere che un usati di recente elenco a un sottomenu
Questa procedura dettagliata si basa sulle dimostrazioni [aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)e viene illustrato come aggiungere un elenco dinamico di un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco più recente (MRU).

Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene visualizzato il menu di scelta, l'ambiente di sviluppo integrato (IDE) di Visual Studio chiede il pacchetto VSPackage per tutti i comandi che devono essere visualizzati nel segnaposto. Un elenco dinamico può verificarsi in qualsiasi punto in un menu. Tuttavia, gli elenchi dinamici vengono in genere archiviati e visualizzati da soli nel sottomenu o al fondo del menu. Utilizzando questi modelli di progettazione, si abilita l'elenco dinamico di comandi per espandere e comprimere senza incidere sulla posizione di altri comandi del menu. In questa procedura dettagliata, viene visualizzato l'elenco MRU dinamico nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.

Tecnicamente, un elenco dinamico è applicabile anche a una barra degli strumenti. Tuttavia, è sconsigliato l'uso poiché una barra degli strumenti deve rimanere invariato, a meno che l'utente richiede passaggi specifici per modificarlo.

Questa procedura dettagliata crea un elenco MRU di quattro elementi che modificarne l'ordine ogni volta che uno di essi è selezionato (Sposta l'elemento selezionato nella parte superiore dell'elenco).

Per altre informazioni sui menu e *vsct* i file, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Creare un'estensione

- Seguire le procedure descritte in [aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu che viene modificato nelle procedure seguenti.

  Le procedure descritte in questa procedura dettagliata si presuppongono che sia il nome del pacchetto VSPackage `TopLevelMenu`, che rappresenta il nome che viene utilizzato [aggiungere un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Creare un comando di elenco elemento dinamico

1. Aprire *TestCommandPackage.vsct*.

2. Nel `Symbols` nella sezione di `GuidSymbol` nodo denominato guidTestCommandPackageCmdSet, aggiungere il simbolo per il `MRUListGroup` gruppo e il `cmdidMRUList` comando, come indicato di seguito.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Nel `Groups` sezione, aggiungere il gruppo dichiarato dopo le voci di gruppo esistente.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. Nel `Buttons` sezione, aggiungere un nodo per rappresentare il comando appena dichiarato, dopo le voci di pulsante esistente.

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

    Il `DynamicItemStart` flag consente il comando deve essere generato in modo dinamico.

5. Compilare il progetto e avviare il debug per testare la visualizzazione del nuovo comando.

    Nel **TestMenu** dal menu fare clic su nuovo sottomenu **sottomenu**, per visualizzare il nuovo comando di **MRU segnaposto**. Dopo aver implementato un elenco MRU dinamico dei comandi nella procedura successiva, questa etichetta comando verrà sostituita da tale elenco ogni volta che viene aperto il sottomenu.

## <a name="filling-the-mru-list"></a>La compilazione di elenco MRU

1. Nelle *TestCommandPackageGuids.cs*, aggiungere le righe seguenti dopo gli ID di comando esistenti nel `TestCommandPackageGuids` definizione di classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Nelle *TestCommand.cs* aggiungere la seguente istruzione using.

    ```csharp
    using System.Collections;
    ```

3. Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata AddCommand. Il `InitMRUMenu` saranno definiti successivamente

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Aggiungere il codice seguente nella classe TestCommand. Questo codice inizializza l'elenco di stringhe che rappresentano gli elementi da visualizzare nell'elenco MRU.

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

5. Dopo il `InitializeMRUList` metodo, aggiungere il `InitMRUMenu` (metodo). Ciò consente di inizializzare i comandi del menu elenco MRU.

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

    È necessario creare un oggetto di comando di menu per tutti gli elementi possibili nell'elenco MRU. Le chiamate dell'IDE di `OnMRUQueryStatus` metodo per ogni elemento nell'elenco MRU fino a quando non sono presenti più elementi. Nel codice gestito, l'unico modo per l'IDE di sapere che non sono presenti altri elementi consiste nel creare innanzitutto tutti gli elementi possibili. Se si desidera, è possibile contrassegnare primi elementi aggiuntivi come non visibili nell'usando `mc.Visible = false;` dopo aver creato il comando di menu. Questi elementi possono quindi essere reso visibili in un secondo momento usando `mc.Visible = true;` nella `OnMRUQueryStatus` (metodo).

6. Dopo il `InitMRUMenu` metodo, aggiungere il codice seguente `OnMRUQueryStatus` (metodo). Questo è il gestore che imposta il testo per ogni elemento MRU.

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

7. Dopo il `OnMRUQueryStatus` metodo, aggiungere il codice seguente `OnMRUExec` (metodo). Questo è il gestore per la selezione di un elemento MRU. Questo metodo consente di spostare l'elemento selezionato nella parte superiore dell'elenco e quindi Visualizza l'elemento selezionato in una finestra di messaggio.

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

## <a name="testing-the-mru-list"></a>Test elenco MRU

1. Compilare il progetto e avviare il debug.

2. Nel **TestMenu** menu, fare clic su **richiamare TestCommand**. Questa operazione consente di visualizzare una finestra di messaggio che indica che il comando è stato selezionato.

    > [!NOTE]
    > Questo passaggio è necessario forzare il pacchetto VSPackage per caricare e visualizzare correttamente l'elenco MRU. Se si ignora questo passaggio, non viene visualizzato l'elenco di usati di recente.

3. Nel **dal Menu Test** menu, fare clic su **sottomenu**. Viene visualizzato un elenco di quattro elementi alla fine del sottomenu di sotto di un separatore. Quando fa clic su **elemento 3**, una finestra di messaggio dovrà essere visualizzato e visualizzare il testo **selezionato elemento 3**. (Se non viene visualizzato l'elenco di quattro elementi, assicurarsi di aver seguito le istruzioni nel passaggio precedente.)

4. Aprire il sottomenu di nuovo. Si noti che **elemento 3** è ora nella parte superiore dell'elenco e gli altri elementi sono stati inseriti verso il basso di una posizione. Fare clic su **elemento 3** anche in questo caso, si nota che la finestra di messaggio Visualizza ancora **selezionato elemento 3**, che indica che il testo è stato spostato correttamente per la nuova posizione con l'etichetta del comando.

## <a name="see-also"></a>Vedere anche
- [Aggiunta dinamica di voci di menu](../extensibility/dynamically-adding-menu-items.md)
