---
title: Spostare tipo di file corrispondente - Refactoring (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0b3fd-d1d9-4e3f-b0f6-9f8ffbbc6297
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 862c144c2319f6247a9fd38d7f71036a4ba090a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Tipo di spostamento in un file corrispondente in Visual Basic
**Novità:** consente di spostare il tipo selezionato in un file distinto con lo stesso nome.

**Quando:** sono presenti più classi, struct, interfacce, e così via. allo stesso file che si desidera separare.  

**Motivo:** inserimento di più tipi nello stesso file può rendere difficile l'individuazione di questi tipi.  Spostando i tipi di file con lo stesso nome, codice diventa più leggibile e di facilitare la navigazione.

**Procedura:**

1. Evidenziare o posizionare il cursore di testo all'interno del nome del tipo di spostamento:

   ![Codice evidenziato](media/movetype_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **spostare tipo *TypeName*vb** nel popup di finestra di anteprima, in cui *TypeName* è il nome del tipo selezionato.
   * **Mouse**
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **spostare tipo *TypeName*vb** nel popup di finestra di anteprima, in cui  *TypeName* è il nome del tipo selezionato.

   Il tipo verrà immediatamente spostato in un nuovo file con tale nome all'interno della soluzione.

   ![Risultato inline](media/movetype_result.png)

## <a name="see-also"></a>Vedere anche
[Refactoring (Visual Basic)](../refactoring-vb.md)