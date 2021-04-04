---
title: Aggiunta della ricerca a una finestra degli strumenti | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: ca1998b5ca3ad78b269c50244ddf51796c9e4005
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215526"
---
# <a name="add-search-to-a-tool-window"></a>Aggiungere la ricerca a una finestra degli strumenti
Quando si crea o si aggiorna una finestra degli strumenti nell'estensione, è possibile aggiungere la stessa funzionalità di ricerca visualizzata altrove in Visual Studio. Questa funzionalità include le funzionalità seguenti:

- Casella di ricerca che si trova sempre in un'area personalizzata della barra degli strumenti.

- Indicatore di stato sovrapposto alla casella di ricerca.

- La possibilità di visualizzare i risultati non appena si immette ogni carattere (Ricerca immediata) o solo dopo aver scelto il tasto **invio** (ricerca su richiesta).

- Elenco che mostra i termini per i quali è stata eseguita la ricerca più di recente.

- Possibilità di filtrare le ricerche in base a campi o aspetti specifici delle destinazioni di ricerca.

Seguendo questa procedura dettagliata, si apprenderà come eseguire le attività seguenti:

1. Creare un progetto VSPackage.

2. Creare una finestra degli strumenti contenente un UserControl con una casella di testo di sola lettura.

3. Aggiungere una casella di ricerca alla finestra degli strumenti.

4. Aggiungere l'implementazione della ricerca.

5. Abilitare la ricerca immediata e la visualizzazione di un indicatore di stato.

6. Aggiungere un'opzione **maiuscole/minuscole** .

7. Aggiungere un filtro **Cerca anche solo righe** .

## <a name="to-create-a-vsix-project"></a>Per creare un progetto VSIX

1. Creare un progetto VSIX denominato `TestToolWindowSearch` con una finestra degli strumenti denominata **TestSearch**. Per ulteriori informazioni, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Per creare una finestra degli strumenti

1. Nel `TestToolWindowSearch` progetto aprire il file *TestSearchControl. XAML* .

2. Sostituire il `<StackPanel>` blocco esistente con il blocco seguente, che aggiunge un oggetto di sola lettura <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.UserControl> nella finestra degli strumenti.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Nel file *TestSearchControl. XAML. cs* aggiungere la direttiva using seguente:

    ```csharp
    using System.Text;
    ```

4. Rimuovere il `button1_Click()` metodo.

     Nella classe **TestSearchControl** aggiungere il codice seguente.

     Questo codice aggiunge una <xref:System.Windows.Controls.TextBox> proprietà pubblica denominata **SearchResultsTextBox** e una proprietà di stringa pubblica denominata **SearchContent**. Nel costruttore, SearchResultsTextBox è impostato sulla casella di testo e SearchContent viene inizializzato su un set di stringhe delimitato da una nuova riga. Il contenuto della casella di testo viene anche inizializzato sul set di stringhe.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb" id="Snippet1":::

5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

6. Sulla barra dei menu scegliere **Visualizza**  >  **altre**  >  **TestSearch** Windows.

     Viene visualizzata la finestra degli strumenti, ma il controllo di ricerca non viene ancora visualizzato.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Per aggiungere una casella di ricerca alla finestra degli strumenti

1. Nel file *TestSearch. cs* aggiungere il codice seguente alla `TestSearch` classe. Il codice esegue l'override della <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Proprietà in modo che la funzione di accesso get restituisca `true` .

     Per abilitare la ricerca, è necessario eseguire l'override della <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Proprietà. La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> e fornisce un'implementazione predefinita che non Abilita la ricerca.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

3. Nell'istanza sperimentale di Visual Studio aprire **TestSearch**.

     Nella parte superiore della finestra degli strumenti viene visualizzato un controllo di ricerca con una filigrana di **ricerca** e un'icona di lente di ingrandimento. Tuttavia, la ricerca non funziona ancora perché il processo di ricerca non è stato implementato.

