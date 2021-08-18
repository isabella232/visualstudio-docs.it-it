---
title: 'Procedura dettagliata: Data binding in un progetto a livello di documento'
description: Informazioni su come associare più celle in un foglio Microsoft Excel dati ai campi nel database Northwind SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ac951f07fc31c901f79b0116ff325be9fb64c0d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147570"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procedura dettagliata: Data binding in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni di base di data binding in un progetto a livello di documento. È possibile associare più celle in un foglio Microsoft Office Excel dati ai campi nel database Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di un'origine dati al progetto della cartella di lavoro.

- Aggiunta di controlli associati a dati a un foglio di lavoro.

- Salvataggio delle modifiche dei dati nel database.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di SQL Server Northwind.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server database.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 Il primo passaggio consiste nel creare un progetto Excel cartella di lavoro.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Excel cartella di lavoro con il nome **My Complex Data Binding**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto **My Complex Data Binding** a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Se la **finestra Origini** dati non è visibile, visualizzarla da sulla barra dei menu, scegliendo Visualizza Windows  >    >  **origini dati**.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database** e quindi fare clic su **Avanti.**

4. Selezionare una connessione dati al database di esempio Northwind SQL Server o aggiungere una nuova connessione usando il **pulsante Nuova** connessione.

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti.**

6. Deselezionare l'opzione per salvare la connessione, se selezionata, e quindi fare clic su **Avanti.**

7. Espandere il **nodo** Tabelle nella finestra **Oggetti di** database .

8. Selezionare la casella di controllo accanto alla **tabella Employees.**

9. Fare clic su **Fine**.

   La procedura guidata aggiunge la **tabella Employees** alla **finestra Origini** dati. Aggiunge anche un set di dati tipizzato al progetto visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Un foglio di lavoro visualizza la **tabella Employees** all'apertura della cartella di lavoro. Gli utenti potranno apportare modifiche ai dati e quindi salvarle di nuovo nel database facendo clic su un pulsante.

 Per associare automaticamente il foglio di lavoro alla tabella, è possibile aggiungere un controllo al foglio di <xref:Microsoft.Office.Tools.Excel.ListObject> lavoro dalla finestra **Origini** dati . Per concedere all'utente la possibilità di salvare le modifiche, aggiungere un <xref:System.Windows.Forms.Button> controllo dalla Casella degli **strumenti**.

#### <a name="to-add-a-list-object"></a>Per aggiungere un oggetto elenco

1. Verificare che la cartella di lavoro My **Complex Data Binding.xlsx** sia aperta nella finestra di progettazione Visual Studio, con **Sheet1** visualizzato.

2. Aprire la **finestra Origini** dati e selezionare il **nodo** Dipendenti.

3. Fare clic sulla freccia a discesa visualizzata.

4. Selezionare **ListObject** nell'elenco a discesa.

