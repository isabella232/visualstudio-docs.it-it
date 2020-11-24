---
title: Eseguire il debug di un'applicazione SharePoint con IntelliTrace
description: Utilizzare IntelliTrace per eseguire più facilmente il debug e la correzione delle applicazioni SharePoint. Creare e aggiungere codice a un ricevitore di funzionalità. Testare il progetto. Raccogli dati IntelliTrace.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c7ab11dbe213208a2e8f5e39c3af2d20b79f5cb
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598484"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace

Con IntelliTrace è possibile eseguire più facilmente il debug delle soluzioni SharePoint. I debugger tradizionali forniscono solo uno snapshot di una soluzione al momento corrente. Tuttavia, è possibile usare IntelliTrace per esaminare gli eventi precedenti che si sono verificati nella soluzione e il contesto in cui si sono verificati e passare al codice.

 In questa procedura dettagliata viene illustrato come eseguire il debug di un progetto SharePoint 2010 o SharePoint 2013 in Visual Studio utilizzando Microsoft Monitoring Agent per raccogliere dati IntelliTrace dalle applicazioni distribuite. Per analizzare i dati, è necessario utilizzare Visual Studio Enterprise. Questo progetto incorpora un ricevitore di funzionalità che, quando la funzionalità è attivata, aggiunge un'attività all'elenco attività e un annuncio all'elenco degli annunci. Quando la funzionalità viene disattivata, l'attività viene contrassegnata come completata e viene aggiunto un secondo annuncio all'elenco degli annunci. Tuttavia, la stored procedure contiene un errore logico che impedisce l'esecuzione corretta del progetto. Con IntelliTrace, è possibile individuare e correggere l'errore.

 **Si applica a:** Le informazioni contenute in questo argomento sono valide per le soluzioni SharePoint 2010 e SharePoint 2013 create in Visual Studio.

 Vengono illustrate le attività seguenti:

