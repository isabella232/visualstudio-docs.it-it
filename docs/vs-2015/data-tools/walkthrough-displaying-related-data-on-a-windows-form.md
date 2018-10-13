---
title: 'Procedura dettagliata: Visualizzazione dei dati correlati in un Windows Form | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282672"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Procedura dettagliata: visualizzazione di dati correlati in un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In molti scenari di applicazioni può essere necessario usare dati provenienti da più tabelle, spesso anche correlate, ovvero usare relazioni padre-figlio. Può ad esempio essere necessario creare un form in cui la selezione del record di un cliente determini la visualizzazione degli ordini relativi. Per visualizzare i record correlati nel form è necessario impostare la proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto figlio <xref:System.Windows.Forms.BindingSource> sull'oggetto <xref:System.Windows.Forms.BindingSource> (non sulla tabella figlio) e impostare la proprietà <xref:System.Windows.Forms.BindingSource.DataMember%2A> dell'oggetto figlio <xref:System.Windows.Forms.BindingSource> sulla relazione dati che collega le tabelle padre e figlio.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un **applicazioni Windows** progetto.  
  
-   Creazione e configurazione di un set di dati nell'applicazione in base il `Customers` e `Orders` le tabelle nel database Northwind tramite il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Aggiunta di controlli per visualizzare i dati della tabella `Customers`.  
  
-   Aggiunta di controlli per visualizzare le voci della tabella `Orders` in base al `Customer` selezionato.  
  
-   Test dell'applicazione selezionando diversi clienti e verificando che vengano visualizzati gli ordini corretti per il cliente selezionato.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per installare i database di esempio, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-windows-application-project"></a>Per creare il progetto Applicazione Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto `RelatedDataWalkthrough`.  
  
3.  Selezionare **applicazione di Windows** e fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **RelatedDataWalkthrough** viene creato e aggiunto al progetto **Esplora soluzioni**.  
  
## <a name="creating-the-data-source"></a>Creazione dell'origine dati  
 In questo passaggio viene creato un set di dati in base alle tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.  
  
6.  Fare clic su **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.  
  
7.  Espandere la **tabelle** nodo il **Scegli oggetti di Database** pagina.  
  
8.  Selezionare il **clienti** e **ordini** tabelle e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il **clienti** inclusa nella tabella il **Zdroje dat** finestra.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Creazione di controlli per visualizzare i dati della tabella Customers  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Per creare controlli che consentano di visualizzare i dati del cliente (record padre)  
  
1.  Nel **Zdroje dat** finestra, seleziona la **clienti** di tabella e quindi fare clic sulla freccia giù.  
  
2.  Scegli **dettagli** dal menu di scelta.  
  
3.  Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra all'inizio dello **Form1**.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Creazione di controlli per visualizzare i dati della tabella Orders  
 ![Finestra Origini dati che mostra relazione](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Per creare controlli che consentano di visualizzare gli ordini di ciascun cliente (record figlio)  
  
-   Nel **Zdroje dat** finestra, espandere il **clienti** nodo e selezionare l'ultima colonna nel **clienti** tabella, che rappresenta un nodo **ordini** nodo e trascinarla in fondo **Form1**.  
  
     Al form viene aggiunto un oggetto <xref:System.Windows.Forms.DataGridView> e alla barra dei componenti vengono aggiunti un nuovo oggetto <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) e un TableAdapter (`OrdersTableAdapter`).  
  
    > [!NOTE]
    >  Aprire il [finestra delle proprietà](../ide/reference/properties-window.md) e selezionare il **OrdersBindingSource**. Esaminare le proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> per stabilire come è configurata l'associazione per la visualizzazione dei record correlati. La proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> è impostata su `CustomersBindingSource` (elemento <xref:System.Windows.Forms.BindingSource> della tabella padre), anziché sulla tabella `Orders`. La proprietà <xref:System.Windows.Forms.BindingSource.DataMember%2A> è impostata su `FK_Orders_Customers`, ovvero il nome dell'oggetto <xref:System.Data.DataRelation> che mette in correlazione tra loro le tabelle.  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Premere F5 per eseguire l'applicazione.  
  
2.  Selezionare diversi clienti mediante il **CustomersBindingNavigator** per verificare gli ordini corretti vengono visualizzati nei <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form master-dettagli. È possibile apportare un miglioramento a questa procedura dettagliata, ovvero:  
  
-   Filtrare i record `Customers` aggiungendo la parametrizzazione alla tabella `Customers`. A tale scopo, selezionare un controllo che visualizza i dati di `Customers` tabella, fare clic sullo smart tag e scegliere **Aggiungi Query**. Completare la [finestra di dialogo Generatore di criteri di ricerca](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Per altre informazioni, vedere [procedura: aggiungere una Query con parametri a un'applicazione di Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: visualizzare correlati i dati in una Windows Forms Application](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Cenni preliminari sul componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Cenni preliminari sul controllo BindingNavigator](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)