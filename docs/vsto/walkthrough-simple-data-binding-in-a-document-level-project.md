---
title: 'Procedura dettagliata: Data binding semplice in un progetto a livello di documento'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ae634a87e8b105df88fed4168b6a70909efbc7f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868999"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procedura dettagliata: Data binding semplice in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni di base di data binding in un progetto a livello di documento. Un singolo campo dati in un database di SQL Server è associato a un intervallo denominato in Microsoft Office Excel. La procedura dettagliata illustra inoltre come aggiungere i controlli che consentono di scorrere tutti i record nella tabella.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
- Creazione di un'origine dati per un progetto di Excel.  
  
- Aggiunta di controlli a un foglio di lavoro.  
  
- Lo scorrimento di record del database.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1. Creare un progetto cartella di lavoro di Excel con il nome **My Data Binding semplice**, usando Visual Basic o c#. Verificare che l'opzione **creare un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Data Binding semplice** progetto al **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1. Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.  
  
2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3. Selezionare **Database** e quindi fare clic su **successivo**.  
  
4. Selezionare una connessione dati al database di SQL Server di esempio Northwind, oppure aggiungere una nuova connessione usando il **nuova connessione** pulsante.  
  
5. Dopo che una connessione è stata selezionata o creata, fare clic su **successivo**.  
  
6. Deselezionare l'opzione per salvare la connessione, se è selezionata, quindi scegliere **successivo**.  
  
7. Espandere la **tabelle** nodo il **degli oggetti di Database** finestra.  
  
8. Selezionare la casella di controllo accanto al **clienti** tabella.  
  
9. Scegliere **Fine**.  
  
   La procedura guidata aggiunge i **clienti** alla tabella il **Zdroje dat** finestra. Aggiunge anche un set di dati tipizzato al progetto che è visibile nel **Esplora soluzioni**.  
  
## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro  
 Per questa procedura dettagliata, sono necessari due gli intervalli denominati e quattro pulsanti presenti nel primo foglio di calcolo. In primo luogo, aggiungere i due intervalli denominati dal **Zdroje dat** finestra in modo che vengano associati automaticamente all'origine dati. Successivamente, aggiungere i pulsanti dal **casella degli strumenti**.  
  
### <a name="to-add-two-named-ranges"></a>Per aggiungere due gli intervalli denominati  
  
1.  Verificare che il *My Binding.xlsx dati semplice* cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **Zdroje dat** finestra ed espandere le **clienti** nodo.  
  
3.  Selezionare il **CompanyName** colonna e quindi fare clic sulla freccia giù visualizzata.  
  
4.  Selezionare **NamedRange** nell'elenco a discesa, quindi trascinare il **CompanyName** colonna cella **A1**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `companyNameNamedRange` viene memorizzato nella cella **A1**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominate `customersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunte al progetto. Il controllo viene associato ai <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato ai <xref:System.Data.DataSet> istanza.  
  
5.  Selezionare il **CustomerID** colonna il **Zdroje dat** finestra e quindi fare clic sulla freccia giù visualizzata.  
  
6.  Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare il **CustomerID** colonna cella **B1**.  
  
7.  Un'altra <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `customerIDNamedRange` viene memorizzato nella cella **B1**e associato ai <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Aggiungere quattro pulsanti  
  
1. Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A3** del foglio di lavoro.  
  
    Questo pulsante viene denominato `Button1`.  
  
2. Aggiungere altri tre pulsanti per le celle seguenti nell'ordine indicato, in modo che i nomi indicati:  
  
   |cella|(Nome)|  
   |----------|--------------|  
   |B3|Button2|  
   |C3|Button3|  
   |D3|Button4|  
  
   Il passaggio successivo è aggiungere testo ai pulsanti e in c# aggiungere gestori di eventi.  
  
## <a name="initialize-the-controls"></a>Inizializzare i controlli  
 Impostare il testo del pulsante e aggiungere i gestori di eventi durante il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento.  
  
### <a name="to-initialize-the-controls"></a>Per inizializzare i controlli  
  
1. Nella **Esplora soluzioni**, fare doppio clic su **Sheet1.vb** oppure **Sheet1.cs**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2. Aggiungere il codice seguente per il `Sheet1_Startup` metodo per impostare il testo per ogni pulsante.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. Solo per c#, aggiungere gestori per il pulsante eventi click per il `Sheet1_Startup` (metodo).  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   A questo punto aggiungere il codice per gestire il <xref:System.Windows.Forms.Control.Click> gli eventi dei pulsanti in modo che l'utente può scorrere i record.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere il codice per abilitare lo scorrimento dei record  
 Aggiungere il codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento di ogni pulsante per spostarsi tra i record.  
  
### <a name="to-move-to-the-first-record"></a>Per spostare il primo record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi del `Button1` pulsante e aggiungere il codice seguente per spostare il primo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Per passare al record precedente  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi del `Button2` pulsante e aggiungere il codice seguente per spostare nuovamente la posizione di uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Per passare al record successivo  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi del `Button3` pulsante e aggiungere il codice seguente per spostare la posizione di uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Per spostarsi all'ultimo record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi del `Button4` pulsante e aggiungere il codice seguente per passare all'ultimo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che è possibile esplorare i record nel database.  
  
### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Verificare che il primo record visualizzato nelle celle **A1** e **B1**.  
  
3.  Scegliere il **>** (`Button3`) pulsante e verificare che il record successivo nella cella **A1** e **B1**.  
  
4.  Fare clic sugli altri pulsanti di scorrimento per confermare che il record viene modificato nel modo previsto.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base di associazione di un intervallo denominato a un campo in un database. Ecco alcune possibili attività successive:  
  
-   Memorizzare nella cache i dati in modo che possa essere usata offline. Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Associare le celle a più colonne in una tabella, invece di un singolo campo. Per altre informazioni, vedere [Procedura dettagliata: Data binding complesso in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Usare un <xref:System.Windows.Forms.BindingNavigator> per scorrere i record di controllo. Per altre informazioni, vedere [Procedura: Esplorare i dati con il controllo BindingNavigator di Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: Data binding complesso in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
