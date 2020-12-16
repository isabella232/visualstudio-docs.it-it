---
title: 'Procedura dettagliata: data binding complesse in un progetto a livello di documento'
description: Informazioni su come è possibile associare più celle di un foglio di lavoro di Microsoft Excel ai campi del database Northwind SQL Server.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 988394595e8aa4710a22e1fedf22a921481c7396
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527119"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procedura dettagliata: data binding complesse in un progetto a livello di documento
  In questa procedura dettagliata vengono illustrate le nozioni di base di data binding complesse in un progetto a livello di documento. È possibile associare più celle di un foglio di lavoro Microsoft Office Excel ai campi del database di SQL Server Northwind.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di un'origine dati al progetto di cartella di lavoro.

- Aggiunta di controlli con associazione a dati a un foglio di foglio.

- Salvataggio delle modifiche dei dati nel database.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di esempio Northwind SQL Server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 Il primo passaggio consiste nel creare un progetto di cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **Data Binding complesso**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto di **Data Binding complesso** al **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati** di Windows.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **database** e quindi fare clic su **Avanti**.

4. Selezionare una connessione dati all'esempio Northwind SQL Server database oppure aggiungere una nuova connessione usando il pulsante **nuova connessione** .

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se selezionata, quindi fare clic su **Avanti**.

7. Espandere il nodo **tabelle** nella finestra **oggetti di database** .

8. Selezionare la casella di controllo accanto alla tabella **Employees** .

9. Fare clic su **Fine**.

   La procedura guidata consente di aggiungere la tabella **Employees** alla finestra **origini dati** . Aggiunge anche un set di dati tipizzato al progetto che è visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di controllo
 Quando la cartella di lavoro viene aperta, un foglio di lavoro visualizzerà la tabella **Employees** . Gli utenti saranno in grado di apportare modifiche ai dati e di salvare di nuovo le modifiche nel database facendo clic su un pulsante.

 Per associare automaticamente il foglio di comando alla tabella, è possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo al foglio di controllo dalla finestra **origini dati** . Per fornire all'utente l'opzione per salvare le modifiche, aggiungere un <xref:System.Windows.Forms.Button> controllo dalla **casella degli strumenti**.

#### <a name="to-add-a-list-object"></a>Per aggiungere un oggetto elenco

1. Verificare che la cartella di lavoro **dati complessi Binding.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.

2. Aprire la finestra **origini dati** e selezionare il nodo **Employees (dipendenti** ).

3. Fare clic sulla freccia a discesa visualizzata.

4. Selezionare **ListObject** nell'elenco a discesa.

5. Trascinare la tabella **Employees** nella cella **a6**.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Viene creato un controllo denominato `EmployeesListObject` nella cella **a6**. Allo stesso tempo, <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` al progetto vengono aggiunti un oggetto denominato, un adattatore di tabella e un' <xref:System.Data.DataSet> istanza. Il controllo è associato a <xref:System.Windows.Forms.BindingSource> , che a sua volta viene associato all' <xref:System.Data.DataSet> istanza di.

### <a name="to-add-a-button"></a>Per aggiungere un pulsante

1. Dalla scheda **controlli comuni** della **casella degli strumenti** aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **a4** del foglio di foglio.

   Il passaggio successivo consiste nell'aggiungere testo al pulsante quando si apre il foglio di esecuzione.

## <a name="initialize-the-control"></a>Inizializzare il controllo
 Aggiungere testo al pulsante nel <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> gestore eventi.

### <a name="to-initialize-the-control"></a>Per inizializzare il controllo

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1. vb** o **Sheet1.cs**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per b `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Solo per C#, aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento al `Sheet1_Startup` metodo.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   A questo punto, aggiungere il codice per gestire l' <xref:System.Windows.Forms.Control.Click> evento del pulsante.

## <a name="save-changes-to-the-database"></a>Salvare le modifiche apportate al database
 Tutte le modifiche apportate ai dati esistono solo nel set di dati locale fino a quando non vengono salvate di nuovo in modo esplicito nel database.

