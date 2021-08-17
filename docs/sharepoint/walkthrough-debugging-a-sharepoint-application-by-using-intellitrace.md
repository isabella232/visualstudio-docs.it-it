---
title: Eseguire il SharePoint'applicazione con IntelliTrace
description: Usare IntelliTrace per eseguire più facilmente il debug e correggere SharePoint applicazioni. Creare e aggiungere codice a un ricevitore di funzionalità. Testare il progetto. Raccogliere dati IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 60a177fec8edf3b2e201eaff63ee0ff0ed4c8d72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123242"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Procedura dettagliata: Eseguire il debug SharePoint'applicazione usando IntelliTrace

Con IntelliTrace è possibile eseguire più facilmente il debug SharePoint soluzioni. I debugger tradizionali offrono solo uno snapshot di una soluzione al momento. È tuttavia possibile usare IntelliTrace per esaminare gli eventi precedenti che si sono verificati nella soluzione e il contesto in cui si sono verificati e passare al codice.

 Questa procedura dettagliata illustra come eseguire il debug di un progetto SharePoint in Visual Studio usando Microsoft Monitoring Agent per raccogliere dati IntelliTrace dalle applicazioni distribuite. Per analizzare i dati, è necessario usare Visual Studio Enterprise. Questo progetto incorpora un ricevitore di funzionalità che, quando la funzionalità viene attivata, aggiunge un'attività all'elenco Attività e un annuncio all'elenco Annunci. Quando la funzionalità viene disattivata, l'attività viene contrassegnata come completata e viene aggiunto un secondo annuncio all'elenco Annunci. Tuttavia, la procedura contiene un errore logico che impedisce la corretta esecuzione del progetto. IntelliTrace consente di individuare e correggere l'errore.

 **Si applica a:** Le informazioni contenute in questo argomento si applicano SharePoint soluzioni create in Visual Studio.

 Vengono illustrate le attività seguenti:

