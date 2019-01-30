---
title: Refactoring con estrazione di un'interfaccia
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: fe61ca799b6df00acc34a0579398d612c142c2c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028459"
---
# <a name="extract-an-interface-refactoring"></a>Refactoring con estrazione di un'interfaccia

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di creare un'interfaccia usando membri esistenti da una classe, uno struct o un'interfaccia.

**Quando:** sono disponibili più classi, struct o interfacce con metodi che possono essere resi comuni e usati da altre classi, altri struct o altre interfacce.

**Perché?:** le interfacce sono costrutti ideali per le progettazioni orientate agli oggetti. Si supponga di avere classi per vari animali (Cane, Gatto, Uccello) che potrebbero contenere tutte metodi comuni, come Mangiare, Bere, Dormire. L'uso di un'interfaccia come IAnimali consentirebbe alle classi Cane, Gatto e Uccello di avere una "firma" comune per questi metodi.

## <a name="how-to"></a>Procedura

1. Evidenziare il nome della classe su cui eseguire l'azione oppure posizionare semplicemente il cursore del testo in un punto nel nome della classe.

   - C#:

       ![Codice evidenziato - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/extractinterface-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+I**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.
   - **Mouse**
      - Selezionare **Modifica > Refactoring - Estrai interfaccia**.
      - Fare clic con il pulsante destro del mouse sul nome della classe, scegliere il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.

3. Nella finestra di dialogo **Estrai interfaccia** visualizzata immettere le informazioni richieste:

   ![Estrai interfaccia](media/extractinterface-dialog-cs.png)


   | Campo | Description |
   | - | - |
   | **Nome nuova interfaccia** | Nome dell'interfaccia da creare. Il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Nome nuovo file** | Nome del file che verrà generato e conterrà l'interfaccia. Come per l'interfaccia, il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Seleziona i membri pubblici per l'interfaccia** | Elementi da estrarre nell'interfaccia. È possibile selezionarne il numero desiderato. |


4. Scegliere **OK**.

   L'interfaccia viene creata nel file con il nome specificato. Inoltre, la classe selezionata implementa tale interfaccia.

   - C#:

      ![Classe risultante - C#](media/extractinterface-class-cs.png)![Interfaccia risultante - C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Classe risultante - Visual Basic](media/extractinterface-class-vb.png)![Interfaccia risultante - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)