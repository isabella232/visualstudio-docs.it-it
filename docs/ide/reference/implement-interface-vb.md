---
title: Implementare un'interfaccia - Generazione del codice (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>Implementare un'interfaccia in Visual Basic
**Cosa:** consente di generare immediatamente il codice necessario per implementare un'interfaccia. 

**Quando:** si vuole ereditare da un'interfaccia.  

**Perché:** è possibile implementare manualmente tutte le interfacce, una alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato aggiunto un riferimento a un'interfaccia, ma che non sono stati implementati tutti i membri obbligatori.

   ![Codice evidenziato](media/interface-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Implementa l'interfaccia in modo esplicito** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Implementa l'interfaccia in modo esplicito** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-vb.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-vb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima dell'implementazione della classe](media/interface-preview-vb.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.
   >
   >Inoltre, è possibile usare i collegamenti **Documento**, **Progetto** e **Soluzione** nella parte inferiore della finestra di anteprima per creare le firme dei metodi appropriate per più classi che implementano l'interfaccia.

1. Le firme del metodo dell'interfaccia verranno create automaticamente, pronte per l'implementazione.

   ![Risultato dell'implementazione della classe](media/interface-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)