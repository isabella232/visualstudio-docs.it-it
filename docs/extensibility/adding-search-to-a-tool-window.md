---
title: Aggiunta di ricerca a una finestra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1d424b7af82a423b4d227b77cd77a63eba2559c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261310"
---
# <a name="add-search-to-a-tool-window"></a>Aggiungi ricerca di una finestra degli strumenti
Quando si creano o aggiorna una finestra degli strumenti nella propria estensione, è possibile aggiungere la stessa funzionalità di ricerca che viene visualizzato in un' posizione in Visual Studio. Questa funzionalità include le funzionalità seguenti:

- Una casella di ricerca che si trova sempre in un'area personalizzata della barra degli strumenti.

- Un indicatore di stato che la casella di ricerca è sovrapposti.

- La possibilità di visualizzare i risultati non appena si immette ogni carattere (ricerca immediata) o solo dopo aver scelto il **invio** chiave (ricerca su richiesta).

- Un elenco che mostra le condizioni per il quale è stata eseguita la ricerca più di recente.

- La possibilità di filtrare le ricerche da campi specifici o gli aspetti delle destinazioni di ricerca.

Seguendo questa procedura dettagliata, si apprenderà come eseguire le attività seguenti:

1. Creare un progetto di VSPackage.

2. Creare una finestra degli strumenti che contiene un elemento UserControl con una casella di testo di sola lettura.

3. Aggiungere una casella di ricerca alla finestra degli strumenti.

4. Aggiungere l'implementazione della ricerca.

5. Abilitare la funzionalità Ricerca immediata e la visualizzazione di un indicatore di stato.

6. Aggiungere un **maiuscole/minuscole** opzione.

7. Aggiungere un **eseguire la ricerca solo righe pari** filtro.

## <a name="to-create-a-vsix-project"></a>Per creare un progetto VSIX

1. Creare un progetto VSIX denominato `TestToolWindowSearch` con una finestra degli strumenti denominata **TestSearch**. Se occorre assistenza in questo modo, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Per creare una finestra degli strumenti

1. Nel `TestToolWindowSearch` progetto, aprire il *TestSearchControl.xaml* file.

2. Sostituire le attuali `<StackPanel>` blocco con il blocco seguente, che aggiunge una proprietà di sola lettura <xref:System.Windows.Controls.TextBox> per il <xref:System.Windows.Controls.UserControl> nella finestra degli strumenti.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Nel *TestSearchControl.xaml.cs* file, aggiungere la seguente istruzione using:

    ```csharp
    using System.Text;
    ```

4. Rimuovere il `button1_Click()` (metodo).

     Nel **TestSearchControl** classe, aggiungere il codice seguente.

     Questo codice aggiunge un pubblico <xref:System.Windows.Controls.TextBox> proprietà denominata **SearchResultsTextBox** e una proprietà di stringa pubblica denominata **SearchContent**. Nel costruttore, SearchResultsTextBox è impostato nella casella di testo e SearchContent viene inizializzato su un set di stringhe delimitato da nuova riga. Il contenuto della casella di testo viene anche inizializzato per l'insieme di stringhe.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

6. Nella barra dei menu, scegliere **View** > **Other Windows** > **TestSearch**.

     Verrà visualizzata la finestra degli strumenti, ma non viene ancora visualizzato il controllo di ricerca.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Per aggiungere una casella di ricerca alla finestra degli strumenti

1. Nel *TestSearch.cs* , aggiungere il codice seguente per il `TestSearch` classe. Il codice esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> proprietà in modo che la funzione di accesso get restituisce `true`.

     Per abilitare la ricerca, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> proprietà. Il <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> e fornisce un'implementazione predefinita che non consentono a ricerca.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

3. Nell'istanza sperimentale di Visual Studio, aprire **TestSearch**.

     Nella parte superiore della finestra degli strumenti, verrà visualizzato un controllo di ricerca con un **ricerca** filigrana e un'icona sulla lente di ingrandimento. Tuttavia, la ricerca non funziona ancora perché non è stato implementato il processo di ricerca.

