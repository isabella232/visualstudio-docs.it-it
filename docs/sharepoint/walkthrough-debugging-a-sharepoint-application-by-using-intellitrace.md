---
title: "Procedura dettagliata: Debug di un'applicazione SharePoint tramite IntelliTrace | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad0d12560b1da99beadf2e519d2e430e8d76a45f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875368"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Procedura dettagliata: Eseguire il debug di un'applicazione SharePoint tramite IntelliTrace

Con IntelliTrace, è più facilmente possibile eseguire il debug di soluzioni di SharePoint. I debugger tradizionali offrono solo uno snapshot di una soluzione nel momento attuale. Tuttavia, è possibile utilizzare IntelliTrace per esaminare eventi passati che si sono verificati all'interno della soluzione e il contesto in cui si è verificato e passare al codice.

 Questa procedura dettagliata illustra come eseguire il debug di un progetto SharePoint 2010 o SharePoint 2013 in Visual Studio usando Microsoft Monitoring Agent per raccogliere dati IntelliTrace dalle applicazioni distribuite. Per analizzare i dati, è necessario usare Visual Studio Enterprise. Questo progetto include un ricevitore di funzionalità che, quando questa caratteristica è attivata, aggiunge un'attività all'elenco di attività e un annuncio all'elenco degli annunci. Quando questa caratteristica è disattivata, l'attività viene contrassegnata come completata e un annuncio secondo viene aggiunto all'elenco degli annunci. Tuttavia, la procedura contiene un errore di logico che impedisce che il progetto in esecuzione correttamente. Con IntelliTrace, si sarà individuare e correggere l'errore.

 **Si applica a:** Le informazioni contenute in questo argomento si applicano alle soluzioni SharePoint 2010 e SharePoint 2013 sono state create in Visual Studio.

 Questa procedura dettagliata illustra le attività seguenti:

