---
title: "Procedura dettagliata: Visualizzazione dei dati correlati in un'applicazione WPF | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 873f20383a3a35dcfc7b51128d07d5efc1d11519
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964328"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Procedura dettagliata: Visualizzazione dei dati correlati in un'applicazione WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata, si creerà un'applicazione WPF che visualizza i dati dalle tabelle di database che hanno una relazione padre/figlio. I dati sono incapsulati in entità in Entity Data Model. L'entità padre contiene informazioni generali per un set di ordini. Ogni proprietà dell'entità è associata a un controllo diverso nell'applicazione. L'entità figlio contiene i dettagli per ogni ordine. Questo set di dati è associato a un <xref:System.Windows.Controls.DataGrid> controllo.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
- Creazione di un'applicazione WPF e un Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.  
  
- Creazione di un set di controlli con associazione a dati che consentono di visualizzare le informazioni generali per un set di ordini. È creare i controlli mediante il trascinamento di un'entità padre dal **Zdroje dat** finestra **WPF Designer**.  
  
- Creazione di un <xref:System.Windows.Controls.DataGrid> controllo che visualizza i dettagli correlati per ogni ordine selezionato. È creare i controlli mediante il trascinamento di un'entità figlio dal **Zdroje dat** a una finestra nella finestra **WPF designer**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:  
  
