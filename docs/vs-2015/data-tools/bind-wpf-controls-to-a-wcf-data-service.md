---
title: Associare controlli WPF a un servizio dati WCF | Microsoft Docs
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3d1aab68e3dc9f33e0b3e9f9a5665d59f6f2ddc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299406"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associare controlli WPF a un servizio di dati WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record cliente incapsulati in un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Verranno inoltre aggiunti i pulsanti che i clienti possono usare per visualizzare e aggiornare i record.

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] che espone i dati nel Entity Data Model a un'applicazione WPF.

- Creazione di un set di controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati** in WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record cliente.

- Creazione di un pulsante che consente di salvare le modifiche apportate ai dati nei controlli nel [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] e nell'origine dati sottostante.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](https://go.microsoft.com/fwlink/?linkid=87843).

  Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- WCF Data Services. Per ulteriori informazioni, vedere [Panoramica](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- Modelli di dati in [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].

- Modelli di Entity Data Model e ADO.NET Entity Framework. Per ulteriori informazioni, vedere [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Uso di WPF Designer. Per ulteriori informazioni, vedere [Cenni preliminari su WPF e Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-service-project"></a>Creare il progetto di servizio
 Avviare la procedura dettagliata creando un progetto per un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

#### <a name="to-create-the-service-project"></a>Per creare il progetto di servizio

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Espandere **Visual C#** o **Visual Basic**, quindi selezionare **Web**.

4. Selezionare il modello di progetto **Applicazione Web ASP.NET**.

5. Nella casella **nome** Digitare `AdventureWorksService` e fare clic su **OK**.

     Visual Studio crea il progetto `AdventureWorksService`.

6. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Default.aspx** e scegliere **Elimina**. Questo file non è necessario per la procedura dettagliata.

## <a name="create-an-entity-data-model-for-the-service"></a>Creare una Entity Data Model per il servizio
 Per esporre i dati in un'applicazione usando un'istanza di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], è necessario definire un modello di dati per il servizio. Il [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] supporta due tipi di modelli di dati: Entity Data Models e modelli di dati personalizzati definiti tramite oggetti Common Language Runtime (CLR) che implementano l'interfaccia <xref:System.Linq.IQueryable%601>. In questa procedura dettagliata, viene creato un modello Entity Data Model per il modello di dati.

#### <a name="to-create-an-entity-data-model"></a>Per creare un modello Entity Data Model

1. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nell'elenco Modelli installati fare clic su **Dati**, quindi selezionare l'elemento di progetto **ADO.NET Entity Data Model**.

3. Modificare il nome in `AdventureWorksModel.edmx`, quindi fare clic su **Aggiungi**.

     Verrà aperta la **Procedura guidata Entity Data Model**.

4. Nella pagina **Scegli contenuto del modello** fare clic su **Genera da database**, quindi su **Avanti**.

5. Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:

    - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.

    - Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.

6. Nella pagina **Seleziona connessione dati** verificare che l'opzione **Salva impostazioni di connessione entità in App.Config come** sia selezionata, quindi fare clic su **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **Tabelle**, quindi selezionare la tabella **SalesOrderHeader**.

8. Scegliere **Fine**.

## <a name="create-the-service"></a>Creare il servizio
 Creare una [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] per esporre i dati nel Entity Data Model a un'applicazione WPF.

#### <a name="to-create-the-service"></a>Per creare il servizio

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Nell'elenco Modelli installati fare clic su **Web**, quindi selezionare l'elemento di progetto **WCF Data Services**.

3. Nella casella **nome** Digitare `AdventureWorksService.svc`e fare clic su **Aggiungi**.

     Visual Studio aggiunge il `AdventureWorksService.svc` al progetto.

## <a name="configure-the-service"></a>Configurare il servizio
 È necessario configurare il servizio in modo da usare il modello Entity Data Model creato.

#### <a name="to-configure-the-service"></a>Per configurare il servizio

1. Nel file di codice `AdventureWorks.svc` sostituire la dichiarazione di classe `AdventureWorksService` con il codice seguente.

     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]

     Questo codice aggiorna la classe `AdventureWorksService`, in modo che derivi da un <xref:System.Data.Services.DataService%601> che opera sulla classe del contesto dell'oggetto `AdventureWorksLTEntities` nel Entity Data Model. Aggiorna inoltre il metodo `InitializeService` per consentire ai client del servizio l'accesso completo in lettura/scrittura all'entità `SalesOrderHeader`.

2. Compilare il progetto e verificare che non siano presenti errori.

## <a name="create-the-wpf-client-application"></a>Creare l'applicazione client WPF
 Per visualizzare i dati di [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], creare una nuova applicazione WPF con un'origine dati basata sul servizio. Più avanti in questa procedura dettagliata, verranno aggiunti all'applicazione i controlli associati a dati.

#### <a name="to-create-the-wpf-client-application"></a>Per creare l'applicazione client WPF

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi** e selezionare **Nuovo progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#** o **Visual Basic**, quindi selezionare **Finestre**.

3. Selezionare il modello di progetto **Applicazione WPF**.

4. Nella casella **Nome** digitare `AdventureWorksSalesEditor` e fare clic su **OK**.

     Visual Studio aggiunge il progetto `AdventureWorksSalesEditor` alla soluzione.

5. Scegliere **Mostra origini dati** dal menu **Dati**.

     Verrà visualizzata la finestra **Origini dati**.

6. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Verrà avviata la **Configurazione guidata origine dati**.

7. Nella pagina **Seleziona un tipo di origine dati** della procedura guidata selezionare **Servizio**, quindi fare clic su **Avanti**.

8. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

     Visual Studio cerca i servizi disponibili nella soluzione corrente e aggiunge `AdventureWorksService.svc` all'elenco dei servizi disponibili nella casella **Servizi** .

9. Nella casella **spazio dei nomi** Digitare `AdventureWorksService`.

10. Nella casella **Servizi** fare clic su **AdventureWorksService.svc**, quindi su **OK**.

     Visual Studio Scarica le informazioni sul servizio e quindi torna alla **Configurazione guidata origine dati** .

11. Nella pagina **Aggiungi riferimento al servizio** fare clic su **Fine**.

     Visual Studio aggiunge i nodi che rappresentano i dati restituiti dal servizio nella finestra **Origini dati**.

## <a name="define-the-user-interface-of-the-window"></a>Definire l'interfaccia utente della finestra
 Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di visualizzare e aggiornare i record delle vendite tramite questi pulsanti.

#### <a name="to-create-the-window-layout"></a>Per creare il layout della finestra

1. In **Esplora soluzioni** fare doppio clic su MainWindow.xaml.

     La finestra verrà aperta in WPF Designer.

2. Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

    ```
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
 Creare controlli che consentono di visualizzare i record dei clienti trascinando il nodo `SalesOrderHeaders` dalla finestra **origini dati** alla finestra di progettazione.

#### <a name="to-create-the-data-bound-controls"></a>Per creare i controlli associati a dati

1. Nella finestra **Origini dati** fare clic sul menu a discesa del nodo **SalesOrderHeaders** e selezionare **Dettagli**.

2. Espandere il nodo **SalesOrderHeaders**.

3. Poiché per questo esempio alcuni campi non verranno visualizzati, fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuno**:

   - **CreditCardApprovalCode**

   - **ModifiedDate**

   - **OnlineOrderFlag**

   - **RevisionNumber**

   - **rowguid**

     Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. Per questa procedura dettagliata, si supponga che l'utente finale non debba visualizzare questi dati.

4. Dalla finestra **Origini dati** trascinare il nodo **SalesOrderHeaders** nella riga della griglia sotto la riga contenente i pulsanti.

    Visual Studio genera l'XAML e il codice che crea un set di controlli associati a dati nella tabella **Product**. Per altre informazioni sul codice XAML e sul codice generato, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

5. Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Customer ID**.

6. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

7. Impostare la proprietà **IsReadOnly** per ognuna delle caselle di testo seguenti:

   - **Purchase Order Number**

   - **Sales Order ID**

   - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>Caricare i dati dal servizio
 Utilizzare l'oggetto proxy del servizio per caricare i dati di vendita dal servizio. Assegnare quindi i dati restituiti all'origine dati per il <xref:System.Windows.Data.CollectionViewSource> nella finestra WPF.

#### <a name="to-load-the-data-from-the-service"></a>Per caricare i dati dal servizio

1. Nella finestra di progettazione, per creare il `Window_Loaded` gestore eventi, fare doppio clic sul collegamento: **MainWindow**

2. Sostituire il gestore eventi con il codice seguente. Assicurarsi di sostituire l'indirizzo *localhost* in questo codice con l'indirizzo dell'host locale nel computer di sviluppo.

     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]

## <a name="navigatesales-records"></a>Record Navigatesales
 Aggiungere il codice che consente agli utenti di scorrere i record delle vendite usando i pulsanti **\<** e **>** .

#### <a name="to-enable-users-to-navigate-sales-records"></a>Per consentire agli utenti di esplorare i record delle vendite

1. Nella finestra di progettazione fare doppio clic sul pulsante **<** nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `backButton_Click` generato:

     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]

3. Tornare alla finestra di progettazione e fare doppio clic sul pulsante **>** .

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `nextButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Aggiungere il codice seguente al gestore eventi `nextButton_Click` generato:

     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]

