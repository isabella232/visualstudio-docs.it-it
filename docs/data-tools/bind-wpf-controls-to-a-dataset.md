---
title: Associare controlli WPF a un set di dati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aef6236b896495f81e91cbdd7befd2923c013a33
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131960"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associare controlli WPF a un set di dati

In questa procedura dettagliata, si crea un'applicazione WPF che contiene i controlli con associazione a dati. I controlli vengono associati a record di prodotto incapsulati in un set di dati. È anche possibile aggiungere i pulsanti per scorrere i prodotti e salvare le modifiche ai record di prodotto.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un'applicazione WPF e di un set di dati generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un set di controlli con associazione a dati trascinando una tabella di dati dal **Zdroje dat** finestra da una finestra in WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record di prodotto.

- Creazione di un pulsante che consente di salvare le modifiche apportate dagli utenti ai record di prodotto nella tabella dati e nell'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Visual Studio

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorks Light (AdventureWorksLT) collegato a esso. È possibile scaricare il database AdventureWorksLT dal [archive CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- Set di dati e oggetti TableAdapter. Per altre informazioni, vedere [strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

- Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Creare il progetto

Creare un nuovo progetto WPF per visualizzare i record di prodotto.

1.  Avviare Visual Studio.

2.  Nel menu **File** selezionare **Nuovo** > **Progetto**.

3.  Espandere **Visual Basic** oppure **Visual c#**, quindi selezionare **Windows**.

4.  Selezionare il **WPF Application** modello di progetto.

5.  Nel **Name** casella, immettere **AdventureWorksProductsEditor** e quindi selezionare **OK**.

   Visual Studio crea il progetto AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Creare un set di dati per l'applicazione

Prima di creare controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungere il **Zdroje dat** finestra. In questa procedura dettagliata viene creato un set di dati da usare come modello di dati.

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

     Il **Zdroje dat** verrà visualizzata la finestra.

2.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Il **configurazione dell'origine dati** verrà visualizzata la procedura guidata.

3.  Nel **scegliere un tipo di origine dati** pagina, selezionare **Database**, quindi fare clic su **successivo**.

4.  Nel **scegliere un modello di Database** pagina, selezionare **set di dati**, quindi fare clic su **successivo**.

5.  Nel **Seleziona connessione dati** pagina, selezionare una delle opzioni seguenti:

    - Se una connessione dati al database AdventureWorksLT di esempio è disponibile nell'elenco a discesa, selezionarlo e quindi fare clic su **successivo**.

    - Fare clic su **nuova connessione**e creare una connessione al database AdventureWorksLT.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, selezionare la **Sì, Salva la connessione con nome** casella di controllo e quindi fare clic su **Avanti**.

7.  Nel **Scegli oggetti di Database** , espandere **tabelle**e quindi selezionare il **Product (SalesLT)** tabella.

8.  Scegliere **Fine**.

     Visual Studio aggiunge un nuovo `AdventureWorksLTDataSet.xsd` file per il progetto che aggiunge un che corrisponde **AdventureWorksLTDataSet** elemento per il **Zdroje dat** finestra. Il `AdventureWorksLTDataSet.xsd` file definisce un set di dati tipizzato denominato `AdventureWorksLTDataSet` e un oggetto TableAdapter denominato `ProductTableAdapter`. Più avanti in questa procedura dettagliata, l'oggetto `ProductTableAdapter` verrà usato per riempire il set di dati con i dati e salvare nuovamente le modifiche nel database.

9. Compilare il progetto.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modifica del metodo fill predefinito dell'oggetto TableAdapter

Per riempire il set di dati con i dati, usare il metodo `Fill` dell'oggetto `ProductTableAdapter`. Per impostazione predefinita, il metodo `Fill` riempie `ProductDataTable` in `AdventureWorksLTDataSet` con tutte le righe di dati della tabella Product. È possibile modificare questo metodo in modo da restituire solo un subset di righe. Per questa procedura dettagliata, modificare il metodo `Fill` in modo da restituire solo di prodotti con foto.

1.  Nelle **Esplora soluzioni**, fare doppio clic il *AdventureWorksLTDataSet* file.

     Viene aperto Progettazione DataSet.

2.  Nella finestra di progettazione, fare doppio clic il **riempire**, **GetData ()** eseguire una query e selezionare **configura**.

     Il **TableAdapter configurazione** verrà visualizzata la procedura guidata.

3.  Nel **immettere un'istruzione SQL** pagina, aggiungere la clausola WHERE seguente dopo il `SELECT` istruzione nella casella di testo.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  Scegliere **Fine**.

## <a name="define-the-user-interface"></a>Definire l'interfaccia utente

Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di scorrere e salvare le modifiche ai record di prodotti con questi pulsanti.

1.  Nelle **Esplora soluzioni**, fare doppio clic su *MainWindow. XAML*.

     Viene visualizzata la finestra di **WPF Designer**.

2.  Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Compilare il progetto.

## <a name="create-data-bound-controls"></a>Creare controlli associati a dati

Creare controlli che visualizzano i record cliente trascinando il `Product` dalla tabella il **Zdroje dat** finestra di progettazione WPF.

1.  Nel **Zdroje dat** finestra, fare clic sul menu a discesa per il **prodotto** nodo e selezionare **dettagli**.

2.  Espandere la **prodotto** nodo.

3.  Per questo esempio, alcuni campi non verranno visualizzati, quindi fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **None**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4.  Fare clic sul menu di riepilogo a discesa accanto al **ThumbNailPhoto** nodo e selezionare **immagine**.

    > [!NOTE]
    > Per impostazione predefinita, gli elementi di **Zdroje dat** finestra che rappresentano le immagini hanno il controllo predefinito impostato su **None**. dal momento che le immagini vengono archiviate come matrici di byte nei database e le matrici di byte possono contenere qualsiasi elemento, da una matrice semplice di byte al file eseguibile di un'applicazione di grandi dimensioni.

5.  Dal **Zdroje dat** finestra, trascinare le **prodotto** nodo nella riga della griglia sotto la riga che contiene i pulsanti.

     Visual Studio genera XAML che definisce un set di controlli associati ai dati di **prodotti** tabella. Genera inoltre il codice che carica i dati. Per altre informazioni sulle XAML e codice generato, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6.  Nella finestra di progettazione, selezionare la casella di testo accanto al **ID prodotto** etichetta.

7.  Nel **delle proprietà** finestra, seleziona la casella di controllo accanto al **IsReadOnly** proprietà.

## <a name="navigate-product-records"></a>Esplorare i record di prodotto

Aggiungere il codice che consente agli utenti di scorrere i record di prodotto usando il **\<** e **>** pulsanti.

1.  Nella finestra di progettazione, fare doppio clic il **<** pulsante nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo `backButton_Click` gestore dell'evento per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Modificare il `Window_Loaded` gestore eventi, in modo che il `ProductViewSource`, `AdventureWorksLTDataSet`, e `AdventureWorksLTDataSetProductTableAdapter` dall'esterno del metodo e accessibili all'intero form. Dichiarare solo questi come globale al form e assegnarli all'interno di `Window_Loaded` gestore dell'evento simile al seguente:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  Aggiungere il codice seguente al gestore eventi `backButton_Click`:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  Tornare alla finestra di progettazione e fare doppio clic il **>** pulsante.

5.  Aggiungere il codice seguente al gestore eventi `nextButton_Click`:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Salvare le modifiche ai record di prodotto

Aggiungere il codice che consente agli utenti di salvare le modifiche ai record di prodotto usando il **salvare le modifiche** pulsante.

1.  Nella finestra di progettazione, fare doppio clic il **salvare le modifiche** pulsante.

     Visual Studio apre il file code-behind e crea un nuovo `saveButton_Click` gestore dell'evento per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Aggiungere il codice seguente al gestore eventi `saveButton_Click`:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Questo esempio usa il metodo `Save` di `TableAdapter` per salvare le modifiche. Tale approccio è appropriato a questa procedura dettagliata, in quanto viene modificata una sola tabella dati. Se è necessario salvare modifiche a più tabelle dati, è possibile usare in alternativa il metodo `UpdateAll` di `TableAdapterManager` generato da Visual Studio con il set di dati. Per altre informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testare l'applicazione

Compilare ed eseguire l'applicazione. Verificare che sia possibile visualizzare e aggiornare i record di prodotto.

1.  Premere **F5**.

     L'applicazione verrà compilata ed eseguita. Verificare quanto segue:

    - Nelle caselle di testo vengono visualizzati i dati del primo record di prodotto contenente una foto. Questo prodotto include l'ID prodotto è 713 e il nome **Long-Sleeve Logo Jersey, S**.

    - È possibile fare clic il **>** oppure **<** pulsanti per spostarsi tra gli altri record di prodotto.

2.  In uno dei record di prodotto, modificare il **dimensioni** valore e quindi fare clic su **salvare le modifiche**.

3.  Chiudere l'applicazione e quindi riavviare l'applicazione premendo **F5** in Visual Studio.

4.  Passare al record di prodotto modificato e verificare che la modifica sia presente.

5.  Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver completato questa procedura dettagliata, è possibile provare le attività correlate seguenti:

- Informazioni su come usare il **Zdroje dat** controlli finestra in Visual Studio per eseguire l'associazione WPF ad altri tipi di origini dati. Per altre informazioni, vedere [WPF di associare controlli a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Informazioni su come usare il **Zdroje dat** finestra in Visual Studio per visualizzare i dati correlati (vale a dire i dati in una relazione padre-figlio) nei controlli WPF. Per altre informazioni, vedere [procedura dettagliata: visualizzare dati correlati in un'app WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Panoramica sul data binding](/dotnet/framework/wpf/data/data-binding-overview)
