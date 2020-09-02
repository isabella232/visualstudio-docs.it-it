---
title: Creazione di Web part Silverlight visualizzazione di OData per SharePoint
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75653f0357bcc605e666ee271a527b616985b641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017172"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procedura dettagliata: creare una Web part Silverlight che visualizza OData per SharePoint
  SharePoint 2010 espone i dati dell'elenco per mezzo di OData. In SharePoint il servizio OData viene implementato dal servizio RESTful ListData. svc. In questa procedura dettagliata viene illustrato come creare una Web part di SharePoint che ospita un'applicazione Silverlight. L'applicazione Silverlight Visualizza le informazioni sull'elenco degli annunci di SharePoint utilizzando ListData. svc. Per ulteriori informazioni, vedere [interfaccia REST di SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) e [Open Data Protocol](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Creare un'applicazione Silverlight e una Web part Silverlight
 Per prima cosa, creare un'applicazione Silverlight in Visual Studio. L'applicazione Silverlight recupera i dati dall'elenco degli annunci di SharePoint usando il servizio ListData. svc.

> [!NOTE]
> Nessuna versione di Silverlight precedente a 4,0 supporta le interfacce necessarie per fare riferimento ai dati degli elenchi di SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Per creare un'applicazione Silverlight e una Web part Silverlight

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** .

2. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Nel riquadro Modelli scegliere il modello di **Web part Silverlight per SharePoint 2010** .

4. Nella casella **nome** immettere **SLWebPartTest** , quindi scegliere il pulsante **OK** .

    Verrà visualizzata la finestra di dialogo **personalizzazione guidata SharePoint** .

5. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito del server SharePoint in cui si desidera eseguire il debug della definizione del sito oppure utilizzare il percorso predefinito (http://<em>System Name</em>/).

6. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm** .

    Sebbene in questo esempio venga utilizzata una soluzione farm, i progetti web part Silverlight possono essere distribuiti come soluzioni farm o in modalità sandbox. Per ulteriori informazioni sulle soluzioni create mediante sandbox e sulle soluzioni farm, vedere Considerazioni sulle soluzioni [create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7. Nella sezione stabilire **come si desidera associare la Web part Silverlight** della pagina specificare le **informazioni di configurazione Silverlight** scegliere il pulsante di opzione **Crea un nuovo progetto Silverlight e associalo al Web part** .

8. Modificare il **nome** in **SLApplication**, impostare la **lingua** su **Visual Basic** o **Visual C#**, quindi impostare la **versione di Silverlight** su **Silverlight 4,0**.

9. Fare clic sul pulsante **Fine**. I progetti vengono visualizzati in **Esplora soluzioni**.

     La soluzione contiene due progetti: un'applicazione Silverlight e una Web part Silverlight. L'applicazione Silverlight recupera e Visualizza i dati dell'elenco da SharePoint e la Web part Silverlight ospita l'applicazione Silverlight, consentendo di visualizzarla in SharePoint.

## <a name="customize-the-silverlight-application"></a>Personalizzare l'applicazione Silverlight
 Aggiungere elementi di codice e di progettazione all'applicazione Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Per personalizzare l'applicazione Silverlight

1. Aggiungere un riferimento ad assembly a System. Windows. Data nell'applicazione Silverlight. Per ulteriori informazioni, vedere [procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. In **Esplora soluzioni**aprire il menu di scelta rapida per **riferimenti**, quindi scegliere **Aggiungi riferimento al servizio**.

    > [!NOTE]
    > Se si usa Visual Basic, è necessario scegliere l'icona **Mostra tutti i file** nella parte superiore di **Esplora soluzioni** per visualizzare il nodo **riferimenti** .

3. Nella casella indirizzo della finestra di dialogo **Aggiungi riferimento al servizio** immettere l'URL del sito di SharePoint, ad esempio **http://MySPSite** , quindi scegliere il pulsante **Vai** .

     Quando Silverlight individua il servizio OData di SharePoint ListData. svc, sostituisce l'indirizzo con l'URL completo del servizio. Per questo esempio, http://myserver diventa http://myserver/_vti_bin/ListData.svc .

4. Scegliere il pulsante **OK** per aggiungere il riferimento al progetto e usare il nome del servizio predefinito, ServiceReference1.

5. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

6. Consente di aggiungere una nuova origine dati al progetto in base al servizio SharePoint. A tale scopo, sulla barra dei menu scegliere **Visualizza**  >  **altre**  >  **origini dati**di Windows.

     Nella finestra **origini dati** vengono visualizzati tutti i dati dell'elenco SharePoint disponibili, ad esempio attività, annunci e calendario.

7. Aggiungere i dati dell'elenco degli annunci all'applicazione Silverlight. È possibile trascinare "annunci" dalla finestra **origini dati** nella finestra di progettazione di Silverlight.

     Viene creato un controllo Grid associato all'elenco degli annunci del sito di SharePoint.

8. Ridimensionare il controllo griglia in modo che corrisponda alla pagina Silverlight.

9. Nel file di codice MainPage. XAML (*MainPage.XAML.cs* per Visual C# o *MainPage. XAML. vb* per Visual Basic) aggiungere i seguenti riferimenti allo spazio dei nomi.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Aggiungere le seguenti dichiarazioni di variabili all'inizio della classe.

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

11. Sostituire la `UserControl_Loaded` procedura con la seguente.

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

     Assicurarsi di sostituire il segnaposto *ServerName* con il nome del server in cui è in esecuzione SharePoint.

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

## <a name="modify-the-silverlight-web-part"></a>Modificare la Web part Silverlight
 Modificare una proprietà nel progetto Web part Silverlight per abilitare il debug di Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Per modificare la Web part Silverlight

1. Aprire il menu di scelta rapida per il progetto Web part Silverlight (**SLWebPartTest**), quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** scegliere la scheda **SharePoint** .

3. Se non è già selezionata, selezionare la casella di controllo **Abilita debug Silverlight (anziché eseguire il debug degli script)** .

4. Salvare il progetto.

## <a name="test-the-silverlight-web-part"></a>Testare la Web part Silverlight
 Testare la nuova Web part Silverlight in SharePoint per assicurarsi che visualizzi correttamente i dati dell'elenco di SharePoint.

#### <a name="to-test-the-silverlight-web-part"></a>Per eseguire il test della web part Silverlight

1. Premere il tasto **F5** per compilare ed eseguire la soluzione SharePoint.

2. In SharePoint scegliere **nuova pagina**dal menu **Azioni sito** .

3. Nella finestra di dialogo **nuova pagina** immettere un titolo, ad esempio **test Web part SL**, quindi scegliere il pulsante **Crea** .

4. Nella scheda **strumenti di modifica** della finestra di progettazione della pagina scegliere **Inserisci**.

5. Nel pannello scheda scegliere **Web part**.

6. Nella casella **categorie** scegliere la cartella **personalizzata** .

7. Nell'elenco **Web part** scegliere la Web part Silverlight, quindi scegliere il pulsante **Aggiungi** per aggiungere la Web part alla finestra di progettazione.

8. Dopo aver apportato tutte le aggiunte alla pagina Web desiderata, scegliere la scheda **pagina** , quindi scegliere il pulsante **Salva & Chiudi** sulla barra degli strumenti.

     La Web part Silverlight dovrebbe ora visualizzare i dati dell'annuncio dal sito di SharePoint. Per impostazione predefinita, la pagina viene archiviata nell'elenco pagine del sito in SharePoint.

    > [!NOTE]
    > Quando si accede ai dati in Silverlight tra domini, Silverlight protegge da vulnerabilità di sicurezza che possono essere usate per sfruttare le applicazioni Web. Se si verificano problemi durante l'accesso ai dati remoti in Silverlight, vedere [rendere disponibile un servizio tra i limiti di dominio](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Vedere anche
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
