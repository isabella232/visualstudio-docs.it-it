---
title: Personalizzare menu e barre degli strumenti
description: Informazioni su come personalizzare Visual Studio menu e barre degli strumenti e su come personalizzare i comandi inclusi nei menu e nelle barre degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 09/01/2021
ms.topic: how-to
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8223dfb14ab626e6509cf0df32cba05526fc707f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710265"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Procedura: personalizzare menu e barre degli strumenti in Visual Studio

È possibile personalizzare Visual Studio non solo aggiungendo e rimuovendo barre degli strumenti e menu nella barra dei menu, ma anche aggiungendo e rimuovendo comandi in una barra degli strumenti o menu specifico.

> [!TIP]
> Per altre informazioni su come personalizzare la barra degli strumenti in modo da renderla personalizzata, vedere il recente post di blog [**Optimizing toolbars for your workflow**](https://devblogs.microsoft.com/visualstudio/optimizing-toolbars-for-your-workflow/)(Ottimizzazione delle barre degli strumenti per il flusso di lavoro).

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Aggiungere, rimuovere o spostare un menu nella barra dei menu

1. Sulla barra dei menu scegliere Strumenti  >  **Personalizza.**

     Viene visualizzata la finestra di dialogo **Personalizza**.

2. Nella scheda **Comandi** lasciare selezionato il pulsante di opzione **Barra dei menu**, lasciare selezionata **Barra dei menu** nell'elenco accanto all'opzione e quindi eseguire una delle procedure indicate di seguito:

    - Per aggiungere un menu, selezionare il pulsante **Aggiungi nuovo menu** e il pulsante **Modifica selezione** e quindi assegnare un nome al menu che si vuole aggiungere.

        ![Finestra di dialogo Personalizza che mostra come aggiungere un menu](../ide/media/addmenu.png)

    - Per rimuovere un menu, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Elimina**.

    - Per spostare un menu all'interno della barra dei menu, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Sposta su** o **Sposta giù**.

## <a name="add-remove-or-move-a-toolbar"></a>Aggiungere, rimuovere o spostare una barra degli strumenti

1. Sulla barra dei menu scegliere Strumenti  >  **Personalizza.**

     Viene visualizzata la finestra di dialogo **Personalizza**.

2. Nella scheda **Barra degli strumenti** seguire una delle procedure indicate di seguito:

    - Per aggiungere una barra degli strumenti, selezionare il pulsante **Nuovo**, specificare un nome per la barra degli strumenti da aggiungere e quindi fare clic sul pulsante **OK**.

        ![Finestra di dialogo Personalizza che mostra come aggiungere una barra degli strumenti](../ide/media/addtoolbar.png)

    - Per rimuovere una barra degli strumenti personalizzata, selezionarla nell'elenco **Barre degli strumenti** e fare clic sul pulsante **Elimina**.

        > [!IMPORTANT]
        > È possibile eliminare le barre degli strumenti create, ma non quelle predefinite.

    - Per spostare una barra degli strumenti in una posizione di ancoraggio diversa, selezionarla nell'elenco **Barre degli strumenti**, fare clic sul pulsante **Modifica selezione** e quindi scegliere una posizione nell'elenco visualizzato.

        È inoltre possibile trascinare una barra degli strumenti per il bordo sinistro e spostarla in qualsiasi punto dell'area di ancoraggio principale.

        > [!NOTE]
        > Per altre informazioni su come migliorare l'uso e l'accessibilità delle barre degli strumenti, vedere [Procedura: Impostare le opzioni di accessibilità IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name=""></a><a name="customizing_menu">Personalizzare un menu o di una barra degli strumenti</a>

> [!WARNING]
> Dopo aver personalizzato una barra degli strumenti o un menu, verificare che la relativa casella di controllo rimanga selezionata nella finestra di dialogo **Personalizza**. In caso contrario, le modifiche non verranno mantenute dopo aver chiuso e riaperto Visual Studio.

1. Sulla barra dei menu scegliere Strumenti  >  **Personalizza.**

    Viene visualizzata la finestra di dialogo **Personalizza**.

2. Nella scheda **Comandi** selezionare il pulsante di opzione per il tipo di elemento che si vuole personalizzare.

3. Nell'elenco relativo al tipo di elemento desiderato selezionare il menu o la barra degli strumenti da personalizzare, quindi eseguire una delle procedure indicate di seguito.

    - Per aggiungere un comando, selezionare il pulsante **Aggiungi comando**.

        Nella finestra di dialogo **Aggiungi comando** scegliere un elemento dall'elenco **Categorie**, scegliere un elemento dall'elenco **Comandi** e quindi fare clic sul pulsante **OK**.

        ![Finestra di dialogo Aggiungi comando in Visual Studio](../ide/media/addcommand.png)

    - Per eliminare un comando, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Elimina**.

    - Per riordinare i comandi, selezionarne uno nell'elenco **Controlli** e fare clic sul pulsante **Sposta su** o **Sposta giù**.

    - Per raggruppare i comandi sotto una linea orizzontale, scegliere il primo comando nell'elenco **Controlli**, fare clic sul pulsante **Modifica selezione** e quindi scegliere **Inizia un gruppo** nel menu visualizzato.

## <a name="reset-a-menu-or-a-toolbar"></a>Reimpostare un menu o una barra degli strumenti

1. Sulla barra dei menu scegliere Strumenti  >  **Personalizza.**

    Viene visualizzata la finestra di dialogo **Personalizza**.

2. Nella scheda **Comandi** selezionare il pulsante di opzione per il tipo di elemento che si vuole reimpostare.

3. Nell'elenco del tipo di elemento desiderato selezionare il menu o la barra degli strumenti da reimpostare.

4. Selezionare il pulsante **Modifica selezione** e scegliere **Reimposta** nel menu visualizzato.

    È anche possibile reimpostare tutti i menu e le barre degli strumenti facendo clic sul pulsante **Reimposta tutto**.

## <a name="see-also"></a>Vedi anche

- [Personalizzare l'IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Personalizzare l'editor](../ide/how-to-change-text-case-in-the-editor.md)