- [Creare un ricevitore di funzionalità](#create-a-feature-receiver)

- [Aggiungere codice al ricevitore di funzionalità](#add-code-to-the-feature-receiver)

- [Testare il progetto](#test-the-project)

- [Raccogliere dati IntelliTrace usando Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Eseguire il debug e correggere la soluzione SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Creazione di un ricevitore di funzionalità

Si crea innanzitutto un progetto SharePoint vuoto con un ricevitore di funzionalità.

1. Creare un progetto di soluzione SharePoint 2010 o SharePoint 2013 e denominarlo **IntelliTraceTest**.

     Viene visualizzata la **personalizzazione guidata SharePoint** , in cui è possibile specificare il sito di SharePoint per il progetto e il livello di attendibilità della soluzione.

2. Scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** .

     IntelliTrace opera solo su soluzioni farm.

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **funzionalità** , quindi scegliere **Aggiungi funzionalità**.

     Viene visualizzato *Feature1. feature* .

4. Aprire il menu di scelta rapida per Feature1. feature, quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un modulo di codice alla funzionalità.

## <a name="add-code-to-the-feature-receiver"></a>Aggiungere codice al ricevitore di funzionalità

Aggiungere quindi il codice a due metodi nel ricevitore della funzionalità: `FeatureActivated` e `FeatureDeactivating` . Questi metodi vengono attivati ogni volta che una funzionalità viene attivata o disattivata rispettivamente in SharePoint.

1. Nella parte superiore della `Feature1EventReceiver` classe aggiungere il codice seguente, che dichiara le variabili che specificano il sito di SharePoint e il sito secondario:

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

Ora che il codice è stato aggiunto al ricevitore della funzionalità e l'agente di raccolta dati è in esecuzione, distribuire ed eseguire la soluzione SharePoint per verificare se funziona correttamente.

> [!IMPORTANT]
> Per questo esempio viene generato un errore nel gestore eventi FeatureDeactivating. Più avanti in questa procedura dettagliata si individua questo errore utilizzando il file con estensione iTrace creato dall'agente di raccolta dati.

1. Distribuire la soluzione in SharePoint e quindi aprire il sito di SharePoint in un browser.

     La funzionalità viene attivata automaticamente, facendo in modo che il ricevitore di funzionalità aggiunga un annuncio e un'attività.

2. Visualizzare il contenuto degli elenchi Annunci e attività.

     L'elenco degli annunci dovrebbe avere un nuovo annuncio denominato **funzionalità attivata: IntelliTraceTest_Feature1** e l'elenco attività deve avere una nuova attività denominata **disattiva funzionalità: IntelliTraceTest_Feature1**. Se uno di questi elementi è mancante, verificare se la funzionalità è attivata. Se non è attivato, attivarlo.

3. Disattivare la funzionalità eseguendo i passaggi seguenti:

   1. Nel menu **Azioni sito** di SharePoint scegliere **Impostazioni sito**.

   2. In **Azioni sito** scegliere il collegamento **Gestisci caratteristiche sito** .

   3. Accanto a **IntelliTraceTest Feature1** scegliere il pulsante **Disattiva** .

   4. Nella pagina avviso scegliere il collegamento **Disattiva la funzionalità** .

      Il gestore eventi FeatureDeactivating () genera un errore.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Raccogliere dati IntelliTrace usando Microsoft Monitoring Agent

Se si installa Microsoft Monitoring Agent nel sistema in cui è in esecuzione SharePoint, è possibile eseguire il debug delle soluzioni SharePoint utilizzando dati più specifici rispetto alle informazioni generiche restituite da IntelliTrace. L'agente funziona all'esterno di Visual Studio usando i cmdlet di PowerShell per acquisire le informazioni di debug durante l'esecuzione della soluzione SharePoint.

> [!NOTE]
> Le informazioni di configurazione in questa sezione sono specifiche per questo esempio. Per altre informazioni sulle altre opzioni di configurazione, vedere [uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Nel computer in cui è in esecuzione SharePoint, [configurare Microsoft Monitoring Agent e avviare il monitoraggio della soluzione](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Disattiva la funzionalità:

   1. Nel menu **Azioni sito** di SharePoint scegliere **Impostazioni sito**.

   2. In **Azioni sito** scegliere il collegamento **Gestisci caratteristiche sito** .

   3. Accanto a **IntelliTraceTest Feature1** scegliere il pulsante **Disattiva** .

   4. Nella pagina avviso scegliere il collegamento **Disattiva la funzionalità** .

      Si verifica un errore, in questo caso a causa dell'errore generato nel gestore dell'evento FeatureDeactivating ().

3. Nella finestra di PowerShell eseguire il comando [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) per creare il file con estensione iTrace, arrestare il monitoraggio e riavviare la soluzione SharePoint.

     **Stop-WebApplicationMonitoring***" \<SharePointSite> \\<SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Eseguire il debug e correggere la soluzione SharePoint

A questo punto è possibile visualizzare il file di log IntelliTrace in Visual Studio per individuare e correggere l'errore nella soluzione SharePoint.

1. Nella cartella \IntelliTraceLogs aprire il file con estensione iTrace in Visual Studio.

     Viene visualizzata la pagina di **Riepilogo di IntelliTrace** . Poiché l'errore non è stato gestito, viene visualizzato un ID correlazione di SharePoint (GUID) nell'area delle eccezioni non gestite della sezione di **analisi** . Scegliere il pulsante **stack di chiamate** se si desidera visualizzare lo stack di chiamate in cui si è verificato l'errore.

2. Scegliere il pulsante **debug Exception** .

     Se richiesto, caricare i file di simboli. Nella finestra **IntelliTrace** l'eccezione viene evidenziata come "generata: errore grave.".

     Nella finestra IntelliTrace scegliere l'eccezione per visualizzare il codice che ha avuto esito negativo.

3. Per correggere l'errore, aprire la soluzione SharePoint e impostare come commento o rimuovere l'istruzione **throw** all'inizio della procedura FeatureDeactivating ().

4. Ricompilare la soluzione in Visual Studio, quindi ridistribuirla in SharePoint.

5. Disattivare la funzionalità eseguendo i passaggi seguenti:

    1. Nel menu **Azioni sito** di SharePoint scegliere **Impostazioni sito**.

    2. In **Azioni sito** scegliere il collegamento **Gestisci caratteristiche sito** .

    3. Accanto a **IntelliTraceTest Feature1** scegliere il pulsante **Disattiva** .

    4. Nella pagina avviso scegliere il collegamento **Disattiva la funzionalità** .

6. Aprire l'elenco attività e verificare che il valore di **stato** dell'attività di disattivazione sia "completato" e che il relativo valore **% complete** sia pari al 100%.

     Il codice ora viene eseguito correttamente.

## <a name="see-also"></a>Vedere anche

- [Verificare ed eseguire il debug del codice SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Procedura dettagliata: verificare il codice SharePoint tramite unit test](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))