- [Creare un ricevitore di funzionalità](#BKMK_CreateReceiver)

- [Aggiungere codice al ricevitore di funzionalità](#BKMK_AddCode)

- [Il progetto di test](#BKMK_Test1)

- [Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Eseguire il debug e correggere la soluzione di SharePoint](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Creare un ricevitore di funzionalità

In primo luogo, si crea un progetto SharePoint vuoto che presenta un ricevitore di funzionalità.

1. Creare un progetto di soluzione SharePoint 2010 o SharePoint 2013 e denominarlo **IntelliTraceTest**.

     Il **Personalizzazione guidata SharePoint** viene visualizzata, in cui è possibile specificare sia il sito di SharePoint per il progetto e il livello di attendibilità della soluzione.

2. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante.

     IntelliTrace funziona solo in soluzioni farm.

3. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **funzionalità** nodo, quindi scegliere **Aggiungi funzionalità**.

     *Feature1* viene visualizzata.

4. Aprire il menu di scelta rapida per Feature1 e quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un modulo di codice alla funzionalità.

## <a name="add-code-to-the-feature-receiver"></a>Aggiungere codice al ricevitore di funzionalità

Successivamente, aggiungere codice a due metodi nel ricevitore di funzionalità: `FeatureActivated` e `FeatureDeactivating`. Questi metodi attivano ogni volta che una funzionalità è attivata o disattivata in SharePoint, rispettivamente.

1. Nella finestra di `Feature1EventReceiver` classe, aggiungere il codice seguente, che dichiara variabili che specificano il sito di SharePoint e il sito secondario:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Sostituire il metodo `FeatureActivated` con il codice seguente:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
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
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Sostituire il metodo `FeatureDeactivating` con il codice seguente:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Il progetto di test

Ora che il codice viene aggiunto al ricevitore di funzionalità e l'agente di raccolta dati è in esecuzione, distribuire ed eseguire la soluzione di SharePoint per verificare se funziona correttamente.

> [!IMPORTANT]
> Per questo esempio, viene generato un errore nel gestore eventi FeatureDeactivating. Più avanti in questa procedura dettagliata individuare l'errore usando il file. iTrace che ha creato l'agente di raccolta dati.

1. Distribuire la soluzione in SharePoint e quindi aprire il sito di SharePoint in un browser.

     La funzionalità viene attivata automaticamente, causando il ricevitore di funzionalità aggiungere un'attività e un annuncio.

2. Visualizzare il contenuto degli elenchi di attività e gli annunci.

     L'elenco di annunci deve avere un nuovo annuncio denominato **funzionalità attivata: IntelliTraceTest_Feature1**, e l'elenco attività deve avere una nuova attività denominata **Disattiva funzionalità: IntelliTraceTest_Feature1**. Se uno di questi elementi è mancante, verificare se la funzionalità è attivata. Se non è attivato, attivarlo.

3. Disattivare la funzionalità attenendosi alla procedura seguente:

   1. Nel **Azioni sito** dal menu in SharePoint, scegliere **Impostazioni sito**.

   2. Sotto **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

   3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

   4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

      Il gestore dell'evento FeatureDeactivating() genera un errore.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent

Se si installa Microsoft Monitoring Agent nel sistema che esegue SharePoint, è possibile eseguire il debug di soluzioni di SharePoint utilizzando i dati più specifico rispetto alle informazioni generiche che IntelliTrace restituisce. L'agente funziona all'esterno di Visual Studio usando i cmdlet di PowerShell per acquisire le informazioni di debug durante l'esecuzione di soluzioni di SharePoint.

> [!NOTE]
> Le informazioni di configurazione in questa sezione sono specifiche per questo esempio. Per altre informazioni sulle altre opzioni di configurazione, vedere [usando l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Nel computer che esegue SharePoint, [configurare Microsoft Monitoring Agent e iniziare a monitorare la tua soluzione](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Disattivare la funzionalità:

   1. Nel **Azioni sito** dal menu in SharePoint, scegliere **Impostazioni sito**.

   2. Sotto **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

   3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

   4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

      Si verifica un errore (in questo caso, a causa dell'errore generata nel gestore dell'evento FeatureDeactivating()).

3. Nella finestra di PowerShell, eseguire la [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) comando per creare il file. iTrace, arrestare il monitoraggio e riavviare la soluzione di SharePoint.

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>Eseguire il debug e correggere la soluzione di SharePoint

A questo punto è possibile visualizzare il file di log di IntelliTrace in Visual Studio per trovare e correggere l'errore nella soluzione di SharePoint.

1. Nella cartella \IntelliTraceLogs, aprire il file. iTrace in Visual Studio.

     Il **riepilogo di IntelliTrace** verrà visualizzata la pagina. Poiché l'errore non è stato gestito, un ID di correlazione (GUID) di SharePoint viene visualizzato nell'area di un'eccezione non gestita del **analisi** sezione. Scegliere il **Stack di chiamate** pulsante se si desidera visualizzare lo stack di chiamate in cui si è verificato l'errore.

2. Scegliere il **Debug eccezione** pulsante.

     Se richiesto, caricare i file di simboli. Nel **IntelliTrace** finestra, l'eccezione è evidenziato come "generata: Si è verificato un errore grave! ".

     Nella finestra di IntelliTrace, scegliere l'eccezione per visualizzare il codice che non è riuscita.

3. Correggere l'errore di apertura della soluzione SharePoint e quindi impostare come commento o rimuovendo le **throw** all'inizio della procedura FeatureDeactivating() l'istruzione.

4. Ricompilare la soluzione in Visual Studio e quindi ridistribuirla in SharePoint.

5. Disattivare la funzionalità attenendosi alla procedura seguente:

    1. Nel **Azioni sito** dal menu in SharePoint, scegliere **Impostazioni sito**.

    2. Sotto **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

    3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

    4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

6. Aprire l'elenco di attività e verificare che il **lo stato** valore dell'attività di disattivazione è "completato" e la relativa **% completato** valore è 100%.

     Il codice ora viene eseguito correttamente.

## <a name="see-also"></a>Vedere anche

- [Verificare ed eseguire il debug del codice di SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Procedura dettagliata: Verificare SharePoint codice tramite Unit test](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))