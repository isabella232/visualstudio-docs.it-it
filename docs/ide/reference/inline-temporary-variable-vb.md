---
title: Sostituire una variabile temporanea con il relativo valore in Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Variabile temporanea inline in Visual Basic

**Cosa:** consente di rimuovere una variabile temporanea e sostituirla con il relativo valore.

**Quando:** l'uso della variabile temporanea rende più difficile la comprensione del codice.

**Perché:** la rimozione di una variabile temporanea può migliorare la leggibilità del codice.

**Come:**

1. Evidenziare o posizionare il cursore di testo all'interno della variabile temporanea da rendere inline:

   ![Codice evidenziato](media/inline-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring**.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**.

1. Selezionare **Variabile temporanea Inline** dal popup della finestra di anteprima.

   La variabile verrà rimossa e i relativi utilizzi sostituiti immediatamente con il valore della variabile.

   ![Risultato inline](media/inline-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)