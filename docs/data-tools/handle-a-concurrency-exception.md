---
title: Gestire un'eccezione di concorrenza
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 57820a7532255c0084bafc5134cf7793b8c88ab6
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407666"
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza

Vengono generate eccezioni di concorrenza ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ) quando due utenti tentano di modificare contemporaneamente gli stessi dati in un database. In questa procedura dettagliata viene creata un'applicazione Windows che illustra come intercettare un oggetto <xref:System.Data.DBConcurrencyException> , individuare la riga che ha provocato l'errore e apprendere una strategia per gestirla.

Questa procedura dettagliata illustra il processo seguente:

1. Creare un nuovo progetto di **applicazione Windows Forms** .

2. Creare un nuovo set di dati in base alla tabella Northwind Customers.

3. Creare un modulo con un oggetto <xref:System.Windows.Forms.DataGridView> per visualizzare i dati.

4. Compilare un set di dati con i dati della tabella Customers nel database Northwind.

5. Utilizzare la funzionalità **Mostra dati tabella** in **Esplora server** per accedere ai dati della tabella Customers e modificare un record.

6. Modificare lo stesso record con un valore diverso, aggiornare il set di dati e tentare di scrivere le modifiche nel database, causando la generazione di un errore di concorrenza.

7. Rilevare l'errore, quindi visualizzare le diverse versioni del record, consentendo all'utente di determinare se continuare e aggiornare il database o di annullare l'aggiornamento.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio** è possibile installare SQL Server Express database locale come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Per iniziare, creare un nuovo Windows Forms Application:

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Forms** .

4. Denominare il progetto **ConcurrencyWalkthrough** , quindi scegliere **OK**.

     Il progetto **ConcurrencyWalkthrough** viene creato e aggiunto a **Esplora soluzioni** e viene aperto un nuovo form nella finestra di progettazione.

## <a name="create-the-northwind-dataset"></a>Creare il set di dati Northwind

Successivamente, creare un set di dati denominato **NorthwindDataSet** :

1. Scegliere **Aggiungi nuova origine dati** dal menu **dati** .

   Viene avviata la Configurazione guidata origine dati.

2. Nella schermata **scegliere un tipo di origine dati** selezionare **database**.

   ![Configurazione guidata origine dati in Visual Studio](media/data-source-configuration-wizard.png)

3. Selezionare una connessione al database di esempio Northwind dall'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco delle connessioni, selezionare **nuova connessione**.

    > [!NOTE]
    > Se ci si connette a un file di database locale, selezionare **No** quando viene richiesto se si desidera aggiungere il file al progetto.

4. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

5. Espandere il nodo **tabelle** e selezionare la tabella **Customers** . Il nome predefinito per il set di dati deve essere **NorthwindDataSet**.

6. Selezionare **fine** per aggiungere il set di dati al progetto.

## <a name="create-a-data-bound-datagridview-control"></a>Creazione di un controllo DataGridView con associazione a dati

In questa sezione viene creato un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> trascinando l'elemento **Customers** dalla finestra **origini dati** nel Windows Form.

1. Per aprire la finestra **origini dati** , scegliere **Mostra origini dati** dal menu **dati** .

2. Nella finestra **origini dati** espandere il nodo **NorthwindDataSet** , quindi selezionare la tabella **Customers** .

3. Selezionare la freccia rivolta verso il basso sul nodo della tabella, quindi selezionare **DataGridView** nell'elenco a discesa.

4. Trascinare la tabella su un'area vuota del modulo.

     Un <xref:System.Windows.Forms.DataGridView> controllo denominato **customersDataGridView** e un oggetto <xref:System.Windows.Forms.BindingNavigator> denominato **CustomersBindingNavigator** vengono aggiunti al form associato a <xref:System.Windows.Forms.BindingSource> . Questo, a sua volta, è associato alla tabella Customers nell'oggetto NorthwindDataSet.

## <a name="test-the-form"></a>Testare il modulo

È ora possibile testare il modulo per verificare che il comportamento sia quello previsto fino a questo punto:

1. Selezionare **F5** per eseguire l'applicazione.

     Il form viene visualizzato con un <xref:System.Windows.Forms.DataGridView> controllo che viene compilato con i dati della tabella Customers.

2. Selezionare **Arresta debug** dal menu **Debug**.

