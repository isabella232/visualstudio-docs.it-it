---
title: Effettuare il refactoring di un campo in una proprietà
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6cb74b64ec03c865ca4e6e52fa3922c997468d6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049931"
---
# <a name="encapsulate-a-field-refactoring"></a>Refactoring Incapsula campo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di trasformare un campo in una proprietà e aggiornare tutti gli utilizzi di quel campo per l'uso della proprietà appena creata.

**Quando:** si vuole spostare un campo in una proprietà e aggiornare tutti i riferimenti al campo.

**Perché:** si vuole consentire ad altre classi di accedere a un campo, ma non si vuole che queste classi abbiano accesso diretto.  Eseguendo il wrapping del campo in una proprietà, è ad esempio possibile scrivere codice per verificare il valore assegnato.

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