---
title: Estrarre un metodo
description: Trasformare un frammento di codice nel metodo corrispondente selezionando il codice e immettendo CTRL+R, CTRL+M.
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a764fd0d95696866e914ec76a560a49d641acb47
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483663"
---
# <a name="extract-a-method-refactoring"></a>Refactoring con estrazione di un metodo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di trasformare un frammento di codice in un metodo.

**Quando:** si dispone di un frammento di codice esistente in un metodo che deve essere chiamato da un altro metodo.

**Perché?:** è possibile copiare e incollare il codice, ma ciò potrebbe causarne la duplicazione. Una soluzione migliore consiste nell'effettuare il refactoring del frammento nel relativo metodo, che può essere chiamato liberamente da qualsiasi altro metodo.

## <a name="how-to"></a>Procedura

1. Evidenziare il codice da estrarre:

   - C#:

       ![Codice evidenziato - C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/extractmethod-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+M**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai metodo** dal popup della finestra di anteprima.
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

3. Quando si è soddisfatti della modifica, scegliere il pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)