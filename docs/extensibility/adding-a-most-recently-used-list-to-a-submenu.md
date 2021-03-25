---
title: Aggiunta di un elenco usato più di recente a un sottomenu | Microsoft Docs
description: Informazioni su come aggiungere un elenco dinamico che contiene i comandi di menu usati più di recente a un sottomenu in Visual Studio Integrated Development Environment (IDE).
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
ms.workload:
- vssdk
ms.openlocfilehash: bb238afb0f583f1b913fbd87f4f50e43679ebd7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060016"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Aggiungere un elenco usato più di recente a un sottomenu
Questa procedura dettagliata si basa sulle dimostrazioni in [aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)e Mostra come aggiungere un elenco dinamico a un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco degli ultimi elementi usati (MRU).

Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene visualizzato il menu, Visual Studio Integrated Development Environment (IDE) chiede al VSPackage tutti i comandi che devono essere visualizzati nel segnaposto. Un elenco dinamico può essere visualizzato in qualsiasi punto di un menu. Tuttavia, gli elenchi dinamici vengono in genere archiviati e visualizzati autonomamente nei sottomenu o nei menu in basso. Usando questi modelli di progettazione, si Abilita l'elenco dinamico dei comandi da espandere e comprimere senza influire sulla posizione di altri comandi nel menu. In questa procedura dettagliata, l'elenco MRU dinamico viene visualizzato nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.

Tecnicamente, è possibile applicare un elenco dinamico anche a una barra degli strumenti. Tuttavia, si sconsiglia l'utilizzo perché una barra degli strumenti deve rimanere invariata, a meno che l'utente non accetti passaggi specifici per modificarlo.

Questa procedura dettagliata crea un elenco MRU di quattro elementi che modificano l'ordine ogni volta che uno di essi è selezionato (l'elemento selezionato si sposta nella parte superiore dell'elenco).

Per ulteriori informazioni sui menu e sui file con *estensione vsct* , vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Creare un'estensione

- Seguire le procedure descritte in [aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu modificato nelle procedure riportate di seguito.

  Le procedure descritte in questa procedura dettagliata presuppongono che il nome del pacchetto VSPackage sia `TestCommand` , ovvero il nome usato in [aggiungere un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Creazione di un comando elenco elementi dinamici

1. Aprire *TestCommandPackage. vsct*.

2. Nella `Symbols` sezione, nel `GuidSymbol` nodo denominato guidTestCommandPackageCmdSet, aggiungere il simbolo per il `MRUListGroup` gruppo e il `cmdidMRUList` comando, come indicato di seguito.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Nella `Groups` sezione aggiungere il gruppo dichiarato dopo le voci di gruppo esistenti.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. Nella `Buttons` sezione aggiungere un nodo per rappresentare il comando appena dichiarato, dopo le voci dei pulsanti esistenti.

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

    Nel menu **Testmenu** fare clic **sul menu nuovo** sottomenu, sottomenu per visualizzare il nuovo comando, il **segnaposto MRU**. Dopo l'implementazione di un elenco di comandi MRU dinamico nella procedura successiva, questa etichetta di comando verrà sostituita da tale elenco ogni volta che viene aperto il sottomenu.

## <a name="filling-the-mru-list"></a>Riempimento dell'elenco MRU

1. In *TestCommandPackageGuids. cs* aggiungere le righe seguenti dopo gli ID dei comandi esistenti nella `TestCommandPackageGuids` definizione della classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. In *TestCommand. cs* aggiungere la seguente istruzione using.

    ```csharp
    using System.Collections;
    ```

3. Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata a AddCommand. `InitMRUMenu`Verrà definito in seguito

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

5. Dopo il `InitializeMRUList` metodo aggiungere il `InitMRUMenu` metodo. Questa operazione consente di inizializzare i comandi di menu elenco MRU.

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

    È necessario creare un oggetto comando di menu per ogni elemento possibile nell'elenco MRU. L'IDE chiama il `OnMRUQueryStatus` metodo per ogni elemento nell'elenco MRU fino a quando non sono presenti altri elementi. Nel codice gestito, l'unico modo per consentire all'IDE di capire che non sono presenti altri elementi consiste nel creare prima tutti gli elementi possibili. Se lo si desidera, è possibile contrassegnare elementi aggiuntivi come non visibili all'inizio utilizzando `mc.Visible = false;` dopo aver creato il comando di menu. Questi elementi possono quindi essere resi visibili in un secondo momento usando `mc.Visible = true;` nel `OnMRUQueryStatus` metodo.

6. Dopo il `InitMRUMenu` metodo aggiungere il metodo seguente `OnMRUQueryStatus` . Si tratta del gestore che imposta il testo per ogni elemento MRU.

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

7. Dopo il `OnMRUQueryStatus` metodo aggiungere il metodo seguente `OnMRUExec` . Si tratta del gestore per la selezione di un elemento MRU. Questo metodo sposta l'elemento selezionato nella parte superiore dell'elenco e quindi Visualizza l'elemento selezionato in una finestra di messaggio.

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

2. Scegliere **richiama TestCommand** dal menu **Testmenu** . Questa operazione Visualizza una finestra di messaggio che indica che il comando è stato selezionato.

    > [!NOTE]
    > Questo passaggio è necessario per forzare il caricamento del pacchetto VSPackage e la visualizzazione corretta dell'elenco MRU. Se si ignora questo passaggio, l'elenco MRU non viene visualizzato.

3. **Scegliere sottomenu dal menu** **test** . Un elenco di quattro elementi viene visualizzato alla fine del sottomenu, sotto un separatore. Quando si fa clic sull' **elemento 3**, viene visualizzata una finestra di messaggio che Visualizza il testo **selezionato elemento 3**. Se l'elenco di quattro elementi non è visualizzato, verificare di aver seguito le istruzioni riportate nel passaggio precedente.

4. Aprire di nuovo il sottomenu. Si noti che l' **elemento 3** è ora all'inizio dell'elenco e gli altri elementi sono stati spostati verso il basso di una posizione. Fare di nuovo clic sull' **elemento 3** . si noti che nella finestra di messaggio viene ancora visualizzato l' **elemento selezionato 3**, che indica che il testo è stato spostato correttamente nella nuova posizione insieme all'etichetta del comando.

## <a name="see-also"></a>Vedi anche
- [Aggiunta dinamica di voci di menu](../extensibility/dynamically-adding-menu-items.md)
