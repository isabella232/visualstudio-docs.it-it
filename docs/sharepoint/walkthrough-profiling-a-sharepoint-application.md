---
title: "Procedura dettagliata: Profilatura di un'applicazione di SharePoint | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f22630a823e592e0cdc2128dfb3ab38e1b177d72
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867706"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Procedura dettagliata: Profilare un'applicazione SharePoint
  In questa procedura dettagliata viene illustrato come utilizzare gli strumenti di profilatura in Visual Studio per ottimizzare le prestazioni di un'applicazione SharePoint. L'applicazione di esempio è un ricevitore di eventi di funzionalità SharePoint contenente un ciclo inattivo che comporta una riduzione delle prestazioni del ricevitore di eventi di funzionalità. Il profiler di Visual Studio consente di individuare ed eliminare la parte più onerosa (esecuzione più lenta) del progetto, noto anche come il *percorso ad accesso frequente*.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- [Addg una funzionalità e un ricevitore di eventi funzionalità](#add-a-feature-and-feature-event-receiver).

- [Configurare e distribuire l'applicazione SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Eseguire l'applicazione SharePoint](#run-the-sharepoint-application).

- [Visualizzare e interpretare i risultati del profilo](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

-   Edizioni supportate di Microsoft Windows e SharePoint.

-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Creare un progetto SharePoint
 Creare innanzitutto un progetto SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Per creare un progetto SharePoint

1. Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.

2. Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.

3. Nel riquadro Modelli scegliere il **progetto SharePoint 2010** modello.

4. Nel **Name** casella, immettere **ProfileTest**e quindi scegliere il **OK** pulsante.

    Il **Personalizzazione guidata SharePoint** viene visualizzata.

5. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint server in cui si desidera eseguire il debug della definizione di sito o utilizzare il percorso predefinito (http://<em>il nome del sistema</em>/) .

6. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione.

    Attualmente, è possibile profilare solo soluzioni farm. Per altre informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7. Scegliere il **fine** pulsante. Il progetto viene visualizzato nella **Esplora soluzioni**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Aggiungere una funzionalità e un ricevitore di eventi
 Successivamente, aggiungere una funzionalità al progetto insieme a un ricevitore di eventi per la funzionalità. In questo ricevitore di eventi sarà incluso il codice da profilare.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Per aggiungere una funzionalità e un ricevitore di eventi di funzionalità

1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **funzionalità** nodo, scegliere **Aggiungi funzionalità**e lasciare il valore predefinito, il nome **Feature1**.

2.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida **Feature1**, quindi scegliere **Aggiungi ricevitore di eventi**.

     Verrà aggiunto un file di codice alla funzionalità con diversi gestori di eventi impostati come commenti e viene aperto il file da modificare.

3.  Nella classe del ricevitore di eventi aggiungere le seguenti dichiarazioni di variabili.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4.  Sostituire la procedura `FeatureActivated` con il codice seguente.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try
    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5.  Aggiungere la procedura seguente sotto il `FeatureActivated`procedure.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto (**ProfileTest**), quindi scegliere **proprietà**.

7.  Nel **delle proprietà** finestra di dialogo scegliere la **SharePoint** scheda.

8.  Nel **configurazione distribuzione attiva** casella di riepilogo **Nessuna attivazione**.

     Se si seleziona questa configurazione di distribuzione è possibile attivare manualmente la funzionalità in un secondo momento in SharePoint.

9. Salvare il progetto.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurare e distribuire l'applicazione SharePoint
 Una volta pronto il progetto SharePoint, è possibile configurarlo e distribuirlo nel server SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Per configurare e distribuire l'applicazione SharePoint

1.  Nel **Analyze** menu, scegliere **Avvia Creazione guidata sessione di prestazioni**.

2.  Nella prima pagina della **Creazione guidata sessione prestazioni**, lasciare il metodo di profilatura come **campionamento CPU** e scegliere il **Avanti** pulsante.

     Gli altri metodi di profilatura possono essere utilizzati in situazioni di profilatura più avanzate. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](/visualstudio/profiling/understanding-performance-collection-methods).

3.  Nella pagina del **Creazione guidata sessione prestazioni**, lasciare la destinazione del profilo come **ProfileTest** e scegliere il **Avanti** pulsante.

     Se in una soluzione sono disponibili più progetti, vengono visualizzati in questo elenco.

4.  Nella terza pagina della **Creazione guidata sessione prestazioni**, deselezionare il **Abilita profilatura interazione tra livelli** casella di controllo e quindi scegliere il **successivo** pulsante.

     La funzionalità di profilatura interazione tra livelli (TIP) è utile per misurare le prestazioni di applicazioni in cui vengono eseguite query sui database e per visualizzare il numero di volte in cui viene richiesta una pagina Web. Poiché i dati non sono necessari per questo esempio, la funzionalità non verrà abilitata.

5.  Nella quarta pagina del **Creazione guidata sessione prestazioni**, lasciare il **avvia profilatura al termine della procedura guidata** selezionata casella di controllo e quindi scegliere il **fine** pulsante.

     La procedura guidata abilita la profilatura dell'applicazione nel server, viene visualizzato il **Esplora prestazioni** finestra e quindi la compilazione, distribuzione e l'esecuzione dell'applicazione SharePoint.

## <a name="run-the-sharepoint-application"></a>Eseguire l'applicazione SharePoint
 Attivare la funzionalità in SharePoint, attivando il codice dell'evento `FeatureActivation` da eseguire.

### <a name="to-run-the-sharepoint-application"></a>Per eseguire l'applicazione SharePoint

1.  In SharePoint, aprire il **Azioni sito** menu, quindi scegliere **Impostazioni sito**.

2.  Nel **Azioni sito** scegliere i **Gestisci caratteristiche sito** collegamento.

3.  Nel **caratteristiche** scegliere il **Activate** accanto alla **ProfileTest Feature1**.

     Vi sarà una pausa quando verrà eseguita questa operazione, a causa del ciclo inattivo chiamato nella funzione `FeatureActivated`.

4.  Nel **avvio veloce** barra, scegliere **Elenca** e quindi il **Elenca** scegliere **annunci**.

     Si noti che un nuovo annuncio è stato aggiunto all'elenco per indicare che la funzionalità è stata attivata.

5.  Chiudere il sito di SharePoint.

     Dopo aver chiuso SharePoint, il profiler crea e visualizza un Report di profilatura di esempio e salvarlo come file con estensione vsp nel **ProfileTest** cartella del progetto.

## <a name="view-and-interpret-the-profile-results"></a>Visualizzare e interpretare i risultati del profilo
 Dopo aver eseguito e profilato l'applicazione SharePoint, visualizzare i risultati del test.

### <a name="to-view-and-interpret-the-profile-results"></a>Per visualizzare e interpretare i risultati del profilo

1.  Nel **funzioni che svolgono più lavoro individuale** sezione del Report di profilatura di esempio, si noti che `TimeCounter` nella parte superiore dell'elenco.

     Questa posizione indica che `TimeCounter` è una delle funzioni con il numero più elevato di campioni, pertanto è uno dei più grandi colli di bottiglia delle prestazioni nell'applicazione. Questa situazione non è insolita, tuttavia, dal momento che si tratta di una modalità progettata espressamente a scopo dimostrativo.

2.  Nel **funzioni che svolgono più lavoro individuale** keychains le `ProcessRequest` link per visualizzare la distribuzione dei costi per il `ProcessRequest` (funzione).

     Nel **le funzioni chiamate** sezione per `ProcessRequest`, si noti che il **FeatureActiviated** funzione viene elencata come la più costosa chiamata alla funzione.

3.  Nel **le funzioni chiamate** keychains le **FeatureActivated** pulsante.

     Nel **le funzioni chiamate** sezione per **FeatureActivated**, il `TimeCounter` funzione viene elencata come la più costosa chiamata alla funzione. Nel **visualizzazione codice funzione** riquadro, il codice evidenziato (`TimeCounter`) è l'area sensibile e indica dove è necessaria la correzione.

4.  Chiudere il Rapporto sulla profilatura dei campioni.

     Per visualizzare il report in qualsiasi momento, aprire il file con estensione vsp nel **Esplora prestazioni** finestra.

## <a name="fix-the-code-and-reprofile-the-application"></a>Correggere il codice e riprofilare l'applicazione
 Una volta identificata la funzione relativa all'area sensibile nell'applicazione SharePoint, correggerla.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Per correggere il codice e riprofilare l'applicazione

1.  Nel codice del ricevitore di eventi di funzionalità impostare come commento la chiamata al metodo `TimeCounter` in `FeatureActivated` per impedire che venga chiamato.

2.  Salvare il progetto.

3.  Nelle **Esplora prestazioni**, aprire la cartella destinazioni e quindi scegliere il **ProfileTest** nodo.

4.  Nel **Esplora prestazioni** sulla barra degli strumenti, nella **azioni** scheda, scegliere il **avvia profilatura** pulsante.

     Se si desidera modificare le proprietà di profilatura prima di riprofilare l'applicazione, scegliere il **Avvia Creazione guidata sessione di prestazioni** pulsante invece.

5.  Seguire le istruzioni di **esecuzione dell'applicazione SharePoint** sezione, in precedenza in questo argomento.

     L'attivazione della funzionalità dovrebbe essere molto più veloce una volta che è stata eliminata la chiamata al ciclo inattivo. Il Rapporto sulla profilatura dei campioni dovrebbe riflettere questa situazione.

## <a name="see-also"></a>Vedere anche
- [Esplora prestazioni](/visualstudio/profiling/performance-explorer)
- [Panoramica delle sessioni di prestazioni](/visualstudio/profiling/performance-session-overview)
- [Guida per principianti alla profilatura delle prestazioni](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Trovare i colli di bottiglia dell'applicazione con Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)
