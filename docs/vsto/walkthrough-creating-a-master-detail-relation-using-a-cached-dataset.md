---
title: Crea relazione dettaglio Master con il set di dati memorizzato nella cache
description: Informazioni sulla creazione di una relazione master/dettaglio in un foglio di lavoro e sulla memorizzazione nella cache dei dati in modo che la soluzione possa essere usata offline.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 843718ea49ae7df7d34775283ce8120f077b0a0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925513"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Procedura dettagliata: creare una relazione di dettaglio master usando un set di dati memorizzato nella cache
  In questa procedura dettagliata viene illustrata la creazione di una relazione master/dettaglio in un foglio di lavoro e la memorizzazione dei dati nella cache in modo che la soluzione possa essere utilizzata offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere controlli a un foglio di foglio.

- Configurare un set di dati da memorizzare nella cache in un foglio di foglio.

- Aggiungere il codice per consentire lo scorrimento dei record.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso al database di esempio Northwind SQL Server. Il database può trovarsi nel computer di sviluppo o in un server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio verrà creato un progetto di cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **My Master-Details**, usando Visual Basic o C#. Assicurarsi che sia selezionata l'opzione **Crea un nuovo documento** . Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto **Master-Detail** a **Esplora soluzioni**.

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

8. Selezionare la tabella **Orders** e la tabella **Order Details** .

9. Fare clic su **Fine**.

   La procedura guidata aggiunge le due tabelle alla finestra **origini dati** . Aggiunge anche un set di dati tipizzato al progetto che è visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di controllo
 In questo passaggio si aggiungerà un intervallo denominato, un oggetto elenco e due pulsanti al primo foglio di esecuzione. Aggiungere innanzitutto l'intervallo denominato e l'oggetto elenco dalla finestra **origini dati** in modo che vengano associati automaticamente all'origine dati. Aggiungere quindi i pulsanti dalla **casella degli strumenti**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Per aggiungere un intervallo denominato e un oggetto elenco

1. Verificare che la cartella di lavoro **My Master-Detail.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.

2. Aprire la finestra **origini dati** ed espandere il nodo **Orders** .

3. Selezionare la colonna **OrderID** , quindi fare clic sulla freccia a discesa visualizzata.

4. Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare la colonna **OrderID** sulla cella **a2**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Viene creato un controllo denominato `OrderIDNamedRange` nella cella **a2**. Allo stesso tempo, <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` al progetto vengono aggiunti un oggetto denominato, un adattatore di tabella e un' <xref:System.Data.DataSet> istanza. Il controllo è associato a <xref:System.Windows.Forms.BindingSource> , che a sua volta viene associato all' <xref:System.Data.DataSet> istanza di.

5. Scorrere verso il basso le colonne presenti nella tabella **Orders** . Nella parte inferiore dell'elenco è presente la tabella **Order Details** . è un elemento figlio della tabella **Orders** . Selezionare la tabella **Order Details** , non quella che si trova allo stesso livello della tabella **Orders** , quindi fare clic sulla freccia a discesa visualizzata.

6. Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare la tabella **OrderDetails** sulla cella **a6**.

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato **Order_DetailsListObject** viene creato nella cella **a6** e associato a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Per aggiungere due pulsanti

1. Dalla scheda **controlli comuni** della **casella degli strumenti** aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **a3** del foglio di comando.

    Questo pulsante è denominato `Button1` .

2. Aggiungere un altro <xref:System.Windows.Forms.Button> controllo alla cella **B3** del foglio di foglio.

    Questo pulsante è denominato `Button2` .

   Contrassegnare quindi il set di dati da memorizzare nella cache del documento.

## <a name="cache-the-dataset"></a>Memorizzare nella cache il set di dati
 Contrassegnare il set di dati da memorizzare nella cache nel documento rendendo pubblico il set di dati e impostando la proprietà **CacheInDocument** .

### <a name="to-cache-the-dataset"></a>Per memorizzare nella cache il set di dati

1. Selezionare **NorthwindDataSet** nella barra dei componenti.

2. Nella finestra **Proprietà** modificare la proprietà **Modifiers** in **public**.

    I set di impostazioni devono essere pubblici prima che la memorizzazione nella cache sia abilitata.

3. Modificare la proprietà **CacheInDocument** in **true**.

   Il passaggio successivo consiste nell'aggiungere testo ai pulsanti e in C# aggiungere il codice per associare i gestori eventi.

## <a name="initialize-the-controls"></a>Inizializzare i controlli
 Impostare il testo del pulsante e aggiungere i gestori eventi durante l' <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento.

### <a name="to-initialize-the-data-and-the-controls"></a>Per inizializzare i dati e i controlli

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1. vb** o **Sheet1.cs**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per i pulsanti.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Solo per C#, aggiungere i gestori eventi per gli eventi click del pulsante al `Sheet1_Startup` metodo.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere codice per consentire lo scorrimento dei record
 Aggiungere il codice al <xref:System.Windows.Forms.Control.Click> gestore eventi di ogni pulsante per spostarsi tra i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

1. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento di `Button1` e aggiungere il codice seguente per spostarsi all'indietro nei record:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Aggiungere un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento di `Button2` e aggiungere il codice seguente per avanzare nei record:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Testare l'applicazione
 A questo punto è possibile testare la cartella di lavoro per assicurarsi che i dati vengano visualizzati come previsto e che sia possibile usare la soluzione offline.

### <a name="to-test-the-data-caching"></a>Per testare la memorizzazione nella cache dei dati

1. Premere **F5**.

2. Verificare che l'intervallo denominato e l'oggetto elenco siano riempiti con i dati dell'origine dati.

3. Scorrere alcuni record facendo clic sui pulsanti.

4. Salvare la cartella di lavoro, quindi chiudere la cartella di lavoro e Visual Studio.

5. Disabilitare la connessione al database. Scollegare il cavo di rete dal computer se il database si trova in un server oppure arrestare il servizio SQL Server se il database si trova nel computer di sviluppo.

6. Aprire Excel, quindi aprire **My Master-Detail.xlsx** dalla directory *\bin* (*\My Master-Detail\bin* in Visual Basic o *\My Master-Detail\bin\debug* in C#).

7. Scorrere alcuni record per verificare che il foglio di funzionamento venga eseguito normalmente in caso di disconnessione.

8. Riconnettersi al database. Connettere di nuovo il computer alla rete se il database si trova in un server o avviare il servizio SQL Server se il database si trova nel computer di sviluppo.

## <a name="next-steps"></a>Passaggi successivi
 In questa procedura dettagliata vengono illustrate le nozioni di base per la creazione di una relazione master/dettaglio dati in un foglio di lavoro e la memorizzazione nella cache Ecco alcune possibili attività successive:

- Distribuzione della soluzione. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Vedi anche
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Dati cache](../vsto/caching-data.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
