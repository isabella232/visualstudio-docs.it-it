---
title: Aggiunta di una barra degli strumenti | Microsoft Docs
description: Informazioni su come aggiungere una barra degli strumenti contenente pulsanti associati ai comandi Visual Studio ambiente di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 40d28a92e6c4c0695c21bc7271417aff2fd778f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035319"
---
# <a name="add-a-toolbar"></a>Aggiungere una barra degli strumenti
Questa procedura dettagliata illustra come aggiungere una barra degli strumenti all Visual Studio IDE.

 Una barra degli strumenti è una striscia orizzontale o verticale che contiene pulsanti associati ai comandi. A seconda dell'implementazione, una barra degli strumenti nell'IDE può essere riposizionata, ancorata su qualsiasi lato della finestra principale dell'IDE o impostata per rimanere davanti ad altre finestre.

 Inoltre, gli utenti possono aggiungere comandi a una barra degli strumenti o rimuoverli da essa usando la **finestra di** dialogo Personalizza. In genere, le barre degli strumenti nei pacchetti VSPackage sono personalizzabili dall'utente. L'IDE gestisce tutte le personalizzazioni e il pacchetto VSPackage risponde ai comandi. Il pacchetto VSPackage non deve sapere dove si trova fisicamente un comando.

 Per altre informazioni sui menu, vedere [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-toolbar"></a>Creare un'estensione con una barra degli strumenti
 Creare un progetto VSIX denominato `IDEToolbar` . Aggiungere un modello di voce di comando di menu **denominato ToolbarTestCommand**. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Creare una barra degli strumenti per l'IDE

1. In *ToolbarTestCommandPackage.vsct* cercare la sezione Simboli. Nell'elemento GuidSymbol denominato guidToolbarTestCommandPackageCmdSet aggiungere dichiarazioni per una barra degli strumenti e un gruppo di barre degli strumenti, come indicato di seguito.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Nella parte superiore della sezione Comandi creare una sezione Menu. Aggiungere un elemento Menu alla sezione Menu per definire la barra degli strumenti.

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

     Le barre degli strumenti non possono essere annidate come sottomenu. Pertanto, non è necessario assegnare un gruppo padre. Inoltre, non è necessario impostare una priorità, perché l'utente può spostare le barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti viene definita a livello di codice, ma le modifiche successive apportate dall'utente vengono rese persistenti.

3. Nella sezione [Gruppi,](../extensibility/groups-element.md) dopo la voce di gruppo esistente, definire un [elemento Group](../extensibility/group-element.md) per contenere i comandi per la barra degli strumenti.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Fare in modo che il pulsante venga visualizzato sulla barra degli strumenti. Nella sezione Pulsanti sostituire il blocco Padre in Pulsante sulla barra degli strumenti. Il blocco Button risultante dovrebbe essere simile al seguente:

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

6. Fare clic con il pulsante destro Visual Studio menu di scelta rapida per ottenere l'elenco delle barre degli strumenti. Selezionare Barra **degli strumenti di test**.

7. A questo punto la barra degli strumenti dovrebbe essere visualizzata come icona a destra dell'icona Trova nei file. Quando si fa clic sull'icona, verrà visualizzata una finestra di messaggio che indica **ToolbarTestCommandPackage. All'interno di IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
