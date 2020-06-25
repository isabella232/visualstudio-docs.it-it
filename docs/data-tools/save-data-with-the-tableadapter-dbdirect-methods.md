---
title: Salvare dati con i metodi DBDirect di TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 77d7aa0859ee383258f80dfd74f36d584790e464
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281609"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare dati con i metodi DBDirect di TableAdapter

In questa procedura dettagliata vengono fornite istruzioni dettagliate per l'esecuzione di istruzioni SQL direttamente in un database utilizzando i metodi DBDirect di un TableAdapter. I metodi DBDirect di un oggetto TableAdapter consentono un elevato livello di controllo degli aggiornamenti del database. È possibile usarli per eseguire istruzioni SQL e stored procedure specifiche chiamando i singoli `Insert` metodi, `Update` e in base alle `Delete` esigenze dell'applicazione, anziché il metodo di overload `Update` che esegue le istruzioni Update, INSERT e DELETE in un'unica chiamata.

Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova **applicazione Windows Forms**.

- Creare e configurare un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Selezionare il controllo da creare nel form tramite il trascinamento degli elementi dalla finestra **Origini dati**. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creare il controllo associato a dati tramite il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Aggiungere metodi per accedere direttamente al database ed eseguire inserimenti, aggiornamenti ed eliminazioni.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**è possibile installare SQL Server Express database locale come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare un' **applicazione Windows Forms**.

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Forms** .

4. Denominare il progetto **TableAdapterDbDirectMethodsWalkthrough**, quindi scegliere **OK**.

     Il progetto **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Region` presente nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database Northwind di esempio, vedere [procedura: installare database di](../data-tools/installing-database-systems-tools-and-samples.md)esempio.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Mostra origini dati**dal menu **dati** .

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati** selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database** espandere il nodo **tabelle** .

8. Selezionare la `Region` tabella, quindi fare clic su **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Region` viene visualizzata nella finestra **Origini dati**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Aggiungere i controlli al form per visualizzare i dati

Creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

Per creare controlli associati a dati in Windows Form, trascinare il nodo **area** principale dalla finestra **origini dati** nel form.

Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter` , <xref:System.Windows.Forms.BindingSource> e viene <xref:System.Windows.Forms.BindingNavigator> visualizzato nella barra dei componenti.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter

1. Trascinare tre controlli <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** in **Form1** (sotto l'oggetto **RegionDataGridView**).

2. Impostare le proprietà **Name** e **Text** seguenti per ciascun pulsante.

    |Nome|Text|
    |----------|----------|
    |`InsertButton`|**Insert**|
    |`UpdateButton`|**Update**|
    |`DeleteButton`|**Elimina**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database

1. Selezionare **InsertButton** per creare un gestore eventi per l'evento click e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database

1. Fare doppio clic su **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere il codice per eliminare i record dal database

1. Selezionare **DeleteButton** per creare un gestore eventi per l'evento click e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Eseguire l'applicazione

- Selezionare **F5** per eseguire l'applicazione.

- Selezionare il pulsante **Inserisci** e verificare che il nuovo record venga visualizzato nella griglia.

- Selezionare il pulsante **Aggiorna** e verificare che il record sia stato aggiornato nella griglia.

- Selezionare il pulsante **Elimina** e verificare che il record sia stato rimosso dalla griglia.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, è possibile eseguire diversi passaggi dopo la creazione di un form associato a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Aggiunta di funzionalità di ricerca al form.

- Aggiunta di altre tabelle al set di dati tramite selezione di **Configura il Dataset con la procedura guidata** nella finestra **Origini dati**. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