## <a name="saving-changes-to-sales-records"></a>Salvataggio delle modifiche ai record delle vendite
 Aggiungere il codice che consente agli utenti di visualizzare e salvare le modifiche ai record delle vendite usando il pulsante **Salva modifiche**.

#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Per aggiungere la possibilità di salvare le modifiche ai record delle vendite

1. Nella finestra di progettazione fare doppio clic sul pulsante **Salva modifiche**.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]

## <a name="testing-the-application"></a>Test dell'applicazione
 Compilare ed eseguire l'applicazione per verificare che sia possibile visualizzare e aggiornare i record cliente.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Nel menu **Compila** fare clic su **Compila soluzione**. Verificare che la soluzione venga compilata senza errori.

2. Premere **CTRL + F5**.

     Visual Studio avvia il progetto **AdventureWorksService** senza eseguirne il debug.

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **AdventureWorksSalesEditor**.

4. Scegliere **Debug** dal menu di scelta rapida, quindi **Avvia nuova istanza**.

     Verrà eseguita l'applicazione. Verificare quanto segue:

    - Nelle caselle di testo vengono visualizzati campi di dati diversi dal primo record di vendite il cui ID ordine vendite è **71774**.

    - È possibile fare clic sui pulsanti **>** o **<** per spostarsi tra gli altri record delle vendite.

5. In uno dei record delle vendite digitare del testo nella casella **Commento**, quindi fare clic su **Salva modifiche**.

6. Chiudere l'applicazione, quindi avviarla di nuovo da Visual Studio.

7. Passare al record delle vendite modificato e verificare che la modifica sia presente dopo avere chiuso e riaperto l'applicazione.

8. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

- Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre-figlio, nei controlli WPF. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [associare controlli WPF a un set](../data-tools/bind-wpf-controls-to-a-dataset.md) di dati [Cenni](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb) preliminari [Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0) Panoramica di [WPF e Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) Cenni preliminari sull' [associazione dati](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
