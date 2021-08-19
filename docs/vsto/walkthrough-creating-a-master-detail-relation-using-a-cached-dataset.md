---
title: Creare una relazione master-dettagli usando il set di dati memorizzato nella cache
description: Informazioni sulla creazione di una relazione master/dettagli in un foglio di lavoro e sulla memorizzazione nella cache dei dati in modo che la soluzione possa essere usata offline.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c4d8d32ea4abfd7b81e6e86bc8d1affa32d1c3b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059868"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Procedura dettagliata: Creare una relazione master-dettagli usando un set di dati memorizzato nella cache
  Questa procedura dettagliata illustra la creazione di una relazione master/dettagli in un foglio di lavoro e la memorizzazione nella cache dei dati in modo che la soluzione possa essere usata offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere controlli a un foglio di lavoro.

- Configurare un set di dati da memorizzare nella cache in un foglio di lavoro.

- Aggiungere codice per abilitare lo scorrimento tra i record.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso al database di SQL Server Northwind. Il database può essere nel computer di sviluppo o in un server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio si creerà un progetto Excel cartella di lavoro.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un Excel cartella di lavoro con il nome **My Master-Detail** usando Visual Basic o C#. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto **My Master-Detail** **a Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Se la **finestra Origini** dati non è visibile, visualizzarla scegliendo Visualizza altre origini Windows  >    >  **dati.**

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database** e quindi fare clic su **Avanti.**

4. Selezionare una connessione dati al database di esempio Northwind SQL Server oppure aggiungere una nuova connessione usando il **pulsante Nuova** connessione.

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti.**

6. Deselezionare l'opzione per salvare la connessione, se selezionata, quindi fare clic su **Avanti.**

7. Espandere il **nodo** Tabelle nella **finestra Oggetti di** database .

8. Selezionare la **tabella Orders** e la tabella **Order Details.**

9. Fare clic su **Fine**.

   La procedura guidata aggiunge le due tabelle alla **finestra Origini** dati . Aggiunge anche un set di dati tipizzato al progetto visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 In questo passaggio si aggiungeranno un intervallo denominato, un oggetto elenco e due pulsanti al primo foglio di lavoro. Aggiungere prima di tutto l'intervallo denominato e l'oggetto elenco dalla finestra Origini **dati** in modo che siano associati automaticamente all'origine dati. Aggiungere quindi i pulsanti dalla casella **degli strumenti**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Per aggiungere un intervallo denominato e un oggetto elenco

1. Verificare che la **cartella di lavoro Master-Detail.xlsx** sia aperta nella finestra Visual Studio, con **Sheet1** visualizzato.

2. Aprire la **finestra Origini** dati ed espandere il **nodo** Ordini .

3. Selezionare la **colonna OrderID** e quindi fare clic sulla freccia a discesa visualizzata.

