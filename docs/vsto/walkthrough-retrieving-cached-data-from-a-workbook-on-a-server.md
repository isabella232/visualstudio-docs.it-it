---
title: 'Procedura dettagliata: recuperare i dati memorizzati nella cache da una cartella di lavoro in un server'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b70283e63a2f71c0c85bf26a24f2e6f4a3492880
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985413"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Procedura dettagliata: recuperare i dati memorizzati nella cache da una cartella di lavoro in un server
  Questa procedura dettagliata illustra come recuperare dati da un set di dati memorizzato nella cache di una cartella di lavoro di Excel Microsoft Office senza avviare Excel usando la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- Definizione di un set di dati che contiene i dati del database *AdventureWorksLT* .

- Creazione di istanze del set di dati in un progetto di cartella di lavoro di Excel e in un progetto di applicazione console.

- Creazione di un <xref:Microsoft.Office.Tools.Excel.ListObject> associato al set di dati nella cartella di lavoro e popolamento del <xref:Microsoft.Office.Tools.Excel.ListObject> con i dati quando viene aperta la cartella di lavoro.

- Aggiunta del set di dati nella cartella di lavoro alla cache di dati.

- Lettura dei dati dal set di dati memorizzato nella cache nel set di dati nell'applicazione console, senza avviare Excel.

  Sebbene in questa procedura dettagliata si presuppone che il codice sia in esecuzione nel computer di sviluppo, il codice illustrato in questa procedura dettagliata può essere utilizzato in un server in cui non è installato Excel.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisites
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un'istanza in esecuzione di Microsoft SQL Server o Microsoft SQL Server Express a cui è collegato il database di esempio AdventureWorksLT. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

  - Per aggiungere un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere [procedura: connessione di un database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Per aggiungere un database tramite la riga di comando, vedere [procedura: allineare un file di database a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Creare un progetto libreria di classi che definisce un set di dati
 Per usare lo stesso set di dati in un progetto di cartella di lavoro di Excel e in un'applicazione console, è necessario definire il set di dati in un assembly separato a cui fanno riferimento entrambi i progetti. Per questa procedura dettagliata, definire il set di dati in un progetto libreria di classi.

### <a name="create-the-class-library-project"></a>Creare il progetto di libreria di classi

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Nel riquadro modelli espandere  **C# Visual** o **Visual Basic**e quindi fare clic su **Windows**.

4. Nell'elenco dei modelli di progetto selezionare **libreria di classi**.

5. Nella casella **nome** digitare **AdventureWorksDataSet**.

6. Fare clic su **Sfoglia**, passare alla cartella *documenti%userprofile%\My* (per Windows XP e versioni precedenti) o *%UserProfile%\Documenti* (per Windows Vista), quindi fare clic su **Seleziona cartella**.

7. Nella finestra di dialogo **nuovo progetto** assicurarsi che la casella **di controllo Crea directory per soluzione** non sia selezionata.

8. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **AdventureWorksDataSet** al **Esplora soluzioni** e apre il file di codice *Class1.cs* o *Class1. vb* .

9. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su *Class1.cs* o *Class1. vb*, quindi fare clic su **Elimina**. Questo file non è necessario per questa procedura dettagliata.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definire un set di dati nel progetto di libreria di classi
 Definire un DataSet tipizzato che contiene i dati del database AdventureWorksLT per SQL Server 2005. Più avanti in questa procedura dettagliata verrà fatto riferimento a questo set di dati da un progetto di cartella di lavoro di Excel e da un progetto di applicazione console.

 Il set di dati è un *DataSet tipizzato* che rappresenta i dati nella tabella Product del database AdventureWorksLT. Per ulteriori informazioni sui dataset tipizzati, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definire un set di dati tipizzato nel progetto di libreria di classi

1. In **Esplora soluzioni**fare clic sul progetto **AdventureWorksDataSet** .

2. Se la finestra **origini dati** non è visibile, visualizzarla nella barra dei menu scegliendo **Visualizza** > **altre** **origini dati**di Windows > .

3. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Selezionare **Database**e quindi scegliere **Avanti**.

5. Se si dispone di una connessione esistente al database AdventureWorksLT, scegliere questa connessione e fare clic su **Avanti**.

    In caso contrario, scegliere **Nuova connessione**e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **tabelle** e selezionare **Product (SalesLT)** .

8. Scegliere **Fine**.

    Il file *AdventureWorksLTDataSet. xsd* viene aggiunto al progetto **AdventureWorksDataSet** . Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta il contenuto della tabella Product nel database AdventureWorksLT.

   - Oggetto TableAdapter denominato `ProductTableAdapter`. Questo TableAdapter può essere utilizzato per leggere e scrivere dati nel `AdventureWorksLTDataSet`. Per altre informazioni, vedere [Panoramica di TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

9. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **AdventureWorksDataSet** e scegliere **Compila**.

     Verificare che il progetto venga compilato senza errori.

## <a name="create-an-excel-workbook-project"></a>Creare un progetto di cartella di lavoro di Excel
 Creare un progetto di cartella di lavoro di Excel per l'interfaccia per i dati. Più avanti in questa procedura dettagliata verrà creato un <xref:Microsoft.Office.Tools.Excel.ListObject> che consente di visualizzare i dati e verrà aggiunta un'istanza del set di dati alla cache di dati nella cartella di lavoro.

### <a name="create-the-excel-workbook-project"></a>Creare il progetto cartella di lavoro di Excel

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet** , scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.

2. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

3. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

4. Nell'elenco di modelli di progetto selezionare il progetto **Cartella di lavoro di Excel 2010** o **Cartella di lavoro di Excel 2013** .

5. Nella casella **nome** digitare **AdventureWorksReport**. Non modificare il percorso.

6. Fare clic su **OK**.

     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

7. Verificare che l'opzione **Crea un nuovo documento** sia selezionata e fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre la cartella di lavoro **AdventureWorksReport** nella finestra di progettazione e aggiunge il progetto **AdventureWorksReport** al **Esplora soluzioni**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Aggiungere il set di dati alle origini dati nel progetto cartella di lavoro di Excel
 Prima di poter visualizzare il set di dati nella cartella di lavoro di Excel, è necessario innanzitutto aggiungere il set di dati alle origini dati nel progetto cartella di lavoro di Excel.

1. In **Esplora soluzioni**fare doppio clic su *Sheet1.cs* o *Sheet1. vb* nel progetto **AdventureWorksReport** .

     La cartella di lavoro viene aperta nella finestra di progettazione.

2. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Viene avviata la **Configurazione guidata origine dati**.

3. Fare clic su **oggetto**, quindi su **Avanti**.

4. Nella pagina **selezionare l'oggetto che si desidera associare** fare clic su **Aggiungi riferimento**.

5. Nella scheda **progetti** fare clic su **AdventureWorksDataSet** , quindi fare clic su **OK**.

6. Nello spazio dei nomi **AdventureWorksDataSet** dell'assembly **AdventureWorksDataSet** fare clic su **AdventureWorksLTDataSet** e quindi su **fine**.

     Viene visualizzata la finestra **origini dati** e **AdventureWorksLTDataSet** viene aggiunto all'elenco di origini dati.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creare un oggetto ListObject associato a un'istanza del set di dati
 Per visualizzare il set di dati nella cartella di lavoro, creare un <xref:Microsoft.Office.Tools.Excel.ListObject> associato a un'istanza del set di dati. Per altre informazioni sull'associazione di controlli ai dati, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

1. Nella finestra **origini dati** espandere il nodo **AdventureWorksLTDataSet** in **AdventureWorksDataSet**.

2. Selezionare il nodo **Product** , fare clic sulla freccia a discesa visualizzata e selezionare **ListObject** nell'elenco a discesa.

     Se la freccia a discesa non viene visualizzata, verificare che la cartella di lavoro sia aperta nella finestra di progettazione.

3. Trascinare la tabella **Product** sulla cella a1.

     Viene creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `productListObject` nel foglio di foglio, a partire dalla cella a1. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

## <a name="add-the-dataset-to-the-data-cache"></a>Aggiungere il set di dati alla cache di dati
 Per abilitare il codice esterno al progetto cartella di lavoro di Excel per accedere al set di dati nella cartella di lavoro, è necessario aggiungere il set di dati alla cache di dati. Per ulteriori informazioni sulla cache dei dati, vedere la pagina relativa ai [dati memorizzati nella cache nelle personalizzazioni a livello di documento e nei](../vsto/cached-data-in-document-level-customizations.md) [dati della cache](../vsto/caching-data.md).

1. Nella finestra di progettazione fare clic su **AdventureWorksLTDataSet**.

2. Nella finestra **Proprietà** impostare la proprietà **Modifiers** su **public**.

3. Impostare la proprietà **CacheInDocument** su **true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inizializzare il set di dati nella cartella di lavoro
 Prima di poter recuperare i dati dal set di dati memorizzato nella cache utilizzando l'applicazione console, è necessario innanzitutto popolare il set di dati memorizzato nella cache con i dati.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file *Sheet1.cs* o *Sheet1. vb* e scegliere **Visualizza codice**.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Questo codice usa un'istanza della classe `ProductTableAdapter` definita nel progetto **AdventureWorksDataSet** per riempire il set di dati memorizzato nella cache con i dati, se è attualmente vuoto.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Compilare ed eseguire il progetto cartella di lavoro di Excel per assicurarsi che venga compilato ed eseguito senza errori. Questa operazione compila inoltre il set di dati memorizzato nella cache e salva i dati nella cartella di lavoro.

### <a name="build-and-run-the-project"></a>Compilare ed eseguire il progetto

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **AdventureWorksReport** , scegliere **debug**e quindi fare clic su **Avvia nuova istanza**.

     Il progetto viene compilato e la cartella di lavoro viene aperta in Excel. Verificare quanto segue:

    - Il <xref:Microsoft.Office.Tools.Excel.ListObject> compila i dati.

    - Il valore nella colonna **ListPrice** per la prima riga del <xref:Microsoft.Office.Tools.Excel.ListObject> è 1431,5. Più avanti in questa procedura dettagliata si userà un'applicazione console per modificare i valori nella colonna **ListPrice** .

2. Salvare la cartella di lavoro. Non modificare il nome del file o il percorso della cartella di lavoro.

3. Chiudere Excel.

## <a name="create-a-console-application-project"></a>Creare un progetto di applicazione console
 Creare un progetto di applicazione console da utilizzare per modificare i dati nel set di dati memorizzato nella cache della cartella di lavoro.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet** , scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.

2. Nel riquadro **Tipi progetto** espandere **Visual C#**  o **Visual Basic**e quindi fare clic su **Windows**.

3. Nel riquadro **modelli** selezionare **applicazione console**.

4. Nella casella **nome** digitare **DataReader**. Non modificare il percorso.

5. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **DataReader** al **Esplora soluzioni** e apre il file di codice *Program.cs* o *Module1. vb* .

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Recuperare dati dal set di dati memorizzato nella cache tramite l'applicazione console
 Utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> nell'applicazione console per leggere i dati in un oggetto `AdventureWorksLTDataSet` locale. Per confermare che il set di dati locale è stato inizializzato con i dati del set di dati memorizzato nella cache, l'applicazione Visualizza il numero di righe nel set di dati locale.

### <a name="retrieve-data-from-the-cached-dataset"></a>Recuperare i dati dal set di dati memorizzato nella cache

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DataReader** e scegliere **Aggiungi riferimento**.

2. Nella scheda **.NET** selezionare **Microsoft. VisualStudio. Tools. Applications. ServerDocument**.

3. Fare clic su **OK**.

4. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DataReader** e scegliere **Aggiungi riferimento**.

5. Nella scheda **progetti** , selezionare **AdventureWorksDataSet**e fare clic su **OK**.

6. Aprire il file *Program.cs* o *Module1. vb* nell'editor di codice.

7. Aggiungere la seguente istruzione **using** ( C#per) o **imports** (for Visual Basic) all'inizio del file di codice.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Aggiungere al metodo `Main` il seguente codice. Questo codice dichiara gli oggetti seguenti:

   - Istanza del tipo di `AdventureWorksLTDataSet` definito nel progetto **AdventureWorksDataSet** .

   - Percorso della cartella di lavoro di AdventureWorksReport nella cartella Build del progetto **AdventureWorksReport** .

   - Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> da utilizzare per accedere alla cache dei dati nella cartella di lavoro.

     > [!NOTE]
     > Nel codice seguente si presuppone che la cartella di lavoro venga salvata utilizzando l'estensione *xlsx* . Se la cartella di lavoro nel progetto ha un'estensione diversa, modificare il percorso in modo che sia necessario.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Aggiungere il codice seguente al metodo `Main`, dopo il codice aggiunto nel passaggio precedente. Mediante il codice vengono effettuate le seguenti attività:

   - Usa la proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere al set di dati memorizzato nella cache nella cartella di lavoro.

   - Legge i dati dal set di dati memorizzato nella cache nel set di dati locale.

   - Viene visualizzato il numero di righe nel set di dati locale per verificare che disponga di dati.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. Scegliere **Compila DataReader**dal menu **Compila** .

## <a name="test-the-project"></a>Testare il progetto
 Quando si esegue l'applicazione console, viene visualizzato il numero di righe nel set di dati locale.

### <a name="test-the-workbook"></a>Testare la cartella di lavoro

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DataReader** , scegliere **debug**e quindi fare clic su **Avvia nuova istanza**.

     Verificare che l'applicazione segnali che il set di dati locale contiene 295 righe.

2. Premere **invio** per chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sull'uso dei dati memorizzati nella cache, vedere questi argomenti:

- Modifica dei dati in un set di dati memorizzato nella cache senza avviare Excel. Per ulteriori informazioni, vedere [procedura dettagliata: modificare i dati memorizzati nella cache in una cartella di lavoro di in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: inserimento di dati in una cartella di lavoro in un server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Procedura dettagliata: modificare i dati memorizzati nella cache in una cartella di lavoro in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
