---
title: Sostituire una variabile temporanea con il relativo valore in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 836f7b847a2a57de83f6bea7f05bed83571e7485
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="inline-a-temporary-variable-refactoring"></a>Refactoring con variabile temporanea inline

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rimuovere una variabile temporanea e sostituirla con il relativo valore.

**Quando:** l'uso della variabile temporanea rende più difficile la comprensione del codice.

**Perché:** la rimozione di una variabile temporanea può migliorare la leggibilità del codice.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore di testo all'interno della variabile temporanea da rendere inline:

   - C#:

    ![Codice evidenziato - C#](media/inline-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato - Visual Basic](media/inline-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**.

1. Selezionare **Variabile temporanea Inline** dal popup della finestra di anteprima.

   La variabile viene rimossa e i relativi utilizzi sostituiti con il valore della variabile.

   - C#:

    ![Risultato inline - C#](media/inline-result-cs.png)

   - Visual Basic:

    ![Risultato inline - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)