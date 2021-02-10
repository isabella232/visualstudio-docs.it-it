---
title: 'Procedura dettagliata: data binding semplice in un progetto a livello di documento'
description: Informazioni sulle nozioni di base di data binding in un progetto a livello di documento e che un singolo campo dati in un database SQL Server è associato a un intervallo denominato in Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31084703a581999a1f25bfc82db6c36d9e2cbf6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937409"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procedura dettagliata: data binding semplice in un progetto a livello di documento
  In questa procedura dettagliata vengono illustrate le nozioni di base di data binding in un progetto a livello di documento. Un singolo campo dati in un database SQL Server è associato a un intervallo denominato in Microsoft Office Excel. Nella procedura dettagliata viene inoltre illustrato come aggiungere controlli che consentono di scorrere tutti i record nella tabella.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un'origine dati per un progetto di Excel.

- Aggiunta di controlli a un foglio di foglio.

- Scorrimento dei record del database.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di esempio Northwind SQL Server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio verrà creato un progetto di cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **My Simple Data Binding**, usando Visual Basic o C#. Assicurarsi che sia selezionata l'opzione **Crea un nuovo documento** . Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto di **associazione dati semplice** a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati** di Windows.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **database** e quindi fare clic su **Avanti**.

4. Selezionare una connessione dati all'esempio Northwind SQL Server database o aggiungere una nuova connessione usando il pulsante **nuova connessione** .

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se selezionata, quindi fare clic su **Avanti**.

7. Espandere il nodo **tabelle** nella finestra **oggetti di database** .

8. Selezionare la casella di controllo accanto alla tabella **Customers** .

9. Fare clic su **Fine**.

   La procedura guidata consente di aggiungere la tabella **Customers** alla finestra **origini dati** . Aggiunge anche un set di dati tipizzato al progetto che è visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di controllo
 Per questa procedura dettagliata sono necessari due intervalli denominati e quattro pulsanti nel primo foglio di foglio. In primo luogo, aggiungere i due intervalli denominati dalla finestra **origini dati** in modo che vengano associati automaticamente all'origine dati. Aggiungere quindi i pulsanti dalla **casella degli strumenti**.

### <a name="to-add-two-named-ranges"></a>Per aggiungere due intervalli denominati

1. Verificare che la cartella di lavoro *Simple Data Binding.xlsx* sia aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.

2. Aprire la finestra **origini dati** ed espandere il nodo **Customers** .

3. Selezionare la colonna **CompanyName** , quindi fare clic sulla freccia a discesa visualizzata.

4. Selezionare **NamedRange** nell'elenco a discesa, quindi trascinare la colonna **CompanyName** sulla cella **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Viene creato un controllo denominato `companyNameNamedRange` nella cella **a1**. Allo stesso tempo, <xref:System.Windows.Forms.BindingSource> `customersBindingSource` al progetto vengono aggiunti un oggetto denominato, un adattatore di tabella e un' <xref:System.Data.DataSet> istanza. Il controllo è associato a <xref:System.Windows.Forms.BindingSource> , che a sua volta viene associato all' <xref:System.Data.DataSet> istanza di.

5. Selezionare la colonna **CustomerID** nella finestra **origini dati** , quindi fare clic sulla freccia a discesa visualizzata.

6. Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare la colonna **CustomerID** sulla cella **B1**.

7. Un altro <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `customerIDNamedRange` viene creato nella cella **B1** e associato a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Per aggiungere quattro pulsanti

1. Dalla scheda **controlli comuni** della **casella degli strumenti** aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **a3** del foglio di comando.

    Questo pulsante è denominato `Button1` .

2. Aggiungere altri tre pulsanti alle celle seguenti in questo ordine, in modo che i nomi siano quelli indicati di seguito:

   |Cell (Cella)|(Nome)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Il passaggio successivo consiste nell'aggiungere testo ai pulsanti e in C# aggiungere i gestori eventi.

## <a name="initialize-the-controls"></a>Inizializzare i controlli
 Impostare il testo del pulsante e aggiungere i gestori eventi durante l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento.

### <a name="to-initialize-the-controls"></a>Per inizializzare i controlli

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1. vb** o **Sheet1.cs**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per ogni pulsante.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Solo per C#, aggiungere i gestori eventi per gli eventi click del pulsante al `Sheet1_Startup` metodo.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   A questo punto, aggiungere il codice per gestire gli <xref:System.Windows.Forms.Control.Click> eventi dei pulsanti in modo che l'utente possa sfogliare i record.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere codice per consentire lo scorrimento dei record
 Aggiungere il codice al <xref:System.Windows.Forms.Control.Click> gestore eventi di ogni pulsante per spostarsi tra i record.

### <a name="to-move-to-the-first-record"></a>Per passare al primo record

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento del `Button1` pulsante e aggiungere il codice seguente per passare al primo record:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Per passare al record precedente

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento del `Button2` pulsante e aggiungere il codice seguente per spostare la posizione indietro di uno:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Per passare al record successivo

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento del `Button3` pulsante e aggiungere il codice seguente per avanzare la posizione di uno:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Per passare all'ultimo record

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento del `Button4` pulsante e aggiungere il codice seguente per passare all'ultimo record:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Testare l'applicazione
 A questo punto è possibile testare la cartella di lavoro per verificare che sia possibile esplorare i record nel database.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Verificare che il primo record venga visualizzato nelle celle **a1** e **b1**.

3. Fare clic **>** sul `Button3` pulsante () e verificare che il record successivo venga visualizzato nella cella **a1** e **B1**.

4. Fare clic sugli altri pulsanti di scorrimento per verificare che il record venga modificato come previsto.

## <a name="next-steps"></a>Passaggi successivi
 In questa procedura dettagliata vengono illustrate le nozioni di base sull'associazione di un intervallo denominato a un campo di un database. Ecco alcune possibili attività successive:

- Memorizzare nella cache i dati in modo che possano essere usati offline. Per altre informazioni, vedere [procedura: memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Associare le celle a più colonne di una tabella, anziché a un campo. Per altre informazioni, vedere [procedura dettagliata: data binding complessi in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Utilizzare un <xref:System.Windows.Forms.BindingNavigator> controllo per scorrere i record. Per altre informazioni, vedere [procedura: esplorare i dati con il controllo BindingNavigator Windows Form](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Vedi anche
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Procedura dettagliata: data binding complesse in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
