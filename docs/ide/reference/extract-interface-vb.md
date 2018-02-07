---
title: Estrarre un'interfaccia in Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 98a3a96357eb6e7391eb92bd0ac3a53dd00f09f5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="extract-an-interface-in-visual-basic"></a>Estrarre un'interfaccia in Visual Basic

**Novità:** consente di creare un'interfaccia usando membri esistenti da una classe, uno struct o un'interfaccia.

**Quando:** sono disponibili più classi, struct o interfacce con metodi che potrebbero essere resi comuni e usati da altre classi, altri struct o altre interfacce.

**Perché:** le interfacce sono costrutti ideali per le progettazioni orientate agli oggetti.  Si supponga di avere classi per vari animali (Cane, Gatto, Uccello) che potrebbero contenere tutte metodi comuni, come Mangiare, Bere, Dormire.  L'uso di un'interfaccia come IAnimali consentirebbe alle classi Cane, Gatto e Uccello di avere una "firma" comune per questi metodi.  

**Come:**

1. Evidenziare il nome della classe su cui eseguire l'azione oppure posizionare semplicemente il cursore del testo in un punto nel nome della classe.

   ![Codice evidenziato](media/extractinterface-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+R** e quindi **CTRL+I**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > Refactoring - Estrai interfaccia**.
     * Fare clic con il pulsante destro del mouse sul nome della classe, scegliere il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.

1. Nella finestra di dialogo **Estrai interfaccia** visualizzata immettere le informazioni richieste: ![Estrai interfaccia](media/extractinterface-dialog-vb.png)
   | Campo | Descrizione |
   | --- | --- |
   | **Nome nuova interfaccia** | Nome dell'interfaccia da creare. Il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Nome nuovo file** | Nome del file che verrà generato e conterrà l'interfaccia. Come per l'interfaccia, il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Seleziona i membri pubblici per l'interfaccia** | Elementi da estrarre nell'interfaccia.  È possibile selezionarne il numero desiderato. |

1. Fare clic su **OK**.

   L'interfaccia verrà creata immediatamente nel file con il nome specificato.  Inoltre, la classe selezionata implementerà ora tale interfaccia.

   ![Classe risultante](media/extractinterface-class-vb.png)
   ![Interfaccia risultante](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)