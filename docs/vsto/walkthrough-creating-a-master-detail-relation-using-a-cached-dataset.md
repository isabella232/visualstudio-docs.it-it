---
title: 'Procedura dettagliata: Creare una relazione master/dettaglio mediante un dataset memorizzato nella cache'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07c286a9166421272866662dea4c244fa50eb168
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875654"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Procedura dettagliata: Creare una relazione master/dettaglio mediante un dataset memorizzato nella cache
  Questa procedura dettagliata illustra la creazione di una relazione master/dettaglio in un foglio di lavoro e la memorizzazione nella cache i dati in modo che la soluzione possa essere usata offline.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere controlli a un foglio di lavoro.  
  
-   Configurare un set di dati da memorizzare nella cache in un foglio di lavoro.  
  
-   Aggiungere codice per abilitare lo scorrimento dei record.  
  
-   Testare il progetto.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso al database di esempio Northwind di SQL Server. Il database può essere nel computer di sviluppo o in un server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1. Creare un progetto cartella di lavoro di Excel con il nome **My Master-Detail**, usando Visual Basic o c#. Verificare che l'opzione **creare un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Master-Detail** progetto al **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1. Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.  
  
2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3. Selezionare **Database** e quindi fare clic su **successivo**.  
  
4. Selezionare una connessione dati al database di SQL Server di esempio Northwind, oppure aggiungere una nuova connessione usando il **nuova connessione** pulsante.  
  
5. Dopo aver selezionato o la creazione di una connessione, fare clic su **successivo**.  
  
6. Deselezionare l'opzione per salvare la connessione, se è selezionata, quindi scegliere **successivo**.  
  
7. Espandere la **tabelle** nodo il **degli oggetti di Database** finestra.  
  
8. Selezionare il **ordini** tabella e il **Order Details** tabella.  
  
9. Scegliere **Fine**.  
  
   La procedura guidata consente di aggiungere le due tabelle per il **Zdroje dat** finestra. Aggiunge anche un set di dati tipizzato al progetto che è visibile nel **Esplora soluzioni**.  
  
## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro  
 In questo passaggio si aggiungerà un intervallo denominato, un oggetto elenco e due pulsanti al primo foglio di lavoro. In primo luogo, aggiungere l'intervallo denominato e l'oggetto elenco dal **Zdroje dat** finestra in modo che vengano associati automaticamente all'origine dati. Successivamente, aggiungere i pulsanti dal **casella degli strumenti**.  
  
### <a name="to-add-a-named-range-and-a-list-object"></a>Per aggiungere un intervallo denominato e un oggetto elenco  
  
1.  Verificare che il **My Master-Detail.xlsx** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **Zdroje dat** finestra ed espandere le **ordini** nodo.  
  
3.  Selezionare il **OrderID** colonna e quindi fare clic sulla freccia giù visualizzata.  
  
4.  Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare il **OrderID** colonna cella **A2**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `OrderIDNamedRange` viene memorizzato nella cella **A2**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominate `OrdersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunte al progetto. Il controllo viene associato ai <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato ai <xref:System.Data.DataSet> istanza.  
  
5.  Scorrere verso il basso oltre le colonne che sono sotto il **ordini** tabella. Nella parte inferiore dell'elenco è il **Order Details** tabella; è qui perché è un figlio delle **ordini** tabella. Selezionare questa opzione **Order Details** tabella, non quello che si trova allo stesso livello di **ordini** di tabella e quindi fare clic sulla freccia giù visualizzata.  
  
6.  Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare il **OrderDetails** alla cella **A6**.  
  
7.  Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato **Order_DetailsListObject** viene memorizzato nella cella **A6**e associato ai <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-two-buttons"></a>Per aggiungere due pulsanti  
  
1. Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A3** del foglio di lavoro.  
  
    Questo pulsante viene denominato `Button1`.  
  
2. Aggiungere un'altra <xref:System.Windows.Forms.Button> controllo alla cella **B3** del foglio di lavoro.  
  
    Questo pulsante viene denominato `Button2`.  
  
   Successivamente, contrassegna il set di dati da memorizzare nella cache del documento.  
  
## <a name="cache-the-dataset"></a>Memorizzare nella cache il set di dati  
 Contrassegna il set di dati da memorizzare nella cache del documento, rendendo il set di dati pubblico e impostando il **CacheInDocument** proprietà.  
  
### <a name="to-cache-the-dataset"></a>Per memorizzare nella cache il set di dati  
  
1. Selezionare **NorthwindDataSet** nella barra dei componenti.  
  
2. Nel **delle proprietà** finestra Modifica il **modificatori** proprietà **pubblica**.  
  
    I set di dati devono essere pubblici prima di abilitare la memorizzazione nella cache.  
  
3. Modifica il **CacheInDocument** proprietà **True**.  
  
   Il passaggio successivo è aggiungere testo ai pulsanti e in c# aggiungere il codice per associare i gestori di eventi.  
  
## <a name="initialize-the-controls"></a>Inizializzare i controlli  
 Impostare il testo del pulsante e aggiungere i gestori di eventi durante il <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento.  
  
### <a name="to-initialize-the-data-and-the-controls"></a>Per inizializzare i dati e i controlli  
  
1.  Nella **Esplora soluzioni**, fare doppio clic su **Sheet1.vb** oppure **Sheet1.cs**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il `Sheet1_Startup` metodo per impostare il testo dei pulsanti.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Solo per c#, aggiungere gestori per il pulsante eventi click per il `Sheet1_Startup` (metodo).  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere il codice per abilitare lo scorrimento dei record  
 Aggiungere il codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento di ogni pulsante per spostarsi tra i record.  
  
### <a name="to-scroll-through-the-records"></a>Per scorrere i record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi di `Button1`e aggiungere il codice seguente per spostare indietro tra i record:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> eventi di `Button2`e aggiungere il codice seguente per passare tra i record:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che i dati vengono visualizzati come previsto e che è possibile usare la soluzione non in linea.  
  
### <a name="to-test-the-data-caching"></a>Per testare la memorizzazione nella cache di dati  
  
1.  Premere **F5**.  
  
2.  Verificare che l'intervallo denominato e l'oggetto elenco sono compilati con i dati dall'origine dati.  
  
3.  Lo scorrimento di alcuni record facendo clic sui pulsanti.  
  
4.  Salvare la cartella di lavoro e quindi chiudere la cartella di lavoro e Visual Studio.  
  
5.  Disabilitare la connessione al database. Scollegare il cavo di rete dal computer se il database si trova in un server o arrestare il servizio SQL Server se il database si trova nel computer di sviluppo.  
  
6.  Aprire Excel e quindi aprire **My Master-Detail.xlsx** dalle *\bin* directory (*\My Master-Detail\bin* in Visual Basic o *\My Master-Detail\bin\ eseguire il debug* in c#).  
  
7.  Scorrere tra alcuni dei record per verificare che il foglio di lavoro viene eseguito in genere quando si è disconnessi.  
  
8.  Ristabilire la connessione al database. Connettere nuovamente il computer alla rete se il database si trova in un server, o avviare il servizio SQL Server se il database si trova nel computer di sviluppo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base di creazione di una relazione tra dati master/dettaglio in un foglio di lavoro e la memorizzazione nella cache un set di dati. Ecco alcune possibili attività successive:  
  
-   Distribuire la soluzione. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Dati della cache](../vsto/caching-data.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
