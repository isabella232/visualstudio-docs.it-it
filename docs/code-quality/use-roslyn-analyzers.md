---
title: Configurazione analizzatore
ms.date: 05/10/2021
description: Informazioni su come personalizzare le regole dell'analizzatore Roslyn. Informazioni su come modificare i livelli di gravità dell'analizzatore, eliminare le violazioni e designare i file come codice generato.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973382"
---
# <a name="overview"></a>Panoramica

Ogni diagnostica o  regola dell'analizzatore Roslyn ha uno stato di gravità ed eliminazione predefinito che può essere sovrascritto e personalizzato per il progetto. Questo articolo illustra l'impostazione dei livelli di gravità dell'analizzatore e l'eliminazione delle violazioni dell'analizzatore.

## <a name="configure-severity-levels"></a>Configurare i livelli di gravità

::: moniker range=">=vs-2019"

A partire da Visual Studio 2019 versione 16.3, è possibile configurare la gravità delle regole dell'analizzatore, o *diagnostica,* in un [file EditorConfig](#set-rule-severity-in-an-editorconfig-file), dal [menu](#set-rule-severity-from-the-light-bulb-menu)lampadina e dall'elenco degli errori.

::: moniker-end

::: moniker range="vs-2017"

È possibile configurare la gravità delle regole dell'analizzatore, o *diagnostica,* se si installano gli [analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet. È possibile modificare la gravità di una regola da [Esplora soluzioni](#set-rule-severity-from-solution-explorer) [o in un file del set di regole](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

La tabella seguente illustra le diverse opzioni di gravità:

| Gravità (Esplora soluzioni) | Gravità (file EditorConfig) | Comportamento in fase di compilazione | Comportamento dell'editor |
|-|-|-|
| Errore | `error` | Le violazioni vengono visualizzate come *errori* nell'elenco errori e nell'output di compilazione della riga di comando e causano l'esito negativo delle compilazioni.| Il codice danneggiato è sottolineato da una sottolineatura ondulata rossa e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate come *avvisi* nell'elenco errori e nell'output di compilazione della riga di comando, ma non causano errori nelle compilazioni. | Il codice danneggiato è sottolineato da una sottolineatura ondulata verde e contrassegnato da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate *come messaggi* nell'elenco errori e non nell'output di compilazione della riga di comando. | Il codice danneggiato è sottolineato da una sottolineatura ondulata grigia e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Nascosto | `silent` | Non visibile all'utente. | Non visibile all'utente. La diagnostica viene tuttavia segnalata al motore di diagnostica IDE. |
| Nessuno | `none` | Eliminato completamente. | Eliminato completamente. |
| Predefinito | `default` | Corrisponde alla gravità predefinita della regola. Per determinare qual è il valore predefinito per una regola, cercare nella Finestra Proprietà. | Corrisponde alla gravità predefinita della regola. |

Se le violazioni delle regole vengono trovate da un analizzatore,  vengono segnalate nell'editor di codice (come a forma di antessamento sotto il codice in errore) e nella finestra Elenco errori.

Le violazioni dell'analizzatore segnalate nell'elenco errori corrispondono all'impostazione del livello [di gravità](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) della regola. Le violazioni dell'analizzatore vengono inoltre mostrate nell'editor di codice sotto il codice in errore. L'immagine seguente mostra tre violazioni: un errore &mdash; (arrotolamento), un avviso (arrotola verde) e un suggerimento (tre punti grigi):

