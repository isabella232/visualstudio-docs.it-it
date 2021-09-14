---
title: Modificare la firma di un metodo
description: Aggiungere, rimuovere o modificare l'ordine dei parametri di un metodo. Fare clic con il pulsante destro del mouse sul metodo, scegliere Azioni rapide e refactoring e quindi Cambia firma.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6a999635c8e59d8cac2969fe8fd80a98425cdfdf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709423"
---
# <a name="change-a-method-signature-refactoring"></a>Refactoring con modifica della firma di un metodo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rimuovere o modificare l'ordine dei parametri di un metodo.

**Quando:** si vuole spostare o rimuovere un parametro di un metodo usato in varie posizioni.

**Motivo:** è possibile rimuovere e riordinare manualmente i parametri, per poi cercare tutte le chiamate al metodo e modificarle una alla volta, ma si tratta di un processo soggetto a errori.  Questo strumento di refactoring eseguirà l'attività automaticamente.

## <a name="how-to"></a>Procedure

1. Evidenziare o posizionare il cursore del testo all'interno del nome del metodo da modificare o un uno dei relativi utilizzi:

   - C#:

       ![Codice evidenziato C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Codice evidenziato Visual Basic](media/changesignature-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+V**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Cambia firma** dal popup della finestra di anteprima.
   - **Mouse**
      - Selezionare **Modifica > Refactoring > Rimuovi parametri**.
      - Selezionare **Modifica > Refactoring > Riordina parametri**.
      - Fare clic con il pulsante destro del mouse sul codice, scegliere il menu **Azioni rapide e refactoring** e selezionare **Cambia firma** dal popup della finestra di anteprima.

3. Nella finestra di dialogo **Modifica firma** visualizzata è possibile usare i pulsanti a destra per modificare la firma del metodo:

   ![Finestra di dialogo Cambia firma](media/change-signature.png)

   | Pulsante | Descrizione
   | ------ | ---
   | **Su/Giù** | Consente di spostare il parametro selezionato verso l'alto e verso il basso nell'elenco
   | **Aggiungere** | Consente di aggiungere un nuovo parametro all'elenco
   | **Rimuovi** | Consente di rimuovere il parametro selezionato dall'elenco
   | **Restore** | Consente di ripristinare il parametro selezionato e barrato nell'elenco

   > [!TIP]
   > Usare la **casella di controllo Anteprima modifiche di** riferimento per visualizzare il risultato [prima](../../ide/preview-changes.md) di eseguire il commit.

4. Selezionando **Aggiungi** nella finestra **di dialogo Cambia** firma verrà aperta la finestra di dialogo **Aggiungi** parametro. La finestra di dialogo **Aggiungi parametro** consente di aggiungere un nome di tipo e un nome di parametro. È possibile scegliere di rendere il parametro obbligatorio o facoltativo con un valore predefinito. È quindi possibile aggiungere un valore nel sito di chiamata e scegliere un argomento denominato per tale valore oppure è possibile introdurre una variabile TODO. La variabile TODO inserisce un valore TODO nel codice in modo che sia possibile visualizzare ogni errore, esaminare ogni sito di chiamata in modo indipendente e decidere cosa passare. Per i parametri facoltativi è possibile omettere completamente il sito di chiamata.

    ![Finestra di dialogo Aggiungi parametro - C #](media/add-parameter-dialog.png)

5. Al termine dell'aggiunta di un parametro, premere **OK** per visualizzare in anteprima le modifiche.

    ![Finestra di dialogo Cambia firma](media/change-signature.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)