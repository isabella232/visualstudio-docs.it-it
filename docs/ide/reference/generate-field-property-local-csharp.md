---
title: "Generare un campo, una proprietà o un elemento locale - Generazione del codice (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 7cc27d498cbc082ad76d47d2326d1ee8fb0ebbb0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-field-property-or-local-in-c"></a>Generare un campo, una proprietà o un elemento locale in C# #
**Cosa:** consente di generare immediatamente il codice per un campo, una proprietà o un elemento locale non dichiarato in precedenza. 

**Quando:** si introduce un nuovo campo, proprietà o elemento locale durante la digitazione e si vuole dichiararlo in modo corretto, automaticamente.  

**Perché:** si potrebbe dichiarare il campo, la proprietà o l'elemento locale prima dell'uso, tuttavia questa funzionalità genera la dichiarazione e il tipo automaticamente. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica l'uso di un campo, una proprietà o un elemento locale che non esiste ancora.

   ![Codice evidenziato](media/field-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera il campo/la proprietà/l'elemento locale** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera il campo/la proprietà/l'elemento locale** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima della generazione di campo/proprietà/elemento locale](media/field-preview-cs.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. Il campo, la proprietà o l'elemento locale verrà creato automaticamente con il tipo dedotto dal relativo utilizzo.

   ![Risultato della generazione di campo/proprietà/elemento locale](media/field-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
