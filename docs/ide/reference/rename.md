---
title: Refactoring con ridenominazione
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48e45373c41358ba3e9c2d70222ace07cdf1b59e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925524"
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactoring con ridenominazione di un simbolo di codice

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rinominare gli identificatori per i simboli del codice, ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi.

**Quando:** si vuole rinominare un elemento in modo sicuro senza dover trovare tutte le istanze e copiare/incollare il nuovo nome.

**Perché?:** è probabile che copiare e incollare il nuovo nome in un intero progetto causi errori. Questo strumento di refactoring eseguirà in modo accurato l'azione di ridenominazione.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore del testo all'interno dell'elemento da rinominare:

   - C#:

       ![Codice evidenziato - C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/rename-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+R**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
   - **Mouse**
      - Selezionare **Modifica > Refactoring > Rinomina**.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere **Rinomina**.

3. Rinominare l'elemento semplicemente digitando il nuovo nome.

   - C#:

      ![Animazione della ridenominazione - C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Ridenominazione - VB](media/rename-rename-vb.png)

   > [!TIP]
   > È anche possibile aggiornare i commenti e altre stringhe per l'uso del nuovo nome e [visualizzare in anteprima le modifiche](../../ide/preview-changes.md) prima del salvataggio usando le caselle di controllo della finestra di dialogo **Rinomina** visualizzata in alto a destra nell'editor.

4. Quando si è soddisfatti della modifica, scegliere il pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

> [!NOTE]
> Se si usa un nome già esistente che causerebbe un conflitto, nella finestra di dialogo **Rinomina** verrà visualizzato un avviso.
>
> ![Conflitto di ridenominazione](media/rename-conflict-cs.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
