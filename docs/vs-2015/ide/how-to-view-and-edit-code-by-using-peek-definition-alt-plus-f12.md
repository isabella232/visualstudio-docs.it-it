---
title: 'Procedura: Visualizzare e modificare il codice usando Visualizza definizione (ALT+F12) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24db36d6bb3a431d5ee3848eb8a6a794980f919a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777303"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Procedura: visualizzare e modificare il codice utilizzando la finestra Visualizza definizione (ALT+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare il comando **Visualizza definizione** per visualizzare e modificare il codice senza uscire dal codice in fase di scrittura. **Visualizza definizione** e **Vai a definizione** visualizzano le stesse informazioni, ma **Visualizza definizione** mostra il codice in una finestra popup e **Vai a definizione** mostra il codice in una finestra separata. **Vai a definizione** determina il passaggio del contesto (ovvero la finestra di codice attiva, la riga corrente e la posizione del cursore) alla finestra del codice della definizione. Tramite **Visualizza definizione** è possibile visualizzare e modificare la definizione e spostarsi all'interno del file di definizione, mantenendo la stessa posizione nel file di codice originale.  
  
 È possibile usare **Visualizza definizione** con codice C#, Visual Basic e C++. In Visual Basic **Visualizza definizione** contiene un collegamento a **Visualizzatore oggetti** per i simboli sprovvisti di metadati di definizione, ad esempio tipi .NET Framework predefiniti.  
  
> [!IMPORTANT]
>  Non è possibile utilizzare questo comando nelle versioni Express di Visual Studio 2013.  
  
## <a name="working-with-peek-definition"></a>Utilizzo di Visualizza definizione  
  
#### <a name="to-open-a-peek-definition-window"></a>Per aprire una finestra Visualizza definizione  
  
1.  Per trovare **Visualizza definizione**, aprire il menu di scelta rapida per il metodo che si vuole esplorare. Tastiera: ALT+F12.  
  
     Questa illustrazione mostra la finestra **Visualizza definizione** per un metodo denominato `Print()`:  
  
     ![Finestra di visualizzazione](../ide/media/peekwindow.png "PeekWindow")  
  
     La finestra di definizione appare sotto la riga `printer.Print(“Hello World!”)` nel file originale. La finestra non nasconde alcuna sezione di codice nel file originale. Le righe che seguono la chiamata `printer.Print(“Hello World!”)` vengono visualizzate al di sotto della finestra di definizione.  
  
2.  È possibile spostare il cursore in posizioni diverse all'interno della finestra di definizione del codice. È comunque possibile spostarsi nella finestra del codice originale al di sopra o al di sotto della finestra di definizione.  
  
3.  È possibile copiare una stringa dalla finestra di definizione e incollarla nel codice originale. È inoltre possibile trascinare e rilasciare la stringa dalla finestra di definizione nel codice originale senza eliminarla dalla finestra di definizione.  
  
4.  È possibile chiudere la finestra di definizione usando ESC o il pulsante **Chiudi** nella scheda della finestra di definizione.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Per aprire una finestra Visualizza definizione all'interno di una finestra Visualizza definizione  
  
-   Se è già aperta una finestra **Visualizza definizione**, è possibile chiamare di nuovo **Visualizza definizione** per il codice in tale finestra. Verrà visualizzata un'altra finestra di definizione. Accanto alla scheda della finestra di definizione verrà visualizzato un set di punti di navigazione, che è possibile utilizzare per spostarsi tra le finestre di definizione. La descrizione comando in ciascun punto indica il nome e il percorso del file di definizione rappresentato dal punto.  
  
     ![Finestra di visualizzazione all'interno di una finestra di visualizzazione](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Per utilizzare Visualizza definizione con più risultati  
  
-   Se si usa **Visualizza definizione** per codice con più definizioni, ad esempio codice di classi parziali, a destra della visualizzazione della definizione del codice viene visualizzato un elenco di risultati. È possibile scegliere qualsiasi risultato nell'elenco per visualizzarne la definizione.  
  
     ![Finestra di visualizzazione con più risultati](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Per apportare modifiche all'interno della finestra Visualizza Definizione  
  
-   All'avvio del processo di modifica all'interno di una finestra **Visualizza definizione**, il file sottoposto a modifiche viene visualizzato automaticamente sotto forma di scheda separata nell'editor di codice e riflette le modifiche già apportate. È possibile continuare ad apportare, annullare e salvare modifiche nella finestra **Visualizza definizione**. La scheda continuerà a riflettere tali modifiche. Anche se si chiude la finestra senza salvare le modifiche, è possibile apportare, annullare e salvare altre modifiche nella scheda, riprendendo esattamente dal punto precedente nella finestra.  
  
     ![Modifica in una finestra di visualizzazione](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Per utilizzare tasti di scelta rapida per Visualizza definizione  
  
-   Nella finestra **Visualizza definizione** è possibile usare questi tasti di scelta rapida:  
  
    |Funzionalità|Tasto di scelta rapida|  
    |-------------------|-----------------------|  
    |Consente di aprire la finestra di definizione|ALT+F12|  
    |Consente di chiudere la finestra di definizione|ESC|  
    |Consente di alzare di livello la finestra di definizione in una scheda documento normale|MAIUSC+ALT+HOME|  
    |Consente di spostarsi tra le finestre di definizione|CTRL+ALT+- e CTRL+ALT+=|  
    |Consente di spostarsi tra più risultati|F8 e MAIUSC+F8|  
    |Consente di alternare la visualizzazione della finestra dell'editor di codice e la finestra di definizione|MAIUSC+ESC|  
  
    > [!NOTE]
    >  Per modificare codice in una finestra **Visualizza definizione** è anche possibile usare gli stessi tasti di scelta rapida utilizzabili in qualsiasi altra posizione in Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Suggerimenti per la produttività](../ide/productivity-tips-for-visual-studio.md)
