---
title: Creare un'applicazione dati semplice tramite ADO.NET
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 36fc5dd306782779f553d4144c272c91c7e0f0af
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929401"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Creare un'applicazione dati semplice tramite ADO.NET

Quando si crea un'applicazione che modifica i dati in un database, è possibile eseguire attività di base, ad esempio la definizione delle stringhe di connessione, l'inserimento di dati e l'esecuzione di stored procedure. Seguendo questo argomento, è possibile individuare come interagire con un database dall'interno di un'applicazione semplice Windows Form "Form over data" utilizzando l'oggetto visivo C# o Visual Basic e ADO.NET.  Tutte le tecnologie di dati .NET, inclusi DataSet, LINQ to SQL ed Entity Framework, in definitiva, eseguire i passaggi che sono molto simili a quelli illustrati in questo articolo.

Questo articolo illustra un modo semplice per ottenere dati da un database in modo rapido. Se l'applicazione deve modificare i dati in modi non semplice e aggiornare il database, è consigliabile mediante Entity Framework e l'uso di data binding per la sincronizzazione automatica controlli dell'interfaccia utente per le modifiche nei dati sottostanti.

> [!IMPORTANT]
> Per semplificare il codice, non include la gestione delle eccezioni dell'ambiente di produzione.

## <a name="prerequisites"></a>Prerequisiti

Per creare l'applicazione, è necessario disporre di:

-   Visual Studio.

-   LocalDB di SQL Server Express. Se non si dispone di SQL Server Express LocalDB, è possibile installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

