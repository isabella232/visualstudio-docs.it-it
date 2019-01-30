---
title: Introdurre una variabile locale
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2fcd6032879dc8e218aa782d27a34250982fb7c3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961949"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introdurre una variabile locale in Visual Studiio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente una variabile locale per sostituire un'espressione esistente.

**Quando:** si dispone di codice che potrebbe essere facilmente riutilizzato in seguito se fosse in una variabile locale.

**Perché?:** è possibile copiare e incollare il codice più volte per usarlo in vari punti, ma è preferibile eseguire l'operazione una sola volta, archiviare il risultato in una variabile locale e usare poi quest'ultima.

## <a name="how-to"></a>Procedura

1. Evidenziare l'espressione che si vuole assegnare a una nuova variabile locale.

   - C#:

       ![Codice evidenziato C#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/local-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima di Introduce l'elemento locale](media/local-preview-cs.png)

3. Scegliere **Introduce la variabile locale per tutte le occorrenze di '*espressione*'** dal menu a discesa.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

   La variabile locale viene creata con il tipo dedotto dal relativo utilizzo. Assegnare alla nuova variabile locale un nuovo nome.

   - C#:

       ![Risultato di implementazione dell'interfaccia C#](media/local-result-cs.png)

   - Visual Basic:

       ![Risultato di implementazione dell'interfaccia VB](media/local-result-vb.png)

   > [!NOTE]
   > È possibile usare l'opzione di menu **....tutte le occorrenze di...** per sostituire ogni istanza dell'espressione selezionata e non solo quella evidenziata in modo specifico.

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)