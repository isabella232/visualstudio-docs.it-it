---
title: Aggiunta di Ricerca a una finestra degli strumenti | Microsoft Docs
description: Informazioni su come aggiungere funzionalità di ricerca, tra cui una casella di ricerca, un filtro e un indicatore di stato, a una finestra degli strumenti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 10dac90d0415aa030de48463d46acab1ae8de6ac
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439756"
---
# <a name="add-search-to-a-tool-window"></a>Aggiungere la ricerca a una finestra degli strumenti
Quando si crea o si aggiorna una finestra degli strumenti nell'estensione, è possibile aggiungere la stessa funzionalità di ricerca visualizzata altrove in Visual Studio. Questa funzionalità include le funzionalità seguenti:

- Casella di ricerca che si trova sempre in un'area personalizzata della barra degli strumenti.

- Indicatore di stato sovrapposto alla casella di ricerca stessa.

- Possibilità di visualizzare i risultati non appena si immette ogni carattere (ricerca immediata) o solo dopo aver scelto il tasto **INVIO** (ricerca su richiesta).

- Elenco che mostra i termini per cui è stata cercata l'ultima volta.

- Possibilità di filtrare le ricerche in base a campi o aspetti specifici delle destinazioni di ricerca.

Seguendo questa procedura dettagliata, si apprenderà come eseguire le attività seguenti:

1. Creare un progetto VSPackage.

2. Creare una finestra degli strumenti contenente un controllo UserControl con un controllo TextBox di sola lettura.

3. Aggiungere una casella di ricerca alla finestra degli strumenti.

4. Aggiungere l'implementazione della ricerca.

5. Abilitare la ricerca immediata e la visualizzazione di un indicatore di stato.

6. Aggiungere **un'opzione Maiuscole/minuscole.**

7. Aggiungere un **filtro Cerca solo righe** pari.

## <a name="to-create-a-vsix-project"></a>Per creare un progetto VSIX

