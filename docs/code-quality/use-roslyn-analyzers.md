---
title: Gravità e eliminazione delle regole dell'analizzatore
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431410"
---
# <a name="use-code-analyzers"></a>Usare analizzatori di codiceUse code analyzers

Gli analizzatori di codice della piattaforma del compilatore .NET ("Roslyn") analizzano il codice di C o Visual Basic durante la digitazione. Ogni *diagnostica* o regola ha uno stato di gravità e eliminazione predefinito che può essere sovrascritto per il progetto. In questo articolo viene illustrata l'impostazione della gravità delle regole, l'utilizzo di set di regole e l'eliminazione delle violazioni.

## <a name="analyzers-in-solution-explorer"></a>Analizzatori in Esplora soluzioni

È possibile eseguire gran parte della personalizzazione della diagnostica dell'analizzatore da **Esplora soluzioni**. Se si [installano analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, nel nodo Riferimenti o **Dipendenze** verrà visualizzato un nodo **Dipendenze** in **Esplora soluzioni**. **References** Se si espande **Analyzers**, quindi si espande uno degli assembly dell'analizzatore, verrà visualizzata tutta la diagnostica nell'assembly.

![Nodo Analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, inclusa la descrizione e la gravità predefinita, nella finestra **Proprietà.You** can view the properties of a diagnostic, including its description and default severity, in the Properties window. Per visualizzare le proprietà, fare clic con il pulsante destro del mouse sulla regola e selezionare **Proprietà**oppure selezionare la regola e quindi premere **ALT**+**INVIO**.

![Proprietà diagnostiche nella finestra Proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione in linea per una diagnostica, fare clic con il pulsante destro del mouse sulla diagnostica e scegliere **Visualizza Guida**.

Le icone accanto a ogni diagnostica in **Esplora soluzioni** corrispondono alle icone visualizzate nel set di regole quando viene aperto nell'editor:

- la "x" in un cerchio indica una [gravità](#rule-severity) di **errore**
- il "!" in un triangolo indica una [gravità](#rule-severity) di **Avvertimento**
- la "i" in un cerchio indica una [gravità](#rule-severity) di **Info**
- la "i" in un cerchio su sfondo di colore **Hidden** chiaro indica una [gravità](#rule-severity)
- la freccia rivolta verso il basso in un cerchio indica che la diagnostica è soppressa

![Icone di diagnostica in Esplora soluzioniDiagnostics icons in Solution Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravità della regola

::: moniker range=">=vs-2019"

È possibile configurare la gravità delle regole dell'analizzatore, o *diagnostica,* se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet. A partire da Visual Studio 2019 versione 16.3, è possibile configurare la gravità di una regola [in un file EditorConfig](#set-rule-severity-in-an-editorconfig-file). È inoltre possibile modificare la gravità di una regola [da Esplora soluzioni](#set-rule-severity-from-solution-explorer) o in un file di set di [regole.](#set-rule-severity-in-the-rule-set-file)

::: moniker-end

::: moniker range="vs-2017"

È possibile configurare la gravità delle regole dell'analizzatore, o *diagnostica,* se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet. È possibile modificare la gravità di una regola [da Esplora soluzioni](#set-rule-severity-from-solution-explorer) o in un file di set di [regole.](#set-rule-severity-in-the-rule-set-file)

::: moniker-end

Nella tabella seguente vengono illustrate le diverse opzioni di gravità:The following table shows the different severity options:

| Gravità (Esplora soluzioni)Severity (Solution Explorer) | Gravità (file EditorConfig) | Comportamento in fase di compilazione | Comportamento dell'editor |
|-|-|-|
| Errore | `error` | Le violazioni vengono visualizzate come *errori* nell'elenco errori e nell'output di compilazione della riga di comando e causano l'esito negativo delle compilazioni.| Il codice offensivo è sottolineato con una sottolineatura ondulata rossa e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate come *avvisi* nell'elenco errori e nell'output di compilazione della riga di comando, ma non causano l'esito negativo delle compilazioni. | Il codice offensivo è sottolineato con una sottolineatura ondulata verde e contrassegnato da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate come *messaggi* nell'elenco errori e non nell'output di compilazione della riga di comando. | Il codice offensivo è sottolineato con una sottolineatura ondulata grigia e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Nascosto | `silent` | Non visibile all'utente. | Non visibile all'utente. La diagnostica viene tuttavia segnalata al motore di diagnostica IDE. |
| nessuno | `none` | Soppresso completamente. | Soppresso completamente. |
| Predefinito | `default` | Corrisponde alla gravità predefinita della regola. Per determinare il valore predefinito per una regola, cercare nella finestra Proprietà.To determine what the default value for a rule is, look in the Properties window. | Corrisponde alla gravità predefinita della regola. |

La schermata seguente dell'editor di codice mostra tre diverse violazioni con livelli di gravità diversi. Si noti il colore della scarabocchia e il piccolo quadrato colorato nella barra di scorrimento a destra.

![Violazione di errore, avviso e informazioni nell'editor di codice](media/diagnostics-severity-colors.png)

The following screenshot shows the same three violations as they appear in the Error List:

![Errore, avviso e violazione delle informazioni nell'elenco errori](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Impostare la gravità della regola in un file EditorConfigSet rule severity in an EditorConfig file

(Visual Studio 2019 versione 16.3 e successive)

È possibile impostare la gravità per gli avvisi del compilatore o le regole dell'analizzatore in un file EditorConfig con la sintassi seguente:You can set the severity for compiler warnings or analyzer rules in an EditorConfig file with the following syntax:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

L'impostazione della gravità di una regola in un file EditorConfig ha la precedenza su qualsiasi gravità impostata in un set di regole o in Esplora soluzioni. È possibile configurare [manualmente](#manually-configure-rule-severity) la gravità in un file EditorConfig o [automaticamente](#automatically-configure-rule-severity) tramite la lampadina visualizzata accanto a una violazione.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Impostare la gravità della regola di più regole dell'analizzatore contemporaneamente in un file EditorConfigSet rule severity of multiple analyzer rules at once in an EditorConfig file

(Visual Studio 2019 versione 16.5 e successive)

È possibile impostare la gravità per una categoria specifica di regole analizzatore o per tutte le regole dell'analizzatore con una singola voce in un file EditorConfig.You can set the severity for a specific category of analyzer rules or for all analyzer rules with a single entry in an EditorConfig file.

- Impostare la gravità della regola per una categoria di regole dell'analizzatore:Set rule severity for a category of analyzer rules:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Impostare la gravità della regola per tutte le regole dell'analizzatore:Set rule severity for all analyzer rules:

`dotnet_analyzer_diagnostic.severity = <severity>`

Se si dispone di più voci applicabili a un ID regola specifico, l'ordine di precedenza per scegliere la voce applicabile è il seguente:

- La voce di gravità per una singola regola in base all'ID ha la precedenza sulla voce di gravità per una categoria.
- La voce di gravità per una categoria ha la precedenza sulla voce di gravità per tutte le regole dell'analizzatore.

Si consideri il seguente esempio EditorConfig, in cui [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) ha la categoria "Performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Nell'esempio precedente, tutte e tre le voci sono applicabili a CA1822. Tuttavia, utilizzando le regole di precedenza specificate, la prima voce di gravità basata su ID regola vince sulle voci successive. In questo esempio, CA1822 avrà una gravità effettiva di "errore". Tutte le regole rimanenti con la categoria "Prestazioni" avranno la gravità "avviso". Tutte le restanti regole analizzatori, che non dispongono della categoria "Prestazioni", avranno un "suggerimento" di gravità.

#### <a name="manually-configure-rule-severity"></a>Configurare manualmente la gravità della regola

1. Se non si dispone già di un file EditorConfig per il progetto, [aggiungerne uno.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Aggiungere una voce per ogni regola che si desidera configurare con l'estensione di file corrispondente. Ad esempio, per impostare la gravità `error` per [CA1822](ca1822.md) su per i file C , la voce appare come segue:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Per gli analizzatori di codice IDE, è inoltre possibile configurarli in `dotnet_style_qualification_for_field = false:suggestion`un file EditorConfig utilizzando una sintassi diversa, ad esempio . Tuttavia, se si imposta `dotnet_diagnostic` una gravità utilizzando la sintassi, ha la precedenza. Per ulteriori informazioni, vedere [Convenzioni di linguaggio per EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertire un file set di regole esistente in file EditorConfig

A partire da Visual Studio 2019 versione 16.5, i file del set di regole sono deprecati a favore del file EditorConfig per la configurazione dell'analizzatore per il codice gestito. La maggior parte degli strumenti di Visual Studio per la configurazione di gravità della regola dell'analizzatore è stata aggiornata per funzionare sui file EditorConfig anziché sui file del set di regole. I file EditorConfig consentono di configurare sia i livelli di gravità delle regole dell'analizzatore che le opzioni dell'analizzatore, incluse le opzioni di stile del codice dell'IDE di Visual Studio.EditorConfig files allow you to configure both analyzer rule severities and analyzer options, including Visual Studio IDE code style options. È consigliabile convertire il file del set di regole esistente in un file EditorConfig. Si consiglia inoltre di salvare il file EditorConfig nella radice del repository o nella cartella della soluzione. Utilizzando la radice del repository o della cartella della soluzione, si garantisce che le impostazioni di gravità di questo file vengano applicate automaticamente rispettivamente all'intero repository o soluzione.

Esistono due modi per convertire un file del set di regole esistente in un file EditorConfig:There are a couple ways to convert an existing ruleset file to an EditorConfig file:

- Dall'Editor set di regole in Visual Studio (richiede Visual Studio 2019 16.5 o versione successiva). Se il progetto utilizza già un `CodeAnalysisRuleSet`file del set di regole specifico come relativo , è possibile convertirlo in un file EditorConfig equivalente dall'Editor set di regole all'interno di Visual Studio.

    1. Fare doppio clic sul file del set di regole in Esplora soluzioni.

       Il file del set di regole dovrebbe essere aperto nell'Editor set di regole. Dovresti vedere una **barra informazioni** selezionabile nella parte superiore dell'editor del set di regole.

       ![Convertire il set di regole in file EditorConfig nell'Editor set di regole](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Fare clic sul** collegamento della barra informazioni.

       Verrà visualizzata una finestra di dialogo **Salva** con nome che consente di selezionare la directory in cui si desidera generare il file EditorConfig.

    3. **Fare clic** sul pulsante **Salva** per generare il file EditorConfig.

       L'EditorConfig generato deve essere aperto nell'editor. Inoltre, la proprietà `CodeAnalysisRuleSet` MSBuild viene aggiornata nel file di progetto in modo che non faccia più riferimento al file del set di regole originale.

- Dalla riga di comando:

    1. Installare il pacchetto NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Eseguire `RulesetToEditorconfigConverter.exe` dal pacchetto installato, con percorsi al file del set di regole e file EditorConfig come argomenti della riga di comando.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Di seguito è riportato un file del set di regole di esempio da convertire:Here is an example ruleset file to convert:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Ecco il file EditorConfig convertito:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Configurare automaticamente la gravità della regola

##### <a name="configure-from-light-bulb-menu"></a>Configurare dal menu lampadina

Visual Studio fornisce un modo pratico per configurare la gravità di una regola dal menu lampadina [Azioni rapide.](../ide/quick-actions.md)

1. Dopo che si verifica una violazione, passa il mouse sopra la squiggle di violazione nell'editor e apri il menu della lampadina. In alternativa, posizionare il cursore sulla riga e premere **CTRL**+**.** (punto).

2. Dal menu lampadina, selezionare **Configura o Elimina problemi** > **Configura \<ID regola> gravità**.

   ![Configurare la gravità della regola dal menu lampadina in Visual StudioConfigure rule severity from light bulb menu in Visual Studio](media/configure-rule-severity.png)

3. Da lì, selezionare una delle opzioni di gravità.

   ![Configurare la gravità della regola come suggerimentoConfigure rule severity as Suggestion](media/configure-rule-severity-suggestion.png)

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto, come illustrato nella casella di anteprima.

   > [!TIP]
   > Se non si dispone già di un File EditorConfig nel progetto, Visual Studio ne crea uno automaticamente.

##### <a name="configure-from-error-list"></a>Configura dall'elenco degli errori

Visual Studio fornisce anche un modo pratico per configurare la gravità di una regola dal menu di scelta rapida dell'elenco errori.

1. Dopo che si verifica una violazione, fare clic con il pulsante destro del mouse sulla voce di diagnostica nell'elenco degli errori.

2. Dal menu di scelta rapida, selezionare **Imposta gravità**.

   ![Configurare la gravità della regola dall'elenco degli errori in Visual StudioConfigure rule severity from error list in Visual Studio](media/configure-rule-severity-error-list.png)

3. Da lì, selezionare una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto.

   > [!TIP]
   > Se non si dispone già di un File EditorConfig nel progetto, Visual Studio ne crea uno automaticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Impostare la gravità della regola da Esplora soluzioniSet rule severity from Solution Explorer

1. In Esplora soluzioni espandere**Analizzatori** **di riferimenti** > (o**Analizzatori** **dipendenze** > per progetti .NET Core).

2. Espandere l'assembly contenente la regola per la quale si desidera impostare la gravità.

::: moniker range=">=vs-2019"
3. Fare clic con il pulsante destro del mouse sulla regola e **scegliere Imposta gravità**. Nel menu di scelta rapida, selezionare una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto. Se il progetto utilizza un file del set di regole anziché un file EditorConfig, la voce di gravità viene aggiunta al file del set di regole.

   > [!TIP]
   > Se non si dispone già di un file EditorConfig o di un file di set di regole nel progetto, Visual Studio crea automaticamente un nuovo file EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Fare clic con il pulsante destro del mouse sulla regola e **selezionare Imposta gravità set di**regole . Nel menu di scelta rapida, selezionare una delle opzioni di gravità.

   La gravità della regola viene salvata nel file del set di regole attivo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Impostare la gravità della regola nel file del set di regoleSet rule severity in the rule set file

![File del set di regole in Esplora soluzioni](media/ruleset-in-solution-explorer.png)

1. Aprire il file del set di regole attivo facendo doppio clic su di esso in **Esplora soluzioni**, selezionando **Apri set** di regole attivo dal menu di scelta rapida del **References** > nodo**Analizzatori** riferimenti oppure selezionando **Apri** nella pagina delle proprietà **Analisi codice** per il progetto.

   Se è la prima volta che si modifica il set di regole, Visual Studio * \<* crea una copia del file del set di regole predefinito, lo denomina nomeprogetto>set di regole e lo aggiunge al progetto. Questo set di regole personalizzate diventa anche il set di regole attivo per il progetto.

   > [!NOTE]
   > I progetti .NET Core e .NET Standard non supportano i comandi di menu per i set di regole in **Esplora soluzioni,** ad esempio Apri set di **regole attive**. Per specificare un set di regole non predefinite per un progetto .NET Core o .NET Standard, aggiungere manualmente [la proprietà **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al file di progetto. È comunque possibile configurare le regole all'interno del set di regole nell'interfaccia utente dell'editor del set di regole di Visual Studio.You can still configure the rules within the rule set in the Visual Studio rule set editor UI.

1. Passare alla regola espandendo l'assembly che lo contiene.

1. Nella colonna **Azione** selezionare il valore per aprire un elenco a discesa e selezionare la gravità desiderata dall'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Eliminazione delle violazioni

Esistono diversi modi per eliminare le violazioni delle regole:There are multiple ways to suppress rule violations:

::: moniker range=">=vs-2019"

- In un **file EditorConfig**

  Impostare il `none`livello di `dotnet_diagnostic.CA1822.severity = none`gravità su , ad esempio .

- Dal menu **Analizza**

  Selezionare **Analizza compilazione** > **ed elimina problemi attivi** sulla barra dei menu per eliminare tutte le violazioni correnti. Questo è a volte indicato come "baselining".

::: moniker-end

::: moniker range="vs-2017"

- Dal menu **Analizza**

  Selezionare **Analizza** > analisi codice di esecuzione**ed Elimina problemi attivi** sulla barra dei menu per eliminare tutte le violazioni correnti. Questo è a volte indicato come "baselining".

::: moniker-end

- Da **Esplora soluzioni**

  Impostare la gravità della regola su **Nessuno**.

- **Dall'editor** del set di regole

  Deselezionare la casella accanto al nome o **impostare** **Azione** su Nessuno .

- **Dall'editor di codice**

  Posizionare il cursore nella riga di codice con la violazione e premere **Ctrl**+**Periodo (.)** per aprire il menu Azioni **rapide.** Selezionare **Elimina CAXXXX** > **in Origine/in File di sospensione**.

  ![Elimina la diagnostica dal menu delle azioni rapide](media/suppress-diagnostic-from-editor.png)

- **Dall'elenco degli errori**

  Selezionare le regole che si desidera eliminare, quindi fare clic con il pulsante destro del mouse e selezionare **Sopprimi** > nel file**di eliminazione/In di soppressione**.

  - Se si elimina **in Origine**, viene visualizzata la finestra di dialogo **Anteprima modifiche** con un'anteprima della direttiva di avviso [di c'è #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable](/dotnet/visual-basic/language-reference/directives/directives) che viene aggiunta al codice sorgente.

    ![Anteprima dell'aggiunta di avvisi di #pragma nel file di codice](media/pragma-warning-preview.png)

  - Se si seleziona **In File di soppressione**, viene <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> visualizzata la finestra di dialogo Anteprima **modifiche** con un'anteprima dell'attributo aggiunto al file delle eliminazioni globali.

    ![Anteprima dell'aggiunta dell'attributo SuppressMessage al file di eliminazione](media/preview-changes-in-suppression-file.png)

  Nella finestra di dialogo **Anteprima modifiche,** selezionare **Applica**.

  > [!NOTE]
  > Se l'opzione di menu **Elimina** non è visualizzata in **Esplora soluzioni**, è probabile che la violazione provenga dalla compilazione e non dall'analisi in tempo reale. **L'Elenco errori** visualizza la diagnostica, o violazioni delle regole, sia dall'analisi del codice in tempo reale che dalla compilazione. Poiché la diagnostica di compilazione può essere obsoleta, ad esempio, se il codice è stato modificato per correggere la violazione ma non è stato ricompilato, non è possibile eliminare questi dati diagnostica **dall'elenco errori**. La diagnostica dall'analisi in tempo reale, o IntelliSense, è sempre aggiornata con le origini correnti e può essere eliminata **dall'elenco errori**. Per escludere la diagnostica di *compilazione* dalla selezione, impostare il filtro di origine **Elenco errori** da **Compilazione e IntelliSense** **a Solo IntelliSense**. Quindi, selezionare la diagnostica che si desidera eliminare e procedere come descritto in precedenza.
  >
  > ![Filtro di origine Elenco errori in Visual StudioError List source filter in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Utilizzo della riga di comando

Quando si compila il progetto dalla riga di comando, le violazioni delle regole vengono visualizzate nell'output di compilazione se vengono soddisfatte le condizioni seguenti:When you build your project at the command line, rule violations appear in the build output if the following conditions are met:

- Gli analizzatori vengono installati come pacchetto NuGet e non come estensione VSIX.

- Una o più regole vengono violate nel codice del progetto.

- La [gravità](#rule-severity) di una regola violata è impostata su **avviso**, nel qual caso le violazioni non causano l'esito negativo della compilazione o un **errore**, nel qual caso le violazioni causano l'esito negativo della compilazione.

Il livello di dettaglio dell'output di compilazione non influisce sulla visualizzazione delle violazioni delle regole. Anche con un livello di dettaglio **non interattivo,** le violazioni delle regole vengono visualizzate nell'output di compilazione.

> [!TIP]
> Se sei abituato a eseguire l'analisi legacy dalla riga di comando, con *FxCopCmd.exe* o tramite msbuild con il flag **RunCodeAnalysis,** ecco come farlo con analizzatori di codice.

Per visualizzare le violazioni dell'analizzatore nella riga di comando quando si compila il progetto utilizzando msbuild, eseguire un comando simile al seguente:To see analyzer violations at the command line when you build your project using msbuild, run a command like this:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L'immagine seguente mostra l'output di compilazione da riga di comando dalla compilazione di un progetto che contiene una violazione della regola dell'analizzatore:The following image shows the command-line build output from building a project that contains an analyzer rule violation:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Progetti dipendenti

In un progetto .NET Core, se si aggiunge un riferimento a un progetto con analizzatori NuGet, tali analizzatori vengono aggiunti automaticamente anche al progetto dipendente. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto di unit test, contrassegnare il pacchetto NuGet come privato nel file *con estensione csproj* o *vbproj* del progetto a cui si fa riferimento impostando l'attributo **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual StudioOverview of code analyzers in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug dell'analizzatore di codiceSubmit a code analyzer bug](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utilizzare i set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Eliminare gli avvisi dell'analisi del codice](../code-quality/in-source-suppression-overview.md)
