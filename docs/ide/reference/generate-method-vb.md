---
title: Generare un metodo - Generazione del codice (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 08e46cb961ecd6511f79410a7424969f2db227ed
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-method-in-visual-basic"></a>Generare un metodo in Visual Basic
**Cosa:** consente di aggiungere immediatamente un metodo a una classe. 

**Quando:** si introduce un nuovo metodo e si vuole dichiararlo in modo corretto, automaticamente.  

**Perché:** si potrebbero dichiarare il metodo e i parametri prima dell'uso, tuttavia questa funzionalità genera la dichiarazione automaticamente. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica è stato usato un metodo che non esiste ancora.

   ![Codice evidenziato](media/method-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera il metodo** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera il metodo** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-vb.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-vb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima della generazione del metodo](media/method-preview-vb.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. Il metodo verrà creato automaticamente con gli eventuali parametri dedotti dal relativo utilizzo.

   ![Risultato della generazione del metodo](media/method-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)