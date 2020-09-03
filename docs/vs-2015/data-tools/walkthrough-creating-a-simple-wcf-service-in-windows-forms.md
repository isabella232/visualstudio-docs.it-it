---
title: 'Procedura dettagliata: creazione di un servizio WCF semplice in Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671073"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creazione di un servizio WCF semplice in Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], testarlo e accedervi da un'applicazione Windows Form.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Creazione del servizio

#### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF

1. Scegliere **nuovo** dal menu **file** , quindi fare clic su **progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e fare clic su **WCF**, seguito da **Libreria del servizio WCF**. Fare clic su **OK** per aprire il progetto.

     ![Progetto della libreria di servizi WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.

3. ![File IService1](../data-tools/media/wcf2.png "wcf2")

     In **Esplora soluzioni** fare doppio clic su IService1.vb o IService1.cs e quindi trovare la riga seguente:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Modificare il tipo per il parametro `value` su `String`:

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.

4. ![File Service1](../data-tools/media/wcf3.png "wcf3")

     In **Esplora soluzioni** fare doppio clic su Service1.vb o IService1.cs e quindi trovare la riga seguente:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Modificare il tipo per il parametro value su `String`:

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Test del servizio

#### <a name="to-test-a-wcf-service"></a>Per testare un servizio WCF

1. Premere **F5** per eseguire il servizio. Verrà visualizzato un modulo **client di prova WCF** che caricherà il servizio.

2. Nel form **Client di prova WCF** fare doppio clic sul metodo **GetData()** in **IService1**. Verrà visualizzata la scheda **GetData** .

     ![Metodo GetData&#40;&#41; ](../data-tools/media/wcf4.png "wcf4")

3. Nella casella **Richiesta** selezionare il campo **Valore** e digitare `Hello`.

     ![Campo Valore](../data-tools/media/wcf5.png "wcf5")

4. Fare clic sul pulsante **Richiama**. Se viene visualizzata una finestra di dialogo **avviso di sicurezza** , fare clic su **OK**. Il risultato verrà visualizzato nella casella **risposta** .

     ![Risultato nella casella Risposta](../data-tools/media/wcf6.png "wcf6")

5. Nel menu **File** fare clic su **Esci** per chiudere il form di test.

## <a name="accessing-the-service"></a>Accesso al servizio

#### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF

1. Scegliere **Aggiungi** dal menu **file** , quindi fare clic su **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e selezionare **Windows**, quindi selezionare **Windows Forms applicazione**. Fare clic su **OK** per aprire il progetto.

     ![Progetto Applicazione Windows Form](../data-tools/media/wcf7.png "wcf7")

3. Fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Aggiungi riferimento al servizio**. Verrà visualizzata la finestra di dialogo **Aggiungi riferimento al servizio** .

4. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

     ![Finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png "wcf8")

     **Service1** verrà visualizzato nel riquadro **Servizi** .

5. Fare clic su **OK** per aggiungere il riferimento al servizio.

#### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client

1. In **Esplora soluzioni** fare doppio clic su **Form1.vb** o **Form1.cs** per aprire Progettazione Windows Form, se non è già aperto.

2. Dalla **Casella degli strumenti** trascinare i controlli `TextBox`, `Label` e `Button` nel form.

     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png "wcf9")

3. Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Imposta come progetto di avvio**.

5. Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta visualizza "Valore immesso:" e il testo immesso.

     ![Form che visualizza il risultato](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Vedere anche
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
