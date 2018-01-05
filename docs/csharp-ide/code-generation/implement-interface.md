---
title: Implementare un'interfaccia - la generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e0b8df77e82ada8197b89fcdf451e4234a43669f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implement-an-interface-in-c"></a>Implementare un'interfaccia in c# #
**Novità:** consente di generare immediatamente il codice necessario per implementare un'interfaccia. 

**Quando:** che si desidera ereditare da un'interfaccia.  

**Motivo:** è possibile implementare manualmente tutte le interfacce uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme di metodo. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica si è fatto riferimento a un'interfaccia ma non sono implementati tutti i membri obbligatori.

   ![Codice evidenziato](media/interface_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **(in modo esplicito) implementano** nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **(in modo esplicito) implementano** nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima di classe di implementazione](media/interface_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.
   >
   >Inoltre, è possibile utilizzare il **documento**, **progetto**, e **soluzione** collegamenti nella parte inferiore della finestra di anteprima per creare le firme del metodo corretto in più classi che implementano l'interfaccia.

1. Le firme del metodo dell'interfaccia saranno creati automaticamente, pronto per essere implementato.

   ![Implementare il risultato di classe](media/interface_result.png)

   >[!TIP]
   >Utilizzare il **implementare in modo esplicito l'interfaccia** opzione far precedere ogni generato metodo con il nome dell'interfaccia per evitare conflitti di nome.
   >
   >![Implementa interfaccia comportare in modo esplicito](media/interface_explicitresult.png); 

## <a name="see-also"></a>Vedere anche  
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)  
