---
title: Generare un costruttore - Generazione del codice (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 891a33b74927d45434c4614dc4c5d7f1533ba4c0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-constructor-in-visual-basic"></a>Generare un costruttore in Visual Basic
**Cosa:** consente di generare immediatamente il codice per un nuovo costruttore in una classe. 

**Quando:** si introduce un nuovo costruttore e si vuole dichiararlo in modo corretto, automaticamente.  

**Perché:** si potrebbe dichiarare il costruttore prima di usarlo, tuttavia questa funzionalità consente di generarlo automaticamente, con i parametri appropriati. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato usato un costruttore che non esiste ancora.

   ![Codice evidenziato](media/constructor-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera il costruttore in '*NomeTipo*'** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera il costruttore in '*NomeTipo*'** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-vb.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-vb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima della generazione di un costruttore](media/constructor-preview-vb.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. Il costruttore verrà creato automaticamente con gli eventuali parametri dedotti dal relativo utilizzo.

   ![Risultato della generazione del costruttore](media/constructor-result-vb.png)
 
## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)