---
title: Generare un costruttore - la generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 9ffa85d768939522935199edde6d0f19b3f2b7a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-c"></a>Generare un costruttore in c# #
**Novità:** consente di generare immediatamente il codice per un nuovo costruttore in una classe. 

**Quando:** si introduce un nuovo costruttore e si desidera correttamente dichiarare automaticamente o si modifica un costruttore esistente. 

**Motivo:** era possibile dichiarare il costruttore prima di utilizzarlo, tuttavia questa funzionalità verrà generato automaticamente, con i parametri appropriati, automaticamente. Inoltre, la modifica di un costruttore esistente, è necessario aggiornare tutti i callsites solo se si utilizza questa funzionalità per l'aggiornamento automatico.

**Procedura:** esistono diversi modi per generare un costruttore:
- [Genera costruttore e selezionare i membri](#pick)
- [Generare un costruttore dai campi selezionati](#selection)
- [Costruttore di generazione dall'utilizzo di nuovi](#usage)
- [Aggiungere un parametro al costruttore esistente](#addparameter)
- [Creare e inizializzare la proprietà o campo da un parametro di costruttore](#create)

## <a id = "pick"></a>Genera costruttore e selezionare i membri
1. Posizionare il cursore in qualsiasi riga vuota in una classe:

   ![Cursore nella riga vuota](media/constructor1_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **genera costruttore...**  nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **genera costruttore...**  nel popup di finestra di anteprima.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo è già sulla riga vuota della classe.

   ![Generare l'anteprima di costruttore](media/constructor1_preview.png)

1. Verrà visualizzata una finestra di dialogo che consente di scegliere i membri che si desidera essere utilizzati come parametri del costruttore nonché ordinarle (con il su e freccia giù). Premere **Ok** per salvare le modifiche.
  
   ![Finestra di dialogo di selezione membri](media/constructor1_dialog.png)

   >[!TIP] 
   >È possibile controllare il **aggiungere i controlli null** casella di controllo per generare automaticamente i controlli null per i parametri del costruttore.

1. Verrà creato il costruttore con parametri selezionati nell'ordine specificato.
   ![Generare il risultato di costruttore](media/constructor1_result.png)

## <a id="selection"></a>Generare un costruttore dai campi selezionati
1. Evidenziare i membri che si desidera rendere il costruttore generato: ![evidenziare i membri](media/constructor2_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **genera costruttore 'TypeName(...)'**  nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **genera costruttore 'TypeName(...)'**  nel popup di finestra di anteprima.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la selezione.

     ![Generare l'anteprima di costruttore](media/constructor2_preview.png)

1. Verrà creato il costruttore con parametri selezionati.
     ![Generare il risultato di costruttore](media/constructor2_result.png)

## <a id="usage"></a>Costruttore di generazione dall'utilizzo di nuovi
1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica è stato usato un costruttore che non esiste ancora.

   ![Codice evidenziato](media/constructor_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu  **genera costruttore '*TypeName*' * * nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu  **genera costruttore '*TypeName*' * * nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima di costruttore](media/constructor_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Verrà creato automaticamente il costruttore con parametri dedotti dal relativo utilizzo.

   ![Generare il risultato di costruttore](media/constructor_result.png)

## <a id="selection"></a>Aggiungere un parametro al costruttore esistente
1. Aggiungere un parametro a un'istanza di oggetto esistente.

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica è stato usato un costruttore che non esiste ancora.
    
    ![Genera costruttore evidenziazione](media/constructor4_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **aggiungere parametro 'TypeName(...)'**  nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **aggiungere parametro 'TypeName(...)'**  nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Generare l'anteprima di costruttore](media/constructor4_preview.png)

1. Il parametro verrà aggiunto automaticamente con il tipo dedotto dal relativo utilizzo.
   
   ![Generare il risultato di costruttore](media/constructor4_result.png)

## <a id="create"></a>Creare e inizializzare la proprietà o campo da un parametro di costruttore
1. Da un costruttore esistente, aggiungere un parametro:

   ![Genera costruttore evidenziazione](media/constructor5_highlight.png)

1. Posizionare il cursore all'interno del parametro appena aggiunto.

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **creare e inizializzare la proprietà 'YourProperty'** o **creare e inizializzare il campo 'YourField'** dal Popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **creare e inizializzare la proprietà 'YourProperty'** o **creare e inizializzare il campo 'YourField'**nel popup di finestra di anteprima.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con il parametro aggiunto.

   ![Generare l'anteprima di costruttore](media/constructor5_preview.png)

1. Il campo o la proprietà verrà creata e assegnato automaticamente un nome per la corrispondenza dei tipi.

   ![Generare il risultato di costruttore](media/constructor5_result.png)
  
## <a name="see-also"></a>Vedere anche  
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)