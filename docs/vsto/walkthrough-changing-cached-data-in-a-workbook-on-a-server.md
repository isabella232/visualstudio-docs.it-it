---
title: 'Procedura dettagliata: modificare i dati memorizzati nella cache in una cartella di lavoro in un server'
description: Informazioni su come modificare un set di dati memorizzato nella cache di una cartella di lavoro di Microsoft Excel senza avviare Excel usando la classe ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01ae4894d76e22f619bf498b4ac6a53f1232b5d5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527274"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Procedura dettagliata: modificare i dati memorizzati nella cache in una cartella di lavoro in un server
  Questa procedura dettagliata illustra come modificare un set di dati memorizzato nella cache in una Microsoft Office cartella di lavoro di Excel senza avviare Excel usando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Vengono illustrate le attività seguenti:

- Definizione di un set di dati che contiene i dati del database AdventureWorksLT.

- Creazione di istanze del set di dati in un progetto di cartella di lavoro di Excel e in un progetto di applicazione console.

- Creazione di un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> associato al set di dati nella cartella di lavoro e popolamento dell'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> con i dati quando la cartella di lavoro viene aperta.

- Aggiunta del set di dati nella cartella di lavoro alla cache di dati.

- Modifica di una colonna di dati nel set di dati memorizzato nella cache tramite l'esecuzione di codice nell'applicazione console, senza avviare Excel.

  Sebbene in questa procedura dettagliata si presuppone che il codice sia in esecuzione nel computer di sviluppo, il codice illustrato in questa procedura dettagliata può essere utilizzato in un server in cui non è installato Excel.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un'istanza in esecuzione di Microsoft SQL Server o Microsoft SQL Server Express a cui è collegato il database di esempio AdventureWorksLT. È possibile scaricare il database AdventureWorksLT dal [repository GitHub SQL Server Samples](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

  - Per aggiungere un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere [procedura: connessione di un database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Per aggiungere un database tramite la riga di comando, vedere [procedura: allineare un file di database a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Creare un progetto libreria di classi che definisce un set di dati
 Per usare lo stesso set di dati in un progetto di cartella di lavoro di Excel e in un'applicazione console, è necessario definire il set di dati in un assembly separato a cui fanno riferimento entrambi i progetti. Per questa procedura dettagliata, definire il set di dati in un progetto libreria di classi.

### <a name="to-create-the-class-library-project"></a>Per creare il progetto libreria di classi

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

3. Nel riquadro modelli espandere **Visual C#** o **Visual Basic** e quindi fare clic su **Windows**.

4. Nell'elenco dei modelli di progetto selezionare **libreria di classi**.

5. Nella casella **nome** digitare **AdventureWorksDataSet**.

6. Fare clic su **Sfoglia**, passare alla cartella *documenti%userprofile%\My* (per Windows XP e versioni precedenti) o *%UserProfile%\Documenti* (per Windows Vista), quindi fare clic su **Seleziona cartella**.

7. Nella finestra di dialogo **nuovo progetto** assicurarsi che la casella **di controllo Crea directory per soluzione** non sia selezionata.

8. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **AdventureWorksDataSet** a **Esplora soluzioni** e apre il file di codice **Class1.cs** o **Class1. vb** .

9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Class1.cs** o **Class1. vb**, quindi fare clic su **Elimina**. Questo file non è necessario per questa procedura dettagliata.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definire un set di dati nel progetto di libreria di classi
 Definire un DataSet tipizzato che contiene i dati del database AdventureWorksLT per SQL Server 2005. Più avanti in questa procedura dettagliata verrà fatto riferimento a questo set di dati da un progetto di cartella di lavoro di Excel e da un progetto di applicazione console.

 Il set di dati è un *DataSet tipizzato* che rappresenta i dati nella tabella Product del database AdventureWorksLT. Per ulteriori informazioni sui dataset tipizzati, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Per definire un set di dati tipizzato nel progetto di libreria di classi

1. In **Esplora soluzioni** fare clic sul progetto **AdventureWorksDataSet** .

2. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati** di Windows.

3. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Selezionare **Database** e quindi scegliere **Avanti**.

5. Se si dispone di una connessione esistente al database AdventureWorksLT, scegliere questa connessione e fare clic su **Avanti**.

    In caso contrario, scegliere **Nuova connessione** e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

7. Nella pagina **Seleziona oggetti di database** espandere **tabelle** e selezionare **Product (SalesLT)**.

8. Fare clic su **Fine**.

    Il file *AdventureWorksLTDataSet. xsd* viene aggiunto al progetto **AdventureWorksDataSet** . Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta il contenuto della tabella Product nel database AdventureWorksLT.

   - Oggetto TableAdapter denominato `ProductTableAdapter` . Questo TableAdapter può essere utilizzato per leggere e scrivere dati in `AdventureWorksLTDataSet` . Per altre informazioni, vedere [Panoramica di TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **AdventureWorksDataSet** e scegliere **Compila**.

     Verificare che il progetto venga compilato senza errori.

## <a name="create-an-excel-workbook-project"></a>Creare un progetto di cartella di lavoro di Excel
 Creare un progetto di cartella di lavoro di Excel per l'interfaccia per i dati. Più avanti in questa procedura dettagliata verrà creato un oggetto in <xref:Microsoft.Office.Tools.Excel.ListObject> cui vengono visualizzati i dati e verrà aggiunta un'istanza del set di dati alla cache di dati nella cartella di lavoro.

### <a name="to-create-the-excel-workbook-project"></a>Per creare il progetto cartella di lavoro di Excel

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet** , scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.

2. Nel riquadro modelli espandere **Visual C#** o **Visual Basic**, quindi espandere **Office**.

3. Nel nodo **Office** espanso selezionare il nodo **2010** .

4. Nell'elenco dei modelli di progetto selezionare il progetto cartella di lavoro di Excel.

5. Nella casella **nome** digitare **AdventureWorksReport**. Non modificare il percorso.

6. Fare clic su **OK**.

     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

7. Verificare che l'opzione **Crea un nuovo documento** sia selezionata e fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre la cartella di lavoro **AdventureWorksReport** nella finestra di progettazione e aggiunge il progetto **AdventureWorksReport** a **Esplora soluzioni**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Aggiungere il set di dati alle origini dati nel progetto cartella di lavoro di Excel
 Prima di poter visualizzare il set di dati nella cartella di lavoro di Excel, è necessario innanzitutto aggiungere il set di dati alle origini dati nel progetto cartella di lavoro di Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Per aggiungere il set di dati alle origini dati nel progetto cartella di lavoro di Excel

1. In **Esplora soluzioni** fare doppio clic su **Sheet1.cs** o **Sheet1. vb** nel progetto **AdventureWorksReport** .

     La cartella di lavoro viene aperta nella finestra di progettazione.

2. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Verrà avviata la **Configurazione guidata origine dati** .

3. Fare clic su **oggetto**, quindi su **Avanti**.

4. Nella pagina **selezionare l'oggetto che si desidera associare** fare clic su **Aggiungi riferimento**.

5. Nella scheda **progetti** fare clic su **AdventureWorksDataSet** , quindi fare clic su **OK**.

6. Nello spazio dei nomi **AdventureWorksDataSet** dell'assembly **AdventureWorksDataSet** fare clic su **AdventureWorksLTDataSet** e quindi su **fine**.

     Viene visualizzata la finestra **origini dati** e **AdventureWorksLTDataSet** viene aggiunto all'elenco di origini dati.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creare un oggetto ListObject associato a un'istanza del set di dati
 Per visualizzare il set di dati nella cartella di lavoro, creare un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> associato a un'istanza del set di dati. Per altre informazioni sull'associazione di controlli ai dati, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Per creare un oggetto ListObject associato a un'istanza del set di dati

1. Nella finestra **origini dati** espandere il nodo **AdventureWorksLTDataSet** in **AdventureWorksDataSet**.

2. Selezionare il nodo **Product** , fare clic sulla freccia a discesa visualizzata e selezionare **ListObject** nell'elenco a discesa.

     Se la freccia a discesa non viene visualizzata, verificare che la cartella di lavoro sia aperta nella finestra di progettazione.

3. Trascinare la tabella **Product** sulla cella a1.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Viene creato un controllo denominato nel foglio di controllo `productListObject` , a partire dalla cella a1. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

## <a name="add-the-dataset-to-the-data-cache"></a>Aggiungere il set di dati alla cache di dati
 Per abilitare il codice esterno al progetto cartella di lavoro di Excel per accedere al set di dati nella cartella di lavoro, è necessario aggiungere il set di dati alla cache di dati. Per ulteriori informazioni sulla cache dei dati, vedere la pagina relativa ai [dati memorizzati nella cache nelle personalizzazioni a livello di documento e nei](../vsto/cached-data-in-document-level-customizations.md) [dati della cache](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Per aggiungere il set di dati alla cache di dati

1. Nella finestra di progettazione fare clic su **AdventureWorksLTDataSet**.

2. Nella finestra **Proprietà** impostare la proprietà **Modifiers** su **public**.

3. Impostare la proprietà **CacheInDocument** su **true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inizializzare il set di dati nella cartella di lavoro
 Prima di poter recuperare i dati dal set di dati memorizzato nella cache utilizzando l'applicazione console, è necessario innanzitutto popolare il set di dati memorizzato nella cache con i dati.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Per inizializzare il set di dati nella cartella di lavoro

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file **Sheet1.cs** o **Sheet1. vb** e scegliere **Visualizza codice**.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Questo codice usa un'istanza della `ProductTableAdapter` classe definita nel progetto **AdventureWorksDataSet** per riempire il set di dati memorizzato nella cache con i dati, se è attualmente vuoto.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Compilare ed eseguire il progetto cartella di lavoro di Excel per assicurarsi che venga compilato ed eseguito senza errori. Questa operazione compila inoltre il set di dati memorizzato nella cache e salva i dati nella cartella di lavoro.

### <a name="to-build-and-run-the-project"></a>Per compilare ed eseguire il progetto

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **AdventureWorksReport** , scegliere **debug** e quindi fare clic su **Avvia nuova istanza**.

     Il progetto viene compilato e la cartella di lavoro viene aperta in Excel. Verificare gli elementi seguenti:

    - L'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> Compila i dati.

    - Il valore nella colonna **ListPrice** per la prima riga di <xref:Microsoft.Office.Tools.Excel.ListObject> è 1431,5. Più avanti in questa procedura dettagliata si userà un'applicazione console per modificare i valori nella colonna **ListPrice** .

2. Salvare la cartella di lavoro. Non modificare il nome del file o il percorso della cartella di lavoro.

3. Chiudere Excel.

## <a name="create-a-console-application-project"></a>Creare un progetto di applicazione console
 Creare un progetto di applicazione console da utilizzare per modificare i dati nel set di dati memorizzato nella cache della cartella di lavoro.

### <a name="to-create-the-console-application-project"></a>Per creare il progetto di applicazione console

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet** , scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.

2. Nel riquadro **Tipi progetto** espandere **Visual C#** o **Visual Basic** e quindi fare clic su **Windows**.

3. Nel riquadro **Modelli** selezionare **Applicazione console**.

4. Nella casella **nome** Digitare **DataWriter**. Non modificare il percorso.

5. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **DataWriter** a **Esplora soluzioni** e apre il file di codice **Program.cs** o **Module1. vb** .

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Modificare i dati nel set di dati memorizzato nella cache utilizzando l'applicazione console
 Utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'applicazione console per leggere i dati in un oggetto locale `AdventureWorksLTDataSet` , modificare questi dati e quindi salvarli nuovamente nel set di dati memorizzato nella cache.

### <a name="to-change-data-in-the-cached-dataset"></a>Per modificare i dati nel set di dati memorizzato nella cache

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **DataWriter** e scegliere **Aggiungi riferimento**.

2. Nella scheda **.NET** selezionare **Microsoft. VisualStudio. Tools. Applications**.

3. Fare clic su **OK**.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **DataWriter** e scegliere **Aggiungi riferimento**.

5. Nella scheda **progetti** , selezionare **AdventureWorksDataSet** e fare clic su **OK**.

6. Aprire il file *Program.cs* o *Module1. vb* nell'editor di codice.

7. Aggiungere la seguente istruzione **using** (per C#) o **Imports** (for Visual Basic) all'inizio del file di codice.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Aggiungere il codice seguente al metodo `Main` . Questo codice dichiara gli oggetti seguenti:

   - Istanza del `AdventureWorksLTDataSet` tipo definito nel progetto **AdventureWorksDataSet** .

   - Percorso della cartella di lavoro di AdventureWorksReport nella cartella Build del progetto **AdventureWorksReport** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Oggetto da utilizzare per accedere alla cache dei dati nella cartella di lavoro.

     > [!NOTE]
     > Nel codice seguente si presuppone l'utilizzo di una cartella di lavoro con estensione *xlsx* . Se la cartella di lavoro nel progetto ha un'estensione di file diversa, modificare il percorso in modo che sia necessario.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Aggiungere il codice seguente al `Main` metodo, dopo il codice aggiunto nel passaggio precedente. Il codice esegue queste operazioni:

   - Usa la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per accedere al set di dati memorizzato nella cache nella cartella di lavoro.

   - Legge i dati dal set di dati memorizzato nella cache nel set di dati locale.

   - Viene modificato il `ListPrice` valore di ogni prodotto nella tabella Product del set di dati.

   - Salva le modifiche apportate al set di dati memorizzato nella cache nella cartella di lavoro.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **DataWriter** , scegliere **debug**, quindi fare clic su **Avvia nuova istanza**.

     L'applicazione console Visualizza i messaggi durante la lettura del set di dati memorizzato nella cache nel set di dati locale, modifica i prezzi dei prodotti nel set di dati locale e salva i nuovi valori nel set di dati memorizzato nella cache. Premere **INVIO** per chiudere l'applicazione.

## <a name="test-the-workbook"></a>Testare la cartella di lavoro
 Quando si apre la cartella di lavoro, <xref:Microsoft.Office.Tools.Excel.ListObject> ora Visualizza le modifiche apportate alla `ListPrice` colonna di dati nel set di dati memorizzato nella cache.

### <a name="to-test-the-workbook"></a>Per testare la cartella di lavoro

1. Chiudere la cartella di lavoro AdventureWorksReport nella finestra di progettazione di Visual Studio, se è ancora aperta.

2. Aprire la cartella di lavoro AdventureWorksReport che si trova nella cartella Build del progetto **AdventureWorksReport** . Per impostazione predefinita, la cartella Build si trova in una delle posizioni seguenti:

    - *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (per Windows XP e versioni precedenti)

    - *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (per Windows Vista)

3. Verificare che il valore nella colonna **ListPrice** per la prima riga di <xref:Microsoft.Office.Tools.Excel.ListObject> sia ora 1574,65.

4. Chiudere la cartella di lavoro.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: inserimento di dati in una cartella di lavoro in un server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
