---
title: Creare una web part Silverlight che visualizza OData per SharePoint
titleSuffix: ''
description: Creare una web part Silverlight che visualizza OData per SharePoint. Personalizzare l'applicazione Silverlight e modificare e testare la web part Silverlight.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 03c4089706d15178425c193f9dcabd4a592db2b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711406"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procedura dettagliata: Creare una web part Silverlight che visualizza OData per SharePoint
  SharePoint 2010 espone i dati dell'elenco tramite OData. In SharePoint, il servizio OData viene implementato dal servizio RESTful ListData.svc. Questa procedura dettagliata illustra come creare una SharePoint web part che ospita un'applicazione Silverlight. L'applicazione Silverlight visualizza SharePoint elenco annunci usando ListData.svc. Per altre informazioni, vedere [interfaccia REST SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) e [Open Data Protocol](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Creare un'applicazione Silverlight e una web part Silverlight
 Creare prima di tutto un'applicazione Silverlight in Visual Studio. L'applicazione Silverlight recupera i dati dall SharePoint di annunci usando il servizio ListData.svc.

> [!NOTE]
> Nessuna versione di Silverlight precedente alla 4.0 supporta le interfacce necessarie per fare riferimento SharePoint dati elenco.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Per creare un'applicazione Silverlight e una web part Silverlight

1. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project** per visualizzare la finestra **di dialogo Project** nuova cartella.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel riquadro dei modelli scegliere il **modello SharePoint Web part Silverlight 2010.**

4. Nella casella **Nome** immettere **SLWebPartTest** e quindi scegliere **il pulsante OK.**

    Verrà **visualizzata SharePoint finestra di dialogo** Personalizzazione guidata funzionalità.

5. Nella  pagina Specificare il sito e il livello di sicurezza per il debug immettere l'URL per il sito del server SharePoint in cui si vuole eseguire il debug della definizione del sito o usare il percorso predefinito (http:// nome di sistema<em>/).</em>

6. Nella sezione **Qual è il livello di attendibilità** per SharePoint soluzione? scegliere il pulsante **di** opzione Distribuisci come soluzione farm.

    Anche se questo esempio usa una soluzione farm, i progetti web part Silverlight possono essere distribuiti come soluzioni farm o sandbox. Per altre informazioni sulle soluzioni in modalità sandbox e sulle soluzioni farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. Nella sezione **Come associare** la web part Silverlight della pagina Impostazione informazioni di configurazione **silverlight** scegliere il pulsante di opzione Crea un nuovo progetto Silverlight e associarlo alla **web part.**

8. Modificare il **nome** in **SLApplication,** impostare **Language** su **Visual Basic** o **Visual C#** e quindi impostare **Versione silverlight** su **Silverlight 4.0.**

9. Fare clic sul pulsante **Fine**. I progetti vengono visualizzati in **Esplora soluzioni**.

     La soluzione contiene due progetti: un'applicazione Silverlight e una web part Silverlight. L'applicazione Silverlight recupera e visualizza i dati dell'elenco da SharePoint e la web part Silverlight ospita l'applicazione Silverlight, consentendo di visualizzarli in SharePoint.

## <a name="customize-the-silverlight-application"></a>Personalizzare l'applicazione Silverlight
 Aggiungere codice ed elementi di progettazione all'applicazione Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Per personalizzare l'applicazione Silverlight

1. Aggiungere un riferimento all'assembly a System. Windows. Dati nell'applicazione Silverlight. Per altre informazioni, vedere [Procedura: Aggiungere o rimuovere riferimenti tramite](/previous-versions/wkze6zky(v=vs.140))la finestra di dialogo Aggiungi riferimento .

2. In **Esplora soluzioni** aprire il menu di scelta rapida per **Riferimenti**, quindi scegliere **Aggiungi riferimento al servizio**.

    > [!NOTE]
    > Se si usa Visual Basic, è necessario  scegliere l'icona Mostra tutti i file nella parte superiore Esplora soluzioni **per** visualizzare il **nodo** Riferimenti.

