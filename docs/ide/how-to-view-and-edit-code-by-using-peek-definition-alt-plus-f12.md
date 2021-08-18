---
title: Uso di Visualizza definizione
description: Informazioni su come usare il comando Visualizza definizione per visualizzare e modificare il codice senza dover cambiare contesto dal codice che si sta scrivendo.
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 925acb8a046647ec1ea64f2eb2f446e30fdb5d6d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078284"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Procedura: Visualizzare e modificare il codice usando Visualizza definizione (ALT+F12)

È possibile usare il comando **Visualizza definizione** per visualizzare e modificare il codice senza uscire dal codice in fase di scrittura. **Visualizza definizione** e **Vai a definizione** visualizzano le stesse informazioni, ma **Visualizza definizione** mostra il codice in una finestra popup e **Vai a definizione** mostra il codice in una finestra separata. **Vai a definizione** determina il passaggio del contesto (ovvero la finestra di codice attiva, la riga corrente e la posizione del cursore) alla finestra del codice della definizione. Tramite **Visualizza definizione** è possibile visualizzare e modificare la definizione e spostarsi all'interno del file di definizione, mantenendo la stessa posizione nel file di codice originale.

È possibile usare **Visualizza definizione** con codice C#, Visual Basic e C++. In Visual Basic **Visualizza definizione** contiene un collegamento a **Visualizzatore oggetti** per i simboli sprovvisti di metadati di definizione, ad esempio i tipi .NET predefiniti.

## <a name="use-peek-definition"></a>Usare Visualizza definizione

### <a name="open-a-peek-definition-window"></a>Aprire una finestra Visualizza definizione

1. È possibile visualizzare una definizione scegliendo **Visualizza definizione** dal menu di scelta rapida per un tipo o un membro che si vuole esplorare. Se l'opzione è abilitata, è possibile visualizzare una definizione anche usando il mouse premendo **CTRL** (o un altro modificatore) e facendo clic sul nome del membro. In caso contrario, premere **ALT** + **F12** dalla tastiera.

     Questa illustrazione mostra la finestra **Visualizza definizione** per un metodo denominato `Print()`:

     ![Finestra di anteprima](../ide/media/peekwindow.png)

     La finestra di definizione appare sotto la riga `printer.Print("Hello World!")` nel file originale. La finestra non nasconde alcuna sezione di codice nel file originale. Le righe che seguono `printer.Print("Hello World!")` sono visualizzate al di sotto della finestra di definizione.

1. È possibile spostare il cursore in posizioni diverse all'interno della finestra di definizione. È anche possibile continuare a spostarsi nella finestra del codice originale.

1. È possibile copiare una stringa dalla finestra di definizione e incollarla nel codice originale. È inoltre possibile trascinare e rilasciare la stringa dalla finestra di definizione nel codice originale senza eliminarla dalla finestra di definizione.

1. È possibile chiudere la finestra di definizione usando il tasto **ESC** o il pulsante **Chiudi** nella scheda della finestra di definizione.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Aprire una finestra Visualizza definizione dall'interno di una finestra Visualizza definizione

Se è già aperta una finestra **Visualizza definizione**, è possibile chiamare di nuovo **Visualizza definizione** per il codice in tale finestra. Verrà visualizzata un'altra finestra di definizione. Accanto alla scheda della finestra di definizione verrà visualizzato un set di punti di navigazione, che è possibile utilizzare per spostarsi tra le finestre di definizione. La descrizione comando in ciascun punto indica il nome e il percorso del file di definizione rappresentato dal punto.

   ![Finestra di anteprima in una finestra di anteprima](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Visualizza definizione con più risultati

Se si usa **Visualizza definizione** per codice con più definizioni, ad esempio una classe parziale, a destra della visualizzazione della definizione del codice viene visualizzato un elenco di risultati. È possibile scegliere qualsiasi risultato nell'elenco per visualizzarne la definizione.

   ![Finestra di anteprima di più risultati](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Apportare modifiche all'interno della finestra Visualizza definizione

Quando si inizia ad apportare modifiche all'interno di una finestra **Visualizza definizione**, il file da modificare viene aperto automaticamente sotto forma di scheda separata nell'editor di codice e riflette le modifiche apportate. È possibile continuare ad apportare, annullare e salvare modifiche nella finestra **Visualizza definizione**. La scheda continuerà a riflettere tali modifiche. Anche se si chiude la finestra **Visualizza definizione** senza salvare le modifiche, è possibile apportare, annullare e salvare altre modifiche nella scheda, riprendendo esattamente dal punto precedente nella finestra **Visualizza definizione**.

   ![Modifica in una finestra di anteprima](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Per modificare le opzioni per Visualizza definizione

1. Passare a **Strumenti Opzioni**  >  **Editor di** testo  >    >  **Generale**.

1. Selezionare l'opzione **Apri definizione in visualizzazione rapida**.

1. Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni** .

   ![Impostazione dell'opzione Visualizza definizione con clic del mouse](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Tasti di scelta rapida per Visualizza definizione

Nella finestra **Visualizza definizione** è possibile usare questi tasti di scelta rapida:

|Funzionalità|Tasto di scelta rapida|
|-------------------|:-----------------------:|
|Consente di aprire la finestra di definizione|**ALT** + **F12**|
|Consente di chiudere la finestra di definizione|**ESC**|
|Consente di alzare di livello la finestra di definizione in una scheda documento normale|**CTRL+FRECCIA DESTRA** + **ALT** + **Home**|
|Consente di spostarsi tra le finestre di definizione|**CTRL+FRECCIA DESTRA** +  + ALT **-** e **CTRL** + **ALT**+**=**|
|Consente di spostarsi tra più risultati|**F8** e **MAIUSC**+**F8**|
|Consente di alternare la visualizzazione della finestra dell'editor di codice e la finestra di definizione|**MAIUSC** + **Esc**|

> [!NOTE]
> Per modificare codice in una finestra **Visualizza definizione** è anche possibile usare gli stessi tasti di scelta rapida utilizzabili in qualsiasi altra posizione in Visual Studio.

## <a name="see-also"></a>Vedi anche

- [Spostarsi all'interno del codice](../ide/navigating-code.md)
- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)
- [Funzionalità di produttività in Visual Studio](../ide/productivity-features.md)