### <a name="to-save-changes-to-the-database"></a>Per salvare le modifiche apportate al database

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento di `button` e aggiungere il codice seguente per eseguire il commit di tutte le modifiche apportate nel set di dati al database.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Test dell'applicazione
 A questo punto è possibile testare la cartella di lavoro per verificare che i dati vengano visualizzati come previsto e che sia possibile modificare i dati nell'oggetto elenco.

### <a name="to-test-the-data-binding"></a>Per testare la data binding

- Premere **F5**.

     Verificare che, quando viene aperta la cartella di lavoro, l'oggetto elenco venga compilato con i dati della tabella **Employees** .

### <a name="to-modify-data"></a>Per modificare i dati

1. Fare clic sulla cella **B7**, che dovrebbe contenere il nome **Davolio**.

2. Digitare il nome **Anderson**, quindi premere **invio**.

### <a name="to-modify-a-column-header"></a>Per modificare un'intestazione di colonna

1. Fare clic sulla cella che contiene il **Cognome** dell'intestazione di colonna.

2. Digitare **Last Name**, incluso uno spazio tra le due parole, quindi premere **invio**.

### <a name="to-save-data"></a>Per salvare i dati

1. Fare clic su **Salva** nel foglio di foglio.

2. Uscire da Excel. Quando viene richiesto di salvare le modifiche apportate, fare clic su **No** .

3. Premere **F5** per eseguire nuovamente il progetto.

     L'oggetto elenco viene compilato con i dati della tabella **Employees** .

4. Si noti che il nome nella cella **B7** è ancora **Anderson**, ovvero la modifica dei dati apportata e salvata di nuovo nel database. Il **Cognome** dell'intestazione di colonna è stato modificato nel formato originale senza spazio, perché l'intestazione di colonna non è associata al database e le modifiche apportate al foglio di foglio non sono state salvate.

### <a name="to-add-new-rows"></a>Per aggiungere nuove righe

1. Selezionare una cella all'interno dell'oggetto elenco.

    Viene visualizzata una nuova riga nella parte inferiore dell'elenco, con un asterisco (* *\** _) nella prima cella della nuova riga.

2. Aggiungere le informazioni seguenti nella riga vuota.

   |EmployeeID|LastName|FirstName|Titolo|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Direttore commerciale|

### <a name="to-delete-rows"></a>Per eliminare righe

- Fare clic con il pulsante destro del mouse sul numero 16 (riga 16) all'estrema sinistra del foglio di lavori, quindi scegliere _ * Elimina * *.

### <a name="to-sort-the-rows-in-the-list"></a>Per ordinare le righe nell'elenco

1. Selezionare una cella all'interno dell'elenco.

     I pulsanti freccia vengono visualizzati in ogni intestazione di colonna.

2. Fare clic sul pulsante freccia nell'intestazione della colonna **Last Name** .

3. Fare clic su **ordinamento crescente**.

     Le righe vengono ordinate alfabeticamente in base ai cognomi.

### <a name="to-filter-information"></a>Per filtrare le informazioni

1. Selezionare una cella all'interno dell'elenco.

2. Fare clic sul pulsante freccia nell'intestazione della colonna **titolo** .

3. Fare clic su **Sales Representative**.

     Nell'elenco vengono visualizzate solo le righe con **rappresentante vendite** nella colonna **titolo** .

4. Fare di nuovo clic sul pulsante freccia nell'intestazione della colonna **titolo** .

5. Fare clic su **(tutti)**.

     Il filtro viene rimosso e vengono visualizzate tutte le righe.

## <a name="next-steps"></a>Passaggi successivi
 In questa procedura dettagliata vengono illustrate le nozioni di base sull'associazione di una tabella in un database a un oggetto elenco. Ecco alcune possibili attività successive:

- Memorizzare nella cache i dati in modo che possano essere usati offline. Per altre informazioni, vedere [procedura: memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Distribuzione della soluzione. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

- Creare una relazione Master-Details tra un campo e una tabella. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di una relazione Master Detail utilizzando un set di dati memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Vedere anche
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Procedura dettagliata: data binding semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
