---
title: 'Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e14944157a14be4a5e06c26464a4de2cdb2bff1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519120"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: creazione di un semplice servizio WCF in Windows Form](https://docs.microsoft.com/visualstudio/data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms).  
  
  
In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], testarlo e accedervi da un'applicazione Windows Form.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Creazione del servizio  
  
#### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF  
  
1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual c#** nodo e fare clic su **WCF**, seguita da **WCF Libreria servizi**. Fare clic su **OK** per aprire il progetto.  
  
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
  
2.  Nel **Client di prova WCF** formano, fare doppio clic il **GetData ()** metodo sottoposto a **IService1**. Il **GetData** verrà visualizzata la scheda.  
  
     ![Il metodo GetData&#40; &#41; metodo](../data-tools/media/wcf4.png "wcf4")  
  
3.  Nel **richiedere** , quindi selezionare la **valore** campo e tipo `Hello`.  
  
     ![Il campo del valore](../data-tools/media/wcf5.png "wcf5")  
  
4.  Scegliere il **Invoke** pulsante. Se un **avviso di sicurezza** verrà visualizzata la finestra di dialogo, fare clic su **OK**. Il risultato verrà visualizzato nei **risposta** casella.  
  
     ![Il risultato nella finestra di risposta](../data-tools/media/wcf6.png "wcf6")  
  
5.  Nel **File** menu, fare clic su **uscita** per chiudere il modulo di test.  
  
## <a name="accessing-the-service"></a>Accesso al servizio  
  
#### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF  
  
1.  Nel **File** dal menu **Add** e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual c#** nodo e selezionare **Windows**e quindi scegliere **Windows Forms Application**. Fare clic su **OK** per aprire il progetto.  
  
     ![Progetto Windows Forms Application](../data-tools/media/wcf7.png "wcf7")  
  
3.  Fare doppio clic su **WindowsApplication1** e fare clic su **Aggiungi riferimento al servizio**. Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.  
  
4.  Nel **Aggiungi riferimento al servizio** finestra di dialogo, fare clic su **Discover**.  
  
     ![La finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** verrà visualizzato nei **Services** riquadro.  
  
5.  Fare clic su **OK** per aggiungere il riferimento al servizio.  
  
#### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **Form1.vb** oppure **Form1.cs** per aprire la finestra di progettazione Windows Form, se non è già aperto.  
  
2.  Dal **casella degli strumenti**, trascinare un `TextBox` (controllo), una `Label` (controllo) e un `Button` controllo nel form.  
  
     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png "wcf9")  
  
3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  Nelle **Esplora soluzioni**, fare doppio clic su **WindowsApplication1** e fare clic su **imposta come progetto di avvio**.  
  
5.  Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta visualizza "Valore immesso:" e il testo immesso.  
  
     ![Form che visualizza il risultato](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

