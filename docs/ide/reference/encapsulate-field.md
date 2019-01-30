---
title: Effettuare il refactoring di un campo in una proprietà
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4b0ccda198cede5f7f4f3094605043eec4defba2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932246"
---
# <a name="encapsulate-a-field-refactoring"></a>Refactoring Incapsula campo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di trasformare un campo in una proprietà e aggiornare tutti gli utilizzi di quel campo per l'uso della proprietà appena creata.

**Quando:** si vuole spostare un campo in una proprietà e aggiornare tutti i riferimenti al campo.

**Perché?:** si vuole consentire ad altre classi di accedere a un campo, ma non si vuole che queste classi abbiano accesso diretto.  Eseguendo il wrapping del campo in una proprietà, è ad esempio possibile scrivere codice per verificare il valore assegnato.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore del testo all'interno del nome del campo da incapsulare:

   - C#:

       ![Codice evidenziato - C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/encapsulate-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+E**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare la voce **Incapsula campo** dal popup della finestra di anteprima.
   - **Mouse**
      - Selezionare **Modifica > Refactoring > Incapsula campo**.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare la voce **Incapsula campo** dal popup della finestra di anteprima.

   Selection | Description
   --------- | -----------
   **Incapsula i campi (e usa la proprietà)** | Incapsula il campo con una proprietà e aggiorna tutti gli utilizzi del campo per l'uso della proprietà generata
   **Incapsula i campi (ma continua a usarli)** | Incapsula il campo con una proprietà, ma lascia invariati tutti gli utilizzi del campo

   La proprietà viene creata e vengono aggiornati i riferimenti al campo, se selezionato.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella finestra popup [per controllare il risultato in anteprima](../../ide/preview-changes.md) prima di eseguire il commit.

   - C#:

      ![Risultato dell'incapsulamento della proprietà - C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Risultato dell'incapsulamento della proprietà - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)