Questo argomento si presuppone che si ha familiarità con la funzionalità di base dell'IDE di Visual Studio e può creare un'applicazione Windows Forms, aggiungere form al progetto, inserire i pulsanti e altri controlli nei form, impostare le proprietà dei controlli e semplici eventi di codice. Se non si ha familiarità con queste attività, si consiglia di completare la [Introduzione a Visual C# e Visual Basic](../ide/quickstart-visual-basic-console.md) argomento prima di iniziare questa procedura dettagliata.

## <a name="set-up-the-sample-database"></a>Impostare il database di esempio

Creare il database di esempio seguendo questa procedura:

1. In Visual Studio, aprire il **Esplora Server** finestra.

2. Fare clic su **connessioni dati** e scegliere **Crea nuovo Database di SQL Server**.

3. Nel **nome Server** testo casella, immettere **(localdb) \mssqllocaldb**.

4. Nel **nuovo nome del database** testo casella, immettere **Sales**, quindi scegliere **OK**.

     Vuoto **Sales** database viene creato e aggiunto al nodo Connessioni dati in Esplora Server.

5. Fare clic sui **vendite** connessione dati e selezionare **nuova Query**.

     Apre una finestra dell'editor di query.

6. Copia il [script di Transact-SQL Sales](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) negli Appunti.

7. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

     Dopo un breve periodo di tempo, termina l'esecuzione di query e vengono creati gli oggetti di database. Il database contiene due tabelle: clienti e ordini. Queste tabelle inizialmente non contengono dati, ma è possibile aggiungere i dati quando si esegue l'applicazione che verrà creata. Il database contiene inoltre quattro stored procedure semplici.

## <a name="create-the-forms-and-add-controls"></a>Creare i form e aggiungere i controlli

1. Creare un progetto per Windows Forms Application e denominarlo **SimpleDataApp**.

    Visual Studio crea il progetto e diversi file, tra cui un form Windows vuoto denominato **Form1**.

2. Aggiungere due form Windows al progetto in modo da disporre di tre form e assegnare i nomi seguenti:

   -   **Navigazione**

   -   **NewCustomer**

   -   **FillOrCancel**

3. Per ogni form, aggiungere caselle di testo, pulsanti e altri controlli come illustrato nelle figure seguenti. Per ciascun controllo, impostare le proprietà descritte nelle tabelle.

   > [!NOTE]
   > La casella di gruppo e i controlli Label migliorano la leggibilità, ma non vengono usati nel codice.

   **Form Navigazione**

   ![Finestra di dialogo Navigazione](../data-tools/media/simpleappnav.png)

|Controlli per il form Navigazione|Proprietà|
| - |----------------|
|Button|Name = btnGoToAdd|
|Button|Name = btnGoToFillOrCancel|
|Button|Name = btnExit|

 **Form NewCustomer**

 ![Aggiungere un nuovo cliente e inserire un ordine](../data-tools/media/simpleappnewcust.png)

|Controlli per il form NewCustomer|Proprietà|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|Button|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Nome = dtpOrderDate|
|Button|Name = btnPlaceOrder|
|Button|Name = btnAddAnotherAccount|
|Button|Name = btnAddFinish|

 **Form FillOrCancel**

 ![Completare o annullare gli ordini](../data-tools/media/simpleappcancelfill.png)

|Controlli del form FillOrCancel|Proprietà|
| - |----------------|
|TextBox|Name = txtOrderID|
|Button|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Button|Name = btnCancelOrder|
|Button|Name = btnFillOrder|
|Button|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Archiviare la stringa di connessione
 Quando l'applicazione tenta di aprire una connessione al database, l'applicazione deve disporre dell'accesso alla stringa di connessione. Per evitare di immettere la stringa manualmente in ciascun form, archiviare la stringa nel *app. config* nel progetto e creare un metodo che restituisce la stringa quando viene chiamato il metodo da qualsiasi form nell'applicazione.

 È possibile trovare la stringa di connessione facendo clic sui **vendite** connessione dati in **Esplora Server** e scegliendo **proprietà**. Individuare il **ConnectionString** proprietà, quindi usare **Ctrl**+**oggetto**, **Ctrl**+**C**  per selezionare e copiare la stringa negli Appunti.

1.  Se si usa C#, in **Esplora soluzioni**, espandere il **proprietà** nodo sotto il progetto e quindi aprire il **innanzi** file.
    Se si usa Visual Basic, in **Esplora soluzioni**, fare clic su **Mostra tutti i file**, espandere il **My Project** nodo e quindi aprire il **innanzi** file.

2.  Nel **Name** colonna, immettere `connString`.

3.  Nel **tipo** elenco, selezionare **(stringa di connessione)**.

4.  Nel **ambito** elenco, selezionare **applicazione**.

5.  Nel **valore** colonna, immettere la stringa di connessione (senza alcuna all'esterno delle virgolette) e quindi salvare le modifiche.

> [!NOTE]
> In un'applicazione reale, è consigliabile archiviare la stringa di connessione in modo sicuro, come descritto in [stringhe di connessione e i file di configurazione](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Scrivere il codice per i form

Questa sezione include brevi descrizioni generali delle operazioni eseguite da ogni modulo. Fornisce inoltre il codice che definisce la logica sottostante, quando viene selezionato un pulsante nel form.

### <a name="navigation-form"></a>Form Navigazione

Quando si esegue l'applicazione, verrà visualizzato il form Navigazione. Il pulsante **Aggiungi un account** consente di aprire il form NewCustomer. Il pulsante **Completare o annullare gli ordini** consente di aprire il form FillOrCancel. Il pulsante **Esci** consente di chiudere l'applicazione.

#### <a name="make-the-navigation-form-the-startup-form"></a>Impostare il form Navigazione come form di avvio

Se si usa C#, in **Esplora soluzioni** aprire **Program.cs** e modificare la riga `Application.Run` nel seguente modo: `Application.Run(new Navigation());`

Se si usa Visual Basic, in **Esplora soluzioni**, aprire il **delle proprietà** finestra, seleziona il **applicazione** scheda e quindi selezionare  **Simpledataapp. Navigation** nella **form di avvio** elenco.

#### <a name="create-auto-generated-event-handlers"></a>Creare i gestori eventi generato automaticamente

Fare doppio clic sui tre pulsanti nel form navigazione per creare metodi del gestore eventi vuoto. Fare doppio clic sul pulsante aggiunge anche il codice generato automaticamente nel file di codice di progettazione che consente a un clic del pulsante generare un evento.

#### <a name="add-code-for-the-navigation-form-logic"></a>Aggiungere il codice per la logica di form navigazione

Nella tabella codici per il form navigazione, completamento i corpi di metodo per il pulsante tre gestori degli eventi click come illustrato nel codice seguente.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Form NewCustomer

Quando si immettono un nome di cliente e quindi selezionare il **creare un Account** pulsante, il form NewCustomer crea un account del cliente e SQL Server restituisce un valore IDENTITY come nuovo ID cliente. È quindi possibile inserire un ordine per il nuovo account specificando una quantità e una data di ordine e selezionando il **effettuare l'ordine** pulsante.

#### <a name="create-auto-generated-event-handlers"></a>Creare i gestori eventi generato automaticamente

Creare un Click vuoto gestore eventi per ogni pulsante nel form NewCustomer facendo doppio clic su ciascuna delle quattro pulsanti. Fare doppio clic sul pulsante aggiunge anche il codice generato automaticamente nel file di codice di progettazione che consente a un clic del pulsante generare un evento.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Aggiungere il codice per la logica di form NewCustomer

Per completare la logica di form NewCustomer, seguire questa procedura.

1. Portare il `System.Data.SqlClient` dello spazio dei nomi nell'ambito in modo da non dover completamente qualificare i nomi dei relativi membri.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Aggiungere alcune variabili e metodi helper per la classe come illustrato nel codice seguente.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Completa i corpi di metodo per il pulsante quattro gestori degli eventi click come illustrato nel codice seguente.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Form FillOrCancel

Il form FillOrCancel esegue una query per restituire un ordine quando si immette un ID ordine e quindi scegliere il **Find Order** pulsante. La riga restituita viene visualizzata in una griglia di dati di sola lettura. È possibile contrassegnare l'ordine come annullato (X) se si seleziona il **Cancel Order** pulsante oppure è possibile contrassegnarlo come evaso (F) se si seleziona il **Fill Order** pulsante. Se si seleziona il **Find Order** nuovamente clic sul pulsante, viene visualizzata la riga aggiornata.

#### <a name="create-auto-generated-event-handlers"></a>Creare i gestori eventi generato automaticamente

Creare vuota fare clic sui gestori eventi per i quattro pulsanti nel form FillOrCancel facendo doppio clic sui pulsanti. Fare doppio clic sul pulsante aggiunge anche il codice generato automaticamente nel file di codice di progettazione che consente a un clic del pulsante generare un evento.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Aggiungere il codice per la logica di form FillOrCancel

Per completare la logica di form FillOrCancel, seguire questa procedura.

1. Portare i seguenti due spazi dei nomi nell'ambito in modo che non è necessario specificare i nomi dei relativi membri completi.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Aggiungere un variabile e metodo di supporto alla classe, come illustrato nel codice seguente.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Completa i corpi di metodo per il pulsante quattro gestori degli eventi click come illustrato nel codice seguente.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Eseguire il test dell'applicazione

Premere il tasto **F5** per compilare e testare l'applicazione dopo aver inserito il codice in ogni gestore dell'evento Click e quindi dopo aver completato la scrittura del codice.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
