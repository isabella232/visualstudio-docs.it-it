---
title: Creare un'applicazione dati semplice tramite ADO.NET
description: Informazioni su come creare una semplice applicazione da form a dati usando Windows Forms e ADO.NET in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 506983ffacf846969f6e74fd503344d90180ca91
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631518"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Creare un'applicazione dati semplice tramite ADO.NET

Quando si crea un'applicazione che modifica i dati in un database, è possibile eseguire attività di base, ad esempio la definizione delle stringhe di connessione, l'inserimento di dati e l'esecuzione di stored procedure. Seguendo questo argomento, è possibile scoprire come interagire con un database dall'interno di una semplice applicazione Windows Forms "forms over data" usando Visual C# o Visual Basic e ADO.NET.  Tutte le tecnologie dati .NET, inclusi set di dati, LINQ to SQL e Entity Framework, eseguono infine passaggi molto simili a quelli illustrati in questo articolo.

Questo articolo illustra un modo semplice per ottenere dati da un database in modo rapido. Se l'applicazione deve modificare i dati in modi non semplici e aggiornare il database, è consigliabile usare Entity Framework e data binding per sincronizzare automaticamente i controlli dell'interfaccia utente con le modifiche nei dati sottostanti.

> [!IMPORTANT]
> Per semplificare il codice, non include la gestione delle eccezioni dell'ambiente di produzione.

## <a name="prerequisites"></a>Prerequisiti

Per creare l'applicazione, è necessario disporre di:

- Visual Studio.