## <a name="to-add-the-search-implementation"></a>Per aggiungere l'implementazione della ricerca
 Quando si abilita ricerca su un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, come nella procedura precedente, la finestra degli strumenti consente di creare un host di ricerca. Questo host configura e gestisce i processi di ricerca, che devono essere sempre eseguiti su un thread in background. Poiché il <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe gestisce la creazione di host di ricerca e l'impostazione di backup della ricerca, è necessario solo creare un'attività di ricerca e fornire il metodo di ricerca. Si verifica il processo di ricerca in un thread in background e le chiamate per il controllo di finestra degli strumenti si verificano nel thread dell'interfaccia utente. Pertanto, è necessario usare il [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metodo per gestire tutte le chiamate effettuate a gestire il controllo.

1. Nel *TestSearch.cs* del file, aggiungere il codice seguente `using` istruzioni:

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

2. Nel `TestSearch` classe, aggiungere il codice seguente, che esegue le azioni seguenti:

    - Esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodo per creare un'attività di ricerca.

    - Esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodo per ripristinare lo stato della casella di testo. Questo metodo viene chiamato quando un utente annulla un'attività di ricerca e quando un utente imposta o si deseleziona le opzioni o filtri. Entrambe <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> vengono chiamati sul thread UI. Pertanto, non è necessario accedere alla casella di testo tramite il [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) (metodo).

    - Crea una classe denominata `TestSearchTask` che eredita da <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, che fornisce un'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.

         In `TestSearchTask`, il costruttore imposta un campo privato che fa riferimento la finestra degli strumenti. Per fornire il metodo di ricerca, si esegue l'override di <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> e <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metodi. Il <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> metodo è dove si implementa il processo di ricerca. Questo processo include eseguendo la ricerca, la visualizzazione dei risultati di ricerca nella casella di testo e chiamare l'implementazione di classe di base di questo metodo per segnalare che la ricerca è stata completata.

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

    2. Nell'istanza sperimentale di Visual Studio, aprire la finestra degli strumenti di nuovo, immettere un testo di ricerca nella finestra di ricerca e fare clic su **invio**.

         Verrà visualizzato i risultati corretti.

## <a name="to-customize-the-search-behavior"></a>Per personalizzare il comportamento di ricerca
 Modificando le impostazioni di ricerca, è possibile apportare varie modifiche nel modo in cui viene visualizzato il controllo di ricerca e come viene eseguita la ricerca. Ad esempio, è possibile modificare la filigrana (il testo predefinito visualizzato nella casella di ricerca), il valore minimo e la larghezza massima del controllo di ricerca e se visualizzare un indicatore di stato. È anche possibile modificare il punto in cui risultati della ricerca avviare appaiano (su richiesta o la ricerca immediata) e se visualizzare un elenco di termini recentemente cercate. È possibile trovare l'elenco completo delle impostazioni di <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> classe.

