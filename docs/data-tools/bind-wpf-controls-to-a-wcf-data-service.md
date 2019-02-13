---
title: Associare controlli WPF a un servizio di dati WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 1a84a9a1a8f0a7d30aafc1daa7a0a669674b021e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918018"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associare controlli WPF a un servizio di dati WCF

In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record cliente incapsulati in un servizio dati WCF. Verranno inoltre aggiunti i pulsanti che i clienti possono usare per visualizzare e aggiornare i record.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un servizio dati WCF che espone i dati in Entity Data Model in un'applicazione WPF.

- Creazione di un set di controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati** in WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record cliente.

- Creazione di un pulsante che consente di salvare le modifiche apportate ai dati nei controlli per WCF Data Services e l'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Visual Studio

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- WCF Data Services. Per altre informazioni, vedere [Panoramica](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modelli di dati in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Modelli di Entity Data Model e ADO.NET Entity Framework. Per altre informazioni, vedere [Cenni preliminari su Entity Framework](/dotnet/framework/data/adonet/ef/overview).

- Data binding WPF. Per altre informazioni, vedere [Panoramica sul data binding](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Creare il progetto di servizio

Avviare questa procedura dettagliata creando un progetto per un servizio dati WCF:

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Espandere **Visual C#** o **Visual Basic**, quindi selezionare **Web**.

4. Selezionare il modello di progetto **Applicazione Web ASP.NET**.

5. Nella casella **Nome** digitare **AdventureWorksService** e fare clic su **OK**.

     Visual Studio crea il progetto **AdventureWorksService**.

6. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Default.aspx** e scegliere **Elimina**. Questo file non è necessario per la procedura dettagliata.

## <a name="create-an-entity-data-model-for-the-service"></a>Creare un Entity Data Model per il servizio

Per esporre i dati a un'applicazione usando un servizio dati WCF, è necessario definire un modello di dati per il servizio. WCF Data Services supporta due tipi di modelli di dati: Entity Data Model e modelli di dati personalizzate che vengono definiti utilizzando oggetti common language runtime (CLR) che implementano il <xref:System.Linq.IQueryable%601> interfaccia. In questa procedura dettagliata, viene creato un modello Entity Data Model per il modello di dati.

1. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nell'elenco Modelli installati fare clic su **Dati**, quindi selezionare l'elemento di progetto **ADO.NET Entity Data Model**.

3. Modificare il nome in `AdventureWorksModel.edmx`, fare clic su **Add**.

     Verrà aperta la **Procedura guidata Entity Data Model**.

4. Nella pagina **Scegli contenuto del modello** fare clic su **Genera da database**, quindi su **Avanti**.

5. Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:

    - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.

    - Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.

6. Nella pagina **Seleziona connessione dati** verificare che l'opzione **Salva impostazioni di connessione entità in App.Config come** sia selezionata, quindi fare clic su **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **Tabelle**, quindi selezionare la tabella **SalesOrderHeader**.

8. Scegliere **Fine**.

## <a name="create-the-service"></a>Creare il servizio

Creare un servizio dati WCF per esporre i dati di Entity Data Model in un'applicazione WPF:

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nell'elenco **Modelli installati** fare clic su **Web**, quindi selezionare l'elemento di progetto **WCF Data Services**.

3. Nel **Name** , digitare `AdventureWorksService.svc`, fare clic su **Add**.

     Visual Studio aggiunge il `AdventureWorksService.svc` al progetto.

## <a name="configure-the-service"></a>Configurare il servizio

È necessario configurare il servizio in modo da usare il modello Entity Data Model creato:

1. Nel `AdventureWorks.svc` file di codice, sostituire il **AdventureWorksService** con il codice seguente dichiarazione di classe.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Questo codice aggiorna il **AdventureWorksService** classe, in modo che derivi da un <xref:System.Data.Services.DataService%601> che opera sul `AdventureWorksLTEntities` oggetto classe del contesto del modello Entity Data Model. Aggiorna inoltre il metodo `InitializeService` per consentire ai client del servizio l'accesso completo in lettura/scrittura all'entità `SalesOrderHeader`.

2. Compilare il progetto e verificare che non siano presenti errori.

## <a name="create-the-wpf-client-application"></a>Creare l'applicazione client WPF

Per visualizzare i dati dal servizio dati WCF, creare una nuova applicazione WPF con un'origine dati che si basa sul servizio. Più avanti in questa procedura dettagliata, verranno aggiunti all'applicazione i controlli associati a dati.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi** e selezionare **Nuovo progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#** o **Visual Basic**, quindi selezionare **Finestre**.

3. Selezionare il modello di progetto **Applicazione WPF**.

4. Nella casella **Nome** digitare `AdventureWorksSalesEditor` e fare clic su **OK**.

   Visual Studio aggiunge il `AdventureWorksSalesEditor` progetto alla soluzione.

5. Scegliere **Mostra origini dati** dal menu **Dati**.

   Verrà visualizzata la finestra **Origini dati**.

6. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Verrà avviata la **Configurazione guidata origine dati**.

7. Nella pagina **Seleziona un tipo di origine dati** della procedura guidata selezionare **Servizio**, quindi fare clic su **Avanti**.

8. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

   Visual Studio cerca i servizi disponibili nella soluzione corrente e aggiunge `AdventureWorksService.svc` all'elenco dei servizi disponibili nel **Services** casella.

9. Nella casella **Spazio dei nomi** digitare **AdventureWorksService**.

10. Nella casella **Servizi** fare clic su **AdventureWorksService.svc**, quindi su **OK**.

    Visual Studio scarica le informazioni sul servizio, quindi torna alla **Configurazione guidata origine dati**.

11. Nella pagina **Aggiungi riferimento al servizio** fare clic su **Fine**.

    Visual Studio aggiunge i nodi che rappresentano i dati restituiti dal servizio nella finestra **Origini dati**.

## <a name="define-the-user-interface"></a>Definire l'interfaccia utente

Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di visualizzare e aggiornare i record delle vendite tramite questi pulsanti.

1. In **Esplora soluzioni** fare doppio clic su **MainWindow.xaml**.

   La finestra verrà aperta in WPF Designer.

2. Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Compilare il progetto.

## <a name="create-the-data-bound-controls"></a>Creare i controlli con associazione a dati

Creare controlli che visualizzano i record cliente trascinando il `SalesOrderHeaders` dal nodo il **Zdroje dat** finestra di progettazione.

1. Nella finestra **Origini dati** fare clic sul menu a discesa del nodo **SalesOrderHeaders** e selezionare **Dettagli**.

2. Espandere il nodo **SalesOrderHeaders**.

3. Poiché per questo esempio alcuni campi non verranno visualizzati, fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuno**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. In questa procedura dettagliata si presuppone che l'utente finale non necessario visualizzare i dati.

4. Dalla finestra **Origini dati** trascinare il nodo **SalesOrderHeaders** nella riga della griglia sotto la riga contenente i pulsanti.

     Visual Studio genera l'XAML e il codice che crea un set di controlli associati a dati nella tabella **Product**. Per altre informazioni sulle XAML e codice generato, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Customer ID**.

6. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

7. Impostare la proprietà **IsReadOnly** per ognuna delle caselle di testo seguenti:

    - **Purchase Order Number**

    - **Sales Order ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>Caricare i dati dal servizio

Usare l'oggetto proxy del servizio per caricare i dati di vendita dal servizio. Assegnare quindi i dati restituiti per l'origine dati per il <xref:System.Windows.Data.CollectionViewSource> nella finestra WPF.

1. Nella finestra di progettazione, per creare il `Window_Loaded` gestore eventi, fare doppio clic sul collegamento: MainWindow

2. Sostituire il gestore eventi con il codice seguente. Assicurarsi di sostituire l'indirizzo *localhost* in questo codice con l'indirizzo dell'host locale nel computer di sviluppo.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Esplorare i record delle vendite

Aggiungere il codice che consente agli utenti di scorrere i record delle vendite usando i pulsanti **\<** e **>**.

1. Nella finestra di progettazione fare doppio clic sul pulsante **<** nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `backButton_Click` generato:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Tornare alla finestra di progettazione e fare doppio clic sul pulsante **>**.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `nextButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Aggiungere il codice seguente al gestore eventi `nextButton_Click` generato:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Salvare le modifiche ai record delle vendite

Aggiungere il codice che consente agli utenti di visualizzare e salvare le modifiche ai record delle vendite usando il pulsante **Salva modifiche**:

1. Nella finestra di progettazione fare doppio clic sul pulsante **Salva modifiche**.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Testare l'applicazione

Compilare ed eseguire l'applicazione per verificare che sia possibile visualizzare e aggiornare i record cliente:

1. Sul **compilare** menu, fare clic su **Compila soluzione**. Verificare che la soluzione venga compilata senza errori.

2. Premere **Ctrl**+**F5**.

     Visual Studio avvia il progetto **AdventureWorksService** senza eseguirne il debug.

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **AdventureWorksSalesEditor**.

4. Nel menu di scelta rapida (menu di scelta rapida) sotto **Debug**, fare clic su **Avvia nuova istanza**.

     Verrà eseguita l'applicazione. Verificare quanto segue:

    - Nelle caselle di testo vengono visualizzati campi di dati diversi dal primo record di vendite il cui ID ordine vendite è **71774**.

    - È possibile fare clic sui pulsanti **>** o **<** per spostarsi tra gli altri record delle vendite.

5. In uno dei record delle vendite digitare del testo nella casella **Commento**, quindi fare clic su **Salva modifiche**.

6. Chiudere l'applicazione, quindi avviarla di nuovo da Visual Studio.

7. Passare al record delle vendite modificato e verificare che la modifica sia presente dopo avere chiuso e riaperto l'applicazione.

8. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

- Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [WPF di associare controlli a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre-figlio, nei controlli WPF. Per altre informazioni, vedere [Procedura dettagliata: Visualizzazione di dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Cenni preliminari su WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Panoramica di Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Data Binding Panoramica (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)