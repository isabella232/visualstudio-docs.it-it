---
title: Associare controlli WPF a un set di dati
description: Creare un'applicazione WPF in Visual Studio che contiene controlli associati a dati, associati a record di prodotto incapsulati in un set di dati.
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c0913e3d4f54f312e7d706ec6ab9771732e7b85c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059314"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associare controlli WPF a un set di dati

In questa procedura dettagliata viene creata un'applicazione WPF che contiene controlli associati a dati. I controlli vengono associati a record di prodotto incapsulati in un set di dati. È anche possibile aggiungere pulsanti per esplorare i prodotti e salvare le modifiche ai record dei prodotti.

Vengono illustrate le attività seguenti:

- Creazione di un'applicazione WPF e di un set di dati generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un set di controlli associati a dati mediante il trascinamento di una tabella dati dalla finestra **Origini dati** a una finestra di WPF Designer.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record di prodotto.

- Creazione di un pulsante che consente di salvare le modifiche apportate dagli utenti ai record di prodotto nella tabella dati e nell'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Visual Studio

- Accesso a un'istanza in esecuzione SQL Server o SQL Server Express a cui è collegato il database di esempio AdventureWorks Light (AdventureWorksLT). È possibile scaricare il database AdventureWorksLT [dall'archivio CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- Set di dati e oggetti TableAdapter. Per altre informazioni, vedere [Strumenti set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [TableAdapter.](../data-tools/create-and-configure-tableadapters.md)

- Data binding WPF. Per altre informazioni, vedere [Cenni preliminari sul data binding.](/dotnet/desktop-wpf/data/data-binding-overview)

## <a name="create-the-project"></a>Creare il progetto

Creare un nuovo progetto WPF per visualizzare i record di prodotto.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

2. Scegliere **Nuovo** dal  menu File > **Project**.

3. Espandere **Visual Basic** o **Visual C#**, quindi selezionare **Finestre**.

4. Selezionare il **modello di progetto App WPF.**

5. Nella casella **Nome** immettere **AdventureWorksProductsEditor** e quindi selezionare **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

3. Cercare il modello di progetto **App WPF** C# e seguire i passaggi per creare il progetto, denominando il progetto **AdventureWorksProductsEditor.**

::: moniker-end

   Visual Studio crea il progetto AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Creare un set di dati per l'applicazione

Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**. In questa procedura dettagliata viene creato un set di dati da usare come modello di dati.

1. Scegliere **Mostra origini dati** dal menu **Dati**.

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Verrà **visualizzata la Configurazione guidata** origine dati.

3. Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.

4. Nella pagina **Scegli modello database** selezionare **Dataset** e scegliere **Avanti**.

5. Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:

   - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente, quindi scegliere **Avanti**.

   - Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.

6. Nella pagina **Salva la stringa di connessione nel file di configurazione applicazione** selezionare la casella di controllo **Sì, salva la connessione con nome**, quindi fare clic su **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **Tables**, quindi selezionare la tabella **Product (SalesLT)**.

8. Fare clic su **Fine**.

   Visual Studio aggiunge un nuovo file al progetto e aggiunge un elemento `AdventureWorksLTDataSet.xsd` **AdventureWorksLTDataSet** corrispondente alla **finestra Origini** dati. Il `AdventureWorksLTDataSet.xsd` file definisce un set di dati tipizzato denominato e un oggetto `AdventureWorksLTDataSet` TableAdapter denominato `ProductTableAdapter` . Più avanti in questa procedura dettagliata, l'oggetto `ProductTableAdapter` verrà usato per riempire il set di dati con i dati e salvare nuovamente le modifiche nel database.

9. Compilare il progetto.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modificare il metodo di riempimento predefinito dell'oggetto TableAdapter

Per riempire il set di dati con i dati, usare il metodo `Fill` dell'oggetto `ProductTableAdapter`. Per impostazione predefinita, il metodo `Fill` riempie `ProductDataTable` in `AdventureWorksLTDataSet` con tutte le righe di dati della tabella Product. È possibile modificare questo metodo in modo da restituire solo un subset di righe. Per questa procedura dettagliata, modificare il metodo `Fill` in modo da restituire solo di prodotti con foto.

1. In **Esplora soluzioni** fare doppio clic sul file *AdventureWorksLTDataSet.xsd*.

     Viene aperto Progettazione DataSet.

2. Nella finestra di progettazione fare clic con il pulsante destro del mouse sulla query **Fill**, **GetData()** e scegliere **Configura**.

     Verrà avviata la **Configurazione guidata TableAdapter**.

3. Nella pagina **Immettere un'istruzione SQL** aggiungere la clausola WHERE seguente dopo l'istruzione `SELECT` nella casella di testo.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Fare clic su **Fine**.

## <a name="define-the-user-interface"></a>Definire l'interfaccia utente

Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di scorrere e salvare le modifiche ai record di prodotti con questi pulsanti.

1. In **Esplora soluzioni** fare doppio clic su *MainWindow.xaml*.

    La finestra viene aperta in **WPF Designer.**

2. Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75">&lt;</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">&gt;</Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Compilare il progetto.

## <a name="create-data-bound-controls"></a>Creare controlli associati a dati

Creare controlli che visualizzano i record dei clienti trascinando `Product` la tabella dalla finestra **Origini** dati a WPF Designer.

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

     Visual Studio genera il codice XAML che definisce un set di controlli associati a dati nella tabella **Products**. Genera inoltre il codice che carica i dati. Per altre informazioni sul codice e sul codice XAML generato, vedere [Associare i controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Product ID**.

7. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

## <a name="navigate-product-records"></a>Esplorare i record dei prodotti

Aggiungere codice che consente agli utenti di scorrere i record dei prodotti usando i **\<** and **>** pulsanti.

1. Nella finestra di progettazione fare doppio clic sul **<** pulsante nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Modificare il gestore eventi `Window_Loaded` in modo che `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` siano esterni al metodo e accessibili all'intero form. Dichiarare solo questi elementi come globali nel form e assegnarli all'interno del gestore `Window_Loaded` eventi in modo simile al seguente:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet1":::

3. Aggiungere il codice seguente al gestore eventi `backButton_Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet2":::

4. Tornare alla finestra di progettazione e fare doppio clic sul **>** pulsante.

5. Aggiungere il codice seguente al gestore eventi `nextButton_Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet3":::

## <a name="save-changes-to-product-records"></a>Salvare le modifiche ai record dei prodotti

Aggiungere il codice che consente agli utenti di salvare le modifiche ai record di prodotto usando il pulsante **Salva modifiche**.

1. Nella finestra di progettazione fare doppio clic sul **pulsante Salva** modifiche.

     Visual Studio apre il file code-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Aggiungere il codice seguente al gestore eventi `saveButton_Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet4":::

    > [!NOTE]
    > Questo esempio usa il metodo `Save` di `TableAdapter` per salvare le modifiche. Tale approccio è appropriato a questa procedura dettagliata, in quanto viene modificata una sola tabella dati. Se è necessario salvare modifiche a più tabelle dati, è possibile usare in alternativa il metodo `UpdateAll` di `TableAdapterManager` generato da Visual Studio con il set di dati. Per altre informazioni, vedere [Oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testare l'applicazione

Compilare ed eseguire l'applicazione. Verificare che sia possibile visualizzare e aggiornare i record di prodotto.

1. Premere **F5**.

     L'applicazione verrà compilata ed eseguita. Verificare gli elementi seguenti:

    - Nelle caselle di testo vengono visualizzati i dati del primo record di prodotto contenente una foto. L'ID prodotto è 713, mentre il nome è **Long-Sleeve Logo Jersey, S**.

    - È possibile fare clic sui **>** pulsanti o per spostarsi tra altri record del **<** prodotto.

2. In uno dei record di prodotto modificare il valore **Dimensione**, quindi fare clic su **Salva modifiche**.

3. Chiudere l'applicazione, quindi riavviarla premendo **F5** in Visual Studio.

4. Passare al record di prodotto modificato e verificare che la modifica sia presente.

5. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver completato questa procedura dettagliata, è possibile provare le attività correlate seguenti:

- Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [Associare controlli WPF a un servizio dati WCF.](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)

- Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre-figlio, nei controlli WPF. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare dati correlati in un'app WPF.](../data-tools/display-related-data-in-wpf-applications.md)

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Panoramica del data binding](/dotnet/desktop-wpf/data/data-binding-overview)
