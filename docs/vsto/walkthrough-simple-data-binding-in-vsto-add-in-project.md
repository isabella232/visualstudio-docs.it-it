---
title: 'Procedura dettagliata: data binding semplice nel progetto di componente aggiuntivo VSTO'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67264800fd2baa1ca685bcc578fb4d400e6538dd
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584911"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Procedura dettagliata: data binding semplice nel progetto di componente aggiuntivo VSTO

È possibile associare dati a controlli host e Windows Form in progetti di componente aggiuntivo VSTO. Questa procedura dettagliata illustra come aggiungere controlli a un documento di Microsoft Office Word e associare i controlli ai dati in fase di esecuzione.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Vengono illustrate le attività seguenti:

- Aggiunta di un <xref:Microsoft.Office.Tools.Word.ContentControl> a un documento in fase di esecuzione.

- Creazione di un <xref:System.Windows.Forms.BindingSource> che connette il controllo a un'istanza di un set di dati.

- Abilitazione dell'utente per scorrere i record e visualizzarli nel controllo.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accesso a un'istanza in esecuzione di SQL Server 2005 o SQL Server 2005 Express con il database di esempio `AdventureWorksLT` collegato. È possibile scaricare il `AdventureWorksLT` database dal [repository GitHub SQL Server Samples](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

  - Per aggiungere un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere [procedura: connessione di un database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Per aggiungere un database tramite la riga di comando, vedere [procedura: allineare un file di database a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di componente aggiuntivo VSTO di Word con il nome **Popolamento di documenti da un database**, usando Visual Basic o C#.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il file *ThisAddIn. vb* o *ThisAddIn.cs* e aggiunge il **popolamento dei documenti da un** progetto di database a **Esplora soluzioni**.

2. Se il progetto è destinato [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] a, aggiungere un riferimento all'assembly *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* . Tale riferimento è necessario per aggiungere controlli Windows Form a livello di codice al documento più avanti in questa procedura dettagliata.

## <a name="create-a-data-source"></a>Creare un'origine dati

Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Per aggiungere un set di dati tipizzato al progetto

1. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati**di Windows.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database**e quindi scegliere **Avanti**.

4. Se esiste già una connessione al database `AdventureWorksLT` , selezionarla e quindi scegliere **Avanti**.

    In caso contrario, scegliere **Nuova connessione**e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

5. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

6. Nella pagina **Seleziona oggetti di database** espandere **Tabelle** e quindi selezionare la tabella **Customer (SalesLT)**.

7. Fare clic su **Fine**.

    Il file *AdventureWorksLTDataSet. xsd* viene aggiunto al **Esplora soluzioni**. Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta i contenuti della tabella **Customer (SalesLT)** nel database AdventureWorksLT.

   - Oggetto TableAdapter denominato `CustomerTableAdapter` . Questo TableAdapter può essere utilizzato per leggere e scrivere dati in `AdventureWorksLTDataSet` . Per altre informazioni, vedere [Panoramica di TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

## <a name="create-controls-and-binding-controls-to-data"></a>Creazione di controlli e associazione di controlli ai dati

L'interfaccia per la visualizzazione dei record di database in questa procedura dettagliata è di base e viene creata direttamente all'interno del documento. Un <xref:Microsoft.Office.Tools.Word.ContentControl> visualizza un solo record di database alla volta e due controlli <xref:Microsoft.Office.Tools.Word.Controls.Button> consentono di scorrere avanti e indietro i record. Il controllo contenuto usa un <xref:System.Windows.Forms.BindingSource> per connettersi al database.

Per altre informazioni sull'associazione di controlli ai dati, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Per creare l'interfaccia nel documento

1. Nella classe `ThisAddIn` dichiarare i controlli seguenti per visualizzare e scorrere la tabella `Customer` del database `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. Nel metodo `ThisAddIn_Startup` aggiungere il codice seguente per inizializzare il set di dati, compilare il set di dati con le informazioni del database `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Aggiungere il codice seguente al metodo `ThisAddIn_Startup` . Viene generato un elemento host che estende il documento. Per altre informazioni, vedere [estensione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)in fase di esecuzione.

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Definire diversi intervalli all'inizio del documento. Questi intervalli identificano dove inserire il testo e posizionare i controlli.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Aggiungere i controlli dell'interfaccia agli intervalli definiti in precedenza.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Associare il controllo contenuto a `AdventureWorksLTDataSet` usando <xref:System.Windows.Forms.BindingSource>. Per gli sviluppatori C# aggiungere due gestori eventi per i controlli <xref:Microsoft.Office.Tools.Word.Controls.Button> .

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Aggiungere il codice seguente per spostarsi tra i record del database.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Testare il componente aggiuntivo

Quando si apre Word, il controllo contenuto visualizza i dati del set di dati `AdventureWorksLTDataSet` . Scorrere i record del database selezionando i pulsanti **Avanti** e **Indietro** .

### <a name="to-test-the-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5**.

     Viene creato un controllo contenuto denominato `customerContentControl` e popolato con i dati. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `customerBindingSource` . <xref:Microsoft.Office.Tools.Word.ContentControl> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

2. Selezionare i pulsanti **Avanti** e **Indietro** per scorrere i record del database.

## <a name="see-also"></a>Vedi anche

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
- [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Panoramica sull'uso dei file di database locali nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
