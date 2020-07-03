---
title: Aggiunta di una barra degli strumenti a una finestra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5351fe6a713c217f8fca20d6740b542dc75f053
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904126"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Aggiungere una barra degli strumenti a una finestra degli strumenti
In questa procedura dettagliata viene illustrato come aggiungere una barra degli strumenti a una finestra degli strumenti.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati ai comandi. La lunghezza di una barra degli strumenti in una finestra degli strumenti è sempre uguale alla larghezza o all'altezza della finestra degli strumenti, a seconda del punto in cui la barra degli strumenti è ancorata.

 Diversamente dalle barre degli strumenti nell'IDE, una barra degli strumenti in una finestra degli strumenti deve essere ancorata e non può essere spostata o personalizzata. Se il pacchetto VSPackage è scritto nel codice umanaged, la barra degli strumenti può essere ancorata a tutti i bordi.

 Per ulteriori informazioni su come aggiungere una barra degli strumenti, vedere [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Creare una barra degli strumenti per una finestra degli strumenti

1. Creare un progetto VSIX denominato `TWToolbar` con un comando di menu denominato **TWTestCommand** e una finestra degli strumenti denominata **TestToolWindow**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md) e [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md). È necessario aggiungere il modello di elemento del comando prima di aggiungere il modello della finestra degli strumenti.

2. In *TWTestCommandPackage. vsct*cercare la sezione simboli. Nel nodo GuidSymbol denominato guidTWTestCommandPackageCmdSet dichiarare una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Nella parte superiore della `Commands` sezione creare una `Menus` sezione. Aggiungere un `Menu` elemento per definire la barra degli strumenti.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Le barre degli strumenti non possono essere annidate come i sottomenu. Non è quindi necessario assegnare un elemento padre. Non è inoltre necessario impostare una priorità perché l'utente può spostare le barre degli strumenti. In genere, il posizionamento iniziale di una barra degli strumenti viene definito a livello di codice, ma le successive modifiche da parte dell'utente sono rese permanente.

4. Nella sezione gruppi definire un gruppo che contenga i comandi per la barra degli strumenti.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Nella sezione pulsanti modificare l'elemento padre dell'elemento del pulsante esistente nel gruppo della barra degli strumenti in modo che la barra degli strumenti venga visualizzata.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non ha alcun comando, non viene visualizzata.

     Poiché la nuova barra degli strumenti non viene aggiunta automaticamente alla finestra degli strumenti, è necessario aggiungere la barra degli strumenti in modo esplicito. Questo è discusso nella sezione seguente.

## <a name="add-the-toolbar-to-the-tool-window"></a>Aggiungere la barra degli strumenti alla finestra degli strumenti

1. In *TWTestCommandPackageGuids.cs* aggiungere le righe seguenti.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. In *TestToolWindow.cs* aggiungere l'istruzione using seguente.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. Nel costruttore TestToolWindow aggiungere la riga seguente.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testare la barra degli strumenti nella finestra degli strumenti

1. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.

2. Nel menu **Visualizza/altre finestre** fare clic su **test ToolWindow** per visualizzare la finestra degli strumenti.

     Nella parte superiore sinistra della finestra degli strumenti dovrebbe essere visualizzata una barra degli strumenti (icona predefinita), appena sotto il titolo.

3. Sulla barra degli strumenti fare clic sull'icona per visualizzare il messaggio **TWTestCommandPackage all'interno di TWToolbar. TWTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Vedere anche
- [Aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md)
