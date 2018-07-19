---
title: 'Procedura dettagliata: Data binding complesso in un progetto a livello di documento'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b490eb1afbe8136932cfbe4caf0b1df33fbd3e4b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781670"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procedura dettagliata: Data binding complesso in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni di base di data binding complesso in un progetto a livello di documento. È possibile associare più celle in un foglio di lavoro di Microsoft Office Excel a campi nel database Northwind di SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di un'origine dati al progetto cartella di lavoro.  
  
-   Aggiunta di controlli con associazione a dati a un foglio di lavoro.  
  
-   Salvataggio delle modifiche dei dati nel database.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 Il primo passaggio consiste nel creare un progetto cartella di lavoro di Excel.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Data Binding complesso**. Nella procedura guidata, selezionare **creare un nuovo documento**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Data Binding complesso** progetto al **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi fare clic su **successivo**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind, oppure aggiungere una nuova connessione usando il **nuova connessione** pulsante.  
  
5.  Dopo che una connessione è stata selezionata o creata, fare clic su **successivo**.  
  
6.  Deselezionare l'opzione per salvare la connessione, se è selezionata, quindi scegliere **successivo**.  
  
7.  Espandere la **tabelle** nodo il **degli oggetti di Database** finestra.  
  
8.  Selezionare la casella di controllo accanto al **dipendenti** tabella.  
  
9. Scegliere **Fine**.  
  
 La procedura guidata aggiunge i **dipendenti** alla tabella il **Zdroje dat** finestra. Aggiunge anche un set di dati tipizzato al progetto che è visibile nel **Esplora soluzioni**.  
  
## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro  
 Verrà visualizzato un foglio di lavoro di **dipendenti** tabella quando viene aperta la cartella di lavoro. Gli utenti saranno in grado di apportare modifiche ai dati e quindi salvare le modifiche al database facendo clic su un pulsante.  
  
 Per associare automaticamente il foglio di lavoro per la tabella, è possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo nel foglio di lavoro dal **Zdroje dat** finestra. Per consentire all'utente la possibilità di salvare le modifiche, aggiungere un <xref:System.Windows.Forms.Button> controllare dal **casella degli strumenti**.  
  
#### <a name="to-add-a-list-object"></a>Per aggiungere un oggetto elenco  
  
1.  Verificare che il **My Binding.xlsx dati complessi** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **Zdroje dat** finestra e selezionare il **dipendenti** nodo.  
  
3.  Fare clic sulla freccia giù visualizzata.  
  
4.  Selezionare **ListObject** nell'elenco a discesa.  
  
