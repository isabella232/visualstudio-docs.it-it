---
title: Refactoring Estrai interfaccia - (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 55e17f0a-eacb-41ec-b8ca-74f5c6bbd6de
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 8123154159e34597c0c76e941cd2db5824c9478e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extract-an-interface-in-c"></a>Estrarre un'interfaccia in c# #
**Novità:** consente di creare un'interfaccia usando membri esistenti da una classe, struct o interfaccia.

**Quando:** si dispone di più classi, strutture o interfacce con metodi che potrebbero essere comuni e utilizzato da altre classi, strutture o interfacce.

**Motivo:** interfacce sono costrutti ideale per le progettazioni orientata agli oggetti.  Si supponga la disponibilità delle classi per vari animali (Cat, cane volatile) che contenga tutti i metodi comuni, ad esempio Eat, bevande, sospensione.  Utilizzando un'interfaccia come IAnimal consentirebbe Dog Cat e immagini da hanno una comune "firma" per questi metodi.  

**Procedura:**

1. Evidenziare il nome della classe per eseguire l'azione su, o inserire il cursore di testo in un punto nel nome della classe.

   ![Codice evidenziato](media/extractinterface_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl + R**, quindi **Ctrl + I**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **Estrai interfaccia** nel popup di finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > eseguire il refactoring > Estrai interfaccia**.
     * Fare doppio clic sul nome della classe, seleziona il **azioni rapide e refactoring** dal menu **Estrai interfaccia** nel popup di finestra di anteprima.

1. Nel **Estrai interfaccia** la finestra di dialogo visualizzata, immettere le informazioni frequenti: ![Estrai interfaccia](media/extractinterface_dialog.png)
   | Campo | Descrizione |
   | --- | --- |
   | **Nome della nuova interfaccia** | Il nome dell'interfaccia da creare. Questa impostazione predefinita è*ClassName*, dove *ClassName* è il nome della classe selezionati in precedenza. |
   | **Nuovo nome di file** | Il nome del file che verrà generata che conterrà l'interfaccia. Come con il nome dell'interfaccia, si utilizzerà per impostazione predefinita è*ClassName*, dove *ClassName* è il nome della classe selezionati in precedenza. |
   | **Selezionare i membri pubblici per l'interfaccia** | Elementi da estrarre nell'interfaccia.  È possibile selezionare un numero che si desidera. |

1. Fare clic su **OK**.

   L'interfaccia verrà creato immediatamente nel file del nome specificato.  Inoltre, la classe selezionata verrà ora implementare tale interfaccia.

   ![Classe risultante](media/extractinterface_class.png)
   ![interfaccia risultante](media/extractinterface_interface.png)

## <a name="see-also"></a>Vedere anche  
[Refactoring (C#)](../refactoring-csharp.md)