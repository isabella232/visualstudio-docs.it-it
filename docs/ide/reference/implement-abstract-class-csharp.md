---
title: Implementare una classe astratta - Generazione del codice (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-abstract-class-in-c"></a>Implementare una classe astratta in C# #
**Cosa:** consente di generare immediatamente il codice necessario per implementare una classe astratta. 

**Quando:** si vuole ereditare da una classe astratta.  

**Perché:** è possibile implementare manualmente tutti i membri astratti, uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica l'ereditarietà da una classe astratta, ma che non sono stati implementati tutti i membri obbligatori.

   ![Codice evidenziato](media/abstract-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Implementa classe astratta** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Implementa classe astratta** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima dell'implementazione della classe](media/abstract-preview-cs.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.
   >
   >Inoltre, è possibile usare i collegamenti **Documento**, **Progetto** e **Soluzione** nella parte inferiore della finestra di anteprima per creare le firme dei metodi appropriate per più classi che ereditano dalla classe astratta.

1. Le firme del metodo astratto verranno create automaticamente, pronte per l'implementazione.

   ![Risultato dell'implementazione della classe](media/abstract-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
