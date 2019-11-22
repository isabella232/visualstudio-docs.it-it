---
title: 'Procedura dettagliata: creazione di un servizio dati WCF con WPF e Entity Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5abbb647f93c991d2de626a84e82f47e03f6f71e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299619"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procedura dettagliata: Creazione di un'istanza di WCF Data Services con WPF ed Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come creare un semplice [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] ospitato in un'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] e quindi accedervi da una Windows Forms Application.

 In questa procedura dettagliata vengono illustrate le seguenti operazioni:

- Creare un'applicazione Web per ospitare un servizio [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Creazione di un modello [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] che rappresenta la tabella Customers nel database Northwind.

- Creare un oggetto [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Creare un'applicazione client e aggiungere un riferimento al servizio [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Abilitazione del data binding al servizio e generazione dell'interfaccia utente.

- Aggiunta facoltativa di funzionalità di filtraggio all'applicazione.

## <a name="prerequisites"></a>Prerequisites
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Il database di esempio Northwind.

     Se questo database non è presente nel computer di sviluppo, è possibile scaricarlo dall' [Area download Microsoft](https://go.microsoft.com/fwlink/?LinkID=98088). Per istruzioni, vedere [download di database di esempio](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).

## <a name="creating-the-service"></a>Creazione del servizio
 Per creare un servizio [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], è necessario aggiungere un progetto Web, creare un modello [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], quindi creare il servizio dal modello.

 Nel primo passaggio, verrà aggiunto un progetto Web in cui includere il servizio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-the-web-project"></a>Per creare il progetto Web

1. Sulla barra dei menu scegliere **file**, **nuovo**, **progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere i nodi **Visual Basic** o **Visual C#** e **Web**, quindi scegliere il modello **Applicazione Web ASP.NET**.

3. Nella casella di testo **Nome** immettere **NorthwindWeb**, quindi scegliere **OK**.

4. Nella finestra di dialogo **Nuovo progetto ASP.NET**, nell'elenco **Seleziona modello** scegliere **Vuoto** e quindi fare clic su **OK**.

   In questo passaggio, verrà creato un modello [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] che rappresenta la tabella Customers nel database Northwind.

#### <a name="to-create-the-entity-data-model"></a>Per creare il modello Entity Data Model

1. Nella barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Dati** e quindi scegliere la voce **ADO.NET Entity Data Model**.

3. Nella casella di testo **nome** immettere `NorthwindModel`, quindi scegliere il pulsante **Aggiungi** .

    Verrà visualizzata la procedura guidata Entity Data Model.

4. Nella pagina **Scegli contenuto del modello** della procedura guidata Entity Data Model scegliere l'elemento **Entity Framework Designer da database**, quindi fare clic sul pulsante **Avanti**.

5. Nella pagina **Seleziona connessione dati**, eseguire una delle operazioni seguenti:

   - Nell'elenco a discesa scegliere una connessione dati al database di esempio Northwind, se disponibile.

        oppure

   - Scegliere il pulsante **Nuova connessione** per configurare una nuova connessione dati. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

6. Se il database richiede una password, scegliere il pulsante di opzione **Sì, includi i dati sensibili nella stringa di connessione**, quindi scegliere **Avanti**.

   > [!NOTE]
   > Se viene visualizzata una finestra di dialogo, scegliere **Sì** per salvare il file nel progetto.

7. Nella pagina **Scegli versione elemento** scegliere il pulsante di opzione **Entity Framework 5.0** e quindi fare clic su **Avanti**.

   > [!NOTE]
   > Per usare l'ultima versione di Entity Framework 6 con i servizi WCF, sarà necessario installare il pacchetto NuGet WCF Data Services Entity Framework Provider. Vedere [uso di WCF Data Services 5.6.0 con Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Nella pagina **Seleziona oggetti di database** espandere il nodo **Tabelle**, selezionare la casella di controllo **Clienti**, quindi scegliere **Fine**.

    Viene visualizzato il diagramma del modello di entità e viene aggiunto un file NorthwindModel.edmx al progetto.

   In questo passaggio, verrà creato e verificato il servizio dati.

#### <a name="to-create-the-data-service"></a>Per creare il servizio dati

1. Nella barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Web**, quindi scegliere la voce **WCF Data Service 5.6**.

3. Nella casella di testo **nome** immettere `NorthwindCustomers`, quindi scegliere il pulsante **Aggiungi** .

    Il file NorthwindCustomers.svc verrà visualizzato nell'**editor di codice**.

4. Nell'**editor di codice** trovare il primo commento `TODO:` e sostituire il codice con il seguente:

    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]

5. Sostituire i commenti nel gestore eventi `InitializeService` con il codice seguente:

    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]

6. Per eseguire il servizio, nella barra dei menu scegliere **Debug**, **Avvia senza eseguire debug**. Verrà aperta una finestra del browser nella quale sarà visualizzato l'XML Schema per il servizio.

7. Nella barra degli **indirizzi** immettere `Customers` alla fine dell'URL per NorthwindCustomers. svc, quindi premere il tasto **invio** .

    Verrà visualizzata una rappresentazione XML dei dati della tabella Customers.

   > [!NOTE]
   > In alcuni casi, Internet Explorer interpreterà erroneamente i dati come feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata. Per altre informazioni, vedere [Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md).

