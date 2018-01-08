---
title: Refactoring di ridenominazione - (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: da85803adf3de8afa0912a1f47e2b474952df51d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Rinominare un simbolo di codice in Visual Basic
**Novità:** consente di rinominare gli identificatori per i simboli del codice, ad esempio campi, le variabili locali, metodi, gli spazi dei nomi, proprietà e tipi.

**Quando:** che si desidera rinominare un elemento senza la necessità di trovare tutte le istanze, copia e Incolla il nuovo nome.  

**Motivo:** copiando e incollando il nuovo nome in un intero progetto potrebbe causare errori.  Questo strumento refactoring in modo accurato eseguirà l'azione di ridenominazione.

**Procedura:**

1. Evidenziare o posizionare il cursore di testo all'interno dell'elemento da rinominare:

   ![Codice evidenziato](media/rename_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl + R**, quindi **Ctrl + R**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
   * **Mouse**
     * Selezionare **Modifica > eseguire il refactoring > rinominare**.
     * Il codice e scegliere **rinominare**.

1. Rinominare l'elemento semplicemente digitando il nuovo nome.

   ![Rinominare l'animazione](media/rename_rename.png)

   > [!TIP]
   > È inoltre possibile aggiornare i commenti e altre stringhe da usare il nuovo nome, così come [Anteprima modifiche](../../ide/preview-changes.md) prima del salvataggio, utilizzando le caselle di controllo di **rinominare** casella che viene visualizzata nella parte superiore destra della finestra dell'IDE.

1. Quando si è soddisfatti della modifica, fare clic su di **applica** o preme **invio** e verranno eseguito il commit delle modifiche.

> [!NOTE]
> Se si utilizza un nome che esiste già e che potrebbe causare un conflitto, la **rinominare** casella l'IDE visualizzerà un avviso.
>
> ![Conflitto di ridenominazione](media/rename_conflict.png)

## <a name="see-also"></a>Vedere anche  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)