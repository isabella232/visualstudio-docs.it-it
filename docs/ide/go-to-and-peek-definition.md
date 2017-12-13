---
title: Vai a definizione e Visualizza definizione | Microsoft Docs
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 467d119e67db254b6e15630c08c411bb15283351
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-definition-and-peek-definition"></a>Vai a definizione e Visualizza definizione  
Le funzionalità Vai a definizione e Visualizza definizione consentono di visualizzare facilmente la definizione di un tipo o di un membro.

## <a name="go-to-definition"></a>Vai a definizione  
La funzionalità Vai a definizione consente di passare al sorgente di un tipo o di un membro e di aprire il risultato in una nuova scheda. Se si preferisce usare la tastiera, posizionare il cursore di testo in un punto qualsiasi all'interno del simbolo e premere **F12**. Se si preferisce usare il mouse, selezionare **Vai a definizione** dal menu di scelta rapida o usare la funzionalità **Ctrl + clic** descritta di seguito.  

### <a name="ctrl-click-go-to-definition"></a>Vai a definizione con Ctrl+clic  
In Visual Studio 2017 versione 15.4, per gli utenti che preferiscono il mouse è più facile accedere rapidamente alla funzionalità Vai a definizione. Quando si preme **Ctrl** e si passa il puntatore del mouse su un tipo o su un membro, è possibile fare clic sui simboli. Per passare rapidamente alla definizione di un simbolo, premere **Ctrl** e quindi fare clic sul simbolo. È facile!

![Animazione di Vai a definizione con un clic del mouse](../ide/media/click_gotodef.gif)

È possibile cambiare il tasto di modifica per la funzionalità **Vai a definizione** con clic del mouse da **Strumenti**, **Opzioni**, **Editor di testo**, **Generale**. Selezionare quindi **Alt** o **Ctrl + Alt** dall'elenco a discesa **Usa tasto di modifica**. È anche possibile disabilitare la funzionalità **Vai a definizione** con clic del mouse deselezionando la casella di controllo **Abilita clic del mouse per eseguire Vai a definizione**.  

![Abilitazione del clic del mouse per Vai a definizione](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Visualizza definizione
La funzionalità Visualizza definizione consente di visualizzare in anteprima la definizione di un tipo senza abbandonare la posizione corrente nell'editor. Se si preferisce usare la tastiera, posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo o del membro e premere **Alt+F12**. Se si preferisce usare il mouse, è possibile selezionare **Visualizza definizione** dal menu di scelta rapida. In Visual Studio 2017 15.4 e versioni successive è disponibile un nuovo modo per visualizzare in anteprima una definizione tramite il mouse. Prima, passare a **Strumenti**, **Opzioni**, **Editor di testo**, **Generale**. Selezionare l'opzione **Apri definizione in visualizzazione rapida** e fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.  

![Impostazione dell'opzione Visualizza definizione con clic del mouse](../ide/media/editor_options_peek_view.png)  

Premere quindi **Ctrl** (o il tasto di modifica selezionato in **Opzioni**) e fare clic sul tipo o sul membro.  

![Animazione della funzionalità Visualizza definizione](../ide/media/peek_definition.gif)

Se viene visualizza una definizione diversa da quella della finestra popup, è possibile seguire un percorso di navigazione usando i cerchi e le frecce visualizzati sopra la finestra popup.  

Per altre informazioni, vedere [How to: View and Edit Code by Using Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Procedura: Visualizzare e modificare il codice usando la finestra Visualizza definizione (Alt+F12).  

## <a name="see-also"></a>Vedere anche  
[Spostamento nel codice](../ide/navigating-code.md)  
[Procedura: Visualizzare e modificare il codice usando la finestra Visualizza definizione (ALT+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
