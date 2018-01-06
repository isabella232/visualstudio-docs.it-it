---
title: Estrai metodo - Refactoring (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 6ec25b8c0e2a583364ff3c6418515507cdc04d40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-visual-basic"></a>Estrarre un metodo in Visual Basic
**Novità:** consente di trasformare un frammento di codice in un metodo.

**Quando:** si dispone di un frammento di codice esistente in un metodo che deve essere chiamato da un altro metodo.  

**Motivo:** è possibile copiare e incollare il codice, ma che potrebbe causare la duplicazione.  Una soluzione migliore consiste nell'effettuare il refactoring di frammento nel relativo metodo che può essere chiamato liberamente da qualsiasi altro metodo.

**Procedura:**

1. Evidenziare il codice da estrarre:

   ![Codice evidenziato](media/extractmethod_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl + R**, quindi **Ctrl + M**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **Estrai metodo** nel popup di finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > eseguire il refactoring > Estrai metodo**.
     * Il codice e scegliere **refactoring > estrarre > Estrai metodo**.
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **Estrai metodo** nel popup di finestra di anteprima.

   Il metodo verrà creato immediatamente.  Da qui, è ora possibile rinominare il metodo semplicemente digitandone il nome del nuovo.

   > [!TIP]
   > È inoltre possibile aggiornare i commenti e altre stringhe da usare il nuovo nome, così come [Anteprima modifiche](../../ide/preview-changes.md) prima del salvataggio, utilizzando le caselle di controllo di **rinominare** casella che viene visualizzata nella parte superiore destra della finestra dell'IDE.

   ![Rinomina (metodo)](media/extractmethod_rename.png)

1. Quando si è soddisfatti della modifica, fare clic su di **applica** o preme **invio** e verranno eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedere anche  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)