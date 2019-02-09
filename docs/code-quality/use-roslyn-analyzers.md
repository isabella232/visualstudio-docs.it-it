---
title: Usare e configurare gli analizzatori di Roslyn
ms.date: 03/26/2018
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
ms.openlocfilehash: 887fb6101773a86d346215f558f10216ca4612b8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924604"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurare e usare le regole dell'analizzatore Roslyn

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

Oggetto [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) è un file XML che archivia lo stato della gravità ed eliminazione per la diagnostica singoli. Set di regole si applicano a un singolo progetto e un progetto può avere più set di regole. Per visualizzare la regola attiva impostata nell'editor, fare clic sui **analizzatori** nodo **Esplora soluzioni** e selezionare **Apri Set di regole attivo**. Se questa è la prima volta che si accede a regola impostato, un file denominato  *\<NomeProgetto > estensione ruleset* viene aggiunto al progetto e viene visualizzato nella **Esplora**.

> [!NOTE]
> Set di regole includono analisi statica del codice (binario) e le regole dell'analizzatore Roslyn.

È possibile modificare la regola attiva impostata per un progetto nel **analisi del codice** scheda delle proprietà di un progetto. Selezionare il set di regole nel **eseguire questo set di regole** elenco a discesa. È anche possibile aprire il set di regole dal **analisi del codice** pagina delle proprietà, selezionando **aprire**.

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

### <a name="to-set-rule-severity-from-solution-explorer"></a>Per impostare la gravità di regola da Esplora soluzioni

1. Nelle **Esplora soluzioni**, espandere **riferimenti** > **analizzatori** (**dipendenze**  >  **Analizzatori** per i progetti .NET Core).

1. Espandere l'assembly che contiene la regola che si desidera impostare la gravità per.

1. Pulsante destro del mouse sulla regola e selezionare **imposta gravità Set di regole**. Nel menu a comparsa, selezionare una delle opzioni di gravità.

   La gravità della regola viene salvata nel file di set di regole attivo.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Per impostare regole gravità della regola set di file

1. Aprire il set di regole file facendo doppio clic su esso in **Esplora soluzioni**, selezionando **Apri Set di regole attivo** nel menu di scelta rapida del **analizzatori** nodo, o tramite la selezione **Aperto** nel **analisi del codice** pagina delle proprietà per il progetto.

1. Passare alla regola espandendo relativo assembly che lo contiene.

1. Nel **azione** colonna, selezionare il valore per aprire un elenco a discesa e selezionare il livello di gravità desiderato dall'elenco.

   ![File del set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Non visualizzare le violazioni

Esistono diversi modi per eliminare le violazioni delle regole:

- Per eliminare tutte le violazioni correnti, selezionare **Analyze** > **Esegui analisi del codice ed Elimina problemi attivi** nella barra dei menu. Ciò è talvolta detta "base".

- Per eliminare una diagnostica dal **Esplora soluzioni**, impostare la gravità **None**.

- Per eliminare una diagnostica dall'editor set di regole, deselezionare la casella accanto al relativo nome, o impostare **azione** al **None**.

- Per eliminare una diagnostica dall'editor di codice, posizionare il cursore nella riga di codice con la violazione e premere **Ctrl**+**.** Per aprire la **azioni rapide** menu. Selezionare **sopprimere CAxxxx** > **nell'origine** oppure **sopprimere CAxxxx** > **nel File di eliminazione**.

   ![Non visualizzare diagnostica dal menu Azioni rapide](media/suppress-diagnostic-from-editor.png)

- Per eliminare una diagnostica dal **elenco errori**, vedere [eliminare le violazioni dall'elenco errori](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Non visualizzare le violazioni dall'elenco degli errori

È possibile eliminare uno o molti dati diagnostici dalle **elenco errori** quelle che si desidera eliminare, selezionando e facendo clic e **Suppress** > **In origine**  oppure **sopprimere** > **nel File di eliminazione**.

- Se si seleziona **nell'origine**, il **Anteprima modifiche** della finestra si apre e Mostra un'anteprima del linguaggio c# [#pragma avviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable avviso](/dotnet/visual-basic/language-reference/directives/directives) direttiva che viene aggiunto al codice sorgente.

   ![Anteprima di aggiunta avviso #pragma nel file di codice](media/pragma-warning-preview.png)

- Se si seleziona **File di eliminazione**, il **Anteprima modifiche** della finestra si apre e Mostra un'anteprima del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo che viene aggiunto al file le ulteriori eliminazioni globali.

   ![Anteprima di aggiunta attributo SuppressMessage per file di eliminazione](media/preview-changes-in-suppression-file.png)

Nel **Anteprima modifiche** finestra di dialogo, seleziona **applica**.

Il **elenco errori** Visualizza diagnostica o regola violazioni, sia da analisi di codice in tempo reale e di compilazione. Poiché i dati di diagnostica di compilazione può essere non aggiornato, ad esempio, se è stato modificato il codice per correggere la violazione ma non sono state ricreate, Impossibile eliminare questi dati diagnostici dal **elenco errori**. Tuttavia, la diagnostica di analisi in tempo reale o IntelliSense, sono sempre aggiornati sulle origini correnti e può essere eliminata dal **elenco errori**. Se l'opzione di eliminazione è disabilitato nel menu di scelta, o nel contesto, è probabile perché ne hai uno o più compilazione diagnostica nella selezione. Per escludere i dati di diagnostica di compilazione dalla selezione, passare il **elenco errori** filtro di origine dal **compilazione + IntelliSense** al **solo Intellisense**. Selezionare quindi i dati di diagnostica che si desidera eliminare e procedere come descritto in precedenza.

![Filtro origine dell'elenco errori in Visual Studio](media/error-list-filter.png)

> [!NOTE]
> In un progetto .NET Core, se si aggiunge un riferimento a un progetto con gli analizzatori di NuGet, tali analizzatori vengono automaticamente aggiunti al progetto dipendente troppo. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto di unit test, contrassegnare il pacchetto NuGet come privata nel *file con estensione csproj* oppure *vbproj* file del progetto di riferimento:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

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

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di Roslyn in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug di Analizzatore Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usare set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Non visualizzare gli avvisi dell'analisi codice](../code-quality/in-source-suppression-overview.md)