## <a name="to-add-the-search-implementation"></a>Per aggiungere l'implementazione della ricerca
 Quando si Abilita la ricerca in un oggetto <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , come nella procedura precedente, la finestra degli strumenti crea un host di ricerca. Questo host imposta e gestisce i processi di ricerca, che si verificano sempre in un thread in background. Poiché la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe gestisce la creazione dell'host di ricerca e l'impostazione della ricerca, è necessario creare solo un'attività di ricerca e fornire il metodo di ricerca. Il processo di ricerca si verifica in un thread in background e le chiamate al controllo della finestra degli strumenti si verificano nel thread dell'interfaccia utente. Pertanto, è necessario utilizzare il metodo [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) per gestire le chiamate effettuate durante la gestione del controllo.

1. Nel file *TestSearch. cs* aggiungere le `using` direttive seguenti:

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

2. Nella `TestSearch` classe aggiungere il codice seguente, che esegue le azioni seguenti:

    - Esegue l'override del <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodo per creare un'attività di ricerca.

    - Esegue l'override del <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodo per ripristinare lo stato della casella di testo. Questo metodo viene chiamato quando un utente annulla un'attività di ricerca e quando un utente imposta o Annulla l'impostazione delle opzioni o dei filtri. Sia <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> che <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> vengono chiamati sul thread UI. Non è quindi necessario accedere alla casella di testo tramite il metodo [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Crea una classe denominata `TestSearchTask` che eredita da <xref:Microsoft.VisualStudio.Shell.VsSearchTask> , che fornisce un'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         In `TestSearchTask` il costruttore imposta un campo privato che fa riferimento alla finestra degli strumenti. Per fornire il metodo di ricerca, è necessario eseguire l'override dei <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metodi e. Il <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> metodo è il punto in cui si implementa il processo di ricerca. Questo processo include l'esecuzione della ricerca, la visualizzazione dei risultati della ricerca nella casella di testo e la chiamata all'implementazione della classe di base di questo metodo per segnalare che la ricerca è stata completata.

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

3. Testare l'implementazione della ricerca attenendosi alla procedura seguente:

    1. Ricompilare il progetto e avviare il debug.

    2. Nell'istanza sperimentale di Visual Studio, aprire nuovamente la finestra degli strumenti, immettere un testo di ricerca nella finestra di ricerca e fare clic su **invio**.

         Verranno visualizzati i risultati corretti.

## <a name="to-customize-the-search-behavior"></a>Per personalizzare il comportamento di ricerca
 Modificando le impostazioni di ricerca, è possibile apportare diverse modifiche in modo che il controllo di ricerca appaia e come viene eseguita la ricerca. È ad esempio possibile modificare la filigrana, ovvero il testo predefinito visualizzato nella casella di ricerca, la larghezza minima e massima del controllo di ricerca e se visualizzare un indicatore di stato. È anche possibile modificare il punto in cui vengono visualizzati i risultati della ricerca (su richiesta o ricerca immediata) e se visualizzare un elenco di termini per i quali è stata eseguita una ricerca di recente. È possibile trovare l'elenco completo delle impostazioni nella <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> classe.

1. Nel file * TestSearch. cs * aggiungere il codice seguente alla `TestSearch` classe. Questo codice consente la ricerca immediata anziché la ricerca su richiesta, ovvero l'utente non deve fare clic su **invio**. Il codice esegue l'override del `ProvideSearchSettings` metodo nella `TestSearch` classe, che è necessario per modificare le impostazioni predefinite.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testare la nuova impostazione ricompilando la soluzione e riavviando il debugger.

     I risultati della ricerca vengono visualizzati ogni volta che si immette un carattere nella casella di ricerca.

3. Nel `ProvideSearchSettings` metodo aggiungere la riga seguente, che consente la visualizzazione di un indicatore di stato.

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

     Per visualizzare l'indicatore di stato, è necessario segnalare lo stato di avanzamento. Per segnalare lo stato di avanzamento, rimuovere il commento dal codice seguente nel `OnStartSearch` metodo della `TestSearchTask` classe:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Per rallentare l'elaborazione che l'indicatore di stato è visibile, rimuovere il commento dalla riga seguente nel `OnStartSearch` metodo della `TestSearchTask` classe:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testare le nuove impostazioni ricompilando la soluzione e iniziando a eseguire il debug.

     L'indicatore di stato viene visualizzato nella finestra di ricerca, come una riga blu sotto la casella di testo di ricerca, ogni volta che si esegue una ricerca.

