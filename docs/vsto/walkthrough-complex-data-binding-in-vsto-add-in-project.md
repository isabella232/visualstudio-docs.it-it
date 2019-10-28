---
title: 'Procedura dettagliata: data binding complessi nel progetto di componente aggiuntivo VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99caf87000ea9df9260e8926eee4c7136bc9b848
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985489"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Procedura dettagliata: data binding complessi nel progetto di componente aggiuntivo VSTO
  È possibile associare dati a controlli host e Windows Form in progetti di componente aggiuntivo VSTO. Questa procedura dettagliata illustra come aggiungere controlli a un foglio di lavoro di Microsoft Office Excel e associare i controlli ai dati in fase di esecuzione.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- Aggiunta di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione.

- Creazione di un <xref:System.Windows.Forms.BindingSource> che connette il controllo a un'istanza di un set di dati.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un'istanza in esecuzione di SQL Server 2005 o SQL Server 2005 Express con il database di esempio `AdventureWorksLT` collegato. È possibile scaricare il database `AdventureWorksLT` dal [repository GitHub degli esempi di SQL Server](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

  - Per aggiungere un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere [procedura: connessione di un database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Per aggiungere un database tramite la riga di comando, vedere [procedura: allineare un file di database a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di componente aggiuntivo VSTO di Excel denominato **Popolamento di fogli di lavoro da un database**, usando Visual Basic o C#.

     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il file `ThisAddIn.vb` o `ThisAddIn.cs` e aggiunge il progetto **Popolamento di fogli di lavoro da un database** a **Esplora soluzioni**.

## <a name="create-a-data-source"></a>Creare un'origine dati
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Per aggiungere un set di dati tipizzato al progetto

1. Se la finestra **origini dati** non è visibile, visualizzarla nella barra dei menu scegliendo **Visualizza** > **altre** **origini dati**di Windows > .

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database**e quindi scegliere **Avanti**.

4. Se esiste già una connessione al database `AdventureWorksLT` , selezionarla e quindi scegliere **Avanti**.

    In caso contrario, scegliere **Nuova connessione**e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

5. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

6. Nella pagina **Seleziona oggetti di database** espandere **Tabelle** e quindi selezionare la tabella **Address (SalesLT)** .

7. Scegliere **Fine**.

    Il file *AdventureWorksLTDataSet. xsd* viene aggiunto al **Esplora soluzioni**. Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta i contenuti della tabella **Address (SalesLT)** nel database AdventureWorksLT.

   - Oggetto TableAdapter denominato `AddressTableAdapter`. Questo TableAdapter può essere utilizzato per leggere e scrivere dati nel `AdventureWorksLTDataSet`. Per altre informazioni, vedere [Panoramica di TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

## <a name="create-controls-and-bind-controls-to-data"></a>Creazione di controlli e associazione di controlli ai dati
 Per questa procedura dettagliata il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> visualizza tutti i dati nella tabella selezionata non appena l'utente apre la cartella di lavoro. L'oggetto elenco usa un <xref:System.Windows.Forms.BindingSource> per connettere il controllo al database.

 Per altre informazioni sull'associazione di controlli ai dati, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Per aggiungere l'oggetto elenco, il set di dati e l'adattatore tabella

1. Nella classe `ThisAddIn` dichiarare i controlli seguenti per visualizzare la tabella `Address` del set di dati `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. Nel metodo `ThisAddIn_Startup` aggiungere il codice seguente per inizializzare il set di dati e compilare il set di dati con le informazioni del set di dati `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Aggiungere al metodo `ThisAddIn_Startup` il seguente codice. Viene generato un elemento host che estende il foglio di lavoro. Per altre informazioni, vedere [estensione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)in fase di esecuzione.

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Creare un intervallo e aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> .

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Per associare l'oggetto elenco a `AdventureWorksLTDataSet` , usare <xref:System.Windows.Forms.BindingSource>. Passare i nomi delle colonne da associare all'oggetto elenco.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testare il componente aggiuntivo
 Quando si apre Excel, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> visualizza i dati della tabella `Address` del set di dati `AdventureWorksLTDataSet` .

### <a name="to-test-the-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

- Premere **F5**.

     Nel foglio di lavoro viene creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `addressListObject` . Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `addressBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

## <a name="see-also"></a>Vedere anche

- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: popolare fogli di dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: popolare documenti con dati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: scorrere i record di un database in un foglio di foglio](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Procedura: aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Procedura dettagliata: data binding semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Procedura dettagliata: data binding complesse in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Panoramica sull'uso dei file di database locali nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Panoramica sull'uso dei file di database locali nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
