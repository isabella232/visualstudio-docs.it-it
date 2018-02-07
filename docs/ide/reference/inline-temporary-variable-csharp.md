---
title: Sostituire una variabile temporanea con il relativo valore in C# | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>Variabile temporanea inline con C# #

**Cosa:** consente di rimuovere una variabile temporanea e sostituirla con il relativo valore.

**Quando:** l'uso della variabile temporanea rende più difficile la comprensione del codice.

**Perché:** la rimozione di una variabile temporanea può migliorare la leggibilità del codice.

**Come:**

1. Evidenziare o posizionare il cursore di testo all'interno della variabile temporanea da rendere inline:

   ![Codice evidenziato](media/inline-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring**.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**.

1. Selezionare **Variabile temporanea Inline** dal popup della finestra di anteprima.

   La variabile verrà rimossa e i relativi utilizzi sostituiti immediatamente con il valore della variabile.

   ![Risultato inline](media/inline-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)