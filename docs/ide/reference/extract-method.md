---
title: Estrarre un metodo
description: Trasformare un frammento di codice nel metodo corrispondente selezionando il codice e immettendo CTRL+R, CTRL+M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 28595d4ed837249385a18b4a60cd12f1713b5640
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101427"
---
# <a name="extract-a-method-refactoring"></a>Refactoring con estrazione di un metodo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di trasformare un frammento di codice in un metodo.

**Quando:** si dispone di un frammento di codice esistente in un metodo che deve essere chiamato da un altro metodo.

**Perché:** è possibile copiare e incollare il codice, ma ciò potrebbe causare la duplicazione. Una soluzione migliore consiste nell'effettuare il refactoring del frammento nel relativo metodo, che può essere chiamato liberamente da qualsiasi altro metodo.

## <a name="how-to"></a>Procedure

1. Evidenziare il codice da estrarre:

   - C#:

       ![Screenshot che mostra il codice C# per la classe Program. Nella funzione Main di tale classe è evidenziata una riga di codice.](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Screenshot che Visual Basic codice per main sub. In sub viene evidenziata una riga di codice.](media/extractmethod-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+M**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai metodo** dal popup della finestra di anteprima.
   - **Mouse**
      - Selezionare **Modifica > Refactoring - Estrai metodo**.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere **Refactoring > Estrai > Estrai metodo**.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Estrai metodo** dal popup della finestra di anteprima.

   Il metodo verrà creato immediatamente. Da qui, è ora possibile rinominare il metodo semplicemente digitandone il nuovo nome.

   > [!TIP]
   > È anche possibile aggiornare i commenti e altre stringhe per l'uso del nuovo nome, così come [visualizzare in anteprima le modifiche](../../ide/preview-changes.md) prima del salvataggio, usando le caselle di controllo nella finestra di dialogo **Rinomina** visualizzata in alto a destra dell'IDE.

   - C#:

      ![Screenshot che mostra il codice C# per la classe Program. Un nome di metodo è evidenziato e la finestra popup Rinomina è aperta.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Screenshot che Visual Basic codice per main sub. Un nome di metodo è evidenziato e la finestra popup Rinomina è aperta.](media/extractmethod-rename-vb.png)

3. Quando si è soddisfatti della modifica, scegliere il pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
