---
title: Aggiunta di una barra degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740224"
---
# <a name="add-a-toolbar"></a>Aggiunta di una barra degli strumenti
Questa procedura dettagliata viene illustrato come aggiungere una barra degli strumenti per l'IDE di Visual Studio.This walkthrough shows how to add a toolbar to the Visual Studio IDE.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati ai comandi. A seconda della sua implementazione, una barra degli strumenti nell'IDE può essere riposizionata, ancorata su qualsiasi lato della finestra dell'IDE principale o resa per rimanere davanti ad altre finestre.

 Inoltre, gli utenti possono aggiungere comandi a una barra degli strumenti o rimuoverli da essa utilizzando la finestra di dialogo **Personalizza.** In genere, le barre degli strumenti in VSPackage sono personalizzabili dall'utente. L'IDE gestisce tutte le personalizzazioni e il pacchetto VSPackage risponde ai comandi. Il pacchetto VSPackage non è necessario sapere dove si trova fisicamente un comando.

 Per ulteriori informazioni sui menu, consultate [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-toolbar"></a>Creare un'estensione con una barra degli strumenti
 Creare un progetto `IDEToolbar`VSIX denominato . Aggiungere un modello di elemento di comando di menu denominato **ToolbarTestCommand**. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu .

## <a name="create-a-toolbar-for-the-ide"></a>Creare una barra degli strumenti per l'IDECreate a toolbar for the IDE

1. In *ToolbarTestCommandPackage.vsct*cercare la sezione Symbols . Nell'elemento GuidSymbol denominato guidToolbarTestCommandPackageCmdSet aggiungere le dichiarazioni per una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Nella parte superiore della sezione Comandi, creare una sezione Menu. Aggiungere un Menu elemento per il Menu sezione per definire la barra degli strumenti.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Le barre degli strumenti non possono essere nidificate come sottomenu. Pertanto, non è necessario assegnare un gruppo padre. Inoltre, non è necessario impostare una priorità, perché l'utente può spostare le barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti viene definita a livello di codice, ma le modifiche successive da parte dell'utente vengono mantenute.

3. Nella sezione [Gruppi,](../extensibility/groups-element.md) dopo la voce di gruppo esistente, definire un elemento [Group](../extensibility/group-element.md) per contenere i comandi per la barra degli strumenti.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Fare in modo che il pulsante venga visualizzato sulla barra degli strumenti. Nella sezione Pulsanti sostituire il blocco Parent nel Pulsante sulla barra degli strumenti. Il blocco Button risultante dovrebbe essere simile al seguente:The resulting Button block should look like this:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non dispone di comandi, non viene visualizzata.

5. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

6. Fare clic con il pulsante destro del mouse sulla barra dei menu di Visual Studio per ottenere l'elenco delle barre degli strumenti. Selezionare **Barra degli strumenti di test**.

7. A destra dell'icona Trova nei file dovrebbe essere visualizzata come icona. Quando si fa clic sull'icona, si dovrebbe vedere una finestra di messaggio che dice ToolbarTestCommandPackage.When you click the icon, you should see a message box that says **ToolbarTestCommandPackage. Inside IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
