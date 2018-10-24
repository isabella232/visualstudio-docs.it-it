---
title: 'Procedura dettagliata: Creazione di una Web Part Silverlight che visualizza il servizio OData per SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58f03bc18c2e851bb7732b54ff334e6e3332f74e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878185"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procedura dettagliata: Creare una web part Silverlight che visualizza il servizio OData per SharePoint
  SharePoint 2010 espongono i propri dati elenco tramite OData. In SharePoint, il servizio OData viene implementato dal servizio RESTful ListData.svc. Questa procedura dettagliata viene illustrato come creare una web part di SharePoint che ospita un'applicazione Silverlight. L'applicazione Silverlight consente di visualizzare informazioni relative all'elenco SharePoint annuncio usando ListData.svc. Per altre informazioni, vedere [interfaccia REST di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) e [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Creare un'applicazione Silverlight e web part Silverlight
 In primo luogo, creare un'applicazione Silverlight in Visual Studio. L'applicazione Silverlight recupera i dati nell'elenco di annunci di SharePoint usando il servizio ListData.svc.  
  
> [!NOTE]  
>  Nessuna versione di Silverlight precedenti alla 4.0 supportano le interfacce necessarie per fare riferimento a dati dell'elenco SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Per creare un'applicazione Silverlight e web part Silverlight
  
1. Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.  
  
2. Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3. Nel riquadro Modelli scegliere il **Web Part Silverlight di SharePoint 2010** modello.  
  
4. Nel **Name** casella, immettere **SLWebPartTest** e quindi scegliere il **OK** pulsante.  
  
    Il **Personalizzazione guidata SharePoint** verrà visualizzata la finestra di dialogo.  
  
5. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint server in cui si desidera eseguire il debug della definizione di sito o utilizzare il percorso predefinito (http://<em>il nome del sistema</em>/) .  
  
6. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione.  
  
    Sebbene questo esempio Usa una soluzione farm, i progetti web part di Silverlight possono essere distribuiti come farm o soluzioni create mediante sandbox. Per altre informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Nel **modo in cui si desidera associare la Web Part Silverlight** sezione del **specificare le informazioni di configurazione Silverlight** pagina, scegliere il **crea un nuovo progetto Silverlight e lo si associa la web part** pulsante di opzione.  
  
8. Modifica il **Name** a **SLApplication**, impostare **Language** a una delle due **Visual Basic** o **Visual c#**, e quindi impostare **la versione di Silverlight** al **Silverlight 4.0**.  
  
9. Scegliere il **fine** pulsante. I progetti vengono visualizzati nella **Esplora soluzioni**.  
  
     La soluzione contiene due progetti: un'applicazione Silverlight e una web part Silverlight. L'applicazione Silverlight recupera e visualizza i dati elenco da SharePoint e la web part Silverlight ospita l'applicazione Silverlight, consentendo di visualizzarla in SharePoint.  
  
## <a name="customize-the-silverlight-application"></a>Personalizzare l'applicazione Silverlight
 Aggiungere gli elementi di codice e progettazione per l'applicazione Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Per personalizzare l'applicazione Silverlight
  
1.  Aggiungere un riferimento all'assembly esegua nell'applicazione Silverlight. Per altre informazioni, vedere [procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  Nella **Esplora soluzioni**, aprire il menu di scelta rapida **riferimenti**, quindi scegliere **Aggiungi riferimento al servizio**.  
  
    > [!NOTE]  
    >  Se si usa Visual Basic, è necessario scegliere il **Mostra tutti i file** nella parte superiore del **Esplora soluzioni** per visualizzare il **riferimenti** nodo.  
  
3.  Nella casella dell'indirizzo del **Aggiungi riferimento al servizio** finestra di dialogo casella, immettere l'URL del sito di SharePoint, ad esempio **http://MySPSite**, quindi scegliere il **passare** pulsante.  
  
     Quando Silverlight individua il servizio SharePoint OData ListData.svc, l'indirizzo viene sostituito con l'URL completo del servizio. In questo esempio http://myserver diventa http://myserver/_vti_bin/ListData.svc.  
  
4.  Scegliere il **OK** pulsante per aggiungere il riferimento al servizio al progetto e usare il nome del servizio predefinito, ServiceReference1.  
  
5.  Nella barra dei menu scegliere **Compila** > **Compila soluzione**.  
  
6.  Aggiungere una nuova origine dati per il progetto basato sul servizio di SharePoint. A tale scopo, nella barra dei menu, scegliere **View** > **Other Windows** > **Zdroje dat**.  
  
     Il **Zdroje dat** finestra Mostra tutti i dati elenco SharePoint disponibili, ad esempio attività, annunci e calendario.  
  
7.  Aggiungere i dati dell'elenco di annunci all'applicazione Silverlight. È possibile trascinare "Annunci" dal **Zdroje dat** finestra nella finestra di progettazione di Silverlight.  
  
     Verrà creato un controllo griglia associato all'elenco di annunci del sito di SharePoint.  
  
8.  Ridimensionare il controllo griglia per adattarlo alla pagina Silverlight.  
  
9. Nel file di codice MainPage. XAML (*MainPage.xaml.cs* per Visual c# o *MainPage* per Visual Basic), aggiungere i riferimenti seguenti dello spazio dei nomi.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Aggiungere le dichiarazioni di variabili seguenti all'inizio della classe.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Sostituire il `UserControl_Loaded` procedure con il codice seguente.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Assicurarsi di sostituire il *ServerName* segnaposto con il nome del server che esegue SharePoint.  
  
12. Aggiungere la seguente procedura di gestione degli errori.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modify-the-silverlight-web-part"></a>Modificare la web part Silverlight
 Modificare una proprietà nel progetto Silverlight web part per abilitare il debug di Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Per modificare la web part Silverlight  
  
1.  Aprire il menu di scelta rapida per il progetto di web part Silverlight (**SLWebPartTest**), quindi scegliere **proprietà**.  
  
2.  Nel **delle proprietà** finestra, scegliere il **SharePoint** scheda.  
  
3.  Se non è già selezionata, selezionare la **debug abilitare Silverlight (anziché il debug degli Script)** casella di controllo.  
  
4.  Salvare il progetto.  
  
## <a name="test-the-silverlight-web-part"></a>Testare la web part Silverlight
 Testare la nuova web part di Silverlight in SharePoint per garantire che vengano visualizzati correttamente i dati elenco SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Per testare la web part Silverlight  
  
1.  Scegliere il **F5** chiave per compilare ed eseguire la soluzione di SharePoint.  
  
2.  In SharePoint, nelle **Azioni sito** menu, scegliere **nuova pagina**.  
  
3.  Nel **nuova pagina** finestra di dialogo immettere un titolo, ad esempio **SL Web Part Test**, quindi scegliere il **crea** pulsante.  
  
4.  Nella finestra di progettazione della pagina nel **strumenti di modifica** scheda, scegliere **Inserisci**.  
  
5.  Nella schede, scegliere **Web Part**.  
  
6.  Nel **categorie** scegliere i **Custom** cartella.  
  
7.  Nel **Web part** elenco, scegliere la web part Silverlight e quindi scegliere il **Add** pulsante per aggiungere la web part nella finestra di progettazione.  
  
8.  Dopo che tutte le aggiunte apportate alla pagina web desiderato, scegliere il **pagina** scheda e quindi scegliere il **Salva e Chiudi** pulsante sulla barra degli strumenti.  
  
     La web part Silverlight dovrebbe ora essere visualizzazione dei dati di annuncio al sito di SharePoint. Per impostazione predefinita, la pagina viene archiviata nell'insieme di pagine del sito in SharePoint.  
  
    > [!NOTE]  
    >  L'accesso ai dati in Silverlight nei domini, Silverlight protegge contro le vulnerabilità di sicurezza che possono essere utilizzate per sfruttare le applicazioni web. Se si verificano problemi durante l'accesso a dati remoti in Silverlight, vedere [rendendo un servizio disponibile attraverso i limiti del dominio](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Vedere anche
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Distribuire, pubblicare e aggiornare i pacchetti di soluzioni SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