1. Creare un progetto VSIX denominato `TestToolWindowSearch` con una finestra degli strumenti denominata **TestSearch**. Per assistenza, vedere Creazione [di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Per creare una finestra degli strumenti

1. Nel progetto `TestToolWindowSearch` aprire il file *TestSearchControl.xaml.*

2. Sostituire il blocco esistente con il blocco seguente, che aggiunge un oggetto di sola `<StackPanel>` lettura a nella finestra degli <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.UserControl> strumenti.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Nel file *TestSearchControl.xaml.cs* aggiungere la direttiva using seguente:

    ```csharp
    using System.Text;
    ```

4. Rimuovere il `button1_Click()` metodo .

     Nella classe **TestSearchControl** aggiungere il codice seguente.

     Questo codice aggiunge una proprietà <xref:System.Windows.Controls.TextBox> pubblica denominata **SearchResultsTextBox** e una proprietà di stringa pubblica denominata **SearchContent**. Nel costruttore SearchResultsTextBox è impostato sulla casella di testo e SearchContent viene inizializzato su un set di stringhe delimitato da nuova riga. Anche il contenuto della casella di testo viene inizializzato sul set di stringhe.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb" id="Snippet1":::

5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale Visual Studio.

6. Sulla barra dei menu scegliere **Visualizza**  >  **altro Windows**  >  **TestSearch**.

     Viene visualizzata la finestra degli strumenti, ma il controllo di ricerca non viene ancora visualizzato.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Per aggiungere una casella di ricerca alla finestra degli strumenti

1. Nel file *TestSearch.cs* aggiungere il codice seguente alla `TestSearch` classe . Il codice esegue l'override <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> della proprietà in modo che la funzione di accesso get restituisca `true` .

     Per abilitare la ricerca, è necessario eseguire l'override della <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> proprietà . La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe implementa e fornisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> un'implementazione predefinita che non abilita la ricerca.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

3. Nell'istanza sperimentale di Visual Studio aprire **TestSearch**.

     Nella parte superiore della finestra degli strumenti viene visualizzato un controllo di ricerca con **una** filigrana di ricerca e un'icona a forma di lente di ingrandimento. Tuttavia, la ricerca non funziona ancora perché il processo di ricerca non è stato implementato.

## <a name="to-add-the-search-implementation"></a>Per aggiungere l'implementazione della ricerca
 Quando si abilita la ricerca in <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> un , come nella procedura precedente, la finestra degli strumenti crea un host di ricerca. Questo host configura e gestisce i processi di ricerca, che si verificano sempre in un thread in background. Poiché la classe gestisce la creazione dell'host di ricerca e la configurazione della ricerca, è necessario creare solo un'attività di ricerca <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> e fornire il metodo di ricerca. Il processo di ricerca si verifica in un thread in background e le chiamate al controllo della finestra degli strumenti si verificano nel thread dell'interfaccia utente. Pertanto, è necessario usare il [metodo ThreadHelper.Invoke*](/previous-versions/visualstudio/visual-studio-2013/ee197798%28v%3dvs.120%29) per gestire tutte le chiamate effettuate nella gestione del controllo.

1. Nel file *TestSearch.cs* aggiungere le `using` direttive seguenti:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Nella classe `TestSearch` aggiungere il codice seguente, che esegue le azioni seguenti:

    - Esegue l'override <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> del metodo per creare un'attività di ricerca.

    - Esegue <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> l'override del metodo per ripristinare lo stato della casella di testo. Questo metodo viene chiamato quando un utente annulla un'attività di ricerca e quando un utente imposta o annulla le opzioni o i filtri. Sia <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> che vengono chiamati sul thread <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> dell'interfaccia utente. Pertanto, non è necessario accedere alla casella di testo tramite il [metodo ThreadHelper.Invoke*.](/previous-versions/visualstudio/visual-studio-2013/ee197798%28v%3dvs.120%29)

    - Crea una classe denominata che `TestSearchTask` eredita da , che fornisce <xref:Microsoft.VisualStudio.Shell.VsSearchTask> un'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         In `TestSearchTask` il costruttore imposta un campo privato che fa riferimento alla finestra degli strumenti. Per fornire il metodo di ricerca, eseguire l'override dei <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> metodi e <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> . Il <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> metodo consente di implementare il processo di ricerca. Questo processo include l'esecuzione della ricerca, la visualizzazione dei risultati della ricerca nella casella di testo e la chiamata all'implementazione della classe di base di questo metodo per segnalare che la ricerca è stata completata.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Testare l'implementazione della ricerca eseguendo la procedura seguente:

    1. Ricompilare il progetto e avviare il debug.

    2. Nell'istanza sperimentale di Visual Studio aprire di nuovo la finestra degli strumenti, immettere un testo di ricerca nella finestra di ricerca e fare clic su **INVIO.**

         Verranno visualizzati i risultati corretti.

## <a name="to-customize-the-search-behavior"></a>Per personalizzare il comportamento di ricerca
 Modificando le impostazioni di ricerca, è possibile apportare diverse modifiche alla modalità di visualizzazione del controllo di ricerca e al modo in cui viene eseguita la ricerca. Ad esempio, è possibile modificare la filigrana (il testo predefinito visualizzato nella casella di ricerca), la larghezza minima e massima del controllo di ricerca e se visualizzare un indicatore di stato. È anche possibile modificare il punto in cui iniziano a essere visualizzati i risultati della ricerca (su richiesta o ricerca immediata) e se visualizzare un elenco di termini per cui è stata cercata di recente. È possibile trovare l'elenco completo delle impostazioni nella <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> classe .

1. Nel file TestSearch.cs* aggiungere il codice seguente alla `TestSearch` classe . Questo codice abilita la ricerca immediata anziché la ricerca su richiesta, ovvero l'utente non deve fare clic su **INVIO.** Il codice esegue l'override del metodo nella classe , necessario `ProvideSearchSettings` per modificare le impostazioni `TestSearch` predefinite.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testare la nuova impostazione ricompilando la soluzione e riavviando il debugger.

     I risultati della ricerca vengono visualizzati ogni volta che si immette un carattere nella casella di ricerca.

3. Nel metodo `ProvideSearchSettings` aggiungere la riga seguente, che consente la visualizzazione di un indicatore di stato.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Per visualizzare l'indicatore di stato, è necessario segnalare lo stato di avanzamento. Per segnalare lo stato di avanzamento, rimuovere il commento dal codice seguente `OnStartSearch` nel metodo della classe `TestSearchTask` :

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Per rallentare l'elaborazione in modo che l'indicatore di stato sia visibile, rimuovere il commento dalla riga seguente `OnStartSearch` nel metodo della classe `TestSearchTask` :

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testare le nuove impostazioni ricompilando la soluzione e avviando il debug.

     L'indicatore di stato viene visualizzato nella finestra di ricerca (come riga blu sotto la casella di testo di ricerca) ogni volta che si esegue una ricerca.

## <a name="to-enable-users-to-refine-their-searches"></a>Per consentire agli utenti di perfezionare le ricerche
 È possibile consentire agli utenti di perfezionare le ricerche tramite opzioni come **Maiuscole/minuscole** **o Trova corrispondenza per parola intera.** Le opzioni possono essere booleane, visualizzate come caselle di controllo o comandi, che vengono visualizzate come pulsanti. Per questa procedura dettagliata si creerà un'opzione booleana.

1. Nel file *TestSearch.cs* aggiungere il codice seguente alla `TestSearch` classe . Il codice esegue l'override del metodo , che consente all'implementazione della ricerca di rilevare `SearchOptionsEnum` se una determinata opzione è attivata o disattivata. Il codice in `SearchOptionsEnum` aggiunge un'opzione per la corrispondenza tra maiuscole e minuscole a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumeratore. L'opzione per la corrispondenza tra maiuscole e minuscole viene resa disponibile anche come `MatchCaseOption` proprietà .

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. Nella classe `TestSearchTask` rimuovere il commento dalla riga seguente nel metodo `OnStartSearch` :

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testare l'opzione:

    1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    2. Nella finestra degli strumenti scegliere la freccia GIÙ sul lato destro della casella di testo.

         Verrà **visualizzata la casella di** controllo Maiuscole/minuscole.

    3. Selezionare la **casella di controllo** Maiuscole/minuscole e quindi eseguire alcune ricerche.

## <a name="to-add-a-search-filter"></a>Per aggiungere un filtro di ricerca
 È possibile aggiungere filtri di ricerca che consentono agli utenti di perfezionare il set di destinazioni di ricerca. Ad esempio, è possibile filtrare i file Esplora file in base alle date in cui sono stati modificati più di recente e alle relative estensioni di file. In questa procedura dettagliata si aggiungerà un filtro solo per le righe pari. Quando l'utente sceglie tale filtro, l'host di ricerca aggiunge le stringhe specificate alla query di ricerca. È quindi possibile identificare queste stringhe all'interno del metodo di ricerca e filtrare le destinazioni di ricerca di conseguenza.

1. Nel file *TestSearch.cs* aggiungere il codice seguente alla `TestSearch` classe . Il codice implementa `SearchFiltersEnum` aggiungendo un oggetto che specifica per filtrare i risultati della ricerca in modo che vengano visualizzate solo le righe <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> pari.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Il controllo di ricerca visualizza ora il filtro di ricerca `Search even lines only` . Quando l'utente sceglie il filtro, la stringa `lines:"even"` viene visualizzata nella casella di ricerca. Altri criteri di ricerca possono essere visualizzati contemporaneamente al filtro. Le stringhe di ricerca possono essere visualizzate prima del filtro, dopo il filtro o entrambe.

2. Nel file *TestSearch.cs* aggiungere i metodi seguenti alla `TestSearchTask` classe , che si trova nella classe `TestSearch` . Questi metodi `OnStartSearch` supportano il metodo , che verrà modificato nel passaggio successivo.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Nella classe `TestSearchTask` aggiornare il metodo con il codice `OnStartSearch` seguente. Questa modifica aggiorna il codice per supportare il filtro.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Testare il codice.

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale di Visual Studio aprire la finestra degli strumenti e quindi scegliere la freccia GIÙ nel controllo di ricerca.

     Vengono **visualizzati la casella di** controllo Maiuscole/minuscole e il filtro Cerca solo **righe** pari.

6. Scegliere il filtro.

     La casella di ricerca **contiene righe:"even"** e vengono visualizzati i risultati seguenti:

     2 buono

     4 Buono

     6 Arrivederci

7. Eliminare `lines:"even"` dalla casella di ricerca, selezionare la casella di controllo **Maiuscole/minuscole** e quindi immettere `g` nella casella di ricerca.

     Vengono visualizzati i risultati seguenti:

     1 go

     2 buono

     5 arrivederci

8. Scegliere la X sul lato destro della casella di ricerca.

     La ricerca viene cancellata e viene visualizzato il contenuto originale. Tuttavia, la **casella di controllo** Maiuscole/minuscole è ancora selezionata.
