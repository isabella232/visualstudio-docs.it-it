---
title: Aggiunta di un elenco usato più di recente a un sottomenu | Microsoft Docs
description: Informazioni su come aggiungere un elenco dinamico che contiene i comandi di menu usati più di recente a un sottomenu nell'ambiente di Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71c649d9eeb66b67cde133bef6a525427c618209
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035332"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Aggiungere un elenco usato più di recente a un sottomenu
Questa procedura dettagliata si basa sulle dimostrazioni in Aggiungere un [sottomenu a](../extensibility/adding-a-submenu-to-a-menu.md)un menu e illustra come aggiungere un elenco dinamico a un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco MRU (Most Recently Used).

Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene visualizzato il menu, Visual Studio'ambiente di sviluppo integrato (IDE) chiede al pacchetto VSPackage tutti i comandi che devono essere visualizzati nel segnaposto. Un elenco dinamico può verificarsi in qualsiasi punto di un menu. Tuttavia, gli elenchi dinamici vengono in genere archiviati e visualizzati da soli nei sottomenu o nella parte inferiore dei menu. Usando questi modelli di progettazione, è possibile abilitare l'elenco dinamico di comandi per espandersi e contrarsi senza influire sulla posizione di altri comandi nel menu. In questa procedura dettagliata l'elenco MRU dinamico viene visualizzato nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.

Tecnicamente, un elenco dinamico può essere applicato anche a una barra degli strumenti. Tuttavia, questo utilizzo è sconsigliato perché una barra degli strumenti deve rimanere invariata a meno che l'utente non eserciti passaggi specifici per modificarlo.

Questa procedura dettagliata crea un elenco MRU di quattro elementi che modificano l'ordine ogni volta che ne viene selezionato uno (l'elemento selezionato viene spostato all'inizio dell'elenco).

Per altre informazioni sui menu e *sui file vsct,* vedere [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="create-an-extension"></a>Creare un'estensione

- Seguire le procedure descritte in [Aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu modificato nelle procedure seguenti.

  Le procedure descritte in questa procedura dettagliata presuppongono che il nome del pacchetto VSPackage sia , ovvero il nome usato in Aggiungere un menu alla barra Visual Studio `TestCommand` [menu.](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)

## <a name="create-a-dynamic-item-list-command"></a>Creare un comando elenco di elementi dinamico

1. Aprire *TestCommandPackage.vsct.*

2. Nella sezione `Symbols` nel nodo denominato `GuidSymbol` guidTestCommandPackageCmdSet aggiungere il simbolo per il gruppo e `MRUListGroup` il `cmdidMRUList` comando, come indicato di seguito.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Nella sezione `Groups` aggiungere il gruppo dichiarato dopo le voci del gruppo esistenti.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. Nella sezione `Buttons` aggiungere un nodo per rappresentare il comando appena dichiarato, dopo le voci del pulsante esistenti.

    ```xml
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

    Nel menu **TestMenu** fare clic sul nuovo sottomenu **Sottomenu** per visualizzare il nuovo comando Segnaposto **MRU.** Dopo l'implementazione di un elenco dinamico MRU di comandi nella procedura successiva, questa etichetta di comando verrà sostituita da tale elenco ogni volta che il sottomenu viene aperto.

## <a name="filling-the-mru-list"></a>Compilazione dell'elenco MRU

1. In *TestCommandPackageGuids.cs* aggiungere le righe seguenti dopo gli ID di comando esistenti nella `TestCommandPackageGuids` definizione della classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. In *TestCommand.cs* aggiungere l'istruzione using seguente.

    ```csharp
    using System.Collections;
    ```

3. Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata AddCommand. `InitMRUMenu`L'oggetto verrà definito in un secondo momento

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

5. Dopo il `InitializeMRUList` metodo , aggiungere il metodo `InitMRUMenu` . In questo modo vengono inizializzati i comandi di menu dell'elenco MRU.

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

    È necessario creare un oggetto comando di menu per ogni possibile elemento nell'elenco MRU. L'IDE chiama `OnMRUQueryStatus` il metodo per ogni elemento nell'elenco MRU finché non sono presenti altri elementi. Nel codice gestito, l'unico modo per l'IDE di sapere che non sono presenti altri elementi è creare prima tutti gli elementi possibili. Se si vuole, è possibile contrassegnare elementi aggiuntivi come non visibili all'inizio usando `mc.Visible = false;` dopo la creazione del comando di menu. Questi elementi possono quindi essere resi visibili in un secondo momento usando `mc.Visible = true;` nel `OnMRUQueryStatus` metodo .

6. Dopo il `InitMRUMenu` metodo , aggiungere il metodo `OnMRUQueryStatus` seguente. Si tratta del gestore che imposta il testo per ogni elemento MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Dopo il `OnMRUQueryStatus` metodo , aggiungere il metodo `OnMRUExec` seguente. Questo è il gestore per la selezione di un elemento MRU. Questo metodo sposta l'elemento selezionato all'inizio dell'elenco e quindi visualizza l'elemento selezionato in una finestra di messaggio.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

2. Scegliere Richiama **TestCommand** dal menu **TestMenu**. In questo modo viene visualizzata una finestra di messaggio che indica che il comando è stato selezionato.

    > [!NOTE]
    > Questo passaggio è necessario per forzare il caricamento del pacchetto VSPackage e visualizzare correttamente l'elenco MRU. Se si ignora questo passaggio, l'elenco MRU non viene visualizzato.

3. Scegliere **Sottomenu dal** menu **Test**. Un elenco di quattro elementi viene visualizzato alla fine del sottomenu, sotto un separatore. Quando si fa **clic sull'elemento 3,** viene visualizzata una finestra di messaggio con il testo **Elemento selezionato 3**. Se l'elenco di quattro elementi non viene visualizzato, assicurarsi di aver seguito le istruzioni nel passaggio precedente.

4. Aprire di nuovo il sottomenu. Si noti **che l'elemento 3** si trova ora all'inizio dell'elenco e gli altri elementi sono stati spinti verso il basso di una posizione. Fare di nuovo clic sull'elemento **3** e notare che nella finestra di messaggio viene ancora visualizzato Elemento **selezionato 3**, che indica che il testo è stato spostato correttamente nella nuova posizione insieme all'etichetta del comando.

## <a name="see-also"></a>Vedi anche
- [Aggiunta dinamica di voci di menu](../extensibility/dynamically-adding-menu-items.md)
