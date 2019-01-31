---
title: 'Procedura dettagliata: Creazione di un servizio WCF semplice in Windows Forms'
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 74643d6511fc0eac99eff9693eac9cb9234df88f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966257"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creare un semplice servizio WCF in Windows Form

Questa procedura dettagliata illustra come creare un semplice servizio [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], testarlo e accedervi da un'applicazione Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Creare il servizio

### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF

1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.

2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e fare clic su **WCF**, seguito da **Libreria del servizio WCF**. Fare clic su **OK** per aprire il progetto.

     ![Progetto della libreria di servizi WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.

3.  ![File IService1](../data-tools/media/wcf2.png)

     In **Esplora soluzioni** fare doppio clic su **IService1.vb** o **IService1.cs** e quindi trovare la riga seguente:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Modificare il tipo per il `value` parametro stringa:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.

4.  ![File Service1](../data-tools/media/wcf3.png)

     In **Esplora soluzioni** fare doppio clic su **Service1.vb** o **IService1.cs** e quindi trovare la riga seguente:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Modificare il tipo per il `value` parametro stringa:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testare il servizio

### <a name="to-test-a-wcf-service"></a>Per testare un servizio WCF

1.  Premere **F5** per eseguire il servizio. Oggetto **Client di prova WCF** modulo viene visualizzato e carica il servizio.

2.  Nel form **Client di prova WCF** fare doppio clic sul metodo **GetData()** in **IService1**. Il **GetData** verrà visualizzata la scheda.

     ![Il metodo GetData&#40; &#41; (metodo)](../data-tools/media/wcf4.png)

3.  Nella casella **Richiesta** selezionare il campo **Valore** e digitare `Hello`.

     ![Campo Valore](../data-tools/media/wcf5.png)

4.  Fare clic sul pulsante **Richiama**. Se un **avviso di sicurezza** verrà visualizzata la finestra di dialogo, fare clic su **OK**. Consente di visualizzare il risultato nel **risposta** casella.

     ![Risultato nella casella Risposta](../data-tools/media/wcf6.png)

5.  Nel menu **File** fare clic su **Esci** per chiudere il form di test.

## <a name="access-the-service"></a>Accedere al servizio

### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF

1.  Scegliere **Aggiungi** dal menu **File** e quindi fare clic su **Nuovo progetto**.

2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual C#**  nodo, seleziona **Windows**e quindi scegliere  **Windows Forms Application**. Fare clic su **OK** per aprire il progetto.

     ![Progetto di Windows Forms Application](../data-tools/media/wcf7.png)

3.  Fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Aggiungi riferimento al servizio**. Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.

4.  Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

     ![Finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png)

     **Service1** vengono visualizzati nei **Services** riquadro.

5.  Fare clic su **OK** per aggiungere il riferimento al servizio.

### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client

1.  In **Esplora soluzioni** fare doppio clic su **Form1.vb** o **Form1.cs** per aprire Progettazione Windows Form, se non è già aperto.

2.  Dalla **Casella degli strumenti** trascinare i controlli `TextBox`, `Label` e `Button` nel form.

     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png)

3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Imposta come progetto di avvio**.

5.  Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta Visualizza "è stato immesso:" e viene visualizzato il testo immesso.

     ![Form che visualizza il risultato](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)