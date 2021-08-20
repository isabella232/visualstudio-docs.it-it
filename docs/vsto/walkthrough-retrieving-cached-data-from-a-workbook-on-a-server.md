---
title: 'Procedura dettagliata: Recuperare dati memorizzati nella cache da una cartella di lavoro in un server'
description: Informazioni su come recuperare dati da un set di dati memorizzato nella cache in una cartella di lavoro Microsoft Excel senza avviare Excel usando la classe ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e2a84857f6ad3e58430538e2656b31869f9a4bbe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155421"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Procedura dettagliata: Recuperare dati memorizzati nella cache da una cartella di lavoro in un server
  Questa procedura dettagliata illustra come recuperare dati da un set di dati memorizzato nella cache in una cartella di lavoro Microsoft Office Excel senza avviare Excel usando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Definizione di un set di dati contenente i dati del database *AdventureWorksLT.*

- Creazione di istanze del set di dati in un progetto Excel cartella di lavoro e in un progetto di applicazione console.

- Creazione di un oggetto associato al set di dati nella cartella di lavoro e popolamento di con i dati <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> all'apertura della cartella di lavoro.

- Aggiunta del set di dati nella cartella di lavoro alla cache dei dati.

- Lettura dei dati dal set di dati memorizzato nella cache nel set di dati nell'applicazione console, senza avviare Excel.

  Sebbene questa procedura dettagliata presupponga che il codice sia in esecuzione nel computer di sviluppo, il codice illustrato in questa procedura dettagliata può essere usato in un server in cui non è installato Excel.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un'istanza in Microsoft SQL Server o Microsoft SQL Server Express a cui è collegato il database di esempio AdventureWorksLT. È possibile scaricare il database AdventureWorksLT dal sito [Web CodePlex.](https://archive.codeplex.com/?p=SqlServerSamples) Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

  - Per collegare un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere Procedura: Collegare un [database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Per collegare un database tramite la riga di comando, vedere [Procedura: Collegare un file](/previous-versions/sql/)di database SQL Server Express .

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Creare un progetto di libreria di classi che definisce un set di dati
 Per usare lo stesso set di dati in un progetto Excel cartella di lavoro e in un'applicazione console, è necessario definire il set di dati in un assembly separato a cui fanno riferimento entrambi questi progetti. Per questa procedura dettagliata, definire il set di dati in un progetto di libreria di classi.

### <a name="create-the-class-library-project"></a>Creare il progetto di libreria di classi

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

3. Nel riquadro modelli espandere **Visual C#** o **Visual Basic** e quindi fare clic su **Windows**.

4. Nell'elenco dei modelli di progetto selezionare **Libreria di classi**.

5. Nella casella **Nome** digitare **AdventureWorksDataSet**.

6. Fare clic su **Sfoglia,** passare alla cartella *%UserProfile%\Documenti* (per Windows XP e versioni precedenti) o *%UserProfile%\Documents* (per Windows Vista) e quindi fare clic su **Seleziona cartella**.

7. Nella finestra **di dialogo Project** verificare che la casella di controllo Crea **directory** per soluzione non sia selezionata.

8. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il **progetto AdventureWorksDataSet** **Esplora soluzioni** e apre il file di codice *Class1.cs* o *Class1.vb.*

9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse *su Class1.cs* o *Class1.vb* e quindi scegliere **Elimina**. Questo file non è necessario per questa procedura dettagliata.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definire un set di dati nel progetto di libreria di classi
 Definire un set di dati tipizzato contenente i dati del database AdventureWorksLT per SQL Server 2005. Più avanti in questa procedura dettagliata si farà riferimento a questo set di dati da un progetto Excel cartella di lavoro e da un progetto di applicazione console.

 Il set di *dati è un set di* dati tipizzato che rappresenta i dati nella tabella Product del database AdventureWorksLT. Per altre informazioni sui set di dati tipizzati, vedere Strumenti per set di [dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definire un set di dati tipizzato nel progetto di libreria di classi

1. In **Esplora soluzioni** fare clic sul **progetto AdventureWorksDataSet.**

2. Se la **finestra Origini** dati non è visibile, visualizzarla da sulla barra dei menu, scegliendo Visualizza Windows  >    >  **origini dati**.

3. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Selezionare **Database** e quindi scegliere **Avanti**.

5. Se si dispone di una connessione esistente al database AdventureWorksLT, scegliere questa connessione e fare clic su **Avanti.**

    In caso contrario, scegliere **Nuova connessione** e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

7. Nella pagina **Scegli oggetti di database** espandere **Tabelle** e selezionare **Prodotto (SalesLT).**

8. Fare clic su **Fine**.

    Il file *AdventureWorksLTDataSet.xsd* viene aggiunto al **progetto AdventureWorksDataSet.** Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta il contenuto della tabella Product nel database AdventureWorksLT.

   - Oggetto TableAdapter denominato `ProductTableAdapter` . Questo TableAdapter può essere usato per leggere e scrivere dati in `AdventureWorksLTDataSet` . Per altre informazioni, vedere [Panoramica di TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **su AdventureWorksDataSet** e scegliere **Compila**.

     Verificare che il progetto venga compilato senza errori.

## <a name="create-an-excel-workbook-project"></a>Creare un progetto Excel cartella di lavoro
 Creare un Excel di cartella di lavoro per l'interfaccia ai dati. Più avanti in questa procedura dettagliata si creerà un oggetto che visualizza i dati e si aggiungerà un'istanza del set di dati alla cache dei dati <xref:Microsoft.Office.Tools.Excel.ListObject> nella cartella di lavoro.

### <a name="create-the-excel-workbook-project"></a>Creare il progetto Excel cartella di lavoro

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla **soluzione AdventureWorksDataSet,** scegliere Aggiungi e quindi fare clic su Nuovo **Project**. 

2. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

3. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

4. Nell'elenco di modelli di progetto selezionare il progetto **Cartella di lavoro di Excel 2010** o **Cartella di lavoro di Excel 2013** .

5. Nella casella **Nome** digitare **AdventureWorksReport**. Non modificare il percorso.

6. Fare clic su **OK**.

     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

7. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata e fare clic su **OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre la **cartella di lavoro AdventureWorksReport** nella finestra di progettazione e aggiunge il **progetto AdventureWorksReport** **Esplora soluzioni**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Aggiungere il set di dati alle origini dati nel progetto Excel cartella di lavoro
 Prima di poter visualizzare il set di dati nella cartella Excel, è necessario aggiungere il set di dati alle origini dati nel progetto Excel cartella di lavoro.

1. In **Esplora soluzioni** fare doppio clic su *Sheet1.cs* o *Sheet1.vb* nel **progetto AdventureWorksReport.**

     La cartella di lavoro viene aperta nella finestra di progettazione.

2. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Verrà **visualizzata la Configurazione guidata origine** dati.

3. Fare **clic su Oggetto** e quindi su **Avanti.**

4. Nella pagina **Selezionare l'oggetto a cui si vuole eseguire l'associazione** fare clic **su Aggiungi riferimento**.

5. Nella scheda **Progetti** fare clic su **AdventureWorksDataSet** e quindi su **OK.**

6. Nello spazio **dei nomi AdventureWorksDataSet** dell'assembly **AdventureWorksDataSet** fare clic **su AdventureWorksLTDataSet** e quindi su **Fine.**

     Verrà **visualizzata la finestra** Origini dati e **AdventureWorksLTDataSet** verrà aggiunto all'elenco di origini dati.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creare un oggetto ListObject associato a un'istanza del set di dati
 Per visualizzare il set di dati nella cartella di lavoro, <xref:Microsoft.Office.Tools.Excel.ListObject> creare un oggetto associato a un'istanza del set di dati. Per altre informazioni sull'associazione di controlli ai dati, vedere [Associare dati](../vsto/binding-data-to-controls-in-office-solutions.md)ai controlli in Office soluzioni .

1. Nella finestra **Origini dati** espandere il **nodo AdventureWorksLTDataSet** in **AdventureWorksDataSet**.

2. Selezionare il **nodo Product,** fare clic sulla freccia a discesa visualizzata e **selezionare ListObject** nell'elenco a discesa.

     Se la freccia a discesa non viene visualizzata, verificare che la cartella di lavoro sia aperta nella finestra di progettazione.

3. Trascinare **la tabella Product** nella cella A1.

     Nel foglio di lavoro viene creato un controllo denominato <xref:Microsoft.Office.Tools.Excel.ListObject> , a partire dalla cella `productListObject` A1. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

## <a name="add-the-dataset-to-the-data-cache"></a>Aggiungere il set di dati alla cache dei dati
 Per consentire al codice esterno al Excel cartella di lavoro di accedere al set di dati nella cartella di lavoro, è necessario aggiungere il set di dati alla cache dei dati. Per altre informazioni sulla cache dei dati, vedere Dati memorizzati nella [cache nelle personalizzazioni](../vsto/cached-data-in-document-level-customizations.md) a livello di documento e [Dati della cache](../vsto/caching-data.md).

1. Nella finestra di progettazione fare clic **su adventureWorksLTDataSet**.

2. Nella finestra **Proprietà** impostare la **proprietà Modifiers** su **Public**.

3. Impostare la **proprietà CacheInDocument** su **True.**

## <a name="initialize-the-dataset-in-the-workbook"></a>Inizializzare il set di dati nella cartella di lavoro
 Prima di poter recuperare i dati dal set di dati memorizzato nella cache usando l'applicazione console, è necessario popolare il set di dati memorizzato nella cache con i dati.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file *Sheet1.cs* *o Sheet1.vb* e scegliere **Visualizza codice**.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Questo codice usa un'istanza della classe definita nel progetto `ProductTableAdapter` **AdventureWorksDataSet** per riempire il set di dati memorizzato nella cache con dati, se è attualmente vuoto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Compilare ed eseguire il progetto Excel cartella di lavoro per assicurarsi che venga compilato ed eseguito senza errori. Questa operazione riempie anche il set di dati memorizzato nella cache e salva i dati nella cartella di lavoro.

### <a name="build-and-run-the-project"></a>Compilare ed eseguire il progetto

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto AdventureWorksReport,** scegliere **Debug** e quindi fare clic su Avvia **nuova istanza**.

     Il progetto viene compilato e la cartella di lavoro viene aperta in Excel. Verificare gli elementi seguenti:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>L'oggetto viene riempito con dati.

    - Il valore nella **colonna ListPrice** per la prima riga di <xref:Microsoft.Office.Tools.Excel.ListObject> è 1431,5. Più avanti in questa procedura dettagliata si userà un'applicazione console per modificare i valori nella **colonna ListPrice.**

2. Salvare la cartella di lavoro. Non modificare il nome del file o il percorso della cartella di lavoro.

3. Chiudere Excel.

## <a name="create-a-console-application-project"></a>Creare un progetto di applicazione console
 Creare un progetto di applicazione console da usare per modificare i dati nel set di dati memorizzato nella cache nella cartella di lavoro.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla **soluzione AdventureWorksDataSet,** scegliere Aggiungi e quindi fare clic su Nuovo **Project**. 

2. Nel riquadro **Project tipi espandere** Visual **C#** o **Visual Basic** e quindi fare clic su **Windows**.

3. Nel riquadro **Modelli** selezionare **Applicazione console**.

4. Nella casella **Nome** digitare **DataReader**. Non modificare il percorso.

5. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il **progetto DataReader** **Esplora soluzioni** e apre il file di codice *Program.cs* o *Module1.vb.*

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Recuperare dati dal set di dati memorizzato nella cache usando l'applicazione console
 Usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'applicazione console per leggere i dati in un oggetto `AdventureWorksLTDataSet` locale. Per verificare che il set di dati locale sia stato inizializzato con i dati del set di dati memorizzato nella cache, l'applicazione visualizza il numero di righe nel set di dati locale.

### <a name="retrieve-data-from-the-cached-dataset"></a>Recuperare dati dal set di dati memorizzato nella cache

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto DataReader** e scegliere **Aggiungi riferimento**.

2. Nella scheda **.NET** selezionare **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.

3. Fare clic su **OK**.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto DataReader** e scegliere **Aggiungi riferimento**.

5. Nella scheda **Progetti** selezionare **AdventureWorksDataSet** e fare clic su **OK.**

6. Aprire il file *Program.cs o* *Module1.vb* nell'editor di codice.

7. Aggiungere **l'istruzione using** (per C#) o **Imports** (per Visual Basic) all'inizio del file di codice.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. Aggiungere il codice seguente al metodo `Main` . Questo codice dichiara gli oggetti seguenti:

   - Istanza del `AdventureWorksLTDataSet` tipo definito nel progetto **AdventureWorksDataSet.**

   - Percorso della cartella di lavoro AdventureWorksReport nella cartella di compilazione del **progetto AdventureWorksReport.**

   - Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> da utilizzare per accedere alla cache dei dati nella cartella di lavoro.

     > [!NOTE]
     > Il codice seguente presuppone che la cartella di lavoro sia salvata usando *l'.xlsx* predefinita. Se la cartella di lavoro nel progetto ha un'estensione diversa, modificare il percorso in base alle esigenze.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet10":::

9. Aggiungere il codice seguente al `Main` metodo dopo il codice aggiunto nel passaggio precedente. Il codice esegue queste operazioni:

   - Usa la proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> della classe per accedere al set di dati memorizzato nella cache nella cartella di <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> lavoro.

   - Legge i dati dal set di dati memorizzato nella cache nel set di dati locale.

   - Visualizza il numero di righe nel set di dati locale per verificare che abbia dati.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet11":::

10. Scegliere **Compila DataReader** dal menu **Compila**.

## <a name="test-the-project"></a>Testare il progetto
 Quando si esegue l'applicazione console, viene visualizzato il numero di righe nel set di dati locale.

### <a name="test-the-workbook"></a>Testare la cartella di lavoro

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto DataReader,** scegliere **Debug** e quindi fare clic su Avvia **nuova istanza**.

     Verificare che l'applicazione segnala che il set di dati locale include 295 righe.

2. Premere **INVIO** per chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Altre informazioni sull'uso dei dati memorizzati nella cache sono disponibili negli argomenti seguenti:

- Modifica dei dati in un set di dati memorizzato nella cache senza avviare Excel. Per altre informazioni, vedere [Procedura dettagliata: Modificare i dati memorizzati nella cache in una cartella di lavoro in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Inserire dati in una cartella di lavoro in un server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Procedura dettagliata: Modificare i dati memorizzati nella cache in una cartella di lavoro in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