- LocalDB di SQL Server Express. Se non si dispone di SQL Server Express Local DB, è possibile installarlo dalla pagina [di SQL Server Express download](https://www.microsoft.com/sql-server/sql-server-editions-express).

Questo argomento presuppone che si abbia familiarità con le funzionalità di base dell'IDE di Visual Studio e che sia possibile creare un'applicazione form Windows, aggiungere form al progetto, inserire pulsanti e altri controlli nei form, impostare le proprietà dei controlli ed eventi semplici del codice. Se non si ha familiarità con queste attività, è consigliabile completare l'argomento Introduzione a [Visual C# e Visual Basic](../ide/quickstart-visual-basic-console.md) prima di iniziare questa procedura dettagliata.

## <a name="set-up-the-sample-database"></a>Impostare il database di esempio

Creare il database di esempio seguendo questa procedura:

1. In Visual Studio aprire la **finestra** Esplora server dati.

2. Fare clic con il pulsante destro **del mouse** su Connessioni dati e scegliere Crea nuovo **SQL Server database**.

3. Nella casella **di testo Nome** server immettere **(localdb)\mssqllocaldb**.

4. Nella casella **di testo New database name** (Nuovo nome database) immettere **Sales** e quindi scegliere **OK.**

     Il database **Sales** vuoto viene creato e aggiunto al nodo Connessioni dati in Esplora server.

5. Fare clic con il pulsante destro **del mouse sulla connessione** dati Sales e scegliere Nuova **query**.

     Verrà visualizzata una finestra dell'editor di query.

6. Copiare [lo script Transact-SQL Sales](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) negli Appunti.

7. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

     Dopo un breve periodo di tempo, l'esecuzione della query viene completata e vengono creati gli oggetti di database. Il database contiene due tabelle: Customer e Orders. Queste tabelle inizialmente non contengono dati, ma è possibile aggiungere dati quando si esegue l'applicazione che si creerà. Il database contiene anche quattro stored procedure semplici.

## <a name="create-the-forms-and-add-controls"></a>Creare i form e aggiungere i controlli

1. Creare un progetto per Windows Forms Application e denominarlo **SimpleDataApp**.

    Visual Studio crea il progetto e diversi file, tra cui un form Windows vuoto denominato **Form1**.

2. Aggiungere due form Windows al progetto in modo da disporre di tre form e assegnare i nomi seguenti:

   - **Spostamento**

   - **NewCustomer**

   - **FillOrCancel**

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
Quando l'applicazione tenta di aprire una connessione al database, l'applicazione deve disporre dell'accesso alla stringa di connessione. Per evitare di immettere manualmente la stringa in ogni form, archiviare la stringa nel file *App.config* nel progetto e creare un metodo che restituisca la stringa quando il metodo viene chiamato da qualsiasi form nell'applicazione.

È possibile trovare la stringa di connessione facendo clic con il pulsante destro del mouse sulla connessione dati **Sales** in **Esplora server** e scegliendo **Proprietà**. Individuare la **proprietà ConnectionString,** quindi usare **CTRL** A , CTRL C per + selezionare  +  e copiare la stringa negli Appunti.

1. Se si usa C#, in **Esplora soluzioni** espandere  il nodo Proprietà nel progetto e quindi aprire il file **Impostazioni.settings.**
    Se si usa Visual Basic, in **Esplora soluzioni** fare clic su Mostra tutti i file **,** espandere il nodo **Project** e quindi aprire il file **Impostazioni.settings.**

2. Nella **colonna Nome** immettere `connString` .

3. **Nell'elenco Tipo** selezionare **(Stringa di connessione).**

4. **Nell'elenco** Ambito selezionare **Applicazione**.

5. Nella colonna **Valore** immettere la stringa di connessione (senza virgolette esterne) e quindi salvare le modifiche.

> [!NOTE]
> In un'applicazione reale è consigliabile archiviare la stringa di connessione in modo sicuro, come descritto in [Stringhe di connessione e file di configurazione.](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)

## <a name="write-the-code-for-the-forms"></a>Scrivere il codice per i form

Questa sezione contiene brevi panoramiche delle funzionalità di ogni modulo. Fornisce inoltre il codice che definisce la logica sottostante quando si fa clic su un pulsante nel form.

### <a name="navigation-form"></a>Form Navigazione

Quando si esegue l'applicazione, verrà visualizzato il form Navigazione. Il pulsante **Aggiungi un account** consente di aprire il form NewCustomer. Il pulsante **Completare o annullare gli ordini** consente di aprire il form FillOrCancel. Il pulsante **Esci** consente di chiudere l'applicazione.

#### <a name="make-the-navigation-form-the-startup-form"></a>Impostare il form Navigazione come form di avvio

Se si usa C#, in **Esplora soluzioni** aprire **Program.cs** e modificare la riga `Application.Run` nel seguente modo: `Application.Run(new Navigation());`

Se si usa Visual Basic, in **Esplora soluzioni** aprire la finestra  Proprietà, selezionare  la scheda Applicazione e quindi **selezionare SimpleDataApp.Navigation** nell'elenco Modulo di **avvio.**

#### <a name="create-auto-generated-event-handlers"></a>Creare gestori eventi generati automaticamente

Fare doppio clic sui tre pulsanti nel form di navigazione per creare metodi del gestore eventi vuoti. Facendo doppio clic sui pulsanti viene aggiunto anche il codice generato automaticamente nel file di codice della finestra di progettazione che consente di fare clic su un pulsante per generare un evento.

#### <a name="add-code-for-the-navigation-form-logic"></a>Aggiungere il codice per la logica del modulo di navigazione

Nella tabella codici per il form di navigazione completare i corpi dei metodi per i gestori dell'evento Click a tre pulsanti, come illustrato nel codice seguente.

:::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs" id="Snippet1":::
:::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb" id="Snippet1":::

### <a name="newcustomer-form"></a>Form NewCustomer

Quando si immette il nome  di un cliente e quindi si seleziona il pulsante Crea account, il modulo NewCustomer crea un account cliente e SQL Server restituisce un valore IDENTITY come nuovo ID cliente. È quindi possibile eseguire un ordine per il nuovo account specificando un importo e una data dell'ordine e selezionando il **pulsante Place Order (Ordina).**

#### <a name="create-auto-generated-event-handlers"></a>Creare gestori eventi generati automaticamente

Creare un gestore dell'evento Click vuoto per ogni pulsante nel form NewCustomer facendo doppio clic su ognuno dei quattro pulsanti. Facendo doppio clic sui pulsanti viene aggiunto anche il codice generato automaticamente nel file di codice della finestra di progettazione che consente di fare clic su un pulsante per generare un evento.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Aggiungere il codice per la logica del modulo NewCustomer

Per completare la logica del modulo NewCustomer, seguire questa procedura.

1. Portare lo spazio dei nomi nell'ambito in modo che non sia `System.Data.SqlClient` necessario qualificare completamente i nomi dei relativi membri.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Aggiungere alcune variabili e metodi helper alla classe come illustrato nel codice seguente.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet1":::

3. Completare i corpi dei metodi per i gestori dell'evento Click dei quattro pulsanti, come illustrato nel codice seguente.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet2":::

### <a name="fillorcancel-form"></a>Form FillOrCancel

Il modulo FillOrCancel esegue una query per restituire un ordine quando si immette un ID ordine e quindi si fa clic sul **pulsante Trova** ordine. La riga restituita viene visualizzata in una griglia di dati di sola lettura. È possibile contrassegnare l'ordine come annullato  (X) se si seleziona il pulsante Annulla ordine oppure contrassegnare l'ordine come compilato (F) se si seleziona il pulsante **Completa** ordine. Se si seleziona di **nuovo il pulsante Trova** ordine, viene visualizzata la riga aggiornata.

#### <a name="create-auto-generated-event-handlers"></a>Creare gestori eventi generati automaticamente

Creare gestori dell'evento Click vuoti per i quattro pulsanti nel form FillOrCancel facendo doppio clic sui pulsanti. Facendo doppio clic sui pulsanti viene aggiunto anche il codice generato automaticamente nel file di codice della finestra di progettazione che consente di fare clic su un pulsante per generare un evento.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Aggiungere il codice per la logica del modulo FillOrCancel

Per completare la logica del modulo FillOrCancel, seguire questa procedura.

1. Portare i due spazi dei nomi seguenti nell'ambito in modo che non sia necessario qualificare completamente i nomi dei relativi membri.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Aggiungere una variabile e un metodo helper alla classe come illustrato nel codice seguente.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet1":::

3. Completare i corpi dei metodi per i gestori dell'evento Click dei quattro pulsanti, come illustrato nel codice seguente.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet2":::

## <a name="test-your-application"></a>Testare l'applicazione

Premere il tasto **F5** per compilare e testare l'applicazione dopo aver inserito il codice in ogni gestore dell'evento Click e quindi dopo aver completato la scrittura del codice.

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
