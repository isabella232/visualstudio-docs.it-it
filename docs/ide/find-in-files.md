---
title: Cerca nei file
description: Informazioni sulla funzionalità Trova nei file e su come usarla per cercare un set specifico di file.
ms.custom: SEO-VS-2020
ms.date: 08/02/2021
ms.topic: conceptual
f1_keywords:
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8bc709578539ff299647bae583f8370a3ba1b8d8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625908"
---
# <a name="find-in-files"></a>Cerca nei file

**Trova in File** consente di cercare un set specificato di file. Le corrispondenze Visual Studio trovate sono elencate nella **finestra Risultati** ricerca nell'IDE. La modalità di visualizzazione dei risultati dipende dalle opzioni selezionate **nella** scheda Trova nei file della finestra **di dialogo** Trova e sostituisci .

::: moniker range=">=vs-2019"

:::image type="content" source="media/find-files-vs2019.png" alt-text="Screenshot della finestra di dialogo Trova e sostituisci in Visual Studio 2019, con la scheda Trova nei file aperta.":::

> [!IMPORTANT]
> Se si usa **Visual Studio 2019** versione [**16.6**](/visualstudio/releases/2019/release-notes-v16.6/) o  precedente, la finestra di dialogo Trova e sostituisci potrebbe non essere visualizzata qui. Passare alla versione [Visual Studio 2017](find-in-files.md?view=vs-2017&preserve-view=true) di questa pagina per le descrizioni che corrisponderanno a quanto visualizzato sullo schermo.

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/find-files-vs2017.png" alt-text="Screenshot della finestra di dialogo Trova e sostituisci in Visual Studio 2017, con la scheda Trova nei file aperta.":::

::: moniker-end

## <a name="how-to-display-find-in-files"></a>Come visualizzare Trova nei file

Seguire questa procedura per aprire la finestra **di dialogo** Trova e sostituisci o premere **CTRL** + **MAIUSC** + **F**.

1. Sulla barra dei menu selezionare **Modifica**  >  **Trova e sostituisci**.

1. Scegliere **Trova nei file** dal menu a comparsa.

Per annullare un'operazione Di ricerca, premere + **CTRL+INTERR.**

> [!NOTE]
> Lo **strumento Trova e sostituisci** non esegue ricerche nelle directory con `Hidden` l'attributo o `System` .

::: moniker range="vs-2017"

## <a name="find-what"></a>Find what:

Per cercare una nuova stringa di testo o una nuova espressione, specificarla nella **casella** Trova.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="search-box"></a>Casella di ricerca

Per cercare una nuova stringa di testo o una nuova espressione, specificarla nella casella Di ricerca. Per cercare una delle 20 stringhe ricercate più di recente, aprire l'elenco a discesa e selezionare la stringa.

È possibile selezionare o deselezionare le opzioni seguenti:

- **Maiuscole/minuscole:** usare questa opzione per assicurarsi che la ricerca eserciti la distinzione tra maiuscole e minuscole.
- **Trova la corrispondenza con parola** intera: usare questa opzione per assicurarsi che la ricerca restituisca solo corrispondenze di parole intere.
- **Usa espressioni regolari:** usare questa opzione per usare notazioni speciali che definiscono i modelli di testo di cui trovare la corrispondenza nella casella di ricerca (o nella **casella di** testo Sostituisci). Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

    > [!Important]
    > Il **pulsante Generatore di** espressioni viene visualizzato accanto alla casella Di ricerca solo se è stata selezionata la casella di controllo Usa **espressioni** regolari.
    >
    > :::image type="content" source="media/find-files-expression-builder-vs-2019.png" alt-text="Screenshot della finestra di dialogo Trova nei file che include e delinea il pulsante Generatore di espressioni e la casella di controllo Usa espressioni regolari.":::

## <a name="look-in"></a>Cerca in

L'opzione selezionata nell'elenco a discesa  Cerca in determina se Trova nei file esegue la ricerca nell'intera area di lavoro, nell'intera soluzione, nel progetto corrente, nella directory corrente, **in** tutti i documenti aperti o nel documento corrente.

È anche possibile usare il pulsante **Sfoglia (...)** adiacente per individuare la posizione in cui si vuole eseguire la ricerca. Ancora meglio, se è già stata specificata una directory, questo pulsante accoderà la nuova directory invece di sostituirla. Ad esempio, se il valore "Cerca in" è ".\Code", è possibile fare clic sul pulsante Sfoglia **(...)** e passare a una cartella denominata "Codice condiviso". La **casella Sfoglia (...)** visualizza ora ".\Code;. \Shared Code" e quando viene eseguito il comando Find, esegue la ricerca in entrambe le cartelle.

Per perfezionare la ricerca, è possibile selezionare o deselezionare le opzioni seguenti:

- **Includi elementi esterni:** usare questa opzione per includere elementi esterni, ad esempio file come "windows.h" a cui è possibile fare riferimento ma che non fanno parte di una soluzione.
- **Includi file** esterni: usare questa opzione per includere file esterni, ad esempio file aperti ma che non fanno parte di una soluzione.

## <a name="file-types"></a>Tipi di file

