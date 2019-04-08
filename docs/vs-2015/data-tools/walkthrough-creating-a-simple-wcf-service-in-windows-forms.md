---
title: 'Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a87c88aba4b0a622dd66440fca33ab99fd028d51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966331"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creazione di un servizio WCF semplice in Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], testarlo e accedervi da un'applicazione Windows Form.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Creazione del servizio  
  
#### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF  
  
1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e fare clic su **WCF**, seguito da **Libreria del servizio WCF**. Fare clic su **OK** per aprire il progetto.  
  
     ![Il progetto libreria di servizi WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.  
  
3.  ![Il file IService1](../data-tools/media/wcf2.png "wcf2")  
  
     Nelle **Esplora soluzioni**, fare doppio clic su IService1.vb o IService1.cs e trovare la riga seguente:  
  
     [! codice-csharp [WCFWalkthrough 4] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/IService1 (2).cs n. 4)] [! codice Visual Basic [WCFWalkthrough 4] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/IService1 (2).vb n. 4)]  
  
     Modificare il tipo per il parametro `value` su `String`:  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.  
  
4.  ![Il file Service1](../data-tools/media/wcf3.png "wcf3")  
  
     Nelle **Esplora soluzioni**, fare doppio clic su Service1.vb o Service1.cs e trovare la riga seguente:  
  
     [! codice-csharp [WCFWalkthrough 5] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/Service1 (2).cs n. 5)] [! codice Visual Basic [WCFWalkthrough 5] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/Service1 (2).vb n. 5)]  
  
     Modificare il tipo per il parametro value su `String`:  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Test del servizio  
  
#### <a name="to-test-a-wcf-service"></a>Per testare un servizio WCF  
  
1.  Premere **F5** per eseguire il servizio. Oggetto **Client di prova WCF** verrà visualizzato il modulo e il servizio verrà caricato.  
  
2.  Nel form **Client di prova WCF** fare doppio clic sul metodo **GetData()** in **IService1**. Il **GetData** verrà visualizzata la scheda.  
  
     ![Il metodo GetData&#40; &#41; metodo](../data-tools/media/wcf4.png "wcf4")  
  
3.  Nella casella **Richiesta** selezionare il campo **Valore** e digitare `Hello`.  
  
     ![Il campo del valore](../data-tools/media/wcf5.png "wcf5")  
  
4.  Fare clic sul pulsante **Richiama**. Se un **avviso di sicurezza** verrà visualizzata la finestra di dialogo, fare clic su **OK**. Il risultato verrà visualizzato nei **risposta** casella.  
  
     ![Il risultato nella finestra di risposta](../data-tools/media/wcf6.png "wcf6")  
  
5.  Nel menu **File** fare clic su **Esci** per chiudere il form di test.  
  
## <a name="accessing-the-service"></a>Accesso al servizio  
  
#### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF  
  
1.  Scegliere **Aggiungi** dal menu **File** e quindi fare clic su **Nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual C#** nodo e selezionare **Windows**e quindi scegliere **Windows Forms Application**. Fare clic su **OK** per aprire il progetto.  
  
     ![Progetto Windows Forms Application](../data-tools/media/wcf7.png "wcf7")  
  
3.  Fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Aggiungi riferimento al servizio**. Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.  
  
4.  Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.  
  
     ![La finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** verrà visualizzato nei **Services** riquadro.  
  
5.  Fare clic su **OK** per aggiungere il riferimento al servizio.  
  
#### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client  
  
1.  In **Esplora soluzioni** fare doppio clic su **Form1.vb** o **Form1.cs** per aprire Progettazione Windows Form, se non è già aperto.  
  
2.  Dalla **Casella degli strumenti** trascinare i controlli `TextBox`, `Label` e `Button` nel form.  
  
     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png "wcf9")  
  
3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **WindowsApplication1** e quindi scegliere **Imposta come progetto di avvio**.  
  
5.  Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta visualizza "Valore immesso:" e il testo immesso.  
  
     ![Form che visualizza il risultato](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
