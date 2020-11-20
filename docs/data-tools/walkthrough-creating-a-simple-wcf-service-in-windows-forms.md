---
title: Creazione di un servizio WCF semplice in Windows Forms
description: In questa procedura dettagliata creare un servizio Windows Communication Foundation (WCF) in Visual Studio, testarlo e accedervi da una Windows Forms Application.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 215ae1409c36417526bb1362f0029029ed95e801
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998135"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: creare un servizio WCF semplice in Windows Forms

In questa procedura dettagliata viene illustrato come creare un semplice servizio di Windows Communication Foundation (WCF), eseguirne il test e quindi accedervi da una Windows Forms Application.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Creare un servizio

1. Aprire Visual Studio.

::: moniker range="vs-2017"

2. Nel menu **File**, scegliere **Nuovo** > **Progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e scegliere **WCF**, seguito da **libreria del servizio WCF**.

4. Fare clic su **OK** per creare il progetto.

   ![Progetto della libreria di servizi WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella finestra Start scegliere **Crea un nuovo progetto**.

3. Digitare **libreria del servizio WCF** nella casella di ricerca della pagina **Crea un nuovo progetto** . Selezionare il modello C# o Visual Basic per la **libreria di servizi WCF**, quindi fare clic su **Avanti**.

   ![Creare un nuovo progetto di libreria di servizi WCF in Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Se non vengono visualizzati modelli, potrebbe essere necessario installare il componente **Windows Communication Foundation** di Visual Studio. Scegliere **Installa altri strumenti e funzionalità** per aprire programma di installazione di Visual Studio. Scegliere la scheda **singoli componenti** , scorrere verso il basso fino a **attività di sviluppo**, quindi selezionare **Windows Communication Foundation**. Fare clic su **Modifica**.

4. Nella pagina **Configura nuovo progetto** fare clic su **Crea**.

::: moniker-end

   > [!NOTE]
   > Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.

5. In **Esplora soluzioni** fare doppio clic su **IService1. vb** o **IService1.cs**.

   ![File IService1](../data-tools/media/wcf2.png)

   Trovare la riga seguente:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Modificare il tipo per il `value` parametro in stringa:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.

6. In **Esplora soluzioni** fare doppio clic su **Service1. vb** o **Service1.cs**.

   ![File Service1](../data-tools/media/wcf3.png)

   Trovare la riga seguente:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Modificare il tipo per il `value` parametro in stringa:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testare il servizio

1. Premere **F5** per eseguire il servizio. Verrà visualizzato un modulo **client di prova WCF** che caricherà il servizio.

2. Nel form **Client di prova WCF** fare doppio clic sul metodo **GetData()** in **IService1**. Verrà visualizzata la scheda **GetData** .

     ![Metodo GetData&#40;&#41; ](../data-tools/media/wcf4.png)

3. Nella casella **Richiesta** selezionare il campo **Valore** e digitare `Hello`.

     ![Campo Valore](../data-tools/media/wcf5.png)

4. Fare clic sul pulsante **Richiama**. Se viene visualizzata una finestra di dialogo **avviso di sicurezza** , fare clic su **OK**. Il risultato viene visualizzato nella casella **risposta** .

     ![Risultato nella casella Risposta](../data-tools/media/wcf6.png)

5. Nel menu **File** fare clic su **Esci** per chiudere il form di test.

## <a name="access-the-service"></a>Accedere al servizio

### <a name="reference-the-wcf-service"></a>Fare riferimento al servizio WCF

1. Scegliere **Aggiungi** dal menu **file** , quindi fare clic su **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** , selezionare **Windows**, quindi selezionare **Windows Forms applicazione**. Fare clic su **OK** per aprire il progetto.

     ![Progetto Applicazione Windows Form](../data-tools/media/wcf7.png)

3. Fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Aggiungi riferimento al servizio**. Viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio**.

4. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

     ![Finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png)

     **Service1** viene visualizzato nel riquadro **Servizi** .

5. Fare clic su **OK** per aggiungere il riferimento al servizio.

### <a name="build-a-client-application"></a>Compilare un'applicazione client

1. In **Esplora soluzioni** fare doppio clic su **Form1.vb** o **Form1.cs** per aprire Progettazione Windows Form, se non è già aperto.

2. Dalla **Casella degli strumenti** trascinare i controlli `TextBox`, `Label` e `Button` nel form.

     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png)

3. Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Imposta come progetto di avvio**.

5. Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta Visualizza "è stato immesso:" e Mostra il testo immesso.

     ![Form che visualizza il risultato](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Vedi anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
