---
title: 'Procedura dettagliata: Aggiungere una pagina applicazione a un flusso di lavoro | Microsoft Docs'
description: In questa procedura dettagliata aggiungere una pagina dell'applicazione a una soluzione SharePoint flusso di lavoro. Modificare il codice del flusso di lavoro. Creare, codificare e testare la pagina dell'applicazione.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 50017d9a7c368bdc9cbcfa5438aec09a63d4508b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047543"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro
  Questa procedura dettagliata illustra come aggiungere una pagina dell'applicazione che visualizza i dati derivati da un flusso di lavoro a un progetto del flusso di lavoro. Si basa sul progetto descritto nell'argomento [Procedura dettagliata: Creare un flusso](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)di lavoro con moduli di associazione e di avvio .

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Aggiunta di una pagina dell'applicazione ASPX a un progetto SharePoint flusso di lavoro.

- Recupero dei dati dal progetto del flusso di lavoro e modifica dei dati.

- Visualizzazione dei dati in una tabella nella pagina dell'applicazione.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- È anche necessario completare il progetto nell'argomento [Procedura dettagliata: Creare un flusso](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)di lavoro con i moduli di associazione e avvio .

## <a name="amend-the-workflow-code"></a>Modificare il codice del flusso di lavoro
 Aggiungere prima di tutto una riga di codice al flusso di lavoro per impostare il valore della colonna Risultato sulla quantità della nota spese. Questo valore viene usato in un secondo momento nel calcolo riepilogativo della nota spese.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Per impostare il valore della colonna dei risultati nel flusso di lavoro

1. Caricare il progetto completato dall'argomento [Procedura dettagliata: Creazione di un](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) flusso di lavoro con moduli di associazione e di avvio in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Aprire il codice per *Workflow1.cs o* *Workflow1.vb* (a seconda del linguaggio di programmazione).

3. Alla fine del `createTask1_MethodInvoking` metodo aggiungere il codice seguente:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione
 Aggiungere quindi un form ASPX al progetto. Questo modulo visualizza i dati ottenuti dal progetto del flusso di lavoro della nota spese. A tale scopo, si aggiungerà una pagina dell'applicazione. Una pagina dell'applicazione usa la stessa pagina master di altre pagine SharePoint, il che significa che sarà simile ad altre pagine del SharePoint sito.

#### <a name="to-add-an-application-page-to-the-project"></a>Per aggiungere una pagina dell'applicazione al progetto

1. Scegliere il progetto ExpenseReport e quindi nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

2. Nel riquadro **Modelli** scegliere il modello **Pagina** applicazione, usare il nome predefinito per l'elemento di progetto (**ApplicationPage1.aspx**) e scegliere il **pulsante** Aggiungi.

3. In di [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx sostituire la `PlaceHolderMain` sezione con quanto segue:

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

4. Aggiungere un titolo alla pagina dell'applicazione sostituendo la `PlaceHolderPageTitleInTitleArea` sezione con quanto segue:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Codificare la pagina dell'applicazione
 Aggiungere quindi il codice alla pagina dell'applicazione di riepilogo della nota spese. Quando si apre la pagina, il codice analizza l'elenco attività in SharePoint le spese che superano il limite di spesa allocato. Il report elenca ogni elemento insieme alla somma delle spese.

#### <a name="to-code-the-application-page"></a>Per codificare la pagina dell'applicazione

1. Scegliere il **nodo ApplicationPage1.aspx** e quindi nella barra dei menu scegliere Visualizza codice per visualizzare il codice dietro la  >   pagina dell'applicazione.

2. Sostituire le **istruzioni using** **o Import** (a seconda del linguaggio di programmazione) nella parte superiore della classe con quanto segue:

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
    > Assicurarsi di sostituire "TestServer" nel codice con il nome di un server valido che esegue SharePoint.

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione
 Determinare quindi se la pagina dell'applicazione visualizza correttamente i dati relativi alle spese.

#### <a name="to-test-the-application-page"></a>Per testare la pagina dell'applicazione

1. Scegliere il **tasto F5** per eseguire e distribuire il progetto in SharePoint.

2. Scegliere il **pulsante Home** e  quindi il collegamento Documenti condivisi sulla barra Avvio rapido per visualizzare l'elenco Documenti condivisi nel SharePoint sito.

3. Per rappresentare le note spese per questo esempio, caricare  alcuni nuovi documenti nell'elenco Documenti scegliendo il collegamento Documenti nella scheda **LibreriaStrumenti** nella parte superiore della pagina e quindi scegliendo il pulsante Documento Upload sulla barra **multifunzione** degli strumenti.

4. Dopo aver caricato alcuni documenti, creare  un'istanza del flusso di lavoro scegliendo il collegamento Libreria nella scheda **LibreriaStrumenti** nella parte superiore della pagina e quindi scegliendo il pulsante Libreria **Impostazioni** sulla barra multifunzione degli strumenti.

5. Nella pagina **Raccolta documenti Impostazioni** scegliere il collegamento Flusso di lavoro **Impostazioni** nella sezione **Autorizzazioni e** gestione.

6. Nella pagina **Flusso di Impostazioni** scegliere il collegamento Aggiungi flusso di **lavoro.**

7. Nella pagina **Aggiungi flusso di** lavoro scegliere il flusso di lavoro **ExpenseReport - Workflow1,** immettere un nome per il flusso di lavoro, ad esempio **ExpenseTest,** e quindi scegliere **il pulsante** Avanti.

    Verrà visualizzato il modulo Associazione del flusso di lavoro. Usarlo per segnalare l'importo del limite di spesa.

8. Nel modulo Associazione immettere **1000 nella** casella **Limite** approvazione automatica e quindi scegliere il **pulsante Associa flusso di** lavoro.

9. Scegliere il **pulsante Home** per tornare al SharePoint home page.

10. Scegliere il **collegamento Documenti** condivisi sulla barra Avvio rapido.

11. Scegliere uno dei documenti caricati per visualizzare una freccia a discesa, sceglierlo e quindi scegliere l'elemento **Flussi di** lavoro.

12. Scegliere l'immagine accanto a ExpenseTest per visualizzare il modulo di avvio del flusso di lavoro.

13. Nella casella **di testo Totale** spese immettere un valore maggiore di 1000 e quindi scegliere il pulsante Avvia flusso **di** lavoro.

     Quando una spesa segnalata supera l'importo della spesa allocata, viene aggiunta un'attività al Elenco attività. Viene aggiunta anche una colonna denominata **ExpenseTest** con **il valore Completed** all'elemento della nota spese nell'elenco Documenti condivisi.

14. Ripetere i passaggi da 11 a 13 con altri documenti nell'elenco Documenti condivisi. Il numero esatto di documenti non è importante.

15. Visualizzare la pagina dell'applicazione di riepilogo della nota spese aprendo l'URL seguente in un Web browser: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Nella pagina di riepilogo della nota spese sono elencate tutte le note spese che hanno superato l'importo allocato, l'importo che ha superato e l'importo totale per tutti i report.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sulle SharePoint dell'applicazione, vedere [Creare pagine dell'applicazione SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Per altre informazioni su come progettare SharePoint contenuto della pagina usando Visual Web Designer in Visual Studio argomenti seguenti:

- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creare controlli riutilizzabili per web part o pagine dell'applicazione.](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un flusso di lavoro con moduli di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Procedura: Creare una pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md)
- [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)