5.  Trascinare il **dipendenti** alla cella **A6**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `EmployeesListObject` viene memorizzato nella cella **A6**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominate `EmployeesBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunte al progetto. Il controllo viene associato ai <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato ai <xref:System.Data.DataSet> istanza.  
  
### <a name="to-add-a-button"></a>Per aggiungere un pulsante  
  
1.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A4** del foglio di lavoro.  
  
 Il passaggio successivo consiste nell'aggiungere testo al pulsante quando si apre il foglio di lavoro.  
  
## <a name="initialize-the-control"></a>Inizializzare il controllo  
 Aggiungere testo al pulsante nel <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> gestore dell'evento.  
  
### <a name="to-initialize-the-control"></a>Per inizializzare il controllo  
  
1.  Nella **Esplora soluzioni**, fare doppio clic su **Sheet1.vb** oppure **Sheet1.cs**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il `Sheet1_Startup` metodo per impostare il testo per b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Solo per c#, aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> dell'evento di `Sheet1_Startup` (metodo).  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 A questo punto aggiungere il codice per gestire il <xref:System.Windows.Forms.Control.Click> evento del pulsante.  
  
## <a name="save-changes-to-the-database"></a>Salvare le modifiche al database  
 Sono state apportate modifiche per i dati disponibili solo nel set di dati locale fino a quando non vengono salvati in modo esplicito nel database.  
  
### <a name="to-save-changes-to-the-database"></a>Per salvare le modifiche apportate al database  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi del `button`e aggiungere il codice seguente per eseguire il commit di tutte le modifiche apportate nel set di dati nel database.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per verificare che i dati vengono visualizzati come previsto e che sia possibile modificare i dati nell'oggetto elenco.  
  
### <a name="to-test-the-data-binding"></a>Per testare il data binding  
  
-   Premere **F5**.  
  
     Verificare che quando si apre la cartella di lavoro, il controllo ListObject con dati provenienti dal **dipendenti** tabella.  
  
### <a name="to-modify-data"></a>Per modificare i dati  
  
1.  Fare clic sulla cella **B7**, che deve contenere il nome **Davolio**.  
  
2.  Digitare il nome **Anderson**, quindi premere **invio**.  
  
### <a name="to-modify-a-column-header"></a>Per modificare un'intestazione di colonna  
  
1.  Fare clic sulla cella che contiene l'intestazione di colonna **LastName**.  
  
2.  Tipo di **Last Name**, tra cui uno spazio tra le due parole e quindi premere **invio**.  
  
### <a name="to-save-data"></a>Per salvare i dati  
  
1.  Fare clic su **salvare** nel foglio di lavoro.  
  
2.  Uscire da Excel. Fare clic su **No** quando viene richiesto di salvare le modifiche apportate.  
  
3.  Premere **F5** a eseguire nuovamente il progetto.  
  
     Il controllo ListObject con dati provenienti dal **dipendenti** tabella.  
  
4.  Si noti che il nome nella cella **B7** resta **Anderson**, ovvero i dati di modifica apportate e salvate nel database. L'intestazione di colonna **LastName** è stato modificato al formato originale senza spazio, perché l'intestazione di colonna non è associato al database e le modifiche apportate al foglio di lavoro non è stato salvato.  
  
### <a name="to-add-new-rows"></a>Per aggiungere nuove righe  
  
1.  Selezionare una cella all'interno dell'oggetto elenco.  
  
     Verrà visualizzata una nuova riga nella parte inferiore dell'elenco, con un asterisco (**\***) nella prima cella della nuova riga.  
  
2.  Aggiungere le informazioni seguenti nella riga vuota.  
  
    |EmployeeID|LastName|FirstName|Titolo|  
    |----------------|--------------|---------------|-----------|  
    |10|Greco|Mario|Responsabile vendite|  
  
### <a name="to-delete-rows"></a>Per eliminare righe  
  
-   Fare doppio clic il numero di 16 (riga 16) sul lato sinistro del foglio di lavoro e quindi fare clic su **Elimina**.  
  
### <a name="to-sort-the-rows-in-the-list"></a>Per ordinare le righe nell'elenco  
  
1.  Selezionare una cella all'interno dell'elenco.  
  
     In ogni intestazione di colonna vengono visualizzati i pulsanti freccia.  
  
2.  Fare clic sul pulsante freccia nel **cognome** intestazione di colonna.  
  
3.  Fare clic su **ordinamento crescente**.  
  
     Le righe vengono ordinate in ordine alfabetico in base al cognome.  
  
### <a name="to-filter-information"></a>Per filtrare le informazioni  
  
1.  Selezionare una cella all'interno dell'elenco.  
  
2.  Fare clic sul pulsante freccia nel **titolo** intestazione di colonna.  
  
3.  Fare clic su **rappresentante di vendita**.  
  
     L'elenco Mostra solo le righe che contengono **addetto alle vendite** nel **titolo** colonna.  
  
4.  Fare clic sul pulsante freccia nel **titolo** anche in questo caso l'intestazione di colonna.  
  
5.  Fare clic su **(tutti)**.  
  
     Il filtro viene rimosso e vengono visualizzate tutte le righe.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base di associazione di una tabella in un database a un oggetto elenco. Ecco alcune possibili attività successive:  
  
-   Memorizzare nella cache i dati in modo che possa essere usata offline. Per altre informazioni, vedere [procedura: memorizzare nella Cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Distribuire la soluzione. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Creare una relazione master/dettaglio tra un campo e una tabella. Per altre informazioni, vedere [procedura dettagliata: creare una relazione master/dettaglio mediante un dataset memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: Data binding semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  