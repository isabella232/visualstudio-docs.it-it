---
title: Gravità e eliminazione delle regole dell'analizzatore
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1845647dc1848a7fcd99ef59c29eb163bece979d
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186027"
---
# <a name="use-code-analyzers"></a>Usare gli analizzatori di codice

Gli analizzatori di codice .NET Compiler Platform ("Roslyn") C# analizzano il codice o Visual Basic durante la digitazione. Ogni *diagnostica* o regola ha uno stato di gravità e di eliminazione predefinito che può essere sovrascritto per il progetto. In questo articolo viene illustrata l'impostazione della gravità della regola, l'utilizzo di set di regole e l'eliminazione di violazioni.

## <a name="analyzers-in-solution-explorer"></a>Analizzatori in Esplora soluzioni

È possibile eseguire gran parte della personalizzazione di diagnostica analizzatore da **Esplora soluzioni**. Se si [installano gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, un nodo **analizzatori** viene visualizzato nel nodo **riferimenti** o **dipendenze** in **Esplora soluzioni**. Se si espande **analizzatori**e si espande uno degli assembly dell'analizzatore, vengono visualizzati tutti i dati diagnostici nell'assembly.

![Nodo analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, incluse la descrizione e la gravità predefinita, nella finestra **Proprietà** . Per visualizzare le proprietà, fare clic con il pulsante destro del mouse sulla regola e scegliere **Proprietà**oppure selezionare la regola e quindi premere **ALT**+**invio**.

![Proprietà di diagnostica in Finestra Proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione online per una diagnostica, fare clic con il pulsante destro del mouse sulla diagnostica e selezionare **Visualizza Guida**.

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
| Error | `error` | Le violazioni vengono visualizzate come *errori* nel elenco errori e nell'output di compilazione da riga di comando e causano l'esito negativo delle compilazioni.| Il codice che offende è sottolineato con un ondulato rosso e contrassegnato da una piccola casella rossa nella barra di scorrimento. |
| Avviso | `warning` | Le violazioni vengono visualizzate come *avvisi* nell'elenco errori e nell'output di compilazione da riga di comando, ma non comportano la mancata riuscita delle compilazioni. | Il codice danneggiato è sottolineato con una ondulazione verde e contrassegnata da una piccola casella verde nella barra di scorrimento. |
| Info | `suggestion` | Le violazioni vengono visualizzate come *messaggi* nell'elenco errori e non nell'output di compilazione da riga di comando. | Il codice che causa il danneggiamento è sottolineato con uno ondulato grigio e contrassegnato da una piccola casella grigia nella barra di scorrimento. |
| Hidden | `silent` | Non visibile all'utente. | Non visibile all'utente. Tuttavia, la diagnostica viene segnalata al motore di diagnostica IDE. |
| nessuno | `none` | Eliminati completamente. | Eliminati completamente. |
| Impostazione predefinita | `default` | Corrisponde alla gravità predefinita della regola. Per determinare il valore predefinito di una regola, cercare nell'Finestra Proprietà. | Corrisponde alla gravità predefinita della regola. |

La schermata seguente dell'editor del codice mostra tre violazioni diverse con livelli di gravità diversi. Si noti il colore del zigzag e il piccolo quadrato colorato nella barra di scorrimento a destra.

![Violazione di errori, avvisi e informazioni nell'editor di codice](media/diagnostics-severity-colors.png)

Lo screenshot seguente mostra le stesse tre violazioni visualizzate nel Elenco errori:

![Violazione di errori, avvisi e informazioni in Elenco errori](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Impostare la gravità della regola in un file EditorConfig

(Visual Studio 2019 versione 16,3 e successive)

La sintassi generale per specificare la gravità di una regola in un file EditorConfig è la seguente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

L'impostazione della gravità di una regola in un file EditorConfig ha la precedenza su qualsiasi gravità impostata in un set di regole o in Esplora soluzioni. È possibile configurare [manualmente](#manually-configure-rule-severity) la gravità in un file EditorConfig o [automaticamente](#automatically-configure-rule-severity) tramite la lampadina visualizzata accanto a una violazione.

#### <a name="manually-configure-rule-severity"></a>Configurare manualmente la gravità della regola

1. Se non si dispone già di un file EditorConfig per il progetto, [aggiungerne uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Aggiungere una voce per ogni regola che si desidera configurare con l'estensione di file corrispondente. Ad esempio, per impostare il livello di gravità per [CA1822](ca1822-mark-members-as-static.md) su `error` per C# i file, la voce è simile alla seguente:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Per gli analizzatori in stile codice IDE, è anche possibile configurarli in un file EditorConfig usando una sintassi diversa, ad `dotnet_style_qualification_for_field = false:suggestion`esempio. Tuttavia, se si imposta una gravità usando la `dotnet_diagnostic` sintassi, avrà la precedenza. Per altre informazioni, vedere [convenzioni di lingua per EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Configura automaticamente gravità regola

Visual Studio offre un modo pratico per configurare la gravità di una regola dal menu della lampadina delle [azioni rapide](../ide/quick-actions.md) .

1. Dopo che si è verificata una violazione, passare il puntatore del mouse sulla violazione zigzag nell'editor e aprire il menu lampadina. In alternativa, posizionare il cursore sulla riga e premere **CTRL**+ **.** (punto).

2. Dal menu lampadina selezionare **Configura o Elimina problemi** > **Configura \<ID regola > gravità**.

   ![Configurare la gravità della regola dal menu a bulbo chiaro in Visual Studio](media/configure-rule-severity.png)

3. Da qui, selezionare una delle opzioni di gravità.

   ![Configurare la gravità della regola come suggerimento](media/configure-rule-severity-suggestion.png)

   Visual Studio aggiunge una voce al file EditorConfig per configurare la regola al livello richiesto, come illustrato nella casella Anteprima.

   > [!TIP]
   > Se non si dispone già di un file EditorConfig nel progetto, Visual Studio ne crea uno automaticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Imposta gravità regola da Esplora soluzioni

1. In **Esplora soluzioni**, espandere**analizzatori** di **riferimenti** > (o**analizzatori** di **dipendenze** > per i progetti .NET Core).

1. Espandere l'assembly che contiene la regola per la quale si desidera impostare la gravità.

1. Fare clic con il pulsante destro del mouse sulla regola e selezionare **imposta gravità set di regole**. Nel menu a comparsa selezionare una delle opzioni di gravità.

   Il livello di gravità per la regola viene salvato nel file del set di regole attivo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Imposta gravità regola nel file del set di regole

![File del set di regole in Esplora soluzioni](media/ruleset-in-solution-explorer.png)

1. Aprire il file [del set di regole](analyzer-rule-sets.md) attivo facendo doppio clic su di esso in **Esplora soluzioni**, selezionando **Apri set di regole attivo** dal menu di scelta rapida del nodo**analizzatori** **riferimenti** > oppure selezionando **Apri** in pagina delle proprietà di **analisi del codice** per il progetto.

   Se è la prima volta che si modifica il set di regole, Visual Studio crea una copia del file del set di regole predefinito, ne  *\<assegna il nome NomeProgetto >. RuleSet*e lo aggiunge al progetto. Questo set di regole personalizzate diventa anche il set di regole attive per il progetto.

   > [!NOTE]
   > I progetti .NET Core e .NET Standard non supportano i comandi di menu per i set di regole in **Esplora soluzioni**, ad esempio **aprire il set di regole attive**. Per specificare un set di regole non predefinite per un progetto .NET Core o .NET Standard, [aggiungere manualmente la proprietà **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al file di progetto. È comunque possibile configurare le regole all'interno del set di regole nell'interfaccia utente dell'editor set di regole di Visual Studio.

1. Passare alla regola espandendo l'assembly contenitore.

1. Nella colonna **azione** selezionare il valore per aprire un elenco a discesa e selezionare la gravità desiderata nell'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Non visualizzare le violazioni

Esistono diversi modi per eliminare le violazioni delle regole:

::: moniker range=">=vs-2019"

- In un **file EditorConfig**

  Impostare la gravità su `none`, ad `dotnet_diagnostic.CA1822.severity = none`esempio.

::: moniker-end

- Dal menu **analizza**

  Selezionare **analizza** > **Esegui analisi codice ed evitare i problemi attivi** nella barra dei menu per disattivare tutte le violazioni correnti. Questa operazione viene a volte definita "baselining".

- Da **Esplora soluzioni**

  Impostare la gravità della regola su **None**.

- Dall' **Editor set di regole**

  Deselezionare la casella accanto al nome o impostare **azione** su **nessuno**.

- Dall' **editor di codice**

  Posizionare il cursore nella riga di codice con la violazione e premere **CTRL**+**punto (.)** per aprire il menu **azioni rapide** . Selezionare **Elimina CAXXXX** > **nel file di origine/eliminazione**.

  ![Disattiva diagnostica dal menu azioni rapide](media/suppress-diagnostic-from-editor.png)

- Dal **Elenco errori**

  Selezionare le regole da escludere, quindi fare clic con il pulsante destro del mouse e selezionare **Elimina** > **in origine/in file di eliminazione**.

  - Se si omette **in origine**, viene visualizzata la finestra di dialogo **Anteprima modifiche** che mostra un' C# anteprima della [#pragma avviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic direttiva di [avviso #Disable](/dotnet/visual-basic/language-reference/directives/directives) aggiunta al codice sorgente.

    ![Anteprima dell'aggiunta di #pragma avviso nel file di codice](media/pragma-warning-preview.png)

  - Se si seleziona **in file di eliminazione**, viene visualizzata la finestra di dialogo **Anteprima modifiche** con un' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> anteprima dell'attributo aggiunto al file di eliminazione globale.

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
> Se si è abituati a eseguire l'analisi legacy dalla riga di comando, con *FxCopCmd. exe* o tramite MSBuild con il flag **RunCodeAnalysis** , di seguito viene illustrato come eseguire questa operazione con gli analizzatori di codice.

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
