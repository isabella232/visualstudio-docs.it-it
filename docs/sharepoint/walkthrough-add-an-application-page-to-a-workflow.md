---
title: "Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro | Microsoft Docs"
description: In questa procedura dettagliata aggiungere una pagina dell'applicazione a una soluzione del flusso di lavoro di SharePoint. Modificare il codice del flusso di lavoro. Creare, codificare e testare la pagina dell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d07b5272a31a0c649e12f353aefaa7c63c335eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882661"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro
  In questa procedura dettagliata viene illustrato come aggiungere una pagina dell'applicazione che Visualizza i dati derivati da un flusso di lavoro a un progetto flusso di lavoro. Si basa sul progetto descritto nell'argomento [procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Aggiunta di una pagina dell'applicazione ASPX a un progetto flusso di lavoro di SharePoint.

- Recupero di dati dal progetto flusso di lavoro e manipolazione.

- Visualizzazione dei dati in una tabella nella pagina dell'applicazione.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- È anche necessario completare il progetto nell'argomento [procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="amend-the-workflow-code"></a>Modificare il codice del flusso di lavoro
 Per prima cosa, aggiungere una riga di codice al flusso di lavoro per impostare il valore della colonna risultato sulla quantità della nota spese. Questo valore viene utilizzato in un secondo momento nel calcolo di riepilogo della nota spese.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Per impostare il valore della colonna risultati nel flusso di lavoro

1. Caricare il progetto completato dall'argomento [procedura dettagliata: creazione di un flusso di lavoro con i moduli di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Aprire il codice per *Workflow1.cs* o *Workflow1. vb* , a seconda del linguaggio di programmazione in uso.

3. `createTask1_MethodInvoking`Aggiungere il codice seguente alla fine del metodo:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione
 Aggiungere quindi un modulo ASPX al progetto. In questo modulo vengono visualizzati i dati ottenuti dal progetto flusso di lavoro della nota spese. A tale scopo, verrà aggiunta una pagina dell'applicazione. Una pagina dell'applicazione utilizza la stessa pagina master di altre pagine di SharePoint, ovvero sarà simile ad altre pagine del sito di SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Per aggiungere una pagina dell'applicazione al progetto

1. Scegliere il progetto ExpenseReport, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

2. Nel riquadro **modelli** scegliere il modello di **pagina applicazione** , usare il nome predefinito per l'elemento del progetto (**ApplicationPage1. aspx**) e scegliere il pulsante **Aggiungi** .

3. In [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] di ApplicationPage1. aspx sostituire la `PlaceHolderMain` sezione con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Questo codice aggiunge una tabella alla pagina insieme a un titolo.

4. Aggiungere un titolo alla pagina dell'applicazione sostituendo la `PlaceHolderPageTitleInTitleArea` sezione con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Scrivere il codice della pagina dell'applicazione
 Successivamente, aggiungere il codice alla pagina dell'applicazione di riepilogo delle spese. Quando si apre la pagina, il codice analizza l'elenco attività in SharePoint per le spese che hanno superato il limite di spesa allocato. Il report elenca ogni elemento insieme alla somma delle spese.

#### <a name="to-code-the-application-page"></a>Per codificare la pagina dell'applicazione

1. Scegliere il nodo **ApplicationPage1. aspx** , quindi nella barra dei menu scegliere **Visualizza**  >  **codice** per visualizzare il codice dietro la pagina dell'applicazione.

2. Sostituire le istruzioni **using** o **Import** (a seconda del linguaggio di programmazione) nella parte superiore della classe con gli elementi seguenti:

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
    > Assicurarsi di sostituire "TestServer" nel codice con il nome di un server valido in cui è in esecuzione SharePoint.

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione
 Determinare quindi se la pagina dell'applicazione visualizza correttamente i dati delle spese.

#### <a name="to-test-the-application-page"></a>Per eseguire il test della pagina dell'applicazione

1. Premere il tasto **F5** per eseguire e distribuire il progetto in SharePoint.

2. Scegliere il pulsante **Home** , quindi scegliere il collegamento **documenti condivisi** sulla barra QuickLaunch per visualizzare l'elenco documenti condivisi nel sito di SharePoint.

3. Per rappresentare i report delle spese per questo esempio, caricare alcuni nuovi documenti nell'elenco documenti scegliendo il collegamento **documenti** nella scheda **Strumenti raccolta** nella parte superiore della pagina e quindi scegliendo il pulsante **Carica documento** sulla barra multifunzione dello strumento.

4. Dopo aver caricato alcuni documenti, creare un'istanza del flusso di lavoro scegliendo il collegamento **libreria** nella scheda **Strumenti raccolta** nella parte superiore della pagina e quindi scegliendo il pulsante **Impostazioni libreria** nella barra multifunzione dello strumento.

5. Nella pagina **Impostazioni raccolta documenti** scegliere il collegamento **Impostazioni flusso di lavoro** nella sezione **autorizzazioni e gestione** .

6. Nella pagina **Impostazioni flusso di lavoro** scegliere il collegamento **Aggiungi un flusso di lavoro** .

7. Nella pagina **Aggiungi un flusso di lavoro** scegliere il flusso di lavoro **ExpenseReport-Workflow1** , immettere un nome per il flusso di lavoro, ad esempio **ExpenseTest**, quindi scegliere il pulsante **Avanti** .

    Viene visualizzato il form di associazione del flusso di lavoro. Usarlo per segnalare l'importo del limite di spesa.

8. Nel modulo di associazione, immettere **1000** nella casella **limite approvazione automatica** , quindi scegliere il pulsante **Associa flusso di lavoro** .

9. Scegliere il pulsante **Home** per tornare alla Home page di SharePoint.

10. Scegliere il collegamento **documenti condivisi** sulla barra QuickLaunch.

11. Scegliere uno dei documenti caricati per visualizzare una freccia a discesa, selezionarla, quindi scegliere l'elemento flussi di **lavoro** .

12. Scegliere l'immagine accanto a ExpenseTest per visualizzare il form di avvio del flusso di lavoro.

13. Nella casella di testo **Expense Total** immettere un valore maggiore di 1000, quindi scegliere il pulsante **Avvia flusso di lavoro** .

     Quando una spesa segnalata supera l'importo delle spese allocate, viene aggiunta un'attività al Elenco attività. Una colonna denominata **ExpenseTest** con il valore **Completed** viene aggiunta anche all'elemento expense report nell'elenco Shared Documents.

14. Ripetere i passaggi 11-13 con altri documenti nell'elenco documenti condivisi. Il numero esatto di documenti non è importante.

15. Per visualizzare la pagina dell'applicazione Riepilogo spese, aprire l'URL seguente in un Web browser: **http://**<em>systemname</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Nella pagina Riepilogo spese sono elencate tutte le segnalazioni spese che hanno superato l'importo allocato, la quantità per cui sono state superate e l'importo totale per tutti i report.

## <a name="next-steps"></a>Passaggi successivi
 Per ulteriori informazioni sulle pagine dell'applicazione SharePoint, vedere [creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Per ulteriori informazioni su come progettare il contenuto di una pagina di SharePoint utilizzando la finestra di progettazione visiva Web in Visual Studio, vedere gli argomenti seguenti:

- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creazione di controlli riutilizzabili per Web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Procedura: creare una pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md)
- [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)