## <a name="handle-concurrency-errors"></a>Gestione degli errori di concorrenza

La modalità di gestione degli errori dipende dalle regole business specifiche che governano l'applicazione. Per questa procedura dettagliata, si userà la strategia seguente come esempio per la gestione dell'errore di concorrenza.

L'applicazione presenta all'utente tre versioni del record:

- Record corrente nel database

- Record originale caricato nel set di dati

- Modifiche proposte nel set di dati

L'utente può quindi sovrascrivere il database con la versione proposta oppure annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori del database.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza

1. Creare un gestore di errori personalizzato.

2. Consente di visualizzare le scelte dell'utente.

3. Elaborare la risposta dell'utente.

4. Inviare di nuovo l'aggiornamento o reimpostare i dati nel set di dati.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Aggiungere il codice per gestire l'eccezione di concorrenza

Quando si tenta di eseguire un aggiornamento e viene generata un'eccezione, in genere si desidera eseguire un'operazione con le informazioni fornite dall'eccezione generata. In questa sezione viene aggiunto il codice che tenta di aggiornare il database. È anche possibile gestire gli eventuali <xref:System.Data.DBConcurrencyException> che potrebbero essere generati, nonché qualsiasi altra eccezione.

> [!NOTE]
> I `CreateMessage` `ProcessDialogResults` metodi e vengono aggiunti più avanti nella procedura dettagliata.

1. Aggiungere il codice seguente sotto il `Form1_Load` Metodo:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Sostituire il `CustomersBindingNavigatorSaveItem_Click` metodo per chiamare il `UpdateDatabase` metodo in modo che abbia un aspetto simile al seguente:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Visualizza le opzioni per l'utente

Il codice appena scritto chiama la `CreateMessage` procedura per visualizzare le informazioni sull'errore all'utente. Per questa procedura dettagliata viene usata una finestra di messaggio per visualizzare le diverse versioni del record per l'utente. Ciò consente all'utente di scegliere se sovrascrivere il record con le modifiche o annullare la modifica. Quando l'utente seleziona un'opzione (fa clic su un pulsante) nella finestra di messaggio, la risposta viene passata al `ProcessDialogResult` metodo.

Creare il messaggio aggiungendo il codice seguente all'editor di **codice**. Immettere il codice seguente nel `UpdateDatabase` Metodo:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente

È necessario anche codice per elaborare la risposta dell'utente alla finestra di messaggio. Le opzioni consentono di sovrascrivere il record corrente nel database con la modifica proposta oppure di abbandonare le modifiche locali e aggiornare la tabella dati con il record attualmente presente nel database. Se l'utente sceglie **Sì** , il <xref:System.Data.DataTable.Merge%2A> metodo viene chiamato con l'argomento *preserveChanges* impostato su **true**. In questo modo il tentativo di aggiornamento ha esito positivo, perché la versione originale del record ora corrisponde al record nel database.

Aggiungere il codice seguente sotto il codice aggiunto nella sezione precedente:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form-behavior"></a>Testare il comportamento del modulo

È ora possibile testare il form per assicurarsi che si comportano come previsto. Per simulare una violazione della concorrenza, è necessario modificare i dati nel database dopo aver compilato l'oggetto NorthwindDataSet.

1. Selezionare **F5** per eseguire l'applicazione.

2. Una volta visualizzato il modulo, lasciarlo in esecuzione e passare all'IDE di Visual Studio.

3. Scegliere **Esplora server** dal menu **Visualizza**.

4. In **Esplora server** espandere la connessione usata dall'applicazione, quindi espandere il nodo **tabelle** .

5. Fare clic con il pulsante destro del mouse sulla tabella **Customers** , quindi scegliere **Mostra dati tabella**.

6. Nel primo record ( **ALFKI** ) modificare **ContactName** in **Maria Anders2**.

    > [!NOTE]
    > Passare a una riga diversa per eseguire il commit della modifica.

7. Passare al form in esecuzione di ConcurrencyWalkthrough.

8. Nel primo record nel form ( **ALFKI** ) modificare **ContactName** in **Maria Anders1**.

9. Fare clic sul pulsante **Salva**.

     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.

   Se si seleziona **No** , l'aggiornamento viene annullato e il set di dati viene aggiornato con i valori attualmente presenti nel database. Se **si seleziona Sì** , il valore proposto viene scritto nel database.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