3. Nella casella Indirizzo della finestra **di Aggiungi riferimento al servizio** immettere l'URL del sito SharePoint, ad esempio , quindi scegliere il **http://MySPSite** pulsante **Vai.**

     Quando Silverlight individua il SharePoint servizio OData ListData.svc, sostituisce l'indirizzo con l'URL completo del servizio. Per questo esempio, http://myserver diventa http://myserver/_vti_bin/ListData.svc .

4. Scegliere il **pulsante OK** per aggiungere il riferimento al servizio al progetto e usare il nome del servizio predefinito ServiceReference1.

5. Nella barra dei menu scegliere **Compila**  >  **compila soluzione.**

6. Aggiungere una nuova origine dati al progetto in base al SharePoint servizio. A tale scopo, sulla barra dei menu **scegliere**  >  **Visualizza altre Windows**  >  **dati**.

     La **finestra Origini** dati mostra tutti i dati dell SharePoint disponibili, ad esempio Attività, Annunci e Calendario.

7. Aggiungere i dati dell'elenco Annunci all'applicazione Silverlight. È possibile trascinare "Annunci" dalla **finestra Origini dati** alla finestra di progettazione Silverlight.

     Verrà creato un controllo griglia associato all'SharePoint annunci del sito.

8. Ridimensionare il controllo griglia per adattarlo alla pagina di Silverlight.

9. Nel file di codice MainPage.xaml (*MainPage.xaml.cs* per Visual C# o *MainPage.xaml.vb* per Visual Basic), aggiungere i riferimenti agli spazi dei nomi seguenti.

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

10. Aggiungere le dichiarazioni di variabili seguenti all'inizio della classe .

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

11. Sostituire la `UserControl_Loaded` procedura con quanto segue.

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

     Assicurarsi di sostituire il *segnaposto ServerName* con il nome del server che esegue SharePoint.

12. Aggiungere la procedura di gestione degli errori seguente.

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
 Modificare una proprietà nel progetto web part Silverlight per abilitare il debug di Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Per modificare la web part Silverlight

1. Aprire il menu di scelta rapida per il progetto web part Silverlight (**SLWebPartTest**) e quindi scegliere **Proprietà.**

2. Nella finestra **Proprietà** scegliere la scheda **SharePoint** proprietà.

3. Se non è già selezionata, selezionare la casella di controllo **Abilita debug Silverlight anziché Debug** script.

4. Salvare il progetto.

## <a name="test-the-silverlight-web-part"></a>Testare la web part Silverlight
 Testare la nuova web part Silverlight in SharePoint per assicurarsi che visualizzi correttamente i SharePoint dell'elenco.

#### <a name="to-test-the-silverlight-web-part"></a>Per testare la web part Silverlight

1. Premere **F5 per** compilare ed eseguire la SharePoint soluzione.

2. In SharePoint scegliere Nuova pagina dal menu **Azioni** **sito**.

3. Nella finestra **di dialogo Nuova** pagina immettere un titolo, ad esempio Sl Web Part **Test**, quindi scegliere il **pulsante** Crea.

4. Nella finestra di progettazione della pagina scegliere Inserisci nella scheda **Strumenti** **di modifica.**

5. Nell'elenco schede scegliere **Web part.**

6. Nella **casella Categorie** scegliere la **cartella** Personalizzato.

7. **Nell'Web part,** scegliere la web part Silverlight e quindi  scegliere il pulsante Aggiungi per aggiungere la web part alla finestra di progettazione.

8. Dopo aver apportato tutte le aggiunte alla pagina Web  desiderata, scegliere la scheda Pagina e quindi scegliere il pulsante **Salva** & Chiudi sulla barra degli strumenti.

     La web part Silverlight dovrebbe ora visualizzare i dati dell'annuncio SharePoint sito. Per impostazione predefinita, la pagina viene archiviata nell'elenco Pagine del sito in SharePoint.

    > [!NOTE]
    > Quando si accede ai dati in Silverlight tra domini, Silverlight protegge dalle vulnerabilità di sicurezza che possono essere usate per sfruttare le applicazioni Web. Se si verificano problemi durante l'accesso ai dati remoti in Silverlight, vedere [Making a Service Available Across Domain Boundaries](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Vedi anche
- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Distribuire, pubblicare e aggiornare i pacchetti SharePoint soluzione](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)