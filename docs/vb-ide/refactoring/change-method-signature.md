---
title: Firma del metodo di modifica - Refactoring (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 64b37bca-92b8-4154-9d65-54073e5740fc
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: ac0b8394f71f2f7949cf21b4ea34eba733bf4d34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-visual-basic"></a>Modifica di una firma di metodo in Visual Basic
**Novità:** consente di rimuovere o modificare l'ordine dei parametri del metodo.

**Quando:** che si desidera spostare o rimuovere un parametro del metodo utilizzato in varie posizioni.  

**Motivo:** è Impossibile manualmente rimuovere e riordinare i parametri, quindi trovare tutte le chiamate al metodo e modificarle uno alla volta, ma che potrebbe causare errori.  Questo strumento refactoring eseguirà automaticamente l'attività.

**Procedura:**

1. Evidenziare o posizionare il cursore di testo all'interno del nome del metodo per modificare o uno dei relativi utilizzi:

   ![Codice evidenziato](media/changesignature_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl + R**, quindi **Ctrl + V**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **modifica della firma** nel popup di finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > eseguire il refactoring > rimuovere i parametri**.
     * Selezionare **Modifica > eseguire il refactoring > Riordina parametri**.
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **modifica della firma** nel popup di finestra di anteprima.

1. Nel **modificare firma** finestra di dialogo visualizzata, è possibile utilizzare i pulsanti a destra per modificare la firma del metodo:

   ![Finestra di dialogo Cambia firma](media/changesignature_dialog.png)

   | Button | Descrizione
   | ------ | ---
   | **Su/giù** | Spostare il parametro selezionato su e giù nell'elenco
   | **Rimuovi**  | Rimuovere il parametro selezionato dall'elenco
   | **Recupera** | Ripristinare il parametro selezionato, barrati all'elenco

   > [!TIP]
   > Utilizzare il [ **Anteprima modifiche riferimento** ](../../ide/preview-changes.md) casella di controllo per vedere ciò che il risultato sarà prima di eseguire il commit a esso.

1. Al termine, premere il **OK** pulsante per apportare le modifiche.

   ![Risultato della modifica della firma](media/changesignature_result.png)

## <a name="see-also"></a>Vedere anche  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)