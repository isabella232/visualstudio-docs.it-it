---
title: Gravità della regola dell'analizzatore ed estinzione
ms.date: 03/26/2019
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
ms.openlocfilehash: 7132fae3623e1ad10fb35d2b903935cdbffee12d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676709"
---
# <a name="use-roslyn-analyzers"></a>Usare gli analizzatori di Roslyn

Le regole dell'analizzatore di .NET compiler Platform ("Roslyn"), oppure *diagnostica*, analizzare il codice c# o Visual Basic mentre si digita. Ogni dato diagnostico ha uno stato di gravità e la soppressione predefinito che può essere sovrascritto per il progetto. Questo articolo illustra l'impostazione regola livello di gravità, usando i set di regole e le violazioni di disattivazione.

## <a name="analyzers-in-solution-explorer"></a>Analizzatori in Esplora soluzioni

È possibile eseguire gran parte della personalizzazione di dati diagnostici analyzer dal **Esplora soluzioni**. Se si [installare gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, un **analizzatori** nodo viene visualizzato sotto il **riferimenti** o **dipendenze** nodo  **Esplora soluzioni**. Se si espande **analizzatori**e quindi espandere uno degli assembly dell'analizzatore, noterete che tutti i dati diagnostici nell'assembly.

![Nodo di analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, inclusi nella relativa descrizione e il livello di gravità predefinito, il **proprietà** finestra. Per visualizzare le proprietà, pulsante destro del mouse sulla regola e selezionare **delle proprietà**, oppure selezionare la regola e quindi premere **Alt**+**invio**.

![Proprietà diagnostica nella finestra proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione online per la diagnostica, fare clic su diagnostica e selezionare **Visualizza la Guida**.

Le icone accanto a ogni dato diagnostico nelle **Esplora soluzioni** corrispondono alle icone visualizzate nell'insieme quando si aprono il collegamento nell'editor di regole:

- la "i" in un cerchio indica una [severity](#rule-severity) di **Info**
- il "!" in un triangolo indica una [severity](#rule-severity) di **avviso**
- la "x" in un cerchio indica una [severity](#rule-severity) di **errore**
- la "i" in un cerchio su uno sfondo di colore chiaro indica una [gravità](#rule-severity) di **nascosti**
- la freccia verso il basso in un cerchio indica che la diagnostica viene eliminata

![Icone di diagnostica in Esplora soluzioni](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Set di regole

Oggetto [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) è un file XML che archivia lo stato della gravità ed eliminazione per la diagnostica singoli.

> [!NOTE]
> Set di regole possono includere le regole di analisi statica del codice (binario) e gli analizzatori di Roslyn.

Per modificare la regola attiva impostata nell'editor set di regole, fare clic sui **riferimenti** > **analizzatori** nodo **Esplora soluzioni** e selezionare **Aprire i Set di regole attivo**. Se questa è la prima volta che si modifica il set di regole, Visual Studio crea una copia della regola predefinita di file del set, assegna  *\<NomeProgetto > estensione ruleset*e lo aggiunge al progetto. Questa regola personalizzata anche imposta diventa attiva set di regole per il progetto.

Per modificare la regola attiva impostata per un progetto, passare al **analisi del codice** scheda delle proprietà di un progetto. Selezionare il set di regole da nell'elenco sotto **eseguire questo set di regole**. Per aprire il set di regole, selezionare **aprire**.

> [!NOTE]
> I progetti .NET core e .NET Standard non supportano i comandi di menu per il set di regole **Esplora soluzioni**, ad esempio **Apri Set di regole attivo**. Per specificare una diverso set di regole per un progetto .NET Core o .NET Standard, manualmente [aggiungere i **CodeAnalysisRuleSet** proprietà](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al file di progetto. È comunque possibile configurare le regole all'interno di set di regole in Visual Studio interfaccia utente dell'editor set di regole.

## <a name="rule-severity"></a>Gravità della regola

È possibile configurare il livello di gravità delle regole di Analizzatore, oppure *diagnostics*, se si [installare gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet. Nella tabella seguente mostra le opzioni di gravità per la diagnostica:

|Gravità|Comportamento in fase di compilazione|Comportamento dell'editor|
|-|-|-|
|Error|Violazioni vengono visualizzati come *errori* nel **elenco errori** nella riga di comando dell'output di compilazione e causare compilazioni esito negativo.|Codice all'origine del problema è sottolineato con una linea rossa ondulata e contrassegnata da una piccola casella rossa nella barra di scorrimento.|
|Avviso|Violazioni vengono visualizzati come *gli avvisi* nel **elenco errori** e nella riga di comando dell'output di compilazione, ma non causano compilazioni esito negativo.|Codice all'origine del problema è sottolineato con una linea verde ondulata e contrassegnata da una piccola casella verde nella barra di scorrimento.|
|Info|Violazioni vengono visualizzati come *messaggi* nel **elenco errori**e non ricorrere affatto nell'output di compilazione da riga di comando.|Codice all'origine del problema è sottolineato con un grigio Ondulato e contrassegnato da una piccola casella grigia nella barra di scorrimento.|
|Hidden|Non visibile all'utente.|Non visibile all'utente. La diagnostica viene segnalata al motore di diagnostica di IDE, tuttavia.|
|nessuno|Eliminato completamente.|Eliminato completamente.|

Inoltre, è possibile "Reimposta" gravità della regola impostandolo su **predefinito**. Ogni dato diagnostico con gravità predefiniti che possono essere visualizzate nei **proprietà** finestra.

Lo screenshot seguente mostra tre diverse violazioni di diagnostica nell'editor di codice, con tre diversi livelli di gravità. Si noti che il colore dell'ondulata, come pure la piccola casella nella barra di scorrimento a destra.

![Violazione di errore, avviso e informazioni nell'editor del codice](media/diagnostics-severity-colors.png)

Lo screenshot seguente mostra le violazioni di tre stesso così come appaiono nel **elenco errori**:

![Violazione di errore, avviso e informazioni nell'elenco errori](media/diagnostics-severities-in-error-list.png)

È possibile modificare la gravità di una regola dal **Esplora soluzioni**, o all'interno di  *\<projectname > estensione ruleset* file che viene aggiunto alla soluzione dopo aver modificato la gravità di una regola in  **Esplora soluzioni**.

![File del set di regole in Esplora soluzioni](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Impostare la gravità di regola da Esplora soluzioni

1. Nelle **Esplora soluzioni**, espandere **riferimenti** > **analizzatori** (**dipendenze**  >  **Analizzatori** per i progetti .NET Core).

1. Espandere l'assembly che contiene la regola che si desidera impostare la gravità per.

1. Pulsante destro del mouse sulla regola e selezionare **imposta gravità Set di regole**. Nel menu a comparsa, selezionare una delle opzioni di gravità.

   La gravità della regola viene salvata nel file di set di regole attivo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Impostare la gravità regola nel file di set di regole

1. Aprire il [set di regole](analyzer-rule-sets.md) file facendo doppio clic su esso in **Esplora soluzioni**, selezionando **Apri Set di regole attivo** nel menu di scelta rapida del **analizzatori** nodo, o selezionando **aperta** sul **analisi del codice** pagina delle proprietà per il progetto.

1. Passare alla regola espandendo relativo assembly che lo contiene.

1. Nel **azione** colonna, selezionare il valore per aprire un elenco a discesa e selezionare il livello di gravità desiderato dall'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Non visualizzare le violazioni

Esistono diversi modi per eliminare le violazioni delle regole:

- Dal **Analyze** menu

   Selezionare **Analyze** > **Esegui analisi del codice ed Elimina problemi attivi** nella barra dei menu per eliminare tutte le violazioni correnti. Ciò è talvolta detta "base".

- Da **Esplora soluzioni**

   Per eliminare una violazione **Esplora soluzioni**, impostare la gravità della regola **None**.

- Dal **editor set di regole**

   Per eliminare una violazione da editor set di regole, deselezionare la casella accanto al relativo nome o impostare **azione** al **None**.

- Dal **editor di codice**

   Per eliminare una violazione dall'editor di codice, posizionare il cursore nella riga di codice con la violazione e premere **Ctrl**+**.** Per aprire la **azioni rapide** menu. Selezionare **sopprimere CAXXXX** > **nell'origine/nel File di eliminazione**.

   ![Non visualizzare diagnostica dal menu Azioni rapide](media/suppress-diagnostic-from-editor.png)

- Dal **elenco errori**

   È possibile eliminare uno o molti dati diagnostici dalle **elenco errori** quelle che si desidera eliminare, selezionando e facendo clic e **Suppress** > **Source/In In File di eliminazione**.

   - Se si eliminano **nell'origine**, il **Anteprima modifiche** della finestra si apre e Mostra un'anteprima del C# [#pragma avviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable avviso](/dotnet/visual-basic/language-reference/directives/directives) direttiva che viene aggiunto al codice sorgente.

      ![Anteprima di aggiunta avviso #pragma nel file di codice](media/pragma-warning-preview.png)

   - Se si seleziona **File di eliminazione**, il **Anteprima modifiche** della finestra si apre e Mostra un'anteprima del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo che viene aggiunto al file le ulteriori eliminazioni globali.

      ![Anteprima di aggiunta attributo SuppressMessage per file di eliminazione](media/preview-changes-in-suppression-file.png)

   Nel **Anteprima modifiche** finestra di dialogo, seleziona **applica**.

   > [!NOTE]
   > Se non viene visualizzato il **Suppress** opzione di menu nel **Esplora soluzioni**, la violazione probabilmente proviene dalla compilazione e l'analisi non in tempo reale. Il **elenco errori** Visualizza diagnostica o regola violazioni, sia da analisi di codice in tempo reale e di compilazione. Poiché i dati di diagnostica di compilazione può essere non aggiornato, ad esempio, se è stato modificato il codice per correggere la violazione ma non sono state ricreate, Impossibile eliminare questi dati diagnostici dal **elenco errori**. Diagnostica di analisi in tempo reale o IntelliSense, sono sempre aggiornata con le origini corrente che possono essere eliminata dal **elenco errori**. Per escludere *compilare* diagnostica dalla selezione, passare il **elenco errori** filtro di origine dal **compilazione + IntelliSense** a **solo Intellisense**. Selezionare quindi i dati di diagnostica che si desidera eliminare e procedere come descritto in precedenza.
   >
   > ![Filtro origine dell'elenco errori in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Utilizzo della riga di comando

Quando si compila il progetto nella riga di comando, le violazioni delle regole vengono visualizzati nell'output di compilazione se vengono soddisfatte le condizioni seguenti:

- Gli analizzatori vengono installati come pacchetto Nuget e non come estensione VSIX.

- Uno o più regole vengono violate nel codice del progetto.

- Il [gravità](#rule-severity) di una regola ha violata è impostato su **avviso**, nel qual caso le violazioni non provocare l'errore, di compilazione oppure **errore**, nel qual caso le violazioni provocare l'errore di compilazione.

Il livello di dettaglio dell'output di compilazione non interessa sia le violazioni delle regole sono visualizzate. Nonostante **quiet** livello di dettaglio, le violazioni delle regole visualizzate nell'output della compilazione.

> [!TIP]
> Se si è abituati all'esecuzione di analisi statica del codice dalla riga di comando, specificando *FxCopCmd.exe* o tramite msbuild con i **RunCodeAnalysis** flag, ecco come farlo con analizzatori di Roslyn.

Per visualizzare le violazioni di Analizzatore nella riga di comando quando si compila il progetto usando msbuild, eseguire un comando simile al seguente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L'immagine seguente mostra l'output di compilazione da riga di comando di compilazione di un progetto che contiene una violazione della regola dell'analizzatore:

![Output MSBuild con violazione della regola](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Progetti dipendenti

In un progetto .NET Core, se si aggiunge un riferimento a un progetto con gli analizzatori di NuGet, tali analizzatori vengono automaticamente aggiunti al progetto dipendente troppo. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto di unit test, contrassegnare il pacchetto NuGet come privata nel *file con estensione csproj* oppure *vbproj* file del progetto di riferimento, impostare il **PrivateAssets** attributo:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di Roslyn in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug di Analizzatore Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usare set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Non visualizzare gli avvisi dell'analisi codice](../code-quality/in-source-suppression-overview.md)