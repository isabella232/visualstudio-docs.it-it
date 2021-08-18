---
title: Aggiunta di una barra degli strumenti a una finestra degli strumenti | Microsoft Docs
description: Informazioni su come aggiungere una barra degli strumenti contenente pulsanti associati a comandi a una finestra degli strumenti nell Visual Studio ide (Integrated Development Environment).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6a2c93459dd588a1a04be098cf675aa4c58b8d37
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051365"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Aggiungere una barra degli strumenti a una finestra degli strumenti
Questa procedura dettagliata illustra come aggiungere una barra degli strumenti a una finestra degli strumenti.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati ai comandi. La lunghezza di una barra degli strumenti in una finestra degli strumenti è sempre uguale alla larghezza o all'altezza della finestra degli strumenti, a seconda del punto in cui la barra degli strumenti è ancorata.

 A differenza delle barre degli strumenti nell'IDE, una barra degli strumenti in una finestra degli strumenti deve essere ancorata e non può essere spostata o personalizzata. Se il pacchetto VSPackage è scritto in codice umanamente modificato, la barra degli strumenti può essere ancorata a qualsiasi bordo.

 Per altre informazioni su come aggiungere una barra degli strumenti, vedere Aggiunta [di una barra degli strumenti.](../extensibility/adding-a-toolbar.md)

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-toolbar-for-a-tool-window"></a>Creare una barra degli strumenti per una finestra degli strumenti

1. Creare un progetto VSIX denominato con un comando di menu denominato TWTestCommand e una finestra degli strumenti `TWToolbar` denominata  **TestToolWindow.** Per altre informazioni, vedere [Creare un'estensione con un comando di menu e](../extensibility/creating-an-extension-with-a-menu-command.md) Creare [un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md) È necessario aggiungere il modello di elemento di comando prima di aggiungere il modello della finestra degli strumenti.

2. In *TWTestCommandPackage.vsct* cercare la sezione Simboli. Nel nodo GuidSymbol denominato guidTWTestCommandPackageCmdSet dichiarare una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Nella parte superiore della `Commands` sezione creare una sezione `Menus` . Aggiungere un elemento `Menu` per definire la barra degli strumenti.

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

     Le barre degli strumenti non possono essere annidate come sottomenu. Non è quindi necessario assegnare un elemento padre. Inoltre, non è necessario impostare una priorità, perché l'utente può spostare le barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti viene definita a livello di codice, ma le successive modifiche apportate dall'utente vengono rese persistenti.

4. Nella sezione Gruppi definire un gruppo per contenere i comandi per la barra degli strumenti.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Nella sezione Pulsanti modificare l'elemento padre dell'elemento Button esistente nel gruppo di barre degli strumenti in modo che la barra degli strumenti sia visualizzata.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non contiene comandi, non viene visualizzata.

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

1. Compilare il progetto e avviare il debug. Verrà Visual Studio l'istanza sperimentale.

2. Nel menu **Visualizza/Altro Windows** fare clic su **Strumento di testFinestra** per visualizzare la finestra degli strumenti.

     Verrà visualizzata una barra degli strumenti (simile all'icona predefinita) in alto a sinistra nella finestra degli strumenti, sotto il titolo.

3. Sulla barra degli strumenti fare clic sull'icona per visualizzare il messaggio **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vedi anche
- [Aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md)