- Modelli di Entity Data Model e ADO.NET Entity Framework. Per altre informazioni, vedere [Panoramica di Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Uso di WPF Designer. Per altre informazioni, vedere [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Creare un nuovo progetto WPF per visualizzare i record di ordine.  
  
#### <a name="to-create-a-new-wpf-project"></a>Per creare un nuovo progetto WPF  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Espandere **Visual C#** oppure **Visual Basic**, quindi selezionare **Windows**.  
  
4.  Verificare che l'opzione **.NET Framework 4** è selezionata nella casella combinata nella parte superiore della finestra di dialogo. Il <xref:System.Windows.Controls.DataGrid> controllo utilizzati in questa procedura dettagliata è disponibile solo in .NET Framework 4.  
  
5.  Selezionare il modello di progetto **Applicazione WPF**.  
  
6.  Nella casella **Nome** digitare `AdventureWorksOrdersViewer`.  
  
7.  Fare clic su **OK**.  
  
     Visual Studio crea il `AdventureWorksOrdersViewer` progetto.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Creazione di un Entity Data Model per l'applicazione  
 Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**. In questa procedura dettagliata, il modello di dati è un Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Per creare un modello Entity Data Model  
  
1. Nel **Data** menu, fare clic su **Aggiungi nuova origine dati** per aprire il **configurazione guidata origine dati**.  
  
2. Nel **scegliere un tipo di origine dati** pagina, fare clic su **Database**e quindi fare clic su **Next**.  
  
3. Nel **scegliere un modello di Database** pagina, fare clic su **Entity Data Model**e quindi fare clic su **Next**.  
  
4. Nel **Scegli contenuto Model** pagina, fare clic su **genera da database**e quindi fare clic su **Next**.  
  
5. Nel **Seleziona connessione dati** pagina, effettuare una delle operazioni seguenti:  
  
   - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.  
  
      -oppure-  
  
   - Fare clic su **nuova connessione** e creare una connessione al database AdventureWorksLT.  
  
     Assicurarsi che il **Salva impostazioni di connessione entity in App. config come** opzione è selezionata e quindi fare clic su **successivo**.  
  
6. Nel **Scegli oggetti di Database** , espandere **tabelle**e quindi selezionare le tabelle seguenti:  
  
   -   **SalesOrderDetail**  
  
   -   **SalesOrderHeader**  
  
7. Scegliere **Fine**.  
  
8. Compilare il progetto.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Creazione con associazione a dati controlli che visualizzano gli ordini  
 Creare controlli che visualizzano i record degli ordini trascinando il `SalesOrderHeaders` entità dal **Zdroje dat** finestra di progettazione WPF.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Per creare controlli associati a dati che consentono di visualizzare i record di ordine  
  
1. Nelle **Esplora soluzioni**, fare doppio clic sul file MainWindow. Xaml.  
  
    La finestra verrà aperta in WPF Designer.  
  
2. Modifica di XAML in modo che il **altezza** e **larghezza** le proprietà vengono impostate a 800  
  
3. Nel **Zdroje dat** finestra, fare clic sul menu a discesa per il **SalesOrderHeaders** nodo e selezionare **dettagli**.  
  
4. Espandere il nodo **SalesOrderHeaders**.  
  
5. Fare clic sul menu di riepilogo a discesa accanto a **SalesOrderID** e selezionare **ComboBox**.  
  
6. Per ognuno dei seguenti nodi figlio del **SalesOrderHeaders** nodo, fare clic sul menu di riepilogo a discesa accanto il nodo e selezionare **None**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **SubTotal**  
  
   - **TaxAmt**  
  
   - **Freight**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.  
  
7. Dal **Zdroje dat** finestra, trascinare le **SalesOrderHeaders** nodo nella finestra di **WPF Designer**.  
  
    Visual Studio genera XAML che crea un set di controlli associati ai dati di **SalesOrderHeaders** entità e il codice che carica i dati. Per altre informazioni sulle XAML e codice generato, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. Nella finestra di progettazione fare clic sulla casella combinata accanto al **Sales Order ID** etichetta.  
  
9. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Creazione di un DataGrid che visualizza i dettagli dell'ordine  
 Creare un <xref:System.Windows.Controls.DataGrid> controllo che visualizza i dettagli dell'ordine trascinando le `SalesOrderDetails` entità dal **Zdroje dat** finestra di progettazione WPF.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Per creare un controllo DataGrid in cui vengono visualizzati i dettagli dell'ordine  
  
1. Nel **Zdroje dat** finestra, individuare il **SalesOrderDetails** nodo figlio del **SalesOrderHeaders** nodo.  
  
   > [!NOTE]
   >  È inoltre disponibile un' **SalesOrderDetails** nodo che si trova allo stesso livello di **SalesOrderHeaders** nodo. Assicurarsi di selezionare il nodo figlio del **SalesOrderHeaders** nodo.  
  
2. Espandere l'elemento figlio **SalesOrderDetails** nodo.  
  
3. Per ognuno dei seguenti nodi figlio del **SalesOrderDetails** nodo, fare clic sul menu di riepilogo a discesa accanto il nodo e selezionare **None**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     Questa azione impedisce a Visual Studio, compresi i dati nel <xref:System.Windows.Controls.DataGrid> controllo creato nel passaggio successivo. Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.  
  
4. Dal **Zdroje dat** finestra, trascinare l'elemento figlio **SalesOrderDetails** nodo nella finestra di **WPF Designer**.  
  
    Visual Studio genera XAML per definire una nuova associazione a dati <xref:System.Windows.Controls.DataGrid> controllo e il controllo viene visualizzato nella finestra di progettazione. Visual Studio aggiorna anche il generato `GetSalesOrderHeadersQuery` metodo nel file code-behind per includere i dati nel **SalesOrderDetails** entità.  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 Compilare ed eseguire l'applicazione per verificare che vengano visualizzate i record di ordine.  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Premere **F5**.  
  
     L'applicazione verrà compilata ed eseguita. Verificare quanto segue:  
  
    -   Il **Sales Order ID** casella combinata visualizza **71774**. Questo è il primo ID ordine nell'entità.  
  
    -   Per ogni ordine si seleziona nel **Sales Order ID** combinata, informazioni dettagliate sull'ordine viene visualizzata la finestra di <xref:System.Windows.Controls.DataGrid>.  
  
2.  Chiudere l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver completato questa procedura dettagliata, informazioni su come usare il **Zdroje dat** controlli finestra in Visual Studio per eseguire l'associazione WPF ad altri tipi di origini dati. Per altre informazioni, vedere [WPF di associare controlli a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) e [WPF di associare controlli a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)