- [Creare un ricevitore di funzionalità](#create-a-feature-receiver)

- [Aggiungere codice al ricevitore di funzionalità](#add-code-to-the-feature-receiver)

- [Testare il Project](#test-the-project)

- [Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Eseguire il debug e correggere la soluzione SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Creare un ricevitore di funzionalità

In primo luogo, si crea un progetto SharePoint vuoto con un ricevitore di funzionalità.

1. Creare un SharePoint di soluzione con destinazione la versione di SharePoint installata e deno assegnare al progetto il nome **IntelliTraceTest.**

     Verrà **SharePoint personalizzazione** guidata funzionalità, in cui è possibile specificare sia il sito SharePoint per il progetto che il livello di attendibilità della soluzione.

2. Scegliere il **pulsante di opzione Distribuisci** come soluzione farm e quindi scegliere **il pulsante** Fine.

     IntelliTrace funziona solo su soluzioni farm.

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il **nodo** Funzionalità e quindi scegliere **Aggiungi funzionalità.**

     *Viene visualizzato Feature1.feature.*

4. Aprire il menu di scelta rapida per Feature1.feature e quindi scegliere **Aggiungi ricevitore di** eventi per aggiungere un modulo di codice alla funzionalità.

## <a name="add-code-to-the-feature-receiver"></a>Aggiungere codice al ricevitore di funzionalità

Aggiungere quindi il codice a due metodi nel ricevitore di funzionalità: `FeatureActivated` e `FeatureDeactivating` . Questi metodi vengono attivati ogni volta che una funzionalità viene attivata o disattivata SharePoint, rispettivamente.

1. Nella parte superiore della classe aggiungere il codice seguente, che dichiara le variabili che specificano il SharePoint `Feature1EventReceiver` sito e il sito secondario:

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

## <a name="test-the-project"></a>Testare il progetto

Ora che il codice viene aggiunto al ricevitore di funzionalità e l'agente di raccolta dati è in esecuzione, distribuire ed eseguire la soluzione SharePoint per verificare se funziona correttamente.

> [!IMPORTANT]
> Per questo esempio, viene generato un errore nel gestore dell'evento FeatureDeactivating. Più avanti in questa procedura dettagliata si individua questo errore usando il file con estensione iTrace creato dall'agente di raccolta dati.

1. Distribuire la soluzione in SharePoint e quindi aprire il SharePoint in un browser.

     La funzionalità viene attivata automaticamente, causando l'aggiunta di un annuncio e di un'attività da parte del ricevitore di funzionalità.

2. Visualizzare il contenuto degli elenchi Annunci e Attività.

     L'elenco Annunci dovrebbe avere un nuovo annuncio denominato Funzionalità **attivata: IntelliTraceTest_Feature1** e l'elenco Attività deve avere una nuova attività denominata **Disattiva funzionalità: IntelliTraceTest_Feature1**. Se uno di questi elementi non è presente, verificare se la funzionalità è attivata. Se non è attivato, attivarlo.

3. Disattivare la funzionalità seguendo questa procedura:

   1. Nel menu **Azioni sito** in SharePoint scegliere **Sito Impostazioni**.

   2. In **Azioni sito** scegliere il collegamento Gestisci funzionalità **del** sito.

   3. Accanto a **IntelliTraceTest Feature1** scegliere il **pulsante Disattiva.**

   4. Nella pagina Avviso scegliere il collegamento **Disattiva questa** funzionalità.

      Il gestore dell'evento FeatureDeactivating() genera un errore.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Raccogliere dati IntelliTrace usando Microsoft Monitoring Agent

Se si installa Microsoft Monitoring Agent nel sistema che esegue SharePoint, è possibile eseguire il debug di soluzioni SharePoint usando dati più specifici delle informazioni generiche restituite da IntelliTrace. L'agente funziona al di Visual Studio usando i cmdlet di PowerShell per acquisire informazioni di debug durante l'SharePoint della soluzione.

> [!NOTE]
> Le informazioni di configurazione contenute in questa sezione sono specifiche di questo esempio. Per altre informazioni sulle altre opzioni di configurazione, vedere [Uso dell'agente di raccolta autonomo IntelliTrace.](../debugger/using-the-intellitrace-stand-alone-collector.md)

1. Nel computer che esegue [SharePoint, configurare Microsoft Monitoring Agent e iniziare a monitorare la soluzione](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Disattivare la funzionalità:

   1. Nel menu **Azioni sito** in SharePoint scegliere **Sito Impostazioni**.

   2. In **Azioni sito** scegliere il collegamento Gestisci funzionalità **del** sito.

   3. Accanto a **IntelliTraceTest Feature1** scegliere il **pulsante Disattiva.**

   4. Nella pagina Avviso scegliere il collegamento **Disattiva questa** funzionalità.

      Si verifica un errore (in questo caso, a causa dell'errore generato nel gestore dell'evento FeatureDeactivating().

3. Nella finestra di PowerShell eseguire il comando [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) per creare il file con estensione iTrace, arrestare il monitoraggio e riavviare la SharePoint soluzione.

     **Stop-WebApplicationMonitoring***"<\<SharePointSite> \\ SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Eseguire il debug e correggere la SharePoint soluzione

È ora possibile visualizzare il file di log IntelliTrace in Visual Studio per trovare e correggere l'errore nella SharePoint soluzione.

1. Nella cartella \IntelliTraceLogs aprire il file con estensione iTrace in Visual Studio.

     Verrà **visualizzata la pagina Riepilogo IntelliTrace.** Poiché l'errore non è stato gestito, nell'area delle eccezioni non gestite della  sezione SharePoint viene visualizzato un ID di correlazione (GUID). Scegliere il **pulsante Stack di** chiamate per visualizzare lo stack di chiamate in cui si è verificato l'errore.

2. Scegliere il **pulsante Debug eccezione.**

     Se richiesto, caricare i file di simboli. Nella finestra **IntelliTrace** l'eccezione viene evidenziata come "Generata: Si è verificato un errore grave!".

     Nella finestra IntelliTrace scegliere l'eccezione per visualizzare il codice che ha avuto esito negativo.

3. Correggere l'errore aprendo la soluzione SharePoint e quindi impostando come commento o rimuovendo l'istruzione **throw** all'inizio della procedura FeatureDeactivating().

4. Ricompilare la soluzione in Visual Studio e quindi ridistribuirla in SharePoint.

5. Disattivare la funzionalità seguendo questa procedura:

    1. Nel menu **Azioni sito** in SharePoint scegliere **Sito Impostazioni**.

    2. In **Azioni sito** scegliere il collegamento Gestisci funzionalità **del** sito.

    3. Accanto a **IntelliTraceTest Feature1** scegliere il **pulsante Disattiva.**

    4. Nella pagina Avviso scegliere il collegamento **Disattiva questa** funzionalità.

6. Aprire l'elenco Attività e  verificare che il valore Stato dell'attività Disattiva sia "Completato" e che **il relativo valore %** di completamento sia 100%.

     Il codice viene ora eseguito correttamente.

## <a name="see-also"></a>Vedi anche

- [Verificare ed eseguire il debug SharePoint codice](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Procedura dettagliata: Verificare SharePoint codice usando unit test](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
