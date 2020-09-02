---
title: Aggiunta di una barra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: beb97356daf3c932470bf2598e58e1f5b40ea233
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904069"
---
# <a name="add-a-toolbar"></a>Aggiungere una barra degli strumenti
Questa procedura dettagliata illustra come aggiungere una barra degli strumenti all'IDE di Visual Studio.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati ai comandi. A seconda della relativa implementazione, una barra degli strumenti nell'IDE può essere riposizionata, ancorata a qualsiasi lato della finestra principale dell'IDE o creata per restare davanti ad altre finestre.

 Inoltre, gli utenti possono aggiungere comandi a una barra degli strumenti o rimuoverli tramite la finestra di dialogo **Personalizza** . In genere, le barre degli strumenti in VSPackage sono personalizzabili dall'utente. L'IDE gestisce tutte le personalizzazioni e il pacchetto VSPackage risponde ai comandi. Non è necessario che il pacchetto VSPackage sappia dove si trova fisicamente un comando.

 Per ulteriori informazioni sui menu, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Creare un'estensione con una barra degli strumenti
 Creare un progetto VSIX denominato `IDEToolbar` . Aggiungere un modello di elemento del comando di menu denominato **ToolbarTestCommand**. Per informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Creare una barra degli strumenti per l'IDE

1. In *ToolbarTestCommandPackage. vsct*cercare la sezione simboli. Nell'elemento GuidSymbol denominato guidToolbarTestCommandPackageCmdSet aggiungere le dichiarazioni per una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Nella parte superiore della sezione comandi creare una sezione di menu. Aggiungere un elemento di menu alla sezione menu per definire la barra degli strumenti.

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

     Non è possibile nidificare le barre degli strumenti come sottomenu. Non è pertanto necessario assegnare un gruppo padre. Non è inoltre necessario impostare una priorità perché l'utente può spostare le barre degli strumenti. In genere, il posizionamento iniziale di una barra degli strumenti viene definito a livello di codice, ma le successive modifiche da parte dell'utente sono rese permanente.

3. Nella sezione [gruppi](../extensibility/groups-element.md) , dopo la voce di gruppo esistente, definire un elemento di [gruppo](../extensibility/group-element.md) che contenga i comandi per la barra degli strumenti.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Fare in modo che il pulsante venga visualizzato sulla barra degli strumenti. Nella sezione pulsanti sostituire il blocco padre nel pulsante sulla barra degli strumenti. Il blocco del pulsante risultante sarà simile al seguente:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Per impostazione predefinita, se una barra degli strumenti non ha alcun comando, non viene visualizzata.

5. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

6. Fare clic con il pulsante destro del mouse sulla barra dei menu di Visual Studio per ottenere l'elenco delle barre degli strumenti. Selezionare **barra degli strumenti di test**.

7. A questo punto la barra degli strumenti verrà visualizzata come icona a destra dell'icona Cerca nei file. Quando si fa clic sull'icona, viene visualizzata una finestra di messaggio che indica **ToolbarTestCommandPackage. All'interno di IDEToolbar. ToolbarTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
