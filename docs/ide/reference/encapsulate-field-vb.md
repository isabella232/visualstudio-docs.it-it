---
title: "Effettuare il refactoring di un campo in proprietà in Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 010a297745ed6028f7ee127fffc210097d6d26f5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Incapsulare un campo in Visual Basic

**Cosa:** consente di trasformare un campo in una proprietà e aggiornare tutti gli utilizzi di quel campo per l'uso della nuova proprietà creata.

**Quando:** si vuole spostare un campo in una proprietà e aggiornare tutti i riferimenti a tale campo.  

**Perché:** si vuole consentire l'accesso a un campo ad altre classi, ma non si vuole che tali classi abbiano accesso diretto.  Eseguendo il wrapping del campo in una proprietà, è ad esempio possibile scrivere codice per verificare il valore assegnato.

**Come:**

1. Evidenziare o posizionare il cursore del testo all'interno del nome del campo da incapsulare:

   ![Codice evidenziato](media/encapsulate-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+R** e quindi **CTRL+E**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare la voce **Incapsula campo** dal popup della finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > Refactoring > Incapsula campo**.
     * Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare la voce **Incapsula campo** dal popup della finestra di anteprima.

   Selezione | Descrizione
   --------- | -----------
   **Incapsula i campi (e usa la proprietà)** | Incapsula il campo con una proprietà e aggiorna tutti gli utilizzi del campo per l'uso della proprietà generata
   **Incapsula i campi (ma continua a usarli)** | Incapsula il campo con una proprietà, ma lascia invariati tutti gli utilizzi del campo

   La proprietà verrà creata immediatamente e verranno aggiornati i riferimenti al campo, se selezionato.

   > [!TIP]
   > Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella finestra popup per controllare il risultato in anteprima, prima di eseguire il commit.

   ![Risultato dell'incapsulamento della proprietà](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)