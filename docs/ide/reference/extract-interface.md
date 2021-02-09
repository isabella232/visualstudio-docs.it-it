---
title: Refactoring con estrazione di un'interfaccia
description: Informazioni su come usare il menu azioni rapide e refactoring per creare un'interfaccia usando i membri esistenti di una classe, uno struct o un'interfaccia.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 12db627bde45d11950e661d258c9891b8e935ba1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861036"
---
# <a name="extract-an-interface-refactoring"></a>Refactoring con estrazione di un'interfaccia

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di creare un'interfaccia usando i membri esistenti di una classe, uno struct o un'interfaccia.

**Quando:** Sono presenti membri in una classe, uno struct o un'interfaccia che può essere ereditata da altre classi, struct o interfacce.

**Perché:** le interfacce sono costrutti ideali per le progettazioni orientate agli oggetti. Si supponga di avere classi per vari animali (Cane, Gatto, Uccello) che potrebbero contenere tutte metodi comuni, come Mangiare, Bere, Dormire. L'uso di un'interfaccia come IAnimali consentirebbe alle classi Cane, Gatto e Uccello di avere una "firma" comune per questi metodi.

## <a name="extract-an-interface-refactoring"></a>Refactoring con estrazione di un'interfaccia

1. Posizionare il cursore nel nome della classe.

   - C#:

       ![Codice evidenziato - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/extractinterface-highlight-vb.png)

2. Eseguire quindi una delle azioni seguenti:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+I**. I tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
      - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.
   - **Mouse**
      - Selezionare **Modifica > Refactoring - Estrai interfaccia**.
      - Fare clic con il pulsante destro del mouse sul nome della classe, scegliere il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.

3. Nella finestra di dialogo **Estrai interfaccia** visualizzata immettere le informazioni richieste:

   ![Estrai interfaccia](media/extractinterface-dialog-same-file.png)

   | Campo | Descrizione |
   | - | - |
   | **Nome nuova interfaccia** | Nome dell'interfaccia da creare. Il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Nome nuovo file** | Nome del file generato che conterrà l'interfaccia. Come per l'interfaccia, il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. È anche possibile selezionare l'opzione **Add to current file** (Aggiungi al file corrente). |
   | **Seleziona i membri pubblici per l'interfaccia** | Elementi da estrarre nell'interfaccia. È possibile selezionarne il numero desiderato. |

4. Scegliere **OK**.

   L'interfaccia viene creata nel file con il nome specificato. Inoltre, la classe selezionata implementa tale interfaccia.

   - C#:

      ![Classe risultante - C#](media/extractinterface-class-cs.png)

      ![Interfaccia risultante - C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Classe risultante - Visual Basic](media/extractinterface-class-vb.png)

      ![Interfaccia risultante - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
