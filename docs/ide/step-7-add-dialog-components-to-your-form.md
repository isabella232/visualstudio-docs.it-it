---
title: 'Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo'
description: Informazioni su come aggiungere un <xref:System.Windows.Forms.OpenFileDialog> componente finestra di dialogo e un componente finestra di dialogo al <xref:System.Windows.Forms.ColorDialog> form.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c17251d97dfddd2944b0fdd56bb8a51e30c2251f
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397720"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo

Per consentire all'app di aprire i file di immagine e scegliere un colore di sfondo, in questo passaggio si aggiungono un componente <xref:System.Windows.Forms.OpenFileDialog> e un componente al <xref:System.Windows.Forms.ColorDialog> form.

Un componente è per alcuni aspetti simile a un controllo. Si usa la **casella degli strumenti** per aggiungere un componente al modulo e si impostano le relative proprietà usando la finestra **Proprietà**. A differenza di un controllo, tuttavia, l'aggiunta di un componente al form non aggiunge un elemento visibile da parte dell'utente sul form. Vengono invece forniti determinati comportamenti che è possibile attivare tramite codice. L'apertura della finestra di dialogo **Apri file** viene eseguita da un componente.

## <a name="to-add-dialog-components-to-your-form"></a>Per aggiungere componenti di finestra di dialogo al form

1. Scegliere progettazione **Windows Form** (**Form1.cs [Progettazione]**) e quindi aprire il gruppo **Dialogs** (Finestre di dialogo) nella casella degli **strumenti.**

    > [!NOTE]
    > Il gruppo **Finestre di dialogo** nella **casella degli strumenti** ha componenti che aprono molte finestre di dialogo utili che possono essere usate per l'apertura e il salvataggio di file, l'esplorazione di cartelle e la scelta di tipi di carattere e colori. In questo progetto si usano due componenti di finestra di dialogo: OpenFileDialog e ColorDialog.

1. Per aggiungere un componente denominato **openFileDialog1** al form, fare doppio clic su **OpenFileDialog**. Per aggiungere un componente denominato **colorDialog1** al modulo, fare doppio clic su **ColorDialog** nella **casella degli strumenti**. Questa verrà utilizzata nel passaggio successivo dell'esercitazione. Verrà visualizzata un'area nella parte inferiore di Progettazione  form di **Windows** (sotto il modulo Visualizzatore immagini) con un'icona per ognuno dei due componenti della finestra di dialogo aggiunti, come illustrato nell'immagine seguente.

     ![Componenti della finestra di dialogo](../ide/media/express_dialogsadded.png)<br>***Finestra** di dialogo _ _components*

1. Scegliere l'icona **openFileDialog1** nell'area nella parte inferiore di **Progettazione Windows Form**. Impostare due proprietà:

    - Impostare la proprietà **Filtro** nel seguente modo (è possibile copiare e incollare quanto segue):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Impostare la proprietà **Titolo** sul testo seguente: **Selezionare un file di immagine**

         Le impostazioni della proprietà **Filtro** consentono di specificare i tipi di file visualizzati nella finestra di dialogo relativa alla **selezione di un file immagine**.

    > [!TIP]
    > Per un esempio di finestra di dialogo **Apri file** in un'applicazione diversa, aprire **Blocco note** o **Paint** e sulla barra dei menu scegliere **File** > **Apri**. Si noti che accanto al nome del file è presente un elenco a discesa che consente di scegliere il tipo di file. <br/><br/>È stata usata **la proprietà Filter** nel componente **OpenFileDialog** per configurarlo nell'app. Si noti anche la formattazione in grassetto delle proprietà **Titolo** e **Filtro** nella finestra **Proprietà**. L'IDE imposta tale formattazione per evidenziare le proprietà che sono state modificate rispetto ai valori predefiniti.

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 8: Scrivere il codice](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** per il gestore dell'evento del pulsante Mostra immagine .

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
