---
title: Estrarre un metodo in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d66a0e41f0c68d3d5c4378a664ef36aba0d869b7
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="extract-a-method-refactoring"></a>Refactoring con estrazione di un metodo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di trasformare un frammento di codice in un metodo.

**Quando:** si dispone di un frammento di codice esistente in un metodo che deve essere chiamato da un altro metodo.

**Perché:** è possibile copiare e incollare il codice, ma ciò potrebbe causare la duplicazione. Una soluzione migliore consiste nell'effettuare il refactoring del frammento nel relativo metodo, che può essere chiamato liberamente da qualsiasi altro metodo.

## <a name="how-to"></a>Procedura

1. Evidenziare il codice da estrarre:

   - C#:

    ![Codice evidenziato - C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato - Visual Basic](media/extractmethod-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+R** e quindi **CTRL+M**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai metodo** dal popup della finestra di anteprima.
   - **Mouse**
     - Selezionare **Modifica > Refactoring - Estrai metodo**.
     - Fare clic con il pulsante destro del mouse sul codice e scegliere **Refactoring > Estrai > Estrai metodo**.
     - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Estrai metodo** dal popup della finestra di anteprima.

   Il metodo verrà creato immediatamente. Da qui, è ora possibile rinominare il metodo semplicemente digitandone il nuovo nome.

   > [!TIP]
   > È anche possibile aggiornare i commenti e altre stringhe per l'uso del nuovo nome, così come [visualizzare in anteprima le modifiche](../../ide/preview-changes.md) prima del salvataggio, usando le caselle di controllo nella finestra di dialogo **Rinomina** visualizzata in alto a destra dell'IDE.

   - C#:

    ![Rinominare il metodo - C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

    ![Rinominare il metodo - Visual Basic](media/extractmethod-rename-vb.png)

1. Quando si è soddisfatti della modifica, scegliere il pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)