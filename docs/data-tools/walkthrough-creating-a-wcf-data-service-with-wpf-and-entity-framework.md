---
title: Creare WCF Data Service con WPF & Entity Framework
description: Creare un servizio dati WCF con WPF e Entity Framework ospitato in un'applicazione Web ASP.NET e quindi accedervi da un'applicazione Windows Form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ca3912539d8c651fd65fbcd87c809597748654cc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631055"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procedura dettagliata: Creazione di un'istanza di WCF Data Services con WPF ed Entity Framework
Questa procedura dettagliata illustra come creare un semplice servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] incluso in un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e come accedervi da un'applicazione Windows Forms.

In questa procedura dettagliata:

- Creare un'applicazione Web per ospitare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Creare un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] oggetto che rappresenta la tabella nel database `Customers` Northwind.

- Creare un oggetto [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Creare un'applicazione client e aggiungere un riferimento al servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Abilitazione del data binding al servizio e generazione dell'interfaccia utente.

- Aggiunta facoltativa di funzionalità di filtraggio all'applicazione.

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** Nel **Programma di installazione di Visual Studio**, è possibile installare SQL Server Express Local DB come parte  del carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la **SQL Server Esplora oggetti** predefinita. (**SQL Server Esplora oggetti** viene installato come parte  del carico di lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo . Fare clic con il pulsante destro del mouse sull Local DB e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="creating-the-service"></a>Creazione del servizio
Per creare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] è necessario aggiungere un progetto Web, creare un modello [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], quindi creare il servizio dal modello.

Nel primo passaggio si aggiunge un progetto Web per ospitare il servizio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Per creare il progetto Web

1. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

2. Nella finestra di dialogo **Nuovo progetto** espandere i nodi **Visual Basic** o **Visual C#** e **Web**, quindi scegliere il modello **Applicazione Web ASP.NET**.

3. Nella casella di testo **Nome** immettere **NorthwindWeb**, quindi scegliere **OK**.

4. Nella finestra di dialogo **Nuovo progetto ASP.NET**, nell'elenco **Seleziona modello** scegliere **Vuoto** e quindi fare clic su **OK**.

Nel passaggio successivo si creerà un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] oggetto che rappresenta la tabella nel database `Customers` Northwind.

### <a name="to-create-the-entity-data-model"></a>Per creare il modello Entity Data Model

1. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Dati** e quindi scegliere la voce **ADO.NET Entity Data Model**.

3. Nella casella **di** testo Nome immettere `NorthwindModel` e quindi scegliere il **pulsante** Aggiungi.

     Verrà visualizzata la procedura guidata Entity Data Model.

4. Nella pagina **Scegli contenuto del modello** della procedura guidata Entity Data Model scegliere l'elemento **Entity Framework Designer da database**, quindi fare clic sul pulsante **Avanti**.

5. Nella pagina **Seleziona connessione dati** , eseguire una delle operazioni seguenti:

    - Nell'elenco a discesa scegliere una connessione dati al database di esempio Northwind, se disponibile.

         -oppure-

    - Scegliere il pulsante **Nuova connessione** per configurare una nuova connessione dati. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

6. Se il database richiede una password, scegliere il pulsante di opzione **Sì, includi i dati sensibili nella stringa di connessione**, quindi scegliere **Avanti**.

    > [!NOTE]
    > Se viene visualizzata una finestra di dialogo, scegliere **Sì** per salvare il file nel progetto.

7. Nella pagina **Scegli versione elemento** scegliere il pulsante di opzione **Entity Framework 5.0** e quindi fare clic su **Avanti**.

    > [!NOTE]
    > Per usare l'ultima versione di Entity Framework 6 con i servizi WCF è necessario installare il pacchetto NuGet WCF Data Services Entity Framework Provider. Vedere [Using WCF Data Services 5.6.0 with Entity Framework 6+ (Uso di WCF Data Services 5.6.0 con Entity Framework 6+](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Nella pagina **Seleziona oggetti di database** espandere il nodo **Tabelle**, selezionare la casella di controllo **Clienti**, quindi scegliere **Fine**.

     Viene visualizzato il diagramma del modello di entità e viene aggiunto un file *NorthwindModel.edmx* al progetto.

Nel passaggio successivo verrà creato e testato il servizio dati.

### <a name="to-create-the-data-service"></a>Per creare il servizio dati

1. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Web**, quindi scegliere la voce **WCF Data Service 5.6**.

3. Nella casella **di** testo Nome immettere `NorthwindCustomers` e quindi scegliere il **pulsante** Aggiungi.

     Il file **NorthwindCustomers.svc** verrà visualizzato nell'**editor di codice**.

4. Nell'**editor di codice** trovare il primo commento `TODO:` e sostituire il codice con il seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet1":::

5. Sostituire i commenti nel gestore eventi `InitializeService` con il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet2":::


6. Sulla barra dei menu scegliere **Debug**  >  **Avvia senza eseguire debug** per eseguire il servizio. Verrà visualizzata una finestra del browser con l'XML Schema per il servizio.

7. Nella barra **degli** indirizzi immettere alla fine dell'URL `Customers` per **NorthwindCustomers.svc** e quindi premere **INVIO.**

     Verrà visualizzata una rappresentazione XML dei dati `Customers` nella tabella.

    > [!NOTE]
    > In alcuni casi, Internet Explorer interpreterà erroneamente i dati come feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata. Per altre informazioni, vedere [Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

8. Chiudere la finestra del browser.

Nei passaggi successivi si creerà un'Windows client Forms per utilizzare il servizio.

## <a name="creating-the-client-application"></a>Creazione dell'applicazione client
Per creare l'applicazione client è necessario aggiungere un secondo progetto, aggiungere un riferimento al servizio per il progetto, configurare un'origine dati e creare un'interfaccia utente per visualizzare i dati del servizio.

Nel primo passaggio si aggiunge un progetto Windows Form alla soluzione e lo si imposta come progetto di avvio.

### <a name="to-create-the-client-application"></a>Per creare l'applicazione client

1. Nella barra dei menu scegliere File, **Aggiungi**  >  **nuovo Project**.

2. Nella finestra **di dialogo Project** nuovo nodo espandere il nodo **Visual Basic** o **Visual C#,** scegliere il nodo **Windows** e quindi scegliere **Windows'applicazione Form.**

3. Nella casella di testo **Nome** immettere `NorthwindClient` e quindi scegliere il pulsante **OK**.

4. In **Esplora soluzioni** scegliere il nodo del progetto **NorthwindClient**.

5. Nella barra dei menu scegliere **Progetto**, **Imposta come progetto di avvio**.

Nel passaggio successivo si aggiunge un riferimento al servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] a nel progetto Web.

### <a name="to-add-a-service-reference"></a>Per aggiungere un riferimento al servizio

1. Sulla barra dei menu scegliere **Project**  >  **Aggiungi riferimento al servizio**.

2. Nella finestra di dialogo **Aggiungi riferimento al servizio** scegliere il pulsante **Individua**.

     L'URL per il servizio NorthwindCustomers verrà visualizzato nel campo **Indirizzo**.

3. Scegliere **OK** per aggiungere il riferimento al servizio.

Nel passaggio successivo si configurerà un'origine dati per abilitare data binding al servizio.

### <a name="to-enable-data-binding-to-the-service"></a>Per abilitare il data binding al servizio

1. Sulla barra dei menu scegliere **Visualizza altre**  >  **origini Windows**  >  **dati**.

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** scegliere il pulsante **Aggiungi nuova origine dati**.

3. Nella pagina **Seleziona un tipo di origine dati** di **Configurazione guidata origine dati** scegliere **Oggetto** e quindi **Avanti**.

4. Nella pagina **Selezionare gli oggetti dati** espandere il nodo **NorthwindClient** e il nodo **NorthwindClient.ServiceReference1**.

5. Selezionare la casella di controllo **Customer**, quindi scegliere **Fine**.

Nel passaggio successivo verrà creata l'interfaccia utente che visualizza i dati del servizio.

### <a name="to-create-the-user-interface"></a>Per creare l'interfaccia utente

1. Nella finestra **Origini dati** aprire il menu di scelta rapida per il nodo **Customers** e scegliere **Copia**.

2. Nella finestra di progettazione form **Form1.vb** o **Form1.cs** aprire il menu di scelta rapida e scegliere **Incolla**.

    Al form vengono aggiunti un controllo <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.

3. Scegliere il controllo **CustomersDataGridView** e nella finestra **Proprietà** impostare la proprietà **Ancora** su **Riempimento**.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per  il nodo **Form1** e scegliere Visualizza codice per aprire l'editor di codice e aggiungere l'istruzione o seguente all'inizio `Imports` del `Using` file:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Aggiungere il codice seguente al gestore eventi `Form1_Load` :

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il file **NorthwindCustomers.svc** e scegliere **Visualizza nel browser**. Internet Explorer viene aperto e viene visualizzato lo schema XML per il servizio.

7. Copiare l'URL dalla barra degli indirizzi di Internet Explorer.

8. Nel codice aggiunto nel passaggio 4, selezionare `http://localhost:53161/NorthwindCustomers.svc/` e sostituirlo con l'URL appena copiato.

9. Sulla barra dei menu scegliere **Debug**  >  **Avvia debug** per eseguire l'applicazione. Vengono visualizzate le informazioni sul cliente.

   A questo punto si disporrà di un'applicazione nella quale sarà visualizzato un elenco di clienti del servizio NorthwindCustomers. Se si desidera esporre altri dati tramite il servizio, è possibile modificare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] per includere tabelle aggiuntive dal database Northwind.

Nel passaggio facoltativo successivo si apprenderà come filtrare i dati restituiti dal servizio.

## <a name="adding-filtering-capabilities"></a>Aggiunta di funzionalità di filtraggio
In questo passaggio si personalizza l'applicazione per filtrare i dati in base alla città del cliente.

### <a name="to-add-filtering-by-city"></a>Per aggiungere il filtraggio in base alla città

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Form1.vb** o **Form1.cs** e scegliere **Apri**.

2. Aggiungere al form un controllo <xref:System.Windows.Forms.TextBox> e un controllo <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti**.

3. Aprire il menu di scelta rapida <xref:System.Windows.Forms.Button> per il controllo, **scegliere Visualizza codice** e quindi aggiungere il codice seguente nel `Button1_Click` gestore eventi:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. Nel codice precedente, sostituire `http://localhost:53161/NorthwindCustomers.svc` con l'URL del gestore eventi `Form1_Load`.

5. Sulla barra dei menu scegliere **Debug**  >  **Avvia debug** per eseguire l'applicazione.

6. Nella casella di testo immettere **London**, quindi scegliere il pulsante. Verranno visualizzati solo i clienti di Londra.

## <a name="see-also"></a>Vedi anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
