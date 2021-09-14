---
title: Associare controlli WPF a un servizio di dati WCF
description: Associare i controlli WPF a un servizio dati WCF in Visual Studio. I controlli sono associati ai record dei clienti incapsulati in un servizio dati WCF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 214975aa03da6181108e2d10046610d1afa20580
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631571"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associare controlli WPF a un servizio di dati WCF

In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli sono associati ai record dei clienti incapsulati in un servizio dati WCF. Verranno inoltre aggiunti i pulsanti che i clienti possono usare per visualizzare e aggiornare i record.

Vengono illustrate le attività seguenti:

- Creazione di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un servizio dati WCF che espone i dati nel Entity Data Model a un'applicazione WPF.

- Creazione di un set di controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati** in WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record cliente.

- Creazione di un pulsante che salva le modifiche ai dati nei controlli nel servizio dati WCF e nell'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Visual Studio

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal sito [Web CodePlex.](https://archive.codeplex.com/?p=SqlServerSamples)

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modelli di dati in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Modelli di Entity Data Model e ADO.NET Entity Framework. Per altre informazioni, vedere Entity Framework [panoramica di](/dotnet/framework/data/adonet/ef/overview).

- Data binding WPF. Per altre informazioni, vedere [Panoramica sul data binding](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Creare il progetto di servizio

1. Iniziare questa procedura dettagliata creando un progetto di applicazione Web C# o **Visual Basic ASP.NET web.** Assegnare al progetto **il nome AdventureWorksService**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Default.aspx** e scegliere **Elimina**. Questo file non è necessario per la procedura dettagliata.

## <a name="create-an-entity-data-model-for-the-service"></a>Creare un Entity Data Model per il servizio

Per esporre i dati a un'applicazione usando un servizio dati WCF, è necessario definire un modello di dati per il servizio. WCF Data Service supporta due tipi di modelli di dati: Entity Data Models e modelli di dati personalizzati definiti tramite oggetti CLR (Common Language Runtime) che implementano <xref:System.Linq.IQueryable%601> l'interfaccia . In questa procedura dettagliata, viene creato un modello Entity Data Model per il modello di dati.

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nell'elenco Modelli installati fare clic su **Dati**, quindi selezionare l'elemento di progetto **ADO.NET Entity Data Model**.

3. Modificare il nome in `AdventureWorksModel.edmx` e fare clic su **Aggiungi**.

     Verrà aperta la **Procedura guidata Entity Data Model**.

4. Nella pagina **Scegli contenuto del modello** fare clic su **Genera da database**, quindi su **Avanti**.

5. Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:

    - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.

    - Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.

6. Nella pagina **Seleziona connessione dati** verificare che l'opzione **Salva impostazioni di connessione entità in App.Config come** sia selezionata, quindi fare clic su **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **Tabelle**, quindi selezionare la tabella **SalesOrderHeader**.

8. Fare clic su **Fine**.

## <a name="create-the-service"></a>Creare il servizio

Creare un servizio dati WCF per esporre i dati nel Entity Data Model a un'applicazione WPF:

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

2. Nell'elenco **Modelli installati** fare clic su **Web**, quindi selezionare l'elemento di progetto **WCF Data Services**.

3. Nella casella **Nome** digitare `AdventureWorksService.svc` e fare clic su **Aggiungi**.

     Visual Studio aggiunge `AdventureWorksService.svc` l'oggetto al progetto.

## <a name="configure-the-service"></a>Configurare il servizio

È necessario configurare il servizio in modo da usare il modello Entity Data Model creato:

1. Nel `AdventureWorks.svc` file di codice sostituire la dichiarazione **di classe AdventureWorksService** con il codice seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     Questo codice aggiorna la **classe AdventureWorksService,** in modo che derivi da un oggetto che opera sulla classe del contesto dell'oggetto nel <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` Entity Data Model. Aggiorna inoltre il metodo `InitializeService` per consentire ai client del servizio l'accesso completo in lettura/scrittura all'entità `SalesOrderHeader`.

2. Compilare il progetto e verificare che non siano presenti errori.

## <a name="create-the-wpf-client-application"></a>Creare l'applicazione client WPF

Per visualizzare i dati dal servizio dati WCF, creare una nuova applicazione WPF con un'origine dati basata sul servizio. Più avanti in questa procedura dettagliata, verranno aggiunti all'applicazione i controlli associati a dati.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi** e selezionare **Nuovo progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#** o **Visual Basic**, quindi selezionare **Finestre**.

3. Selezionare il modello di progetto **Applicazione WPF**.

4. Nella casella **Nome** digitare `AdventureWorksSalesEditor` e fare clic su **OK**.

   Visual Studio aggiunge il `AdventureWorksSalesEditor` progetto alla soluzione.

5. Scegliere **Mostra origini dati** dal menu **Dati**.

   Verrà visualizzata la finestra **Origini dati**.

6. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Verrà **visualizzata la Configurazione guidata** origine dati.

7. Nella pagina **Seleziona un tipo di origine dati** della procedura guidata selezionare **Servizio**, quindi fare clic su **Avanti**.

8. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

   Visual Studio cerca i servizi disponibili nella soluzione corrente e aggiunge `AdventureWorksService.svc` all'elenco dei servizi disponibili nella **casella** Servizi .

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

## <a name="create-the-data-bound-controls"></a>Creare i controlli associati a dati

Creare controlli che visualizzano i record dei clienti trascinando il `SalesOrderHeaders` nodo dalla finestra **Origini** dati alla finestra di progettazione.

1. Nella finestra **Origini dati** fare clic sul menu a discesa del nodo **SalesOrderHeaders** e selezionare **Dettagli**.

2. Espandere il nodo **SalesOrderHeaders**.

3. Poiché per questo esempio alcuni campi non verranno visualizzati, fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuno**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **Rowguid**

    Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. Per questa procedura dettagliata, si supponga che l'utente finale non deve visualizzare questi dati.

4. Dalla finestra **Origini dati** trascinare il nodo **SalesOrderHeaders** nella riga della griglia sotto la riga contenente i pulsanti.

     Visual Studio genera l'XAML e il codice che crea un set di controlli associati a dati nella tabella **Product**. Per altre informazioni sul codice XAML e sul codice generato, vedere [Associare](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)i controlli WPF ai dati in Visual Studio .

5. Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Customer ID**.

6. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

7. Impostare la proprietà **IsReadOnly** per ognuna delle caselle di testo seguenti:

    - **Numero ordine di acquisto**

    - **Sales Order ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>Caricare i dati dal servizio

Usare l'oggetto proxy del servizio per caricare i dati di vendita dal servizio. Assegnare quindi i dati restituiti all'origine dati per <xref:System.Windows.Data.CollectionViewSource> nella finestra WPF.

1. Nella finestra di progettazione, per creare il `Window_Loaded` gestore eventi, fare doppio clic sul collegamento: **MainWindow**

2. Sostituire il gestore eventi con il codice seguente. Assicurarsi di sostituire l'indirizzo *localhost* in questo codice con l'indirizzo dell'host locale nel computer di sviluppo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet2":::

## <a name="navigate-sales-records"></a>Esplorare i record di vendita

Aggiungere il codice che consente agli utenti di scorrere i record di vendita usando i **\<** and **>** pulsanti .

1. Nella finestra di progettazione fare doppio clic sul **<** pulsante nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `backButton_Click` generato:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. Tornare alla finestra di progettazione e fare doppio clic sul **>** pulsante.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `nextButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Aggiungere il codice seguente al gestore eventi `nextButton_Click` generato:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>Salvare le modifiche ai record delle vendite

Aggiungere il codice che consente agli utenti di visualizzare e salvare le modifiche ai record delle vendite usando il pulsante **Salva modifiche**:

1. Nella finestra di progettazione fare doppio clic sul pulsante **Salva modifiche**.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `saveButton_Click`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet5":::

## <a name="test-the-application"></a>Testare l'applicazione

Compilare ed eseguire l'applicazione per verificare che sia possibile visualizzare e aggiornare i record cliente:

1. Scegliere **Compila** soluzione dal menu **Compila**. Verificare che la soluzione venga compilata senza errori.

2. Premere **CTRL** + **F5.**

     Visual Studio avvia il progetto **AdventureWorksService** senza eseguirne il debug.

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **AdventureWorksSalesEditor**.

4. Nel menu di scelta rapida in **Debug** fare clic su **Avvia nuova istanza**.

     Verrà eseguita l'applicazione. Verificare gli elementi seguenti:

    - Nelle caselle di testo vengono visualizzati campi di dati diversi dal primo record di vendite il cui ID ordine vendite è **71774**.

    - È possibile fare clic sui **>** pulsanti o per spostarsi tra altri record di **<** vendita.

5. In uno dei record delle vendite digitare del testo nella casella **Commento**, quindi fare clic su **Salva modifiche**.

6. Chiudere l'applicazione, quindi avviarla di nuovo da Visual Studio.

7. Passare al record delle vendite modificato e verificare che la modifica sia presente dopo avere chiuso e riaperto l'applicazione.

8. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

- Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre-figlio, nei controlli WPF. Per altre informazioni, vedere [Procedura dettagliata: Visualizzazione di dati correlati in un'applicazione WPF.](../data-tools/display-related-data-in-wpf-applications.md)

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Panoramica di WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework panoramica (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Panoramica del data binding (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
