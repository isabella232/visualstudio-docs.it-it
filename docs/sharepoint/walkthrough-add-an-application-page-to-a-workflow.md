---
title: "Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032447051bc03b037abba2920d48473f0d73935f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409551"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro
  Questa procedura dettagliata illustra come aggiungere una pagina dell'applicazione che consente di visualizzare i dati derivati da un flusso di lavoro a un progetto di flusso di lavoro. Essendo basato su progetto descritto nell'argomento [procedura dettagliata: Creare un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Aggiunta di una pagina ASPX applicazione a un progetto di flusso di lavoro di SharePoint.

- Recupero di dati dal progetto flusso di lavoro e la manipolazione.

- Visualizzazione dei dati in una tabella nella pagina dell'applicazione.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- Inoltre necessario aver completato il progetto nell'argomento [procedura dettagliata: Creare un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend il codice del flusso di lavoro
 In primo luogo, aggiungere una riga di codice per il flusso di lavoro per impostare il valore della colonna risultato all'importo della nota spese. Questo valore viene usato in un secondo momento nel calcolo delle spese report riepilogo.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Per impostare il valore della colonna risultato nel flusso di lavoro

1. Caricare il progetto completato dall'argomento [procedura dettagliata: Creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Aprire il codice per *Workflow1.cs* oppure *Workflow1.vb* (a seconda del linguaggio di programmazione).

3. In fondo il `createTask1_MethodInvoking` metodo, aggiungere il codice seguente:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Creare una pagina applicazione
 Successivamente, aggiungere un form ASPX al progetto. Questo modulo verrà visualizzati i dati ottenuti dal progetto flusso di lavoro report nota spese. A tale scopo, si aggiungerà una pagina dell'applicazione. Una pagina dell'applicazione usa la stessa pagina master come altre pagine di SharePoint, vale a dire che ricorderà altre pagine nel sito di SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Per aggiungere una pagina dell'applicazione al progetto

1. Scegliere il progetto ExpenseReport e quindi nella barra dei menu scegliere **Project** > **Aggiungi nuovo elemento**.

2. Nel **modelli** riquadro, scegliere il **pagina dell'applicazione** modello, usare il nome predefinito per l'elemento del progetto (**ApplicationPage1.aspx**) e scegliere il **Add** pulsante.

3. Nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] di ApplicationPage1.aspx, sostituire il `PlaceHolderMain` sezione con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Questo codice aggiunge una tabella alla pagina con un titolo.

4. Aggiungere un titolo alla pagina dell'applicazione mediante la sostituzione di `PlaceHolderPageTitleInTitleArea` sezione con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>La pagina dell'applicazione del codice
 Successivamente, aggiungere codice alla pagina di riepilogo dell'applicazione della nota spese. Quando si apre la pagina, il codice analizza l'elenco di attività in SharePoint per le spese che supera il limite di spesa allocato. Il report elenca ogni elemento con la somma delle spese.

#### <a name="to-code-the-application-page"></a>Scrivere codice della pagina dell'applicazione

1. Scegliere il **ApplicationPage1.aspx** nodo, quindi nella barra dei menu, scegliere **View** > **codice** per visualizzare il code-behind della pagina dell'applicazione.

2. Sostituire il **usando** oppure **importazione** istruzioni (a seconda del linguaggio di programmazione) nella parte superiore della classe con quanto segue:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. Aggiungere al metodo `Page_Load` il codice seguente:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > Assicurarsi di sostituire "TestServer" nel codice con il nome di un server valido di cui è eseguito SharePoint.

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione
 Successivamente, determinare se la pagina dell'applicazione vengono visualizzati correttamente i dati di spesa.

#### <a name="to-test-the-application-page"></a>Per testare la pagina dell'applicazione

1. Scegliere il **F5** tasto per eseguire e distribuire il progetto in SharePoint.

2. Scegliere il **casa** pulsante e quindi scegliere il **documenti condivisi** collegamento sulla barra Avvio veloce per visualizzare l'elenco di documenti condivisi nel sito di SharePoint.

3. Per rappresentare le spese per questo esempio, caricare alcuni nuovi documenti in elenco dei documenti, scegliendo la **documenti** sul collegamento il **Strumenti raccolta** scheda nella parte superiore della pagina e quindi scegliendo il  **Caricamento del documento** pulsante sulla barra multifunzione dello strumento.

4. Dopo aver caricato alcuni documenti, creare un'istanza del flusso di lavoro scegliendo la **Library** sul collegamento il **Strumenti raccolta** scheda nella parte superiore della pagina e quindi scegliere il **impostazioni libreria**pulsante sulla barra multifunzione dello strumento.

5. Nel **impostazioni raccolta documenti** pagina, scegliere il **le impostazioni del flusso di lavoro** clic sul collegamento nella **autorizzazioni e gestione** sezione.

6. Nel **delle impostazioni del flusso di lavoro** pagina, scegliere il **aggiungere un flusso di lavoro** collegamento.

7. Nel **aggiungere un flusso di lavoro** pagina, scegliere il **ExpenseReport - Workflow1** flusso di lavoro, immettere un nome per il flusso di lavoro, ad esempio **ExpenseTest**, quindi scegliere il **Successivo** pulsante.

    Viene visualizzato il form di associazione flusso di lavoro. Usarlo per segnalare l'importo del limite di spesa.

8. Nel form di associazione, immettere **1000** nel **limite di approvazione automatica** casella e quindi scegliere il **Associa flusso di lavoro** pulsante.

9. Scegliere il **domestica** per tornare alla home page di SharePoint.

10. Scegliere il **documenti condivisi** collegamento sulla barra Avvio veloce.

11. Scegliere uno dei documenti caricati per visualizzare una freccia a discesa, selezionarlo e quindi scegliere il **flussi di lavoro** elemento.

12. Scegliere l'immagine accanto ExpenseTest per visualizzare il form di avvio del flusso di lavoro.

13. Nel **spese totali** casella di testo, immettere un valore che è superiore a 1000 e quindi scegliere il **Avvia flusso di lavoro** pulsante.

     Quando una spesa segnalata supera l'importo delle spese allocato, un'attività viene aggiunto all'elenco attività. Una colonna denominata **ExpenseTest** con il valore **Completed** viene inoltre aggiunto all'elemento del report nota spese nell'elenco dei documenti condivisi.

14. Ripetere i passaggi da 11 a 13 nell'elenco dei documenti condivisi altri documenti. (Il numero esatto di documenti non è importante.)

15. Visualizzare la pagina di riepilogo dell'applicazione expense report aprendo l'URL seguente in un Web browser: **http://**<em>NomeSistema</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     La pagina Riepilogo della nota spese Elenca tutte le note spese che supera la quantità allocata e la quantità per che è superato la quantità totale per tutti i report.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sulle pagine dell'applicazione SharePoint, vedere [creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 È possibile altre informazioni su come progettare contenuto pagina di SharePoint tramite Visual Web Designer in Visual Studio vedere gli argomenti seguenti:

- [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)
- [Creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)