4. Fare **clic su NamedRange** nell'elenco a discesa e quindi trascinare la **colonna OrderID** nella cella **A2.**

     Nella <xref:Microsoft.Office.Tools.Excel.NamedRange> cella `OrderIDNamedRange` **A2** viene creato un controllo denominato . Allo stesso tempo, un oggetto denominato , un adattatore di tabella e <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` <xref:System.Data.DataSet> un'istanza di vengono aggiunti al progetto. Il controllo è associato <xref:System.Windows.Forms.BindingSource> all'oggetto , che a sua volta è associato all'istanza <xref:System.Data.DataSet> di .

5. Scorrere verso il basso oltre le colonne sotto la **tabella Orders.** Nella parte inferiore dell'elenco è disponibile la **tabella Dettagli** ordine. è qui perché è un elemento figlio della **tabella Orders.** Selezionare questa **tabella Dettagli** ordine, non quella che si trova allo stesso livello della tabella **Orders,** quindi fare clic sulla freccia a discesa visualizzata.

6. Fare **clic su ListObject** nell'elenco a discesa e quindi trascinare la **tabella OrderDetails** nella cella **A6.**

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato **Order_DetailsListObject** viene creato nella cella **A6** e associato a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Per aggiungere due pulsanti

1. Dalla scheda **Controlli comuni** della casella degli **strumenti** aggiungere un controllo alla <xref:System.Windows.Forms.Button> cella **A3** del foglio di lavoro.

    Questo pulsante è denominato `Button1` .

2. Aggiungere un <xref:System.Windows.Forms.Button> altro controllo alla cella **B3 del** foglio di lavoro.

    Questo pulsante è denominato `Button2` .

   Contrassegnare quindi il set di dati da memorizzare nella cache nel documento.

## <a name="cache-the-dataset"></a>Memorizzare nella cache il set di dati
 Contrassegnare il set di dati da memorizzare nella cache nel documento rendendo pubblico il set di dati e impostando la **proprietà CacheInDocument.**

### <a name="to-cache-the-dataset"></a>Per memorizzare nella cache il set di dati

1. Selezionare **NorthwindDataSet** nella barra dei componenti.

2. Nella finestra **Proprietà** modificare la proprietà **Modificatori** in **Pubblico.**

    I set di dati devono essere pubblici prima che sia abilitata la memorizzazione nella cache.

3. Modificare la **proprietà CacheInDocument** in **True.**

   Il passaggio successivo consiste nell'aggiungere testo ai pulsanti e in C# aggiungere il codice per associare i gestori eventi.

## <a name="initialize-the-controls"></a>Inizializzare i controlli
 Impostare il testo del pulsante e aggiungere gestori eventi durante <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> l'evento .

### <a name="to-initialize-the-data-and-the-controls"></a>Per inizializzare i dati e i controlli

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** e quindi scegliere Visualizza **codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al `Sheet1_Startup` metodo per impostare il testo per i pulsanti.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet15":::

3. Solo per C#, aggiungere gestori eventi per gli eventi click del pulsante al `Sheet1_Startup` metodo .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet16":::

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Aggiungere codice per abilitare lo scorrimento tra i record
 Aggiungere codice al gestore <xref:System.Windows.Forms.Control.Click> eventi di ogni pulsante per spostarsi tra i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

1. Aggiungere un gestore eventi per l'evento di e aggiungere il codice seguente per spostarsi indietro <xref:System.Windows.Forms.Control.Click> `Button1` tra i record:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet17":::

2. Aggiungere un gestore eventi per <xref:System.Windows.Forms.Control.Click> l'evento `Button2` di e aggiungere il codice seguente per scorrere i record:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet18":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per assicurarsi che i dati siano visualizzati come previsto e che sia possibile usare la soluzione offline.

### <a name="to-test-the-data-caching"></a>Per testare la memorizzazione dei dati nella cache

1. Premere **F5**.

2. Verificare che l'intervallo denominato e l'oggetto elenco siano compilati con i dati dell'origine dati.

3. Scorrere alcuni dei record facendo clic sui pulsanti.

4. Salvare la cartella di lavoro, quindi chiudere la cartella di lavoro e Visual Studio.

5. Disabilitare la connessione al database. Scollegare il cavo di rete dal computer se il database si trova in un server o arrestare il servizio SQL Server se il database si trova nel computer di sviluppo.

6. Aprire Excel e quindi my **Master-Detail.xlsx** dalla directory *\bin* (*\Master-Detail\bin* in Visual Basic o *\My Master-Detail\bin\debug* in C#).

7. Scorrere alcuni record per verificare che il foglio di lavoro funzioni normalmente quando è disconnesso.

8. Riconnettersi al database. Connessione il computer alla rete se il database si trova in un server o avviare il servizio SQL Server se il database si trova nel computer di sviluppo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base per la creazione di una relazione dati master/dettagli in un foglio di lavoro e la memorizzazione nella cache di un set di dati. Ecco alcune possibili attività successive:

- Distribuzione della soluzione. Per altre informazioni, vedere [Distribuire una Office distribuzione](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Vedi anche
- [Associare dati a controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dati in Office soluzioni](../vsto/data-in-office-solutions.md)
- [Dati cache](../vsto/caching-data.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
