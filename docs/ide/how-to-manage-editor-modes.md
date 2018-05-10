---
title: Modalità schermo intero e modalità Spazio virtuale di Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94bc99bf70340ef76639d0ae0f05e1f7737173a2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-editor-modes"></a>Procedura: Gestire le modalità dell'editor

È possibile visualizzare l'editor di codice di Visual Studio in diverse modalità.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti in questo articolo, a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, ad esempio per implementare le impostazioni **Generali** o **Visual C++**, scegliere **Strumenti** > **Importa/Esporta impostazioni** e quindi scegliere **Reimposta tutte le impostazioni**.

## <a name="enable-full-screen-mode"></a>Abilitare la modalità Schermo intero

È possibile nascondere tutte le caselle degli strumenti e visualizzare solo le finestre dei documenti abilitando la modalità **Schermo intero**.

-   Premere **ALT**+**MAIUSC**+**INVIO** per attivare o disattivare la modalità **schermo intero**.

     --oppure--

-   Eseguire il comando `View.Fullscreen` nella finestra **Comando**.

## <a name="enable-virtual-space-mode"></a>Abilitare la modalità Spazio virtuale

Nella modalità **Spazio virtuale** vengono inseriti spazi alla fine di ogni riga di codice. Selezionare questa opzione per inserire commenti in corrispondenza di un punto coerente accanto al codice.

1.  Scegliere **Opzioni** dal menu **Strumenti**.

2.  Espandere la cartella **Editor di testo** e scegliere **Tutti i linguaggi** per impostare l'opzione a livello globale oppure scegliere la cartella di un linguaggio specifico. Ad esempio, per attivare i numeri di riga solo in Visual Basic, scegliere il nodo **Basic** > **Editor di testo**.

3.  Selezionare **Generale** e in **Impostazioni**selezionare **Attiva spazio virtuale**.

    > [!NOTE]
    > L'opzione **Spazio virtuale** è abilitata nella modalità **Seleziona colonne**. Quando la modalità **Spazio virtuale** non è abilitata, il punto di inserimento passa dalla fine di una riga direttamente al primo carattere della riga successiva.

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'editor](../ide/customizing-the-editor.md)
- [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)