## <a name="to-enable-users-to-refine-their-searches"></a>Per consentire agli utenti di affinare le ricerche
 È possibile consentire agli utenti di affinare le ricerche per mezzo di opzioni come il **case di corrispondenza** o la **parola intera**. Le opzioni possono essere booleane, che vengono visualizzate come caselle di controllo o comandi, che vengono visualizzati come pulsanti. Per questa procedura dettagliata, verrà creata un'opzione booleana.

1. Nel file *TestSearch. cs* aggiungere il codice seguente alla `TestSearch` classe. Il codice esegue l'override del `SearchOptionsEnum` metodo, che consente all'implementazione della ricerca di rilevare se una determinata opzione è attiva o disattivata. Il codice in `SearchOptionsEnum` aggiunge un'opzione per la corrispondenza tra maiuscole e minuscole e un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumeratore. L'opzione per la corrispondenza maiuscole e minuscole viene resa disponibile anche come `MatchCaseOption` Proprietà.

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

2. Nella `TestSearchTask` classe rimuovere il commento dalla riga seguente nel `OnStartSearch` Metodo:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testare l'opzione:

    1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    2. Nella finestra degli strumenti scegliere la freccia rivolta verso il basso sul lato destro della casella di testo.

         Viene visualizzata la casella di controllo **maiuscole/minuscole** .

    3. Selezionare la casella di controllo **maiuscole/minuscole** e quindi eseguire alcune ricerche.

## <a name="to-add-a-search-filter"></a>Per aggiungere un filtro di ricerca
 È possibile aggiungere filtri di ricerca che consentono agli utenti di affinare il set di destinazioni di ricerca. Ad esempio, è possibile filtrare i file in Esplora file in base alle date in cui sono stati modificati più di recente e alle relative estensioni di file. In questa procedura dettagliata verrà aggiunto un filtro solo per le righe. Quando l'utente sceglie tale filtro, l'host di ricerca aggiunge le stringhe specificate alla query di ricerca. È quindi possibile identificare queste stringhe all'interno del metodo di ricerca e filtrare le destinazioni di ricerca di conseguenza.

1. Nel file *TestSearch. cs* aggiungere il codice seguente alla `TestSearch` classe. Il codice implementa `SearchFiltersEnum` aggiungendo un oggetto <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> che specifica di filtrare i risultati della ricerca in modo da visualizzare solo le righe pari.

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

     A questo punto il controllo di ricerca Visualizza il filtro di ricerca `Search even lines only` . Quando l'utente sceglie il filtro, la stringa `lines:"even"` viene visualizzata nella casella di ricerca. Altri criteri di ricerca possono essere visualizzati contemporaneamente al filtro. Le stringhe di ricerca possono essere visualizzate prima del filtro, dopo il filtro o in entrambe.

2. Nel file *TestSearch. cs* aggiungere i metodi seguenti alla `TestSearchTask` classe, che si trova nella `TestSearch` classe. Questi metodi supportano il `OnStartSearch` metodo, che verrà modificato nel passaggio successivo.

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

3. Nella `TestSearchTask` classe aggiornare il `OnStartSearch` metodo con il codice seguente. Questa modifica aggiorna il codice per supportare il filtro.

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

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale di Visual Studio aprire la finestra degli strumenti, quindi fare clic sulla freccia verso il basso nel controllo di ricerca.

     Viene visualizzata la casella di controllo **maiuscole/minuscole** e il filtro **Cerca anche solo righe** .

6. Scegliere il filtro.

     La casella di ricerca contiene **righe: "even"** e vengono visualizzati i risultati seguenti:

     2 valido

     4 valido

     6 Arrivederci

7. Eliminare `lines:"even"` dalla casella di ricerca, selezionare la casella di controllo **maiuscole/minuscole** e quindi immettere `g` nella casella di ricerca.

     Vengono visualizzati i risultati seguenti:

     1 Vai

     2 valido

     5 addio

8. Scegliere la X sul lato destro della casella di ricerca.

     La ricerca viene cancellata e viene visualizzato il contenuto originale. Tuttavia, la casella di controllo **maiuscole/minuscole** è ancora selezionata.
