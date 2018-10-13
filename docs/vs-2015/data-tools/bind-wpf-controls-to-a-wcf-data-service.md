---
title: Associare controlli WPF a un servizio WCF data Services | Microsoft Docs
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdd13647eb485fa20da9c95a1c67ccc3e5f38cc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251836"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associare controlli WPF a un servizio di dati WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record cliente incapsulati in un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Verranno inoltre aggiunti i pulsanti che i clienti possono usare per visualizzare e aggiornare i record.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.  
  
-   Creazione di un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] che espone i dati in Entity Data Model in un'applicazione WPF.  
  
-   Creazione di un set di controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra di progettazione WPF.  
  
-   Creazione di pulsanti per spostarsi avanti e indietro tra i record cliente.  
  
-   Creazione di un pulsante che consente di salvare le modifiche apportate ai dati nei controlli per il [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] e l'origine dati sottostante.  
  
     [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
-   Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:  
  
-   WCF Data Services. Per altre informazioni, vedere [Panoramica](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
-   Modelli di dati in [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].  
  
-   Modelli di Entity Data Model e ADO.NET Entity Framework. Per altre informazioni, vedere [Panoramica di Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
-   Uso di WPF Designer. Per altre informazioni, vedere [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-service-project"></a>Creare il progetto di servizio  
 Avviare la procedura dettagliata creando un progetto per un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
#### <a name="to-create-the-service-project"></a>Per creare il progetto di servizio  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Espandere **Visual c#** oppure **Visual Basic**, quindi selezionare **Web**.  
  
4.  Selezionare il modello di progetto **Applicazione Web ASP.NET**.  
  
5.  Nel **Name** , digitare `AdventureWorksService` e fare clic su **OK**.  
  
     Visual Studio crea il `AdventureWorksService` progetto.  
  
6.  Nelle **Esplora soluzioni**, fare doppio clic su **default. aspx** e selezionare **Elimina**. Questo file non è necessario per la procedura dettagliata.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Creare un Entity Data Model per il servizio  
 Per esporre i dati in un'applicazione usando un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], è necessario definire un modello di dati per il servizio. Il [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] supporta due tipi di modelli di data: Entity Data Model e modelli di dati personalizzate che vengono definiti utilizzando oggetti common language runtime (CLR) che implementano il <xref:System.Linq.IQueryable%601> interfaccia. In questa procedura dettagliata, viene creato un modello Entity Data Model per il modello di dati.  
  
#### <a name="to-create-an-entity-data-model"></a>Per creare un modello Entity Data Model  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nell'elenco Modelli installati, fare clic su **Data**, quindi selezionare la **ADO.NET Entity Data Model** elemento del progetto.  
  
3.  Modificare il nome in `AdventureWorksModel.edmx`, fare clic su **Add**.  
  
     Il **Entity Data Model**verrà visualizzata la procedura guidata.  
  
4.  Nel **Scegli contenuto Model** pagina, fare clic su **genera da database**, fare clic su **Avanti**.  
  
5.  Nel **Seleziona connessione dati** pagina, selezionare una delle opzioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.  
  
    -   Fare clic su **nuova connessione**e creare una connessione al database AdventureWorksLT.  
  
6.  Nel **Seleziona connessione dati** pagina, assicurarsi che le **Salva impostazioni di connessione entity in App. config come** opzione sia selezionata e quindi fare clic su **Avanti**.  
  
7.  Nel **Scegli oggetti di Database** , espandere **tabelle**e quindi selezionare il **SalesOrderHeader** tabella.  
  
8.  Scegliere **Fine**.  
  
## <a name="create-the-service"></a>Creare il servizio  
 Creare un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] per esporre i dati in Entity Data Model in un'applicazione WPF.  
  
#### <a name="to-create-the-service"></a>Per creare il servizio  
  
1.  Nel **Project** dal menu **Aggiungi nuovo elemento**.  
  
2.  Nell'elenco Modelli installati, fare clic su **Web**, quindi selezionare la **WCF Data Services** elemento del progetto.  
  
3.  Nel **Name** , digitare `AdventureWorksService.svc`, fare clic su **Add**.  
  
     Visual Studio aggiunge il `AdventureWorksService.svc` al progetto.  
  
## <a name="configure-the-service"></a>Configurare il servizio  
 È necessario configurare il servizio in modo da usare il modello Entity Data Model creato.  
  
#### <a name="to-configure-the-service"></a>Per configurare il servizio  
  
1.  Nel `AdventureWorks.svc` file di codice, sostituire il `AdventureWorksService` con il codice seguente dichiarazione di classe.  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     Questo codice aggiorna il `AdventureWorksService` classe, in modo che derivi da un <xref:System.Data.Services.DataService%601> che opera sul `AdventureWorksLTEntities` oggetto classe del contesto del modello Entity Data Model. Aggiorna inoltre il metodo `InitializeService` per consentire ai client del servizio l'accesso completo in lettura/scrittura all'entità `SalesOrderHeader`.  
  
2.  Compilare il progetto e verificare che non siano presenti errori.  
  
## <a name="create-the-wpf-client-application"></a>Creare l'applicazione client WPF  
 Per visualizzare i dati di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], creare una nuova applicazione WPF con un'origine dati basata sul servizio. Più avanti in questa procedura dettagliata, verranno aggiunti all'applicazione i controlli associati a dati.  
  
#### <a name="to-create-the-wpf-client-application"></a>Per creare l'applicazione client WPF  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic sul nodo della soluzione, fare clic su **Add**e selezionare **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** oppure **Visual Basic**e quindi selezionare **Windows**.  
  
3.  Selezionare il **WPF Application** modello di progetto.  
  
4.  Nel **Name** , digitare `AdventureWorksSalesEditor`, fare clic su **OK**.  
  
     Visual Studio aggiunge il `AdventureWorksSalesEditor` progetto alla soluzione.  
  
5.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
     Il **Zdroje dat** verrà visualizzata la finestra.  
  
6.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
     Il **configurazione dell'origine dati**verrà visualizzata la procedura guidata.  
  
7.  Nel **scegliere un tipo di origine dati** pagina della procedura guidata, selezionare **servizio**, quindi fare clic su **Avanti**.  
  
8.  Nel **Aggiungi riferimento al servizio** finestra di dialogo, fare clic su **Discover**.  
  
     Visual Studio cerca i servizi disponibili nella soluzione corrente e aggiunge `AdventureWorksService.svc` all'elenco dei servizi disponibili nel **Services** casella.  
  
9. Nel **Namespace** , digitare `AdventureWorksService`.  
  
10. Nel **Services** fare clic su **AdventureWorksService. svc**, quindi fare clic su **OK**.  
  
     Visual Studio scaricherà le informazioni del servizio e restituisce quindi il **configurazione dell'origine dati** procedura guidata.  
  
11. Nel **Aggiungi riferimento al servizio** pagina, fare clic su **fine**.  
  
     Visual Studio aggiunge i nodi che rappresentano i dati restituiti dal servizio per il **Zdroje dat** finestra.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definire l'interfaccia utente della finestra  
 Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di visualizzare e aggiornare i record delle vendite tramite questi pulsanti.  
  
#### <a name="to-create-the-window-layout"></a>Per creare il layout della finestra  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic sul file MainWindow. Xaml.  
  
     La finestra verrà aperta in WPF Designer.  
  
2.  Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compilare il progetto.  
  
## <a name="create-the-data-bound-controls"></a>Creare i controlli con associazione a dati  
 Creare controlli che visualizzano i record cliente trascinando il `SalesOrderHeaders` dal nodo il **Zdroje dat** finestra di progettazione.  
  
#### <a name="to-create-the-data-bound-controls"></a>Per creare i controlli associati a dati  
  
1.  Nel **Zdroje dat** finestra, fare clic sul menu a discesa per il **SalesOrderHeaders** nodo e selezionare **dettagli**.  
  
2.  Espandere la **SalesOrderHeaders** nodo.  
  
3.  Per questo esempio, alcuni campi non verranno visualizzati, quindi fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **None**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. In questa procedura dettagliata si presuppone che l'utente finale non necessario visualizzare i dati.  
  
4.  Dal **Zdroje dat** finestra, trascinare le **SalesOrderHeaders** nodo nella riga della griglia sotto la riga che contiene i pulsanti.  
  
     Visual Studio genera XAML e codice che crea un set di controlli associati ai dati di **prodotto** tabella. Per altre informazioni sulle XAML e codice generato, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  Nella finestra di progettazione, selezionare la casella di testo accanto al **Customer ID** etichetta.  
  
6.  Nel **delle proprietà** finestra, seleziona la casella di controllo accanto al **IsReadOnly** proprietà.  
  
7.  Impostare il **IsReadOnly** proprietà per ognuna delle caselle di testo seguenti:  
  
    -   **Numero di ordine di acquisto**  
  
    -   **ID ordine di vendita**  
  
    -   **Numero di ordine di vendita**  
  
## <a name="load-the-data-from-the-service"></a>Caricare i dati dal servizio  
 Usare l'oggetto proxy del servizio per caricare i dati di vendita dal servizio. Assegnare quindi i dati restituiti per l'origine dati per il <xref:System.Windows.Data.CollectionViewSource> nella finestra WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>Per caricare i dati dal servizio  
  
1.  Nella finestra di progettazione, per creare il `Window_Loaded` gestore dell'evento, fare doppio clic sul testo che legge: **MainWindow**.  
  
2.  Sostituire il gestore eventi con il codice seguente. Assicurarsi di sostituire il *localhost* indirizzo nel codice seguente con l'indirizzo dell'host locale nel computer di sviluppo.  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Record Navigatesales  
 Aggiungere il codice che consente agli utenti di scorrere i record delle vendite usando i **\<** e **>** pulsanti.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Per consentire agli utenti di esplorare i record delle vendite  
  
1.  Nella finestra di progettazione, fare doppio clic il **<** pulsante nell'area della finestra.  
  
     Visual Studio apre il file code-behind e crea un nuovo `backButton_Click` gestore dell'evento per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
2.  Aggiungere il codice seguente al gestore eventi `backButton_Click` generato:  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3.  Tornare alla finestra di progettazione e fare doppio clic il **>** pulsante.  
  
     Visual Studio apre il file code-behind e crea un nuovo `nextButton_Click` gestore dell'evento per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
4.  Aggiungere il codice seguente al gestore eventi `nextButton_Click` generato:  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>Salvataggio delle modifiche ai record delle vendite  
 Aggiungere il codice che consente agli utenti di visualizzare e salvare le modifiche ai record delle vendite usando i **salvare le modifiche** pulsante.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Per aggiungere la possibilità di salvare le modifiche ai record delle vendite  
  
1.  Nella finestra di progettazione, fare doppio clic il **Save Changes** pulsante.  
  
     Visual Studio apre il file code-behind e crea un nuovo `saveButton_Click` gestore dell'evento per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
2.  Aggiungere il codice seguente al gestore eventi `saveButton_Click`.  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>Test dell'applicazione  
 Compilare ed eseguire l'applicazione per verificare che sia possibile visualizzare e aggiornare i record cliente.  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Sul **compilare** menu, fare clic su **Compila soluzione**. Verificare che la soluzione venga compilata senza errori.  
  
2.  Premere **CTRL+F5**.  
  
     Visual Studio avvia il **AdventureWorksService** progetto, senza eseguirne il debug.  
  
3.  Nelle **Esplora soluzioni**, fare doppio clic il **AdventureWorksSalesEditor** progetto.  
  
4.  Nel menu di scelta rapida, sotto **Debug**, fare clic su **Avvia nuova istanza**.  
  
     Verrà eseguita l'applicazione. Verificare quanto segue:  
  
    -   Le caselle di testo visualizzano diversi campi di dati del primo record di vendita, con l'ID dell'ordine vendita **71774**.  
  
    -   È possibile scegliere il **>** oppure **<** pulsanti per spostarsi tra gli altri record delle vendite.  
  
5.  In uno dei record delle vendite digitare del testo nella **commento** e quindi scegliere **salvare le modifiche**.  
  
6.  Chiudere l'applicazione, quindi avviarla di nuovo da Visual Studio.  
  
7.  Passare al record delle vendite modificato e verificare che la modifica sia presente dopo avere chiuso e riaperto l'applicazione.  
  
8.  Chiudere l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:  
  
-   Informazioni su come usare il **Zdroje dat** controlli finestra in Visual Studio per eseguire l'associazione WPF ad altri tipi di origini dati. Per altre informazioni, vedere [WPF di associare controlli a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Informazioni su come usare il **Zdroje dat** finestra in Visual Studio per visualizzare i dati correlati (vale a dire i dati in una relazione padre-figlio) nei controlli WPF. Per altre informazioni, vedere [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Panoramica](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Panoramica di Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [Panoramica di progettazione di Silverlight e WPF](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Panoramica sul data binding](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