8. Chiudere la finestra del browser.

   Nei passaggi successivi, verrà creata un'applicazione client Windows Form che consente di usare il servizio.

## <a name="creating-the-client-application"></a>Creazione dell'applicazione client
 Per creare l'applicazione client, sarà necessario aggiungere un secondo progetto, aggiungere un riferimento al servizio per il progetto, configurare un'origine dati e creare un'interfaccia utente per visualizzare i dati del servizio.

 Nel primo passaggio, alla soluzione verrà aggiunto un progetto Windows Form che sarà impostato come progetto di avvio.

#### <a name="to-create-the-client-application"></a>Per creare l'applicazione client

1. Nella barra dei menu scegliere File, **Aggiungi**, **Nuovo progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** e il nodo **Windows**, quindi scegliere **Applicazione Windows Form**.

3. Nella casella di testo **Nome** immettere `NorthwindClient` e quindi scegliere il pulsante **OK**.

4. In **Esplora soluzioni** scegliere il nodo del progetto **NorthwindClient**.

5. Nella barra dei menu scegliere **Progetto**, **Imposta come progetto di avvio**.

   In questo passaggio, verrà aggiunto un riferimento al servizio [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] nel progetto Web.

#### <a name="to-add-a-service-reference"></a>Per aggiungere un riferimento al servizio

1. Nella barra dei menu scegliere **Progetto**, **Aggiungi riferimento al servizio**.

2. Nella finestra di dialogo **Aggiungi riferimento al servizio** scegliere il pulsante **Individua**.

    L'URL per il servizio NorthwindCustomers verrà visualizzato nel campo **Indirizzo**.

3. Scegliere **OK** per aggiungere il riferimento al servizio.

   In questo passaggio, verrà configurata un'origine dati per consentire il data binding al servizio.

#### <a name="to-enable-data-binding-to-the-service"></a>Per abilitare il data binding al servizio

1. Nella barra dei menu scegliere **Visualizza**, **Altre finestre**, **Origini dati**.

2. Nella finestra **Origini dati** scegliere il pulsante **Aggiungi nuova origine dati**.

3. Nella pagina **Seleziona un tipo di origine dati** di **Configurazione guidata origine dati** scegliere **Oggetto** e quindi **Avanti**.

4. Nella pagina **Selezionare gli oggetti dati** espandere il nodo **NorthwindClient** e il nodo **NorthwindClient.ServiceReference1**.

5. Selezionare la casella di controllo **Customer**, quindi scegliere **Fine**.

   In questo passaggio, verrà creata l'interfaccia utente che consente di visualizzare i dati del servizio.

#### <a name="to-create-the-user-interface"></a>Per creare l'interfaccia utente

1. Nella finestra **Origini dati** aprire il menu di scelta rapida per il nodo **Customers** e scegliere **Copia**.

2. Nella finestra di progettazione form **Form1.vb** o **Form1.cs** aprire il menu di scelta rapida e scegliere **Incolla**.

    Al form vengono aggiunti un controllo <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.

3. Scegliere il controllo **CustomersDataGridView** e nella finestra **Proprietà** impostare la proprietà **Ancora** su **Riempimento**.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Form1** e scegliere **Visualizza codice** per aprire l'editor di codice, quindi aggiungere la seguente istruzione imports o using all'inizio del file:

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

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il file NorthwindCustomers.svc e scegliere **Visualizza nel browser**. Verrà aperto Internet Explorer e verrà visualizzato l'XML Schema per il servizio.

7. Copiare l'URL dalla barra degli indirizzi di Internet Explorer.

8. Nel codice aggiunto nel passaggio 4, selezionare `http://localhost:53161/NorthwindCustomers.svc/` e sostituirlo con l'URL appena copiato.

9. Nella barra dei menu scegliere **Debug**, **Avvia debug** per eseguire l'applicazione. Verranno visualizzate le informazioni sul cliente.

   A questo punto si disporrà di un'applicazione nella quale sarà visualizzato un elenco di clienti del servizio NorthwindCustomers. Se si desidera esporre altri dati tramite il servizio, è possibile modificare [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] per includere tabelle aggiuntive dal database Northwind.

   Nel prossimo passaggio facoltativo, verrà illustrato come filtrare i dati restituiti dal servizio.

## <a name="adding-filtering-capabilities"></a>Aggiunta di funzionalità di filtraggio
 In questo passaggio, verrà personalizzata l'applicazione per filtrare i dati in base alla città del cliente.

#### <a name="to-add-filtering-by-city"></a>Per aggiungere il filtraggio in base alla città

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Form1.vb** o **Form1.cs** e scegliere **Apri**.

2. Aggiungere al form un controllo <xref:System.Windows.Forms.TextBox> e un controllo <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti**.

3. Aprire il menu di scelta rapida per il controllo <xref:System.Windows.Forms.Button> e scegliere **Visualizza codice**, quindi aggiungere il seguente codice nel gestore eventi `Button1_Click`:

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

5. Nella barra dei menu scegliere **Debug**, **Avvia debug** per eseguire l'applicazione.

6. Nella casella di testo immettere **London**, quindi scegliere il pulsante. Verranno visualizzati solo i clienti di Londra.

## <a name="see-also"></a>Vedere anche
 [Windows Communication Foundation di servizi e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
