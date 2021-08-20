---
title: "Procedura dettagliata: Profilatura di un'SharePoint di | Microsoft Docs"
description: In questa procedura dettagliata usare gli strumenti di profilatura in Visual Studio per ottimizzare le prestazioni di un SharePoint appliazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 555f805203e7f0f4097d97d0950d85be859b1c1e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148701"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Procedura dettagliata: Profilare un'SharePoint applicazione
  In questa procedura dettagliata viene illustrato come utilizzare gli strumenti di profilatura in Visual Studio per ottimizzare le prestazioni di un'applicazione SharePoint. L'applicazione di esempio è un ricevitore di eventi di funzionalità SharePoint contenente un ciclo inattivo che comporta una riduzione delle prestazioni del ricevitore di eventi di funzionalità. Il Visual Studio profiler consente di individuare ed eliminare la parte più costosa (con prestazioni più lente) del progetto, nota anche come *percorso critico*.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- [Aggiungere una funzionalità e un ricevitore di eventi di funzionalità](#add-a-feature-and-feature-event-receiver).

- [Configurare e distribuire l'SharePoint applicazione](#configure-and-deploy-the-sharepoint-application).

- [Eseguire l'SharePoint applicazione](#run-the-sharepoint-application).

- [Visualizzare e interpretare i risultati del profilo.](#view-and-interpret-the-profile-results)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Creare un SharePoint progetto
 Creare innanzitutto un progetto SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Per creare un progetto SharePoint

1. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project** per visualizzare la finestra **di dialogo Project** nuova cartella.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel riquadro dei modelli scegliere il **modello SharePoint 2010 Project** 2010.

4. Nella casella **Nome** immettere **ProfileTest** e quindi scegliere **il pulsante OK.**

    Verrà **visualizzata SharePoint personalizzazione** guidata.

5. Nella  pagina Specificare il sito e il livello di sicurezza per il debug immettere l'URL per il sito del server SharePoint in cui si vuole eseguire il debug della definizione del sito o usare il percorso predefinito (http://<em>nome</em>di sistema /).

6. Nella sezione **Qual è il livello di attendibilità** per SharePoint soluzione? scegliere il pulsante **di** opzione Distribuisci come soluzione farm.

    Attualmente, è possibile profilare solo soluzioni farm. Per altre informazioni sulle soluzioni sandbox rispetto alle soluzioni farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. Fare clic sul pulsante **Fine**. Il progetto viene visualizzato in **Esplora soluzioni**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Aggiungere una funzionalità e un ricevitore di eventi di funzionalità
 Successivamente, aggiungere una funzionalità al progetto insieme a un ricevitore di eventi per la funzionalità. In questo ricevitore di eventi sarà incluso il codice da profilare.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Per aggiungere una funzionalità e un ricevitore di eventi di funzionalità

1. In Esplora soluzioni aprire il menu di  scelta rapida per il nodo Funzionalità, scegliere **Aggiungi** funzionalità **e** lasciare il nome sul valore **predefinito, Feature1.**

2. In **Esplora soluzioni** aprire il menu di scelta rapida per **Feature1** e quindi scegliere **Aggiungi ricevitore di eventi.**

     Verrà aggiunto un file di codice alla funzionalità con diversi gestori di eventi impostati come commenti e viene aperto il file da modificare.

3. Nella classe del ricevitore di eventi aggiungere le seguenti dichiarazioni di variabili.

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

4. Sostituire la procedura `FeatureActivated` con il codice seguente.

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

5. Aggiungere la procedura seguente sotto la `FeatureActivated` procedura .

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

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto (**ProfileTest**) e quindi scegliere **Proprietà.**

7. Nella finestra **di** dialogo Proprietà scegliere la **SharePoint** proprietà.

8. **Nell'elenco Configurazione distribuzione** attiva scegliere Nessuna **attivazione.**

     Se si seleziona questa configurazione di distribuzione è possibile attivare manualmente la funzionalità in un secondo momento in SharePoint.

9. Salvare il progetto.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurare e distribuire l'SharePoint applicazione
 Una volta pronto il progetto SharePoint, è possibile configurarlo e distribuirlo nel server SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Per configurare e distribuire l'applicazione SharePoint

1. Scegliere **Avvia** Creazione guidata prestazioni dal menu **Analizza**.

2. Nella prima pagina della Creazione **guidata sessione di** prestazioni lasciare il metodo di profilatura campionamento **CPU** e scegliere **il pulsante** Avanti.

     Gli altri metodi di profilatura possono essere utilizzati in situazioni di profilatura più avanzate. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).

3. Nella seconda pagina della **creazione guidata delle prestazioni** lasciare la destinazione del profilo **ProfileTest** e scegliere **il pulsante** Avanti.

     Se in una soluzione sono disponibili più progetti, vengono visualizzati in questo elenco.

4. Nella tre pagina della **Creazione guidata sessione di** prestazioni deselezionare la casella di controllo **Abilita** profilatura interazione tra livelli e quindi scegliere **il pulsante** Avanti.

     La funzionalità di profilatura interazione tra livelli (TIP) è utile per misurare le prestazioni di applicazioni in cui vengono eseguite query sui database e per visualizzare il numero di volte in cui viene richiesta una pagina Web. Poiché i dati non sono necessari per questo esempio, la funzionalità non verrà abilitata.

5. Nella pagina quattro della Creazione  guidata sessione **di** prestazioni lasciare selezionata la casella di controllo Avvia profilatura al termine della procedura guidata e quindi scegliere **il pulsante** Fine.

     La procedura guidata abilita la profilatura dell'applicazione nel server, visualizza la **finestra Esplora prestazioni** e quindi compila, distribuisce ed esegue l SharePoint appliazione.

## <a name="run-the-sharepoint-application"></a>Eseguire l'SharePoint applicazione
 Attivare la funzionalità in SharePoint, attivando il codice dell'evento `FeatureActivation` da eseguire.

### <a name="to-run-the-sharepoint-application"></a>Per eseguire l'applicazione SharePoint

1. In SharePoint aprire il menu **Azioni** sito e quindi scegliere **Sito Impostazioni**.

2. **Nell'elenco Azioni sito** scegliere il collegamento Gestisci funzionalità **del** sito.

3. **Nell'elenco** Funzionalità scegliere il **pulsante Attiva** accanto a **ProfileTest Feature1.**

     Vi sarà una pausa quando verrà eseguita questa operazione, a causa del ciclo inattivo chiamato nella funzione `FeatureActivated`.

4. Nella barra **Avvio veloce** scegliere **Elenchi** e quindi **nell'elenco** Elenchi scegliere **Annunci.**

     Si noti che un nuovo annuncio è stato aggiunto all'elenco per indicare che la funzionalità è stata attivata.

5. Chiudere il sito di SharePoint.

     Dopo aver chiuso SharePoint, il profiler crea e visualizza un report di profilatura di esempio e lo salva come file con estensione vsp nella cartella del progetto **ProfileTest.**

## <a name="view-and-interpret-the-profile-results"></a>Visualizzare e interpretare i risultati del profilo
 Dopo aver eseguito e profilato l'applicazione SharePoint, visualizzare i risultati del test.

### <a name="to-view-and-interpret-the-profile-results"></a>Per visualizzare e interpretare i risultati del profilo

1. Nella sezione **Functions Doing the Most Individual Work** del rapporto di profilatura di esempio si noti che si trova nella parte superiore `TimeCounter` dell'elenco.

     Questa posizione indica che `TimeCounter` è una delle funzioni con il numero più elevato di campioni, pertanto è uno dei più grandi colli di bottiglia delle prestazioni nell'applicazione. Questa situazione non è insolita, tuttavia, dal momento che si tratta di una modalità progettata espressamente a scopo dimostrativo.

2. Nella sezione **Funzioni che eseranno il lavoro più individuale** scegliere il collegamento per visualizzare la distribuzione dei costi per la `ProcessRequest` `ProcessRequest` funzione.

     Nella sezione **Funzioni chiamate** per si noti che la `ProcessRequest` funzione **FeatureActiviated** è elencata come la funzione chiamata più costosa.

3. Nella sezione **Funzioni chiamate** scegliere il **pulsante FunzionalitàAttivata.**

     Nella sezione **Funzioni chiamate** per **FeatureActivated** la funzione è elencata `TimeCounter` come la funzione chiamata più costosa. Nel riquadro **Visualizzazione codice funzione** il codice evidenziato ( ) è l'hotspot e indica dove è necessaria la `TimeCounter` correzione.

4. Chiudere il Rapporto sulla profilatura dei campioni.

     Per visualizzare di nuovo il report in qualsiasi momento, aprire il file con estensione vsp **nella finestra Esplora prestazioni** report.

## <a name="fix-the-code-and-reprofile-the-application"></a>Correggere il codice e riprofilare l'applicazione
 Una volta identificata la funzione relativa all'area sensibile nell'applicazione SharePoint, correggerla.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Per correggere il codice e riprofilare l'applicazione

1. Nel codice del ricevitore di eventi di funzionalità impostare come commento la chiamata al metodo `TimeCounter` in `FeatureActivated` per impedire che venga chiamato.

2. Salvare il progetto.

3. In **Esplora prestazioni** aprire la cartella Destinazioni e quindi scegliere il **nodo ProfileTest.**

4. Sulla barra **Esplora prestazioni,** nella **scheda Azioni,** scegliere il **pulsante Avvia** profilatura.

     Se si vuole modificare una delle proprietà di profilatura prima di riprodurre l'applicazione, scegliere invece il pulsante Avvia **Creazione guidata** sessione di prestazioni.

5. Seguire le istruzioni riportate nella sezione **Esecuzione dell SharePoint app applicazione,** in precedenza in questo argomento.

     L'attivazione della funzionalità dovrebbe essere molto più veloce una volta che è stata eliminata la chiamata al ciclo inattivo. Il Rapporto sulla profilatura dei campioni dovrebbe riflettere questa situazione.

## <a name="see-also"></a>Vedi anche
- [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)
- [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)
- [Find Application Bottlenecks with Visual Studio Profiler](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler) (Trovare i colli di bottiglia delle applicazioni con il profiler di Visual Studio)