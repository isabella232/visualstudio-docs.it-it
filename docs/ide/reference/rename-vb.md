---
title: Refactoring con ridenominazione in Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f9421ed314dc513d5e8af30bad907766342300a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Rinominare un simbolo del codice in Visual Basic

**Cosa:** consente di rinominare gli identificatori per i simboli del codice, ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi.

**Quando:** si vuole rinominare un elemento in modo sicuro senza dover trovare tutte le istanze e copiare/incollare il nuovo nome.

**Perché:** è probabile che copiare e incollare il nuovo nome in un intero progetto causi errori.  Questo strumento di refactoring eseguirà in modo accurato l'azione di ridenominazione.

**Come:**

1. Evidenziare o posizionare il cursore del testo all'interno dell'elemento da rinominare:

   ![Codice evidenziato](media/rename-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+R** e quindi **CTRL+R**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
   * **Mouse**
     * Selezionare **Modifica > Refactoring > Rinomina**.
     * Fare clic con il pulsante destro del mouse sul codice e scegliere **Rinomina**.

1. Rinominare l'elemento semplicemente digitando il nuovo nome.

   ![Animazione della ridenominazione](media/rename-rename-vb.png)

   > [!TIP]
   > È anche possibile aggiornare i commenti e altre stringhe per l'uso del nuovo nome, così come [visualizzare in anteprima le modifiche](../../ide/preview-changes.md) prima del salvataggio, usando le caselle di controllo nella finestra di dialogo **Rinomina** visualizzata in alto a destra dell'IDE.

1. Quando si è soddisfatti della modifica, fare clic sul pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

> [!NOTE]
> Se si usa un nome già esistente che causerebbe un conflitto, nella finestra di dialogo **Rinomina** nell'IDE verrà visualizzato un avviso.
>
> ![Conflitto di ridenominazione](media/rename-conflict-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)