1. Nel * TestSearch.cs*, aggiungere il codice seguente per il `TestSearch` classe. Questo codice consente a ricerca immediata invece di ricerca on demand (che significa che l'utente non dovrà fare clic su **invio**). Il codice esegue l'override di `ProvideSearchSettings` metodo nella `TestSearch` (classe), che è necessario modificare le impostazioni predefinite.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testare la nuova impostazione per la ricompilazione della soluzione e riavviare il debugger.

     I risultati della ricerca vengono visualizzati ogni volta che si immette un carattere nella casella di ricerca.

3. Nel `ProvideSearchSettings` metodo, aggiungere la riga seguente, che consente di visualizzare un indicatore di stato.

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

     Per l'indicatore di stato venga visualizzato, lo stato di avanzamento debba essere segnalato. Per segnalare lo stato di avanzamento, rimuovere il commento il codice seguente nel `OnStartSearch` metodo di `TestSearchTask` classe:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. A rallentare l'elaborazione sufficienti che lo stato di avanzamento barra è visibile, rimuovere il commento la riga seguente nel `OnStartSearch` metodo di `TestSearchTask` classe:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testare le nuove impostazioni per la ricompilazione della soluzione e avvio del debug.

     L'indicatore di stato viene visualizzato nella finestra di ricerca (come una linea blu sotto la casella di testo di ricerca) ogni volta che si esegue una ricerca.

## <a name="to-enable-users-to-refine-their-searches"></a>Consentire agli utenti di eseguire ricerche selettive
 È possibile consentire agli utenti di eseguire ricerche selettive tramite opzioni, ad esempio **maiuscole/minuscole** oppure **parola intera**. Opzioni possono essere booleane, che vengono visualizzati come caselle di controllo o i comandi, che vengono visualizzati come pulsanti. In questa procedura dettagliata si creerà un'opzione booleana.

1. Nel *TestSearch.cs* , aggiungere il codice seguente per il `TestSearch` classe. Il codice esegue l'override di `SearchOptionsEnum` metodo, che consente l'implementazione della ricerca rilevare se una determinata opzione è attivata o disattivata. Il codice nel `SearchOptionsEnum` aggiunge un'opzione per maiuscole/minuscole per un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumeratore. L'opzione per maiuscole/minuscole è disponibile anche come il `MatchCaseOption` proprietà.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. Nel `TestSearchTask` classe, rimuovere il commento dalla seguente riga nel `OnStartSearch` metodo:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. L'opzione di test:

    1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

    2. Nella finestra degli strumenti, scegliere la freccia verso il basso sul lato destro della casella di testo.

         Il **maiuscole/minuscole** verrà visualizzata la finestra di controllo.

    3. Selezionare il **maiuscole/minuscole** casella di controllo e quindi eseguire alcune ricerche.

## <a name="to-add-a-search-filter"></a>Per aggiungere un filtro di ricerca
 È possibile aggiungere filtri di ricerca che consentono agli utenti rifinire il set di destinazioni di ricerca. Ad esempio, è possibile filtrare i file in Esplora File per le date in cui sono stati modificati più di recente e relative estensioni. In questa procedura dettagliata, si aggiungerà un filtro anche solo per le righe. Quando l'utente sceglie il filtro, l'host di ricerca aggiunge le stringhe specificate per la query di ricerca. È quindi possibile identificare queste stringhe all'interno del metodo di ricerca e filtrare gli obiettivi di ricerca di conseguenza.

1. Nel *TestSearch.cs* , aggiungere il codice seguente per il `TestSearch` classe. Il codice implementa `SearchFiltersEnum` aggiungendo un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> che specifica per filtrare i risultati della ricerca in modo che vengano visualizzati solo righe pari.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Ora controllo di ricerca consente di visualizzare il filtro di ricerca `Search even lines only`. Quando l'utente sceglie il filtro, la stringa `lines:"even"` viene visualizzato nella casella di ricerca. Altri criteri di ricerca possono essere visualizzati allo stesso tempo come filtro. Le stringhe di ricerca possono apparire prima il filtro, dopo il filtro, o entrambi.

2. Nel *TestSearch.cs* , aggiungere i metodi seguenti per il `TestSearchTask` (classe), ovvero nel `TestSearch` classe. Questi metodi supportano il `OnStartSearch` (metodo), che verrà modificato nel passaggio successivo.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Nel `TestSearchTask` classe, aggiornare il `OnStartSearch` metodo con il codice seguente. Questa modifica aggiorna il codice per supportare il filtro.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale di Visual Studio, aprire la finestra degli strumenti e quindi scegliere la freccia di scorrimento nel controllo di ricerca.

     Il **maiuscole/minuscole** casella di controllo e il **Cerca solo righe pari** filtro vengono visualizzati.

6. Scegliere il filtro.

     Contiene la casella di ricerca **righe: "anche"** , e vengono visualizzati i risultati seguenti:

     buona 2

     4 good

     Addio 6

7. Eliminare `lines:"even"` dalla casella di ricerca, selezionare il **maiuscole/minuscole** casella di controllo e quindi immettere `g` nella casella di ricerca.

     Vengono visualizzati i risultati seguenti:

     passare a 1

     buona 2

     Addio 5

8. Scegliere la X a destra della casella di ricerca.

     La ricerca viene cancellata e il contenuto originale viene visualizzato. Tuttavia, il **maiuscole/minuscole** casella di controllo sia ancora selezionata.