**L'opzione** Tipi di file indica i tipi di file da cercare nelle **directory Cerca in.** Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.

:::image type="content" source="media/find-file-types.png" alt-text="Screenshot della sezione Tipi di file della finestra di dialogo Trova nei file .":::

È possibile cercare più tipi di file separandoli con un punto e virgola ( `;` ). È anche possibile escludere cartelle e file antecendo a qualsiasi percorso o tipo di file un punto esclamativo ( `!` ).

### <a name="append-results"></a>Accoda risultati

Usare questa opzione per aggiungere i risultati della ricerca corrente ai risultati della ricerca precedente.

::: moniker-end

::: moniker range="vs-2017"

### <a name="expression-builder"></a>Generatore di espressioni

Se si vogliono usare espressioni regolari nella stringa  di ricerca, selezionare il pulsante generatore di espressioni adiacente accanto alla casella di ricerca. Per altre informazioni, vedere [Uso di espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Il **pulsante Generatore** di espressioni è abilitato solo se è stata selezionata l'opzione Usa espressioni **regolari** in Opzioni **di ricerca**.

## <a name="look-in"></a>Cerca in:

L'opzione selezionata dall'elenco a discesa **Cerca in** determina se la funzione **Cerca nei file** eseguirà la ricerca solo nei file attualmente attivi oppure in tutti i file archiviati all'interno di determinate cartelle.

Selezionare un ambito di ricerca nell'elenco o fare clic sul pulsante **Sfoglia (...)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di directory desiderato. È anche possibile digitare un percorso direttamente nella casella **Cerca in**.

> [!WARNING]
> Se si sceglie **l'opzione Intera soluzione** **o** Project, i file di progetto e di soluzione non vengono cercati. Se si vuole cercare nei file di progetto, selezionare una cartella di ricerca.

> [!NOTE]
> Se si usa l'opzione Cerca **in** per cercare un file estratto dal controllo del codice sorgente, viene trovata solo la versione del file scaricato nel computer locale.

::: moniker-end

::: moniker range="vs-2017"

## <a name="include-subfolders"></a>Includi sottocartelle

Specifica che la ricerca verrà eseguita nelle sottocartelle della cartella **Cerca in**.

## <a name="find-options"></a>Opzioni ricerca

È possibile espandere o comprimere la **sezione Opzioni di** ricerca. È possibile selezionare o deselezionare le opzioni seguenti:

**Maiuscole/minuscole**

Se questa opzione è selezionata, in una ricerca impostata su **Risultati ricerca** viene applicata la distinzione tra maiuscole e minuscole

**Parola intera**

Se questa opzione è selezionata, la finestra **Risultati ricerca** restituirà solo corrispondenze di parole intere.

**Usare espressioni regolari**

Se questa casella di controllo è selezionata, è possibile usare notazioni speciali per definire modelli di testo che devono corrispondere nelle caselle di testo **Trova** o **Sostituisci con**. Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Cerca i seguenti tipi di file**

L'elenco indica i tipi di file da cercare nelle directory **Cerca in**. Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file contenuti nelle directory **Cerca in**.

Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.

## <a name="result-options"></a>Opzioni risultati

È possibile espandere o comprimere la **sezione Opzioni risultato.** Le opzioni seguenti in **Elenca risultati in** possono essere selezionate o deselezionate:

**Finestra Risultati ricerca 1**

Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiscono il contenuto della **finestra Risultati ricerca 1.** Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca. Per aprire questa finestra  manualmente, scegliere Windows **dal** menu Visualizza e quindi selezionare **Risultati ricerca 1.**

**Finestra Risultati ricerca 2**

Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**. Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.

> [!TIP]
> È possibile alternare tra le finestre dei risultati premendo **ALT** + **1** o **ALT** + **2.**

**Trovare la tabella dei risultati**

Visualizza i risultati della ricerca in formato tabella anziché in un elenco di testo.

**Accoda risultati**

Aggiunge i risultati della ricerca a quelli della ricerca precedente.

**Mostra solo nomi file**

Mostra un elenco di file che contengono le corrispondenze invece di visualizzare le corrispondenze stesse.

::: moniker-end

## <a name="multiple-searches"></a>Più ricerche

È possibile mantenere i risultati di una ricerca mentre si eseguono altre ricerche. In questo modo è più semplice confrontare i risultati e vederli side-by-side.

:::image type="content" source="media/find-files-search-results.png" alt-text="Screenshot della finestra Risultati ricerca con tre risultati della ricerca visualizzati come schede.":::

Per mantenere diversi risultati della ricerca, selezionare il **pulsante Mantieni risultati** dopo ogni ricerca. Quindi, quando si cerca un altro elemento, i risultati vengono visualizzati in una nuova scheda. È possibile mantenere i risultati di un massimo di cinque ricerche. Se sono già stati visualizzati cinque risultati della ricerca, la ricerca successiva riuserà la scheda dei risultati della ricerca meno recente.

## <a name="see-also"></a>Vedi anche

- [Sostituire nei file](../ide/replace-in-files.md)
- [Cercare e sostituire testo](../ide/finding-and-replacing-text.md)
- [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)