---
title: Aggiunta di una barra degli strumenti a una finestra degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740241"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Aggiungere una barra degli strumenti a una finestra degli strumenti
In questa procedura dettagliata viene illustrato come aggiungere una barra degli strumenti a una finestra degli strumenti.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati ai comandi. La lunghezza di una barra degli strumenti in una finestra degli strumenti è sempre uguale alla larghezza o all'altezza della finestra degli strumenti, a seconda di dove è ancorata.

 A differenza delle barre degli strumenti nell'IDE, una barra degli strumenti in una finestra degli strumenti deve essere ancorata e non può essere spostata o personalizzata. Se il pacchetto VSPackage è scritto in codice gestito, la barra degli strumenti può essere ancorata a qualsiasi bordo.

 Per ulteriori informazioni su come aggiungere una barra [degli strumenti,](../extensibility/adding-a-toolbar.md)vedere Aggiunta di una barra degli strumenti .

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-toolbar-for-a-tool-window"></a>Creare una barra degli strumenti per una finestra degli strumenti

1. Creare un progetto `TWToolbar` VSIX denominato con un comando di menu denominato **TWTestCommand** e una finestra degli strumenti denominata **TestToolWindow**. Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) di menu e Creare [un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md) È necessario aggiungere il modello di elemento di comando prima di aggiungere il modello di finestra degli strumenti.

2. In *TWTestCommandPackage.vsct*, cercare la sezione Symbols . Nel Nodo GuidSymbol denominato guidTWTestCommandPackageCmdSet dichiara una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Nella parte superiore `Commands` della sezione, creare una `Menus` sezione. Aggiungere `Menu` un elemento per definire la barra degli strumenti.

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

     Le barre degli strumenti non possono essere nidificate come sottomenu. Pertanto, non è necessario assegnare un elemento padre. Inoltre, non è necessario impostare una priorità, perché l'utente può spostare le barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti viene definita a livello di codice, ma le modifiche successive da parte dell'utente vengono mantenute.

4. Nella sezione Gruppi, definire un gruppo per contenere i comandi per la barra degli strumenti.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Nella sezione Pulsanti modificare l'elemento padre dell'elemento Button esistente nel gruppo di barre degli strumenti in modo che venga visualizzata la barra degli strumenti.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non dispone di comandi, non viene visualizzata.

     Poiché la nuova barra degli strumenti non viene aggiunta automaticamente alla finestra degli strumenti, la barra degli strumenti deve essere aggiunta in modo esplicito. Questo è discusso nella sezione seguente.

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

3. Nel TestToolWindow costruttore aggiungere la riga seguente.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testare la barra degli strumenti nella finestra degli strumenti

1. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.The Visual Studio experimental instance should appear.

2. Scegliere **Test ToolWindow** dal menu **Visualizza/Altre finestre** per visualizzare la finestra degli strumenti.

     Dovresti vedere una barra degli strumenti (sembra l'icona predefinita) in alto a sinistra nella finestra degli strumenti, appena sotto il titolo.

3. Nella barra degli strumenti fare clic sull'icona per visualizzare il messaggio **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vedere anche
- [Aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md)
