---
title: 'Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2c9d0bd58adcd0a0595c061fa4dfaa81f629601
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174247"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creare un semplice servizio WCF in Windows Form

In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], testarlo e accedervi da un'applicazione Windows Form.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Creare il servizio

### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF

1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.

2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual c#** nodo e fare clic su **WCF**, seguita da **WCF Libreria servizi**. Fare clic su **OK** per aprire il progetto.

     ![Progetto della libreria di servizi WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.

3.  ![File IService1](../data-tools/media/wcf2.png)

     Nelle **Esplora soluzioni**, fare doppio clic su **IService1.vb** oppure **IService1.cs** e trovare la riga seguente:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Modificare il tipo per il `value` parametro stringa:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.

4.  ![File Service1](../data-tools/media/wcf3.png)

     Nelle **Esplora soluzioni**, fare doppio clic su **Service1.vb** oppure **Service1.cs** e trovare la riga seguente:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Modificare il tipo per il `value` parametro stringa:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testare il servizio

### <a name="to-test-a-wcf-service"></a>Per testare un servizio WCF

1.  Premere **F5** per eseguire il servizio. Oggetto **Client di prova WCF** modulo viene visualizzato e carica il servizio.

2.  Nel **Client di prova WCF** formano, fare doppio clic il **GetData ()** metodo sottoposto a **IService1**. Il **GetData** verrà visualizzata la scheda.

     ![Il metodo GetData&#40; &#41; (metodo)](../data-tools/media/wcf4.png)

3.  Nel **richiedere** , quindi selezionare la **valore** campo e tipo `Hello`.

     ![Campo Valore](../data-tools/media/wcf5.png)

4.  Scegliere il **Invoke** pulsante. Se un **avviso di sicurezza** verrà visualizzata la finestra di dialogo, fare clic su **OK**. Consente di visualizzare il risultato nel **risposta** casella.

     ![Risultato nella casella Risposta](../data-tools/media/wcf6.png)

5.  Nel **File** menu, fare clic su **uscita** per chiudere il modulo di test.

## <a name="access-the-service"></a>Accedere al servizio

### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF

1.  Nel **File** dal menu **Add** e quindi fare clic su **nuovo progetto**.

2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual c#** nodo, seleziona **Windows**e quindi selezionare  **Windows Forms Application**. Fare clic su **OK** per aprire il progetto.

     ![Progetto di Windows Forms Application](../data-tools/media/wcf7.png)

3.  Fare doppio clic su **WindowsApplication1** e fare clic su **Aggiungi riferimento al servizio**. Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.

4.  Nel **Aggiungi riferimento al servizio** finestra di dialogo, fare clic su **Discover**.

     ![Finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png)

     **Service1** vengono visualizzati nei **Services** riquadro.

5.  Fare clic su **OK** per aggiungere il riferimento al servizio.

### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client

1.  Nelle **Esplora soluzioni**, fare doppio clic su **Form1.vb** oppure **Form1.cs** per aprire la finestra di progettazione Windows Form, se non è già aperto.

2.  Dal **casella degli strumenti**, trascinare un `TextBox` (controllo), una `Label` (controllo) e un `Button` controllo nel form.

     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png)

3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  Nelle **Esplora soluzioni**, fare doppio clic su **WindowsApplication1** e fare clic su **imposta come progetto di avvio**.

5.  Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta Visualizza "è stato immesso:" e viene visualizzato il testo immesso.

     ![Form che visualizza il risultato](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)