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
ms.openlocfilehash: edb9cb30be9d62a533e6d011cbb8d0436ef898b1
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801607"
---
# <a name="use-code-analyzers"></a>Usare gli analizzatori di codice

Gli analizzatori di codice .NET Compiler Platform ("Roslyn") analizzano il codice C# o Visual Basic durante la digitazione. Ogni *diagnostica* o regola ha uno stato di gravità e di eliminazione predefinito che può essere sovrascritto per il progetto. In questo articolo viene illustrata l'impostazione della gravità della regola, l'utilizzo di set di regole e l'eliminazione di violazioni.

## <a name="analyzers-in-solution-explorer"></a>Analizzatori in Esplora soluzioni

È possibile eseguire gran parte della personalizzazione di diagnostica analizzatore da **Esplora soluzioni**. Se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, un nodo **analizzatori** viene visualizzato nel nodo **riferimenti** o **dipendenze** in **Esplora soluzioni**. Se si espande **analizzatori**e si espande uno degli assembly dell'analizzatore, vengono visualizzati tutti i dati diagnostici nell'assembly.

![Nodo analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, incluse la descrizione e la gravità predefinita, nella finestra **Proprietà** . Per visualizzare le proprietà, fare clic con il pulsante destro del mouse (oppure selezionare e mantenere) la regola e selezionare **Proprietà**oppure selezionare la regola e quindi premere **ALT** + **invio**.

![Proprietà di diagnostica in Finestra Proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione online per una diagnostica, fare clic con il pulsante destro del mouse (oppure selezionare e mantenere) la diagnostica e selezionare **Visualizza Guida**.

Le icone accanto a ogni diagnostica in **Esplora soluzioni** corrispondono alle icone visualizzate nel set di regole quando lo si apre nell'Editor:

- la "x" in un cerchio indica una [gravità](#rule-severity) dell' **errore**
- "!" in un triangolo indica una [gravità](#rule-severity) dell' **avviso**
- la "i" in un cerchio indica una [gravità](#rule-severity) delle **informazioni**
- la "i" in un cerchio su uno sfondo chiaro indica una [gravità](#rule-severity) **nascosta**
- la freccia rivolta verso il basso in un cerchio indica che la diagnostica è stata evitata

![Icone di diagnostica in Esplora soluzioni](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravità della regola

::: moniker range=">=vs-2019"

Se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, è possibile configurare la gravità delle regole dell'analizzatore o della *diagnostica*. A partire da Visual Studio 2019 versione 16,3, è possibile configurare la gravità di una regola [in un file EditorConfig](#set-rule-severity-in-an-editorconfig-file). È anche possibile modificare la gravità di una regola [da Esplora soluzioni](#set-rule-severity-from-solution-explorer) o [in un file del set di regole](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, è possibile configurare la gravità delle regole dell'analizzatore o della *diagnostica*. È possibile modificare la gravità di una regola [da Esplora soluzioni](#set-rule-severity-from-solution-explorer) o [in un file del set di regole](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

Nella tabella seguente vengono illustrate le diverse opzioni di gravità:

| Gravità (Esplora soluzioni) | Gravità (file EditorConfig) | Comportamento in fase di compilazione | Comportamento dell'editor |
|-|-|-|
| Errore | `error` | Le violazioni vengono visualizzate come *errori* nel elenco errori e nell'output di compilazione da riga di comando e causano l'esito negativo delle compilazioni.| Il codice che offende è sottolineato con una zigzag rossa e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate come *avvisi* nell'elenco errori e nell'output di compilazione da riga di comando, ma non comportano la mancata riuscita delle compilazioni. | Il codice offensivo è sottolineato con una zigzag verde e contrassegnato da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate come *messaggi* nell'elenco errori e non nell'output di compilazione da riga di comando. | Il codice che causa il danneggiamento è sottolineato con un zigzag grigio e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Nascosto | `silent` | Non visibile all'utente. | Non visibile all'utente. Tuttavia, la diagnostica viene segnalata al motore di diagnostica IDE. |
| nessuno | `none` | Eliminati completamente. | Eliminati completamente. |
| Predefinito | `default` | Corrisponde alla gravità predefinita della regola. Per determinare il valore predefinito di una regola, cercare nell'Finestra Proprietà. | Corrisponde alla gravità predefinita della regola. |

La schermata seguente dell'editor del codice mostra tre violazioni diverse con livelli di gravità diversi. Si noti il colore del zigzag e il piccolo quadrato colorato nella barra di scorrimento a destra.

![Violazione di errori, avvisi e informazioni nell'editor di codice](media/diagnostics-severity-colors.png)

Lo screenshot seguente mostra le stesse tre violazioni visualizzate nel Elenco errori:

![Violazione di errori, avvisi e informazioni in Elenco errori](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Impostare la gravità della regola in un file EditorConfig

(Visual Studio 2019 versione 16,3 e successive)

È possibile impostare la gravità per gli avvisi del compilatore o le regole dell'analizzatore in un file EditorConfig con la sintassi seguente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

L'impostazione della gravità di una regola in un file EditorConfig ha la precedenza su qualsiasi gravità impostata in un set di regole o in Esplora soluzioni. È possibile configurare [manualmente](#manually-configure-rule-severity) la gravità in un file EditorConfig o [automaticamente](#automatically-configure-rule-severity) tramite la lampadina visualizzata accanto a una violazione.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Imposta la gravità della regola di più regole dell'analizzatore in un file EditorConfig

(Visual Studio 2019 versione 16,5 e successive)

È possibile impostare la gravità per una categoria specifica di regole dell'analizzatore o per tutte le regole dell'analizzatore con una singola voce in un file EditorConfig.

- Impostare la gravità della regola per una categoria di regole dell'analizzatore:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Imposta gravità regola per tutte le regole dell'analizzatore:

`dotnet_analyzer_diagnostic.severity = <severity>`

Se sono presenti più voci applicabili a un ID di regola specifico, di seguito è riportato l'ordine di precedenza per scegliere la voce applicabile:

- La voce di gravità per una singola regola in base all'ID ha la precedenza sulla voce di gravità per una categoria.
- La voce di gravità per una categoria ha la precedenza sulla voce di gravità per tutte le regole dell'analizzatore.

Si consideri l'esempio EditorConfig seguente, dove [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) ha la categoria "performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Nell'esempio precedente, tutte e tre le voci sono applicabili a CA1822. Tuttavia, usando le regole di precedenza specificate, prevale la prima voce di gravità basata sull'ID della regola rispetto alle voci successive. In questo esempio, CA1822 avrà una gravità effettiva di "Error". Tutte le regole rimanenti con la categoria "performance" avranno la gravità "Warning". Tutte le regole dell'analizzatore rimanenti, che non hanno la categoria "performance", avranno un "suggerimento" di gravità.

#### <a name="manually-configure-rule-severity"></a>Configurare manualmente la gravità della regola

1. Se non si dispone già di un file EditorConfig per il progetto, [aggiungerne uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Aggiungere una voce per ogni regola che si desidera configurare con l'estensione di file corrispondente. Ad esempio, per impostare il livello di gravità per [CA1822](ca1822.md) su `error` per i file C#, la voce è simile alla seguente:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Per gli analizzatori in stile codice IDE, è anche possibile configurarli in un file EditorConfig usando una sintassi diversa, ad esempio `dotnet_style_qualification_for_field = false:suggestion` . Tuttavia, se si imposta una gravità usando la `dotnet_diagnostic` sintassi, avrà la precedenza. Per altre informazioni, vedere [convenzioni di lingua per EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Converte un file di RuleSet esistente nel file EditorConfig

A partire da Visual Studio 2019 versione 16,5, i file di RuleSet sono deprecati a favore del file EditorConfig per la configurazione dell'analizzatore per il codice gestito. La maggior parte degli strumenti di Visual Studio per la configurazione della gravità delle regole dell'analizzatore è stata aggiornata in modo da funzionare sui file EditorConfig anziché sui file di RuleSet. I file EditorConfig consentono di configurare sia le opzioni del livello di gravità delle regole dell'analizzatore, incluse le opzioni di stile del codice IDE di Visual Studio. Si consiglia vivamente di convertire il file di RuleSet esistente in un file EditorConfig. Si consiglia inoltre di salvare il file EditorConfig nella radice del repository o nella cartella della soluzione. Utilizzando la radice del repository o della cartella della soluzione, si verifica che le impostazioni di gravità di questo file vengano applicate automaticamente all'intero repository o alla soluzione, rispettivamente.

Esistono due modi per convertire un file di RuleSet esistente in un file EditorConfig:

- Dall'editor di RuleSet in Visual Studio (richiede Visual Studio 2019 16,5 o versione successiva). Se il progetto usa già un file di RuleSet specifico `CodeAnalysisRuleSet` , è possibile convertirlo in un file EditorConfig equivalente dall'editor di RuleSet in Visual Studio.

    1. Fare doppio clic sul file di RuleSet in Esplora soluzioni.

       Il file di RuleSet verrà aperto nell'editor di RuleSet. Nella parte superiore dell'editor di RuleSet dovrebbe essere visualizzata una **barra informazioni** su cui è possibile fare clic.

       ![Converti il set di regole in un file EditorConfig nell'editor di RuleSet](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Selezionare il collegamento **barra informazioni** .

       Verrà visualizzata una finestra di dialogo **Salva con nome** che consente di selezionare la directory in cui si desidera generare il file EditorConfig.

    3. Selezionare il pulsante **Salva** per generare il file EditorConfig.

       Il EditorConfig generato deve essere aperto nell'editor. Inoltre, la proprietà MSBuild `CodeAnalysisRuleSet` viene aggiornata nel file di progetto in modo che non faccia più riferimento al file di RuleSet originale.

- Dalla riga di comando:

    1. Installare il pacchetto NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Eseguire `RulesetToEditorconfigConverter.exe` dal pacchetto installato, con i percorsi del file di RuleSet e il file EditorConfig come argomenti della riga di comando.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Di seguito è riportato un esempio di file di RuleSet da convertire:

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

#### <a name="automatically-configure-rule-severity"></a>Configura automaticamente gravità regola

##### <a name="configure-from-light-bulb-menu"></a>Configura dal menu lampadina

Visual Studio offre un modo pratico per configurare la gravità di una regola dal menu della lampadina delle [azioni rapide](../ide/quick-actions.md) .

1. Dopo che si è verificata una violazione, passare il puntatore del mouse sulla violazione zigzag nell'editor e aprire il menu lampadina. In alternativa, posizionare il cursore sulla riga e premere **CTRL** + **.** (punto).

2. Dal menu lampadina selezionare **Configura o disattiva problemi** > **Configura \<rule ID> gravità**.

   ![Configurare la gravità della regola dal menu a bulbo chiaro in Visual Studio](media/configure-rule-severity.png)

3. Da qui, scegliere una delle opzioni di gravità.

   ![Configurare la gravità della regola come suggerimento](media/configure-rule-severity-suggestion.png)

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto, come illustrato nella casella Anteprima.

   > [!TIP]
   > Se non si dispone già di un file EditorConfig nel progetto, Visual Studio ne crea uno automaticamente.

##### <a name="configure-from-error-list"></a>Configura da elenco errori

Visual Studio offre anche un modo pratico per configurare la gravità di una regola dal menu di scelta rapida Elenco errori.

1. Dopo che si è verificata una violazione, fare clic con il pulsante destro del mouse (oppure selezionare e mantenere) la voce di diagnostica nell'elenco errori.

2. Dal menu di scelta rapida selezionare **imposta gravità**.

   ![Configurare la gravità della regola dall'elenco errori in Visual Studio](media/configure-rule-severity-error-list.png)

3. Da qui, scegliere una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto.

   > [!TIP]
   > Se non si dispone già di un file EditorConfig nel progetto, Visual Studio ne crea uno automaticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Imposta gravità regola da Esplora soluzioni

1. In Esplora soluzioni selezionare **References**  >  **analizzatori** di riferimenti (o **Dependencies**  >  **analizzatori** di dipendenze per i progetti .NET Core).

2. Espandere l'assembly che contiene la regola per la quale si desidera impostare la gravità.

::: moniker range=">=vs-2019"
3. Fare clic con il pulsante destro del mouse (oppure selezionare e mantenere) la regola e selezionare **imposta gravità**. Nel menu di scelta rapida scegliere una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto. Se il progetto usa un file di RuleSet anziché un file EditorConfig, la voce relativa alla gravità viene aggiunta al file di RuleSet.

   > [!TIP]
   > Se non si dispone già di un file EditorConfig o di un file di RuleSet nel progetto, Visual Studio crea automaticamente un nuovo file EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Fare clic con il pulsante destro del mouse (o selezionare e mantenere) la regola e selezionare **imposta gravità set di regole**. Nel menu di scelta rapida scegliere una delle opzioni di gravità.

   Il livello di gravità per la regola viene salvato nel file del set di regole attivo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Imposta gravità regola nel file del set di regole

![File del set di regole in Esplora soluzioni](media/ruleset-in-solution-explorer.png)

1. Aprire il file del set di regole attivo in uno dei modi seguenti:

- In **Esplora soluzioni**fare doppio clic sul file, fare clic con il pulsante destro del mouse ( **References**oppure selezionare e mantenere)  >  nodo**analizzatori** riferimenti e selezionare **Apri set di regole attive**.
- Nella pagina delle proprietà **analisi codice** per il progetto selezionare **Apri** .

  Se è la prima volta che si modifica il set di regole, Visual Studio crea una copia del file del set di regole predefinito, ne assegna il nome * \<projectname> . RuleSet*e lo aggiunge al progetto. Questo set di regole personalizzate diventa anche il set di regole attive per il progetto.

   > [!NOTE]
   > I progetti .NET Core e .NET Standard non supportano i comandi di menu per i set di regole in **Esplora soluzioni**, ad esempio **aprire il set di regole attive**. Per specificare un set di regole non predefinite per un progetto .NET Core o .NET Standard, [aggiungere manualmente la proprietà **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al file di progetto. È comunque possibile configurare le regole all'interno del set di regole nell'interfaccia utente dell'editor set di regole di Visual Studio.

1. Passare alla regola espandendo l'assembly contenitore.

1. Nella colonna **azione** selezionare il valore per aprire un elenco a discesa e scegliere la gravità desiderata nell'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configurare il codice generato

Gli analizzatori vengono eseguiti su tutti i file di origine in un progetto e segnalano violazioni. Queste violazioni, tuttavia, non sono utili per i file di codice generati, ad esempio i file di codice generati dalla finestra di progettazione, i file di origine temporanei generati dal sistema di compilazione e così via. Gli utenti non possono modificare manualmente questi file e/o non sono interessati alla correzione di violazioni in questi tipi di file generati da strumenti.

Per impostazione predefinita, il driver dell'analizzatore che esegue gli analizzatori considera i file con un nome specifico, un'estensione di file o un'intestazione di file generata automaticamente come file di codice generati. Ad esempio, un nome di file che termina con `.designer.cs` o `.generated.cs` viene considerato codice generato. Tuttavia, queste regole euristiche potrebbero non essere in grado di identificare tutti i file di codice generati personalizzati nel codice sorgente dell'utente.

A partire da Visual Studio 2019 16,5, gli utenti finali possono configurare file e/o cartelle specifici da considerare come codice generato in un [file EditorConfig](https://editorconfig.org/). Per aggiungere una configurazione di questo tipo, attenersi alla procedura seguente:

1. Se non si dispone già di un file EditorConfig per il progetto, [aggiungerne uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Aggiungere la `generated_code = true | false` voce per file e/o cartelle specifici. Ad esempio, per trattare tutti i file il cui nome termina con `.MyGenerated.cs` come codice generato, la voce sarà la seguente:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Non visualizzare le violazioni

Esistono diversi modi per eliminare le violazioni delle regole:

::: moniker range=">=vs-2019"

- In un **file EditorConfig**

  Impostare la gravità su `none` , ad esempio `dotnet_diagnostic.CA1822.severity = none` .

- Dal menu **analizza**

  Selezionare **analizza**  >  **compilazione ed evitare i problemi attivi** nella barra dei menu per disattivare tutte le violazioni correnti. Questa operazione viene a volte definita "baselining".

::: moniker-end

::: moniker range="vs-2017"

- Dal menu **analizza**

  Selezionare **analizza**  >  **Esegui analisi codice ed evitare i problemi attivi** nella barra dei menu per disattivare tutte le violazioni correnti. Questa operazione viene a volte definita "baselining".

::: moniker-end

- Da **Esplora soluzioni**

  Impostare la gravità della regola su **None**.

- Dall' **Editor set di regole**

  Deselezionare la casella di controllo accanto al nome o impostare **azione** su **nessuno**.

- Dall' **editor di codice**

  Posizionare il cursore nella riga di codice con la violazione e premere **CTRL** + **punto (.)** per aprire il menu **azioni rapide** . Selezionare **Elimina CAXXXX**  >  **nel file di origine/eliminazione**.

  ![Disattiva diagnostica dal menu azioni rapide](media/suppress-diagnostic-from-editor.png)

- Dal **Elenco errori**

  Scegliere le regole da escludere, quindi fare clic con il pulsante destro del mouse (oppure selezionare e mantenere) e selezionare **Elimina**  >  **in origine/file di eliminazione**.

  - Se si omette **in origine**, viene visualizzata la finestra di dialogo **Anteprima modifiche** con un'anteprima dell' [avviso #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) C# o Visual Basic la direttiva di [avviso #Disable](/dotnet/visual-basic/language-reference/directives/directives) aggiunta al codice sorgente.

    ![Anteprima dell'aggiunta di #pragma avviso nel file di codice](media/pragma-warning-preview.png)

  - Se si seleziona **in file di eliminazione**, viene visualizzata la finestra di dialogo **Anteprima modifiche** con un'anteprima dell' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo aggiunto al file di eliminazione globale.

    ![Anteprima dell'aggiunta dell'attributo SuppressMessage al file di eliminazione](media/preview-changes-in-suppression-file.png)

  Nella finestra di dialogo **Anteprima modifiche** selezionare **applica**.

  > [!NOTE]
  > Se non viene visualizzata l'opzione di menu non **visualizzare** in **Esplora soluzioni**, è probabile che la violazione provenga da compilazione e non da analisi in tempo reale. Il **Elenco errori** Visualizza la diagnostica, o le violazioni delle regole, dall'analisi del codice in tempo reale e dalla compilazione. Poiché la diagnostica di compilazione può essere obsoleta, ad esempio se è stato modificato il codice per correggere la violazione ma non è stata ricompilata, non è possibile eliminare questi dati diagnostici dal **Elenco errori**. I dati di diagnostica da analisi in tempo reale o IntelliSense sono sempre aggiornati con le origini correnti e possono essere eliminati dal **Elenco errori**. Per escludere la diagnostica di *compilazione* dalla selezione, impostare il filtro di origine **Elenco errori** da **compilazione e IntelliSense** **solo in IntelliSense**. Selezionare quindi la diagnostica che si vuole escludere e procedere come descritto in precedenza.
  >
  > ![Filtro di origine Elenco errori in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso della riga di comando

Quando si compila il progetto dalla riga di comando, le violazioni delle regole vengono visualizzate nell'output di compilazione se vengono soddisfatte le condizioni seguenti:

- Gli analizzatori vengono installati come pacchetto NuGet e non come estensione VSIX.

- Una o più regole sono violate nel codice del progetto.

- Il livello di [gravità](#rule-severity) di una regola violata è impostato su **warning**, nel qual caso le violazioni non causano errori di compilazione o **errore**, nel qual caso le violazioni causano errori di compilazione.

Il livello di dettaglio dell'output di compilazione non influisce sull'eventuale visualizzazione delle violazioni delle regole. Anche con il livello di dettaglio **silenzioso** , le violazioni delle regole vengono visualizzate nell'output di compilazione.

> [!TIP]
> Se si è abituati a eseguire l'analisi legacy dalla riga di comando, con *FxCopCmd.exe* o tramite MSBuild con il flag **RunCodeAnalysis** , di seguito viene illustrato come eseguire questa operazione con gli analizzatori di codice.

Per visualizzare le violazioni dell'analizzatore dalla riga di comando quando si compila il progetto usando MSBuild, eseguire un comando simile al seguente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Nell'immagine seguente viene illustrato l'output di compilazione da riga di comando della compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Progetti dipendenti

In un progetto .NET Core, se si aggiunge un riferimento a un progetto che include analizzatori NuGet, questi analizzatori vengono aggiunti automaticamente al progetto dipendente. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto di unit test, contrassegnare il pacchetto NuGet come privato nel file con *estensione csproj* o *VBPROJ* del progetto a cui si fa riferimento impostando l'attributo **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug dell'analizzatore del codice](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usare set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Non visualizzare gli avvisi di analisi codice](../code-quality/in-source-suppression-overview.md)
