---
title: Refactoring Incapsula campo - (c#) | Documenti Microsoft
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 59b71a0716415dcedeab9954486ef27e0fc438d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-a-field-in-c"></a>Incapsula un campo in c# #
**Novità:** consente di trasformare un campo in una proprietà e aggiornare tutti gli utilizzi di quel campo, utilizzare la proprietà appena creata.

**Quando:** che si desidera spostare un campo in una proprietà e aggiornare tutti i riferimenti a tale campo.  

**Motivo:** si desidera accedere altre classi a un campo, ma non le classi di avere accesso diretto.  Eseguendo il wrapping di campo in una proprietà, è possibile scrivere codice per verificare il valore assegnato, ad esempio.

**Procedura:**

1. Evidenziare o posizionare il cursore di testo all'interno del nome del campo da incapsulare:

   ![Codice evidenziato](media/encapsulate_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl + R**, quindi **Ctrl + E**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** menu e selezionare **Incapsula campo** voce nel popup di finestra di anteprima.
   * **Mouse**
     * Selezionare **Modifica > eseguire il refactoring > Incapsula campo**.
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** menu e selezionare **Incapsula campo** voce nel popup di finestra di anteprima.

   Selection | Descrizione
   --------- | -----------
   **Incapsula campo (e Usa la proprietà)** | Incapsula il campo con una proprietà e aggiorna tutti gli utilizzi del campo da utilizzare la proprietà generata
   **Incapsula campo (ma continua a usarli)** | Incapsula il campo con una proprietà, ma lascia invariati tutti gli utilizzi del campo

   La proprietà verrà creata immediatamente e verranno aggiornati i riferimenti al campo, se selezionato.

   > [!TIP]
   > Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella finestra popup per vedere ciò che il risultato sarà prima di eseguire il commit a esso.

   ![Risultato della proprietà di incapsulare](media/encapsulate_result.png)

## <a name="see-also"></a>Vedere anche  
[Refactoring (C#)](../refactoring-csharp.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)