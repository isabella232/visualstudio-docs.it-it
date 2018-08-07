---
title: Gestire un'eccezione di concorrenza
ms.date: 09/11/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6aca4815672d700fbea9d489f6316b8b0337f8df
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582333"
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza

Le eccezioni di concorrenza (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) vengono generati quando due utenti tentano di modificare gli stessi dati in un database nello stesso momento. In questa procedura dettagliata, si crea un'applicazione Windows che illustra come intercettare una <xref:System.Data.DBConcurrencyException>, individuare la riga che ha causato l'errore e informazioni su una strategia per come gestirlo.

Questa procedura dettagliata illustra il processo seguente:

1. Creare un nuovo progetto di **Applicazione Windows Form**.

2. Creare un nuovo set di dati in base alla tabella Customers di Northwind.

3. Creare un form con un <xref:System.Windows.Forms.DataGridView> per visualizzare i dati.

4. Riempire un set di dati della tabella Customers nel database Northwind.

5. Usare la **Mostra dati tabella** funzionalità in **Esplora Server** per accedere ai dati della tabella Customers e modificare un record.

6. Modificare lo stesso record su un valore diverso, aggiornare il set di dati e tentano di scrivere le modifiche al database, che comporta un errore di concorrenza.

7. Intercetta l'errore, quindi visualizzare le diverse versioni del record, consentendo all'utente determinare se continuare e aggiornare il database o annullare l'aggiornamento.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

> [!NOTE]
> Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o l'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Iniziare creando una nuova applicazione Windows Forms:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **ConcurrencyWalkthrough**, quindi scegliere **OK**.

     Il **ConcurrencyWalkthrough** viene creato e aggiunto al progetto **Esplora soluzioni**, e un nuovo modulo viene aperto nella finestra di progettazione.

## <a name="create-the-northwind-dataset"></a>Creare il set di dati di Northwind

Successivamente, creare un set di dati denominato **NorthwindDataSet**:

1. Nel **Data** menu, scegliere **origine aggiungere nuovi dati**.

   Apre la configurazione guidata origine dati.

2. Nel **scegliere un tipo di origine dati** schermata, seleziona **Database**.

   ![Configurazione guidata origine dati in Visual Studio](media/data-source-configuration-wizard.png)

3. Selezionare una connessione al database di esempio Northwind nell'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco delle connessioni, selezionare **nuova connessione**.

    > [!NOTE]
    > Se ci si connette a un file di database locale, selezionare **No** quando viene chiesto se si desidera aggiungere il file al progetto.

4. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** schermata, seleziona **successivo**.

5. Espandere la **tabelle** nodo e selezionare il **clienti** tabella. Il nome predefinito per il set di dati deve essere **NorthwindDataSet**.

6. Selezionare **fine** per aggiungere il set di dati al progetto.

## <a name="create-a-data-bound-datagridview-control"></a>Creare un controllo DataGridView associato ai dati

In questa sezione si crea una <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> trascinando la **clienti** articolo dal **Zdroje dat** finestra nei Form Windows.

1. Nel **Data** menu, scegliere **Mostra origini dati** per aprire la **finestra Origini dati**.

2. Nel **Zdroje dat** finestra, espandere il **NorthwindDataSet** nodo e quindi selezionare il **clienti** tabella.

3. Selezionare la freccia rivolta verso il basso nel nodo della tabella e quindi selezionare **DataGridView** nell'elenco a discesa.

4. Trascinare la tabella in un'area vuota del form.

     Oggetto <xref:System.Windows.Forms.DataGridView> controllo denominato **CustomersDataGridView**e un <xref:System.Windows.Forms.BindingNavigator> denominato **CustomersBindingNavigator**, vengono aggiunti al form che è associato il <xref:System.Windows.Forms.BindingSource>. Questo è, a sua volta, associato alla tabella Customers di NorthwindDataSet.

## <a name="test-the-form"></a>Verificare il modulo

È ora possibile testare il form per assicurarsi che tutto funzioni come previsto fino a questo punto:

1. Selezionare **F5** per eseguire l'applicazione.

     Viene visualizzato il form con un <xref:System.Windows.Forms.DataGridView> controllo su di esso viene riempita con i dati dalla tabella Customers.

2. Nel **Debug** dal menu **arresta debug**.

## <a name="handle-concurrency-errors"></a>Gestire gli errori di concorrenza

Modalità di gestione degli errori dipende dalle regole business specifici che regolano l'applicazione. Per questa procedura dettagliata, utilizziamo la strategia seguente come esempio per informazioni su come gestire l'errore di concorrenza.

L'applicazione presenta all'utente con le tre versioni di record:

- Il record corrente nel database

- Il record originale che viene caricato nel set di dati

- Le modifiche proposte nel set di dati

L'utente è quindi possibile sovrascrivere il database con la versione proposta, o annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori dal database.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza

1. Creare un gestore errori personalizzato.

2. Visualizzare le scelte per l'utente.

3. Elaborare la risposta dell'utente.

4. Inviare di nuovo l'aggiornamento o ripristinare i dati nel set di dati.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Aggiungere codice per gestire le eccezioni di concorrenza

Quando si tenta di eseguire un aggiornamento e viene generata un'eccezione, in genere si desidera eseguire un'operazione con le informazioni fornite per l'eccezione generata. In questa sezione si aggiunta il codice che tenta di aggiornare il database. È anche possibile gestire qualsiasi <xref:System.Data.DBConcurrencyException> che potrebbero essere generati, oltre a qualsiasi altra eccezione.

> [!NOTE]
> Il `CreateMessage` e `ProcessDialogResults` metodi vengono aggiunti più avanti nella procedura dettagliata.

1. Aggiungere il codice seguente sotto il `Form1_Load` metodo:

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Sostituire il `CustomersBindingNavigatorSaveItem_Click` metodo da chiamare il `UpdateDatabase` metodo in modo che risulti simile al seguente:

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Visualizzare le scelte per l'utente

Il codice sopra riportato consente le chiamate di `CreateMessage` procedura per visualizzare le informazioni sull'errore all'utente. In questa procedura dettagliata si usa una finestra di messaggio per visualizzare le diverse versioni del record per l'utente. Ciò consente all'utente di scegliere se si desidera sovrascrivere il record con le modifiche oppure annullare la modifica. Una volta che l'utente seleziona un'opzione (Seleziona un pulsante) nella finestra di messaggio, la risposta viene passata per il `ProcessDialogResult` (metodo).

Creare il messaggio aggiungendo il codice seguente per il **Editor di codice**. Immettere il codice riportato di seguito il `UpdateDatabase` metodo:

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente

È anche necessario codice per elaborare la risposta dell'utente nella finestra di messaggio. Le opzioni sono a sovrascrivere il record corrente nel database con la modifica proposta, o ignorare le modifiche locali e aggiornare la tabella di dati con il record che è attualmente nel database. Se l'utente sceglie **Yes**, il <xref:System.Data.DataTable.Merge%2A> metodo viene chiamato con il *preserveChanges* argomento impostato su **true**. In questo modo il tentativo di aggiornamento abbia esito positivo, perché la versione originale del record corrisponde a questo punto il record nel database.

Aggiungere il codice seguente sotto il codice che è stato aggiunto nella sezione precedente:

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Verificare il modulo

È ora possibile testare il form per assicurarsi che tutto funzioni come previsto. Per simulare una violazione della concorrenza, è modificare i dati nel database dopo aver compilato NorthwindDataSet.

1. Selezionare **F5** per eseguire l'applicazione.

2. Una volta visualizzato il form, lascia in esecuzione e passare all'IDE di Visual Studio.

3. Nel **View** menu, scegliere **Esplora Server**.

4. Nelle **Esplora Server**, espandere la connessione viene usando l'applicazione e quindi espandere il **tabelle** nodo.

5. Fare doppio clic il **clienti** tabella e quindi selezionare **Mostra dati tabella**.

6. Nel primo record (**ALFKI**), cambiare **ContactName** al **Maria Anders2**.

    > [!NOTE]
    > Passare a un'altra riga per il commit della modifica.

7. Passare al modulo in esecuzione del progetto ConcurrencyWalkthrough.

8. Nel primo record nel form (**ALFKI**), cambiare **ContactName** al **Maria Anders1**.

9. Selezionare il **salvare** pulsante.

     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.

   Selezionando **No** Annulla l'aggiornamento e aggiorna il set di dati con i valori presenti nel database. Selezionando **Sì** scrive il valore proposto per il database.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)