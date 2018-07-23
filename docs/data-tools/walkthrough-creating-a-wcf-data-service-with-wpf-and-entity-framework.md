---
title: 'Procedura dettagliata: Creazione di un servizio dati WCF con WPF ed Entity Framework'
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b796bf5b17460425d25ec91f3ecca7c147784039
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174984"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procedura dettagliata: Creazione di un servizio dati WCF con WPF ed Entity Framework
Questa procedura dettagliata viene illustrato come creare una semplice [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] che è ospitato in un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione Web e quindi accedervi da un'applicazione Windows Forms.

In questa procedura dettagliata è:

-   Creare un'applicazione Web per ospitare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Creare un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] che rappresenta il `Customers` tabella nel database Northwind.

-   Creare un oggetto [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Creare un'applicazione client e aggiungere un riferimento al servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Abilitazione del data binding al servizio e generazione dell'interfaccia utente.

-   Aggiunta facoltativa di funzionalità di filtraggio all'applicazione.

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (**Esplora oggetti di SQL Server** viene installato come parte delle **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="creating-the-service"></a>Creazione del servizio
Per creare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], è necessario aggiungere un progetto Web, creare un modello [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], quindi creare il servizio dal modello.

Nel primo passaggio, si aggiunge un progetto Web per ospitare il servizio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-the-web-project"></a>Per creare il progetto Web

1.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** oppure **Visual c#** e **Web** nodi e quindi scegliere il **ASP. Applicazione Web NET** modello.

3.  Nel **nome** testo immettere **NorthwindWeb**, quindi scegliere il **OK** pulsante.

4.  Nel **nuovo progetto ASP.NET** nella finestra di dialogo il **selezionare un modello** scegliere **vuoto**e quindi scegliere il **OK** pulsante.

Nel passaggio successivo, si crea un' [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] che rappresenta il `Customers` tabella nel database Northwind.

#### <a name="to-create-the-entity-data-model"></a>Per creare il modello Entity Data Model

1.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

2.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **Data** nodo e quindi scegliere il **ADO.NET Entity Data Model** elemento.

3.  Nel **nome** testo immettere `NorthwindModel`, quindi scegliere il **Aggiungi** pulsante.

     Verrà visualizzata la procedura guidata Entity Data Model.

4.  Nella procedura guidata Entity Data Model, nel **Scegli contenuto Model** pagina, scegliere il **Entity Framework Designer da database** elemento e quindi scegliere il **Avanti** pulsante.

5.  Nella pagina **Seleziona connessione dati** , eseguire una delle operazioni seguenti:

    -   Nell'elenco a discesa scegliere una connessione dati al database di esempio Northwind, se disponibile.

         oppure

    -   Scegliere il **nuova connessione** pulsante per configurare una nuova connessione dati. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

6.  Se il database richiede una password, scegliere il **Sì, è possibile includere dati sensibili nella stringa di connessione** pulsante di opzione e quindi scegliere il **successivo** pulsante.

    > [!NOTE]
    >  Se viene visualizzata una finestra di dialogo, scegliere **Sì** per salvare il file al progetto.

7.  Nel **scegliere la versione** pagina, scegliere il **Entity Framework 5.0** pulsante di opzione e quindi scegliere il **Avanti** pulsante.

    > [!NOTE]
    >  Per usare la versione più recente di Entity Framework 6 con i servizi WCF, è necessario installare il pacchetto NuGet del Provider di WCF Data Services Entity Framework. Visualizzare [uso di WCF Data Services 5.6.0 with Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo, seleziona il **clienti** casella di controllo e quindi scegliere il **fine** pulsante.

     Consente di visualizzare il diagramma del modello di entità e un *NorthwindModel* file viene aggiunto al progetto.

Nel passaggio successivo creare e testare il servizio dati.

#### <a name="to-create-the-data-service"></a>Per creare il servizio dati

1.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

2.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **Web** nodo e quindi scegliere il **WCF Data Service 5.6** elemento.

3.  Nel **nome** testo immettere `NorthwindCustomers`, quindi scegliere il **Aggiungi** pulsante.

     Il **NorthwindCustomers. svc** viene visualizzato nel file la **Editor di codice**.

4.  Nel **Editor di codice**, individuare il primo `TODO:` impostare come commento e sostituire il codice con quanto segue:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  Sostituire i commenti nel gestore eventi `InitializeService` con il codice seguente:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  Nella barra dei menu, scegliere **Debug** > **Avvia senza eseguire debug** per eseguire il servizio. Verrà visualizzata una finestra del browser e viene visualizzato il XML schema per il servizio.

7.  Nel **indirizzo** barra, immettere `Customers` alla fine dell'URL per **NorthwindCustomers. svc**, quindi scegliere il **invio** chiave.

     Una rappresentazione XML dei dati di `Customers` viene visualizzata la tabella.

    > [!NOTE]
    >  In alcuni casi, Internet Explorer interpreterà erroneamente i dati come feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata. Per altre informazioni, vedere [risoluzione dei riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

8.  Chiudere la finestra del browser.

Nei passaggi successivi, si crea un'applicazione client di Windows Form usare il servizio.

## <a name="creating-the-client-application"></a>Creazione dell'applicazione client
 Per creare l'applicazione client, aggiungere un secondo progetto, aggiungere un riferimento al progetto, configurare un'origine dati e creare un'interfaccia utente per visualizzare i dati dal servizio.

 Nel primo passaggio, aggiungere un progetto Windows Form alla soluzione e impostarlo come progetto di avvio.

#### <a name="to-create-the-client-application"></a>Per creare l'applicazione client

1.  Nella barra dei menu scegliere File, **Add** > **nuovo progetto**.

2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual Basic** o **Visual c#** nodo, scegliere il **Windows** nodo e quindi scegliere  **Windows Forms Application**.

3.  Nella casella di testo **Nome** immettere `NorthwindClient` e quindi scegliere il pulsante **OK**.

4.  Nelle **Esplora soluzioni**, scegliere il **NorthwindClient** nodo del progetto.

5.  Nella barra dei menu, scegliere **Project**, **imposta come progetto di avvio**.

Nel passaggio successivo, aggiungere un riferimento al servizio il [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] nel progetto Web.

#### <a name="to-add-a-service-reference"></a>Per aggiungere un riferimento al servizio

1.  Nella barra dei menu, scegliere **Project** > **Aggiungi riferimento al servizio**.

2.  Nel **Aggiungi riferimento al servizio** finestra di dialogo scegliere la **Discover** pulsante.

     L'URL per il servizio NorthwindCustomers verrà visualizzato il **indirizzo** campo.

3.  Scegliere il **OK** pulsante per aggiungere il riferimento al servizio.

Nel passaggio successivo, si configura un'origine dati per consentire il data binding al servizio.

#### <a name="to-enable-data-binding-to-the-service"></a>Per abilitare il data binding al servizio

1.  Nella barra dei menu, scegliere **View** > **Other Windows** > **Zdroje dat**.

2.  Nel **Zdroje dat** finestra, scegliere il **Aggiungi nuova origine dati** pulsante.

3.  Nel **scegliere un tipo di origine dati** pagina della **configurazione guidata origine dati**, scegliere **oggetto**e quindi scegliere il **Avanti** pulsante .

4.  Nel **selezionare gli oggetti dati** , espandere il **NorthwindClient** nodo, quindi espandere il **NorthwindClient.ServiceReference1** nodo.

5.  Selezionare **cliente** casella di controllo e quindi scegliere il **fine** pulsante.

Nel passaggio successivo è creare l'interfaccia utente che visualizza i dati dal servizio.

#### <a name="to-create-the-user-interface"></a>Per creare l'interfaccia utente

1.  Nel **Zdroje dat** finestra, aprire il menu di scelta rapida per il **clienti** nodo e scegliere **copia**.

2.  Nel **Form1.vb** oppure **Form1.cs** progettazione form, aprire il menu di scelta rapida e scegliere **Incolla**.

     Al form vengono aggiunti un controllo <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.

3.  Scegliere il **CustomersDataGridView** (controllo) e quindi nel **proprietà** finestra set il **Dock** proprietà **riempire**.

4.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **Form1** nodo e scegliere **Visualizza codice** per aprire l'Editor di codice e aggiungere il codice seguente `Imports` o`Using`all'inizio del file l'istruzione:

    ```vb
    Imports NorthwindClient.ServiceReference1
    ```

    ```csharp
    using NorthwindClient.ServiceReference1;
    ```

5.  Aggiungere il codice seguente al gestore eventi `Form1_Load`:

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

6.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NorthwindCustomers. svc** del file e scegliere **Visualizza nel Browser**. Verrà aperto Internet Explorer e viene visualizzato il XML schema per il servizio.

7.  Copiare l'URL dalla barra degli indirizzi di Internet Explorer.

8.  Nel codice aggiunto nel passaggio 4, selezionare `http://localhost:53161/NorthwindCustomers.svc/` e sostituirlo con l'URL appena copiato.

9. Nella barra dei menu, scegliere **Debug** > **Avvia debug** per eseguire l'applicazione. Vengono visualizzate le informazioni dei clienti.

 A questo punto si disporrà di un'applicazione nella quale sarà visualizzato un elenco di clienti del servizio NorthwindCustomers. Se si desidera esporre altri dati tramite il servizio, è possibile modificare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] per includere tabelle aggiuntive dal database Northwind.

Il prossimo passaggio facoltativo, descrive come filtrare i dati restituiti dal servizio.

## <a name="adding-filtering-capabilities"></a>Aggiunta di funzionalità di filtraggio
 In questo passaggio si personalizza l'applicazione per filtrare i dati in base alla città del cliente.

#### <a name="to-add-filtering-by-city"></a>Per aggiungere il filtraggio in base alla città

1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **Form1.vb** oppure **Form1.cs** nodo e scegliere **aprire**.

2.  Aggiungere un <xref:System.Windows.Forms.TextBox> controllo e una <xref:System.Windows.Forms.Button> controllare dalle **della casella degli strumenti** al form.

3.  Aprire il menu di scelta rapida per il <xref:System.Windows.Forms.Button> controllare, scegliere **Visualizza codice**, quindi aggiungere il codice seguente nel `Button1_Click` gestore dell'evento:

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

4.  Nel codice precedente, sostituire `http://localhost:53161/NorthwindCustomers.svc` con l'URL del gestore eventi `Form1_Load`.

5.  Nella barra dei menu, scegliere **Debug** > **Avvia debug** per eseguire l'applicazione.

6.  Nella casella di testo, immettere **Londra**e quindi scegliere il pulsante. Verranno visualizzati solo i clienti di Londra.

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio WCF Data Services](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)