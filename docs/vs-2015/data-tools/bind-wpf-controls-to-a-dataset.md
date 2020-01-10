---
title: Associare controlli WPF a un set di dati | Microsoft Docs
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852148"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associare controlli WPF a un set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record di prodotto incapsulati in un set di dati. Si aggiungeranno inoltre i pulsanti per scorrere i prodotti e salvare le modifiche ai record di prodotto.

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un'applicazione WPF e di un set di dati generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un set di controlli associati a dati mediante il trascinamento di una tabella dati dalla finestra **Origini dati** a una finestra di WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record di prodotto.

- Creazione di un pulsante che consente di salvare le modifiche apportate dagli utenti ai record di prodotto nella tabella dati e nell'origine dati sottostante.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](https://codeplex.com/SqlServerSamples).

  Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- Set di dati e oggetti TableAdapter. Per altre informazioni, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Uso di WPF Designer. Per ulteriori informazioni, vedere [Cenni preliminari su WPF e Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Creare il progetto
 Creare un nuovo progetto WPF. Il progetto visualizzerà i record di prodotto.

#### <a name="to-create-the-project"></a>Per creare il progetto

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Espandere **Visual Basic** o **Visual C#** , quindi selezionare **Finestre**.

4. Selezionare il modello di progetto **Applicazione WPF**.

5. Digitare `AdventureWorksProductsEditor` nella casella **Nome** e quindi fare clic su **OK**.

     Visual Studio crea il progetto `AdventureWorksProductsEditor`.

## <a name="create-a-dataset-for-the-application"></a>Creare un set di dati per l'applicazione
 Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**. In questa procedura dettagliata viene creato un set di dati da usare come modello di dati.

#### <a name="to-create-a-dataset"></a>Per creare un set di dati

1. Scegliere **Mostra origini dati** dal menu **Dati**.

     Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Verrà avviata la **Configurazione guidata origine dati**.

3. Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.

4. Nella pagina **Scegli modello database** selezionare **Dataset** e scegliere **Avanti**.

5. Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:

    - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente, quindi scegliere **Avanti**.

    - Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.

6. Nella pagina **Salva la stringa di connessione nel file di configurazione applicazione** selezionare la casella di controllo **Sì, salva la connessione con nome**, quindi fare clic su **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **Tables**, quindi selezionare la tabella **Product (SalesLT)** .

8. Scegliere **Fine**.

     Visual Studio aggiunge un nuovo file AdventureWorksLTDataSet. xsd al progetto e aggiunge un elemento **AdventureWorksLTDataSet** corrispondente alla finestra **origini dati** . Il file AdventureWorksLTDataSet.xsd definisce un set di dati tipizzato denominato `AdventureWorksLTDataSet` e un oggetto TableAdapter denominato `ProductTableAdapter`. Più avanti in questa procedura dettagliata, l'oggetto `ProductTableAdapter` verrà usato per riempire il set di dati con i dati e salvare nuovamente le modifiche nel database.

9. Compilazione del progetto.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modificare il metodo Fill predefinito del TableAdapter
 Per riempire il set di dati con i dati, usare il metodo `Fill` dell'oggetto `ProductTableAdapter`. Per impostazione predefinita, il metodo `Fill` riempie `ProductDataTable` in `AdventureWorksLTDataSet` con tutte le righe di dati della tabella Product. È possibile modificare questo metodo in modo da restituire solo un subset di righe. Per questa procedura dettagliata, modificare il metodo `Fill` in modo da restituire solo di prodotti con foto.

#### <a name="to-load-product-rows-that-have-photos"></a>Per caricare le righe di prodotti con foto

1. In **Esplora soluzioni**fare doppio clic sul file AdventureWorksLTDataSet. xsd.

     Viene aperto Progettazione DataSet.

2. Nella finestra di progettazione fare clic con il pulsante destro del mouse sulla query **Fill, GetData ()** e scegliere **Configura**.

     Verrà avviata la **Configurazione guidata TableAdapter**.

3. Nella pagina **Immettere un'istruzione SQL** aggiungere la clausola WHERE seguente dopo l'istruzione `SELECT` nella casella di testo.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Scegliere **Fine**.

## <a name="define-the-user-interface"></a>Definire l'interfaccia utente
 Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di scorrere e salvare le modifiche ai record di prodotti con questi pulsanti.

#### <a name="to-define-the-user-interface-of-the-window"></a>Per definire l'interfaccia utente della finestra

1. In **Esplora soluzioni**fare doppio clic su MainWindow. XAML.

     La finestra verrà aperta in WPF Designer.

2. Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Compilazione del progetto.

## <a name="createdata-bound-controls"></a>Controlli associati a CREATEData
 Creare controlli che consentono di visualizzare i record dei clienti trascinando la tabella `Product` dalla finestra **origini dati** a WPF Designer.

#### <a name="to-create-data-bound-controls"></a>Per creare i controlli associati a dati

1. Nella finestra **Origini dati** fare clic sul menu a discesa del nodo **Product** e selezionare **Dettagli**.

2. Espandere il nodo **Product**.

3. Poiché per questo esempio alcuni campi non verranno visualizzati, fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuno**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. Fare clic sul menu a discesa accanto al nodo **ThumbNailPhoto** e selezionare **Image**.

    > [!NOTE]
    > Per impostazione predefinita, il controllo predefinito degli elementi nella finestra **Origini dati** che rappresentano immagini è impostato su **Nessuno**, dal momento che le immagini vengono archiviate come matrici di byte nei database e le matrici di byte possono contenere qualsiasi elemento, da una matrice semplice di byte al file eseguibile di un'applicazione di grandi dimensioni.

5. Dalla finestra **Origini dati** trascinare il nodo **Product** nella riga della griglia sotto la riga contenente i pulsanti.

     Visual Studio genera il codice XAML che definisce un set di controlli associati a dati nella tabella **Products**. Genera inoltre il codice che carica i dati. Per altre informazioni sul codice XAML e sul codice generato, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Product ID**.

7. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

## <a name="navigating-product-records"></a>Esplorazione di record di prodotto
 Aggiungere il codice che consente agli utenti di scorrere i record di prodotto usando i pulsanti **\<** e **>** .

#### <a name="to-enable-users-to-navigate-product-records"></a>Per consentire agli utenti di esplorare i record di prodotto

1. Nella finestra di progettazione fare doppio clic sul pulsante **<** nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Modificare il gestore eventi `Window_Loaded` in modo che `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` siano esterni al metodo e accessibili all'intero form. Dichiarare solo questi elementi come globali per il form e assegnarli all'interno del gestore dell'evento `Window_Loaded` simile al seguente:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Aggiungere il codice seguente al gestore eventi `backButton_Click` :

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Tornare alla finestra di progettazione e fare doppio clic sul pulsante **>** .

5. Aggiungere il codice seguente al gestore eventi `nextButton_Click` :

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>Da SaveChanges a record di prodotto
 Aggiungere il codice che consente agli utenti di salvare le modifiche ai record di prodotto usando il pulsante **Salva modifiche**.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Per aggiungere la possibilità di salvare le modifiche ai record di prodotto

1. Nella finestra di progettazione fare doppio clic sul pulsante **Salva modifiche**.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `saveButton_Click` :

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > Questo esempio usa il metodo `Save` di `TableAdapter` per salvare le modifiche. Tale approccio è appropriato a questa procedura dettagliata, in quanto viene modificata una sola tabella dati. Se è necessario salvare modifiche a più tabelle dati, è possibile usare in alternativa il metodo `UpdateAll` di `TableAdapterManager` generato da Visual Studio con il set di dati. Per altre informazioni, vedere [Panoramica di TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

## <a name="test-the-application"></a>Testare l'applicazione
 Compilare ed eseguire l'applicazione. Verificare che sia possibile visualizzare e aggiornare i record di prodotto.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Premere **F5**.

     L'applicazione verrà compilata ed eseguita. Verificare quanto segue:

    - Nelle caselle di testo vengono visualizzati i dati del primo record di prodotto contenente una foto. L'ID prodotto è 713, mentre il nome è **Long-Sleeve Logo Jersey, S**.

    - È possibile fare clic sui pulsanti **>** o **<** per spostarsi tra gli altri record di prodotto.

2. In uno dei record di prodotto modificare il valore **Dimensione**, quindi fare clic su **Salva modifiche**.

3. Chiudere l'applicazione, quindi riavviarla premendo **F5** in Visual Studio.

4. Passare al record di prodotto modificato e verificare che la modifica sia presente.

5. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

- Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [associare controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre-figlio, nei controlli WPF. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [associare controlli WPF ai dati in Visual](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) Studio [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) Cenni preliminari sull' [associazione dati](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211) Panoramica di [WPF e Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)