![Aquiggles nell'editor di codice in Visual Studio](media/diagnostics-severity-colors.png)

Lo screenshot seguente mostra le stesse tre violazioni visualizzate nell'Elenco errori:

![Violazione di errori, avvisi e informazioni nell'elenco errori](media/diagnostics-severities-in-error-list.png)

Molte regole dell'analizzatore, *o diagnostica,* hanno una o più correzioni di codice *associate* che è possibile applicare per correggere la violazione della regola. Le correzioni del codice vengono visualizzate nel menu con l'icona a forma di lampadina insieme ad altri tipi di [azioni rapide](../ide/quick-actions.md). Per informazioni su queste correzioni del codice, vedere [Azioni rapide comuni](../ide/quick-actions.md).

![Violazione dell'analizzatore e correzione del codice tramite azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Gravità 'Hidden' e 'None'

`Hidden` Le regole di gravità abilitate per impostazione predefinita sono diverse dalle regole di gravità o `None` disabilitate in due modi.

- Se è stata registrata una correzione del codice per una regola di gravità, la correzione viene offerta come azione di refactoring del codice lampadina in Visual Studio, anche se la diagnostica nascosta non è visibile `Hidden` all'utente. Questo non è il caso delle regole di `None` gravità disabilitate.
- `Hidden` Le regole di gravità possono essere configurate in blocco dalle voci che impostano la gravità delle regole di più regole dell'analizzatore [contemporaneamente in un file EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` Le regole di gravità non possono essere configurate in questo modo. Devono invece essere configurate tramite voci che impostano la gravità della regola in un [file EditorConfig per ogni ID regola](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Impostare la gravità della regola in un file EditorConfig

(Visual Studio 2019 versione 16.3 e successive)

È possibile impostare la gravità per gli avvisi del compilatore o le regole dell'analizzatore in un file EditorConfig con la sintassi seguente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

L'impostazione della gravità di una regola in un file EditorConfig ha la precedenza su qualsiasi gravità impostata in un set di regole o in Esplora soluzioni. È possibile [configurare manualmente](#manually-configure-rule-severity-in-an-editorconfig-file) la gravità [](#set-rule-severity-from-the-light-bulb-menu) in un file EditorConfig o automaticamente tramite la lampadina visualizzata accanto a una violazione.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Impostare la gravità delle regole di più regole dell'analizzatore contemporaneamente in un file EditorConfig

(Visual Studio 2019 versione 16.5 e successive)

È possibile impostare la gravità per una categoria specifica di regole dell'analizzatore o per tutte le regole dell'analizzatore con una singola voce in un file EditorConfig.

- Impostare la gravità della regola per una categoria di regole dell'analizzatore:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Impostare la gravità della regola per tutte le regole dell'analizzatore:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Le voci per configurare più regole dell'analizzatore contemporaneamente si applicano solo alle regole *abilitate per impostazione predefinita.* Le regole dell'analizzatore contrassegnate come disabilitate per impostazione predefinita nel pacchetto dell'analizzatore devono essere abilitate `dotnet_diagnostic.<rule ID>.severity = <severity>` tramite voci esplicite.

Se sono presenti più voci applicabili a un ID regola specifico, di seguito è riportato l'ordine di precedenza per scegliere la voce applicabile:

- La voce relativa alla gravità per una singola regola in base all'ID ha la precedenza sulla voce di gravità per una categoria.
- La voce relativa alla gravità per una categoria ha la precedenza sulla voce di gravità per tutte le regole dell'analizzatore.

Si consideri l'esempio di EditorConfig seguente, in [cui CA1822 ha](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) la categoria "Performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Nell'esempio precedente tutte e tre le voci sono applicabili a CA1822. Tuttavia, usando le regole di precedenza specificate, la prima voce di gravità basata su ID regola ha la precedenza sulle voci seguenti. In questo esempio, CA1822 avrà una gravità effettiva di "errore". Tutte le regole rimanenti con la categoria "Prestazioni" avranno la gravità "avviso". Tutte le regole dell'analizzatore rimanenti, che non hanno la categoria "Prestazioni", avranno la gravità "suggerimento".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Configurare manualmente la gravità della regola in un file EditorConfig

1. Se non si ha già un file EditorConfig per il progetto, [aggiungerne uno.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Aggiungere una voce per ogni regola che si vuole configurare con l'estensione di file corrispondente. Ad esempio, per impostare la gravità per [CA1822 su](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) per i file `error` C#, la voce ha l'aspetto seguente:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Per gli analizzatori di tipo codice IDE, è anche possibile configurarli in un file EditorConfig usando una sintassi diversa, ad esempio `dotnet_style_qualification_for_field = false:suggestion` . Tuttavia, se si imposta una gravità usando la `dotnet_diagnostic` sintassi, ha la precedenza. Per altre informazioni, vedere [Convenzioni del linguaggio per EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Impostare la gravità della regola dal menu lampadina

Visual Studio modo pratico per configurare la gravità di una regola dal menu della lampadina [Azioni](../ide/quick-actions.md) rapide.

1. Dopo che si verifica una violazione, passare il puntatore del mouse sulla barra a comparsa della violazione nell'editor e aprire il menu lampadina. In caso contrario, posizionare il cursore sulla riga e premere + **CTRL.** (punto).

2. Dal menu lampadina selezionare Configura o **Elimina** problemi > **Configurare la \<rule ID> gravità.**

   ![Configurare la gravità della regola dal menu lampadina in Visual Studio](media/configure-rule-severity.png)

3. Da qui scegliere una delle opzioni di gravità.

   ![Configurare la gravità della regola come Suggerimento](media/configure-rule-severity-suggestion.png)

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto, come illustrato nella casella di anteprima.

   > [!TIP]
   > Se nel progetto non è già presente un file EditorConfig, Visual Studio crearne uno automaticamente.

### <a name="set-rule-severity-from-the-error-list-window"></a>Impostare la gravità della regola dalla finestra Elenco errori

Visual Studio offre anche un modo pratico per configurare la gravità di una regola dal menu di scelta rapida dell'elenco errori.

1. Quando si verifica una violazione, fare clic con il pulsante destro del mouse sulla voce di diagnostica nell'elenco errori.

2. Scegliere Imposta gravità dal menu **di scelta rapida.**

   ![Configurare la gravità della regola dall'elenco errori in Visual Studio](media/configure-rule-severity-error-list.png)

3. Da qui scegliere una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto.

   > [!TIP]
   > Se nel progetto non è già presente un file EditorConfig, Visual Studio crearne uno automaticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Impostare la gravità della regola Esplora soluzioni

È possibile eseguire gran parte della personalizzazione della diagnostica dell'analizzatore **Esplora soluzioni**. Se si [installano gli](../code-quality/install-roslyn-analyzers.md) analizzatori  come pacchetto NuGet,  viene visualizzato un nodo Analizzatori nel nodo Riferimenti o  **Dipendenze** in Esplora soluzioni . Se si espande **Analizzatori** e quindi si espande uno degli assembly dell'analizzatore, vengono visualizzati tutti i dati di diagnostica nell'assembly.

![Nodo Analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, incluse la descrizione e la gravità predefinita, nella **finestra** Proprietà. Per visualizzare le proprietà, fare clic con il pulsante destro del mouse sulla regola e scegliere Proprietà **oppure** selezionare la regola e quindi premere **ALT** + **INVIO.**

![Proprietà di diagnostica in Finestra Proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione online per una diagnostica, fare clic con il pulsante destro del mouse sulla diagnostica e **scegliere Visualizza Guida.**

Le icone accanto a ogni diagnostica in **Esplora soluzioni** corrispondono alle icone visualizzate nel set di regole quando lo si apre nell'editor:

- la "x" in un cerchio indica una [gravità dell'errore](#configure-severity-levels) 
- "!" in un triangolo indica una [gravità di](#configure-severity-levels) **avviso**
- la "i" in un cerchio indica una [gravità di](#configure-severity-levels) **Info**
- la "i" in un cerchio su uno sfondo di colore chiaro indica una [gravità](#configure-severity-levels) **nascosta**
- la freccia rivolta verso il basso in un cerchio indica che la diagnostica viene eliminata

![Icone di diagnostica in Esplora soluzioni](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertire un file del set di regole esistente in un file EditorConfig

A partire Visual Studio 2019 versione 16.5, i file del set di regole sono deprecati a favore del file EditorConfig per la configurazione dell'analizzatore per il codice gestito. La maggior parte degli strumenti Visual Studio per la configurazione della gravità delle regole dell'analizzatore è stata aggiornata per funzionare sui file EditorConfig anziché sui file del set di regole. I file EditorConfig consentono di configurare sia i livelli di gravità delle regole dell'analizzatore che le opzioni dell'analizzatore, Visual Studio di stile del codice IDE. È consigliabile convertire il file del set di regole esistente in un file EditorConfig. È anche consigliabile salvare il file EditorConfig nella radice del repo o nella cartella della soluzione. Usando la radice del repo o della cartella della soluzione, assicurarsi che le impostazioni di gravità di questo file siano applicate automaticamente rispettivamente all'intero repo o soluzione.

Esistono due modi per convertire un file del set di regole esistente in un file EditorConfig:

- Dall'editor del set di regole in Visual Studio (richiede Visual Studio 2019 16.5 o versione successiva). Se il progetto usa già un file del set di regole specifico come , è possibile convertirlo in un file EditorConfig equivalente dall'editor del set di regole all'interno `CodeAnalysisRuleSet` Visual Studio.

    1. Fare doppio clic sul file del set di regole in Esplora soluzioni.

       Il file del set di regole dovrebbe essere aperto nell'editor del set di regole. Nella parte superiore dell'editor **del** set di regole dovrebbe essere visualizzata una barra informazioni selezionabile.

       ![Convertire un set di regole in un file EditorConfig nell'editor del set di regole](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Selezionare il **collegamento alla barra** informazioni.

       Verrà visualizzata una **finestra di dialogo** Salva con nome che consente di selezionare la directory in cui si vuole generare il file EditorConfig.

    3. Selezionare il **pulsante Salva** per generare il file EditorConfig.

       L'editorConfig generato dovrebbe essere aperto nell'editor. Inoltre, la proprietà MSBuild viene aggiornata nel file di progetto in modo che non faccia `CodeAnalysisRuleSet` più riferimento al file del set di regole originale.

- Dalla riga di comando:

    1. Installare il pacchetto NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Eseguire `RulesetToEditorconfigConverter.exe` dal pacchetto installato, con i percorsi del file del set di regole e del file EditorConfig come argomenti della riga di comando.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Di seguito è riportato un file del set di regole di esempio da convertire:

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
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Impostare la gravità della regola Esplora soluzioni

1. In Esplora soluzioni espandere **Analizzatori**  >  **riferimenti** (o **Analizzatori**  >  **dipendenze per** i progetti .NET Core).

2. Espandere l'assembly che contiene la regola per cui si vuole impostare la gravità.

::: moniker range=">=vs-2019"
3. Fare clic con il pulsante destro del mouse sulla regola e **scegliere Imposta gravità.** Nel menu di scelta rapida scegliere una delle opzioni di gravità.

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto. Se il progetto usa un file del set di regole anziché un file EditorConfig, la voce relativa alla gravità viene aggiunta al file del set di regole.

   > [!TIP]
   > Se non è già presente un file EditorConfig o un file del set di regole nel progetto, Visual Studio crea automaticamente un nuovo file EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Fare clic con il pulsante destro del mouse sulla regola e **scegliere Imposta gravità set di regole**. Nel menu di scelta rapida scegliere una delle opzioni di gravità.

   La gravità della regola viene salvata nel file del set di regole attivo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Impostare la gravità della regola nel file del set di regole

![File del set di regole Esplora soluzioni](media/ruleset-in-solution-explorer.png)

1. Aprire il file del set di regole attivo in uno dei modi seguenti:

- In **Esplora soluzioni** fare doppio clic sul file, fare clic con il pulsante destro del mouse sul nodo **Analizzatori** riferimenti e scegliere  >   Apri set di regole **attivo**.
- Nella pagina **Code Analysis** proprietà del progetto selezionare **Apri** .

  Se questa è la prima volta che si modifica il set di regole, Visual Studio crea una copia del file del set di regole predefinito, lo nome con estensione *\<projectname> ruleset* e lo aggiunge al progetto. Questo set di regole personalizzato diventa anche il set di regole attivo per il progetto.

   > [!NOTE]
   > I progetti .NET Core e .NET Standard non supportano i comandi di menu per i set di regole **in** Esplora soluzioni , ad esempio Open Active **Rule Set**. Per specificare un set di regole non predefinito per un progetto .NET Core o .NET Standard, aggiungere manualmente la proprietà [ **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al file di progetto. È comunque possibile configurare le regole all'interno del set di regole nell'interfaccia Visual Studio'editor del set di regole.

1. Passare alla regola espandendo l'assembly contenitore.

1. Nella colonna **Azione** selezionare il valore per aprire un elenco a discesa e scegliere la gravità desiderata dall'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configurare il codice generato

Gli analizzatori vengono eseguiti in tutti i file di origine in un progetto e segnalano violazioni su di essi. Tuttavia, queste violazioni non sono utili nei file di codice generati, ad esempio i file di codice generati dalla finestra di progettazione, i file di origine temporanei generati dal sistema di compilazione e così via. Gli utenti non possono modificare manualmente questi file e/o non sono interessati a correggere le violazioni in questo tipo di file generati dagli strumenti.

Per impostazione predefinita, il driver analizzatore che esegue gli analizzatori considera i file con un nome, un'estensione di file o un'intestazione di file generata automaticamente come file di codice generati. Ad esempio, un nome di file che termina con `.designer.cs` o viene considerato codice `.generated.cs` generato. Tuttavia, queste euristiche potrebbero non essere in grado di identificare tutti i file di codice generati personalizzati nel codice sorgente dell'utente.

A partire da Visual Studio 2019 16.5, gli utenti finali possono configurare cartelle e/o file specifici da trattare come codice generato in un [file EditorConfig](https://editorconfig.org/). Seguire questa procedura per aggiungere tale configurazione:

1. Se non si ha già un file EditorConfig per il progetto, [aggiungere un file](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Aggiungere la `generated_code = true | false` voce per cartelle e/o file specifici. Ad esempio, per trattare tutti i file il cui nome termina con come codice `.MyGenerated.cs` generato, la voce sarà la seguente:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Eliminare le violazioni

È possibile eliminare le violazioni delle regole usando vari metodi. Per altre informazioni, vedere Eliminare [le violazioni dell'analisi del codice.](../code-quality/in-source-suppression-overview.md)

## <a name="command-line-usage"></a>Utilizzo della riga di comando

Quando si compila il progetto dalla riga di comando, le violazioni delle regole vengono visualizzate nell'output di compilazione se vengono soddisfatte le condizioni seguenti:

- Gli analizzatori vengono installati con .NET SDK o come pacchetto NuGet e non come estensione VSIX.

  Per gli analizzatori installati con .NET SDK, potrebbe essere necessario [abilitare gli analizzatori](../code-quality/install-net-analyzers.md). Per gli stili di codice, è anche possibile [applicare stili di codice alla compilazione](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) impostando una proprietà MSBuild.

- Una o più regole vengono violate nel codice del progetto.

- La [gravità di](#configure-severity-levels) una regola violata è impostata sull'avviso **,** nel qual caso le violazioni non causano l'esito negativo della compilazione o sull'errore **,** nel qual caso le violazioni causano l'esito negativo della compilazione.

Il livello di dettaglio dell'output di compilazione non influisce sul fatto che le violazioni delle regole siano visualizzate. Anche con **il livello** di dettaglio non interattiva, le violazioni delle regole vengono visualizzate nell'output di compilazione.

> [!TIP]
> Se si è abituati a eseguire l'analisi legacy dalla riga di comando, con *FxCopCmd.exe* o tramite msbuild con il flag **RunCodeAnalysis,** ecco come eseguire questa operazione con gli analizzatori del codice.

Per visualizzare le violazioni dell'analizzatore nella riga di comando quando si compila il progetto usando msbuild, eseguire un comando simile al seguente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L'immagine seguente mostra l'output di compilazione della riga di comando della compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Progetti dipendenti

In un progetto .NET Core, se si aggiunge un riferimento a un progetto con analizzatori NuGet, anche questi vengono aggiunti automaticamente al progetto dipendente. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto unit test, contrassegnare il pacchetto NuGet come privato nel file con estensione *csproj* o *vbproj* del progetto a cui si fa riferimento impostando l'attributo **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori di codice in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug dell'analizzatore del codice](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usare i set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Eliminare gli avvisi di analisi del codice](../code-quality/in-source-suppression-overview.md)
- [Opzioni di configurazione per l'analisi del codice (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