5. Trascinare **la tabella Employees** nella cella **A6.**

     Nella <xref:Microsoft.Office.Tools.Excel.ListObject> cella `EmployeesListObject` **A6** viene creato un controllo denominato . Allo stesso tempo, un denominato , un adattatore di tabella e <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` <xref:System.Data.DataSet> un'istanza vengono aggiunti al progetto. Il controllo è associato a , che a sua <xref:System.Windows.Forms.BindingSource> volta è associato <xref:System.Data.DataSet> all'istanza di .

### <a name="to-add-a-button"></a>Per aggiungere un pulsante

1. Dalla scheda **Controlli comuni della** Casella degli strumenti aggiungere un controllo alla cella  <xref:System.Windows.Forms.Button> **A4** del foglio di lavoro.

   Il passaggio successivo consiste nell'aggiungere testo al pulsante all'apertura del foglio di lavoro.

## <a name="initialize-the-control"></a>Inizializzare il controllo
 Aggiungere testo al pulsante nel gestore <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eventi.

### <a name="to-initialize-the-control"></a>Per inizializzare il controllo

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** e quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per b `utton` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet8":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet8":::

3. Solo per C#, aggiungere un gestore eventi per <xref:System.Windows.Forms.Control.Click> l'evento al `Sheet1_Startup` metodo .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet9":::

   Aggiungere ora il codice per gestire <xref:System.Windows.Forms.Control.Click> l'evento del pulsante.

## <a name="save-changes-to-the-database"></a>Salvare le modifiche apportate al database
 Le modifiche apportate ai dati esistono solo nel set di dati locale finché non vengono salvate in modo esplicito nel database.

### <a name="to-save-changes-to-the-database"></a>Per salvare le modifiche apportate al database

1. Aggiungere un gestore eventi per l'evento di e aggiungere il codice seguente per eseguire il commit di tutte le modifiche apportate nel <xref:System.Windows.Forms.Control.Click> set di dati al `button` database.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet10":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per verificare che i dati siano visualizzati come previsto e che sia possibile modificare i dati nell'oggetto elenco.

### <a name="to-test-the-data-binding"></a>Per testare il data binding

- Premere **F5**.

     Verificare che all'apertura della cartella di lavoro l'oggetto elenco sia compilato con i dati della **tabella Employees.**

### <a name="to-modify-data"></a>Per modificare i dati

1. Fare clic sulla **cella B7,** che deve contenere il **nome Davolio**.

2. Digitare il nome **Anderson** e quindi premere **INVIO.**

### <a name="to-modify-a-column-header"></a>Per modificare un'intestazione di colonna

1. Fare clic sulla cella che contiene l'intestazione di colonna **LastName**.

2. Digitare **Last Name**, incluso uno spazio tra le due parole, e quindi premere **INVIO.**

### <a name="to-save-data"></a>Per salvare i dati

1. Fare **clic su Salva** nel foglio di lavoro.

2. Uscire da Excel. Fare **clic su No** quando viene richiesto di salvare le modifiche apportate.

3. Premere **F5** per eseguire di nuovo il progetto.

     L'oggetto elenco viene compilato con i dati della **tabella Employees.**

4. Si noti che il nome nella cella **B7** è ancora **Anderson**, ovvero la modifica dei dati apportata e salvata di nuovo nel database. L'intestazione di colonna **LastName** è tornata al formato originale senza spazio, perché l'intestazione di colonna non è associata al database e non sono state salvate le modifiche apportate al foglio di lavoro.

### <a name="to-add-new-rows"></a>Per aggiungere nuove righe

1. Selezionare una cella all'interno dell'oggetto elenco.

    Nella parte inferiore dell'elenco viene visualizzata una nuova riga, con un asterisco ( ) nella **\*** prima cella della nuova riga.

2. Aggiungere le informazioni seguenti nella riga vuota.

   |EmployeeID|LastName|FirstName|Titolo|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Direttore commerciale|

### <a name="to-delete-rows"></a>Per eliminare righe

- Fare clic con il pulsante destro del mouse sul numero 16 (riga 16) all'estrema sinistra del foglio di lavoro e quindi scegliere **Elimina**.

### <a name="to-sort-the-rows-in-the-list"></a>Per ordinare le righe nell'elenco

1. Selezionare una cella all'interno dell'elenco.

     I pulsanti freccia vengono visualizzati in ogni intestazione di colonna.

2. Fare clic sul pulsante freccia **nell'intestazione di colonna** Cognome.

3. Fare clic **su Ordina in ordine crescente.**

     Le righe vengono ordinate alfabeticamente in base ai cognome.

### <a name="to-filter-information"></a>Per filtrare le informazioni

1. Selezionare una cella all'interno dell'elenco.

2. Fare clic sul pulsante freccia **nell'intestazione di** colonna Titolo.

3. Fare clic **su Rappresentante vendite**.

     L'elenco mostra solo le righe con **Sales Representative** nella **colonna** Title.

4. Fare di nuovo clic sul pulsante freccia **nell'intestazione** di colonna Titolo.

5. Fare **clic su (Tutto)**.

     Il filtro viene rimosso e vengono visualizzate tutte le righe.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'associazione di una tabella di un database a un oggetto elenco. Ecco alcune possibili attività successive:

- Memorizzare nella cache i dati in modo che possano essere usati offline. Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Distribuzione della soluzione. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

- Creare una relazione master/dettagli tra un campo e una tabella. Per altre informazioni, vedere [Procedura dettagliata: Creare una relazione master dettagliata usando un set di dati memorizzato nella cache.](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)

## <a name="see-also"></a>Vedi anche
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati nelle soluzioni Office dati](../vsto/data-in-office-solutions.md)
- [Procedura dettagliata: Data binding semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
