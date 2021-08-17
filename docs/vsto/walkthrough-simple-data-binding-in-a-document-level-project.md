---
title: 'Procedura dettagliata: Data binding semplice in un progetto a livello di documento'
description: Informazioni di base su data binding in un progetto a livello di documento e sul fatto che un singolo campo dati in un database SQL Server sia associato a un intervallo denominato in Microsoft Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c965b63c4f7aec8229fce45be95b5b7c74bd0c96
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025466"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procedura dettagliata: Data binding semplice in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni di base data binding in un progetto a livello di documento. Un singolo campo dati in un database SQL Server è associato a un intervallo denominato in Microsoft Office Excel. La procedura dettagliata illustra anche come aggiungere controlli che consentono di scorrere tutti i record nella tabella.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un'origine dati per un Excel progetto.

- Aggiunta di controlli a un foglio di lavoro.

- Scorrimento dei record del database.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di SQL Server Northwind.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server database.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio si creerà un progetto Excel cartella di lavoro.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un Excel di cartella di lavoro con il nome **My Simple Data Binding** usando Visual Basic o C#. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto **My Simple Data Binding** a **Esplora soluzioni**.

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

8. Selezionare la casella di controllo accanto **alla tabella** Customers.

9. Fare clic su **Fine**.

   La procedura guidata aggiunge **la tabella Customers** alla finestra **Origini** dati. Aggiunge anche un set di dati tipizzato al progetto visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Per questa procedura dettagliata sono necessari due intervalli denominati e quattro pulsanti nel primo foglio di lavoro. Aggiungere prima di tutto i due intervalli denominati dalla **finestra Origini** dati in modo che siano associati automaticamente all'origine dati. Aggiungere quindi i pulsanti dalla Casella **degli strumenti**.

### <a name="to-add-two-named-ranges"></a>Per aggiungere due intervalli denominati

1. Verificare che la *cartella di lavoro My Simple Data Binding.xlsx* sia aperta nella finestra di progettazione Visual Studio, con **Sheet1** visualizzato.

2. Aprire la **finestra Origini** dati ed espandere il **nodo** Clienti.

3. Selezionare la **colonna CompanyName** e quindi fare clic sulla freccia a discesa visualizzata.

4. Selezionare **NamedRange** nell'elenco a discesa e quindi trascinare la **colonna CompanyName** nella cella **A1.**

     Nella <xref:Microsoft.Office.Tools.Excel.NamedRange> cella `companyNameNamedRange` **A1** viene creato un controllo denominato . Allo stesso tempo, al progetto vengono aggiunti un oggetto denominato , un adattatore di tabella e <xref:System.Windows.Forms.BindingSource> `customersBindingSource` <xref:System.Data.DataSet> un'istanza di . Il controllo è associato a , che a sua <xref:System.Windows.Forms.BindingSource> volta è associato <xref:System.Data.DataSet> all'istanza di .

5. Selezionare la **colonna CustomerID** nella **finestra Origini** dati e quindi fare clic sulla freccia a discesa visualizzata.

6. Fare **clic su NamedRange** nell'elenco a discesa e quindi trascinare la **colonna CustomerID** nella cella **B1.**

7. Un <xref:Microsoft.Office.Tools.Excel.NamedRange> altro controllo denominato viene creato nella cella `customerIDNamedRange` **B1** e associato a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Per aggiungere quattro pulsanti

1. Dalla scheda **Controlli comuni** della Casella degli **strumenti** aggiungere un controllo alla <xref:System.Windows.Forms.Button> cella **A3** del foglio di lavoro.

    Questo pulsante è denominato `Button1` .

2. Aggiungere altri tre pulsanti alle celle seguenti in questo ordine, in modo che i nomi siano come illustrato:

   |Cell (Cella)|(Nome)|
   |----------|--------------|
   |B3|Button2|
   |C3|Pulsante3|
   |D3|Pulsante4|

   Il passaggio successivo consiste nell'aggiungere testo ai pulsanti e in C# aggiungere gestori eventi.

## <a name="initialize-the-controls"></a>Inizializzare i controlli
 Impostare il testo del pulsante e aggiungere gestori eventi durante <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> l'evento .

### <a name="to-initialize-the-controls"></a>Per inizializzare i controlli

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** e quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per ogni pulsante.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet2":::

3. Solo per C#, aggiungere gestori eventi per gli eventi click del pulsante al `Sheet1_Startup` metodo .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet3":::

   Aggiungere ora il codice per gestire <xref:System.Windows.Forms.Control.Click> gli eventi dei pulsanti in modo che l'utente possa esplorare i record.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere codice per abilitare lo scorrimento tra i record
 Aggiungere codice al <xref:System.Windows.Forms.Control.Click> gestore eventi di ogni pulsante per spostarsi tra i record.

### <a name="to-move-to-the-first-record"></a>Per passare al primo record

1. Aggiungere un gestore eventi per <xref:System.Windows.Forms.Control.Click> l'evento del `Button1` pulsante e aggiungere il codice seguente per passare al primo record:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet4":::

### <a name="to-move-to-the-previous-record"></a>Per passare al record precedente

1. Aggiungere un gestore eventi per l'evento del pulsante e aggiungere il codice seguente per spostare nuovamente <xref:System.Windows.Forms.Control.Click> `Button2` la posizione di uno:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet5":::

### <a name="to-move-to-the-next-record"></a>Per passare al record successivo

1. Aggiungere un gestore eventi per l'evento del pulsante e aggiungere il codice seguente per <xref:System.Windows.Forms.Control.Click> `Button3` far avanzare la posizione di uno:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet6":::

### <a name="to-move-to-the-last-record"></a>Per passare all'ultimo record

1. Aggiungere un gestore eventi per <xref:System.Windows.Forms.Control.Click> l'evento del `Button4` pulsante e aggiungere il codice seguente per passare all'ultimo record:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per assicurarsi di poter esplorare i record nel database.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Verificare che il primo record venga visualizzato nelle celle **A1** **e B1.**

3. Fare clic **>** sul pulsante ( ) e verificare che il record successivo venga visualizzato nelle celle `Button3` **A1** e **B1**.

4. Fare clic su altri pulsanti di scorrimento per verificare che il record cambi come previsto.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'associazione di un intervallo denominato a un campo di un database. Ecco alcune possibili attività successive:

- Memorizzare nella cache i dati in modo che possano essere usati offline. Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Associare celle a più colonne in una tabella anziché a un campo. Per altre informazioni, vedere [Procedura dettagliata: data binding in un progetto a livello di documento.](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)

- Usare un <xref:System.Windows.Forms.BindingNavigator> controllo per scorrere i record. Per altre informazioni, vedere [Procedura: Esplorare i dati](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)con il controllo BindingNavigator Windows Forms .

## <a name="see-also"></a>Vedi anche
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati nelle soluzioni Office dati](../vsto/data-in-office-solutions.md)
- [Procedura dettagliata: Data binding in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
