---
title: Risoluzione dei problemi di code coverage
description: Informazioni su come risolvere messaggi di risultati vuoti non corretti quando si prevede Visual Studio raccogliere dati per assembly nativi e gestiti.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ea2976e01f8f02b0d6ea858afceb43ecad7ef1c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054119"
---
# <a name="troubleshoot-code-coverage"></a>Risolvere i problemi di code coverage

Lo code coverage di analisi dei Visual Studio raccoglie i dati per gli assembly nativi e gestiti *(.dll* o *.exe* file). In alcuni casi, tuttavia, nella finestra **Risultati code coverage** viene visualizzato un errore simile a "Risultati vuoti generati: ...." Esistono diversi motivi per cui è possibile ottenere risultati vuoti. Questo articolo consente di risolvere tali problemi.

## <a name="what-you-should-see"></a>Elementi che dovrebbero essere visualizzati

Se si sceglie un **comando Analizza code coverage** dal menu **Test** e se la compilazione e i test vengono eseguiti correttamente, nella finestra Code coverage verrà visualizzato un elenco **di** risultati. Potrebbe essere necessario espandere gli elementi per visualizzare il dettaglio.

::: moniker range=">=vs-2019"
![Risultati del code coverage con colorazione](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Risultati del code coverage con colorazione](../test/media/codecoverage1.png)
::: moniker-end

Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Cause possibili per la restituzione di nessun risultato o di risultati obsoleti

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>L'edizione di Visual Studio in uso è corretta?

È necessario Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nessun test è stato eseguito

Analisi: verificare la finestra di output. Nell'elenco a discesa **Mostra output di** scegliere **Test**. Verificare se sono presenti avvisi o errori registrati.

Spiegazione: l'analisi del code coverage viene eseguita mentre i test sono in esecuzione. Include solo gli assembly caricati in memoria quando i test vengono eseguiti. Se nessun test viene eseguito, il code coverage non ha nulla da riportare.

Risoluzione: in Esplora test scegliere **Esegui tutto** per verificare che i test vengano eseguiti correttamente. Correggere eventuali errori prima di usare l'opzione **Analizza code coverage**.

### <a name="youre-looking-at-a-previous-result"></a>È visualizzato un risultato precedente

Quando si modificano e si rieseguono i test, i risultati di un code coverage precedente possono rimanere visibili, inclusa la colorazione del codice dell'esecuzione precedente.

1. Eseguire **Analizza code coverage.**

2. Assicurarsi di aver selezionato il set di risultati più recente nella finestra **Risultati code coverage.**

### <a name="pdb-symbol-files-are-unavailable"></a>I file con estensione pdb (simbolo) non sono disponibili

Analisi Aprire la cartella di destinazione di compilazione (in genere &mdash; *bin\debug)* e verificare che per ogni assembly sia presente un file con estensione *pdb* nella stessa directory del file *.dll* *o.exe.*

Spiegazione Il motore code coverage richiede che a ogni assembly sia associato un file con estensione &mdash; *pdb* accessibile durante l'esecuzione dei test. Se non è presente alcun file *con estensione pdb* per un determinato assembly, l'assembly non viene analizzato.

Il file *con estensione pdb* deve essere generato dalla stessa compilazione dei file *.dll* o *.exe* file.

Soluzione &mdash; Assicurarsi che le impostazioni di compilazione generino il file con estensione *pdb.* Se i *file con estensione pdb* non vengono aggiornati quando il progetto viene compilato, aprire le proprietà del progetto, selezionare la **pagina** Compilazione, scegliere **Avanzate** ed esaminare Informazioni **di debug**.

Per i progetti C++, assicurarsi che i file con estensione pdb generati abbiano informazioni di debug complete. Aprire le proprietà del progetto e verificare che l'opzione Genera informazioni di debug del debug del **linker** sia impostata su Genera informazioni di debug ottimizzata per la condivisione e la pubblicazione  >    >   **(/DEBUG:FULL).**

Se i file con estensione *pdb* *.dll* *o.exe* sono in posizioni diverse, copiare il file con estensione *pdb* nella stessa directory. È anche possibile configurare un motore code coverage per la ricerca di file con estensione *pdb* in un'altra posizione. Per altre informazioni, vedere [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Usare un binario instrumentato o ottimizzato

Analisi Determinare se il file binario è stato sottoposto a qualsiasi forma di ottimizzazione avanzata, ad esempio l'ottimizzazione &mdash; *PGO,* o è stato instrumentato da uno strumento di profilatura, ad esempio *vsinstr.exe* ovsperfmon.exe.

Spiegazione: se l'assembly è già stato instrumentato o ottimizzato da un altro strumento di profilatura, l'assembly viene omesso dall'analisi di code coverage. L'analisi di code coverage non può essere eseguita su tali assembly.

Risoluzione: disattivare l'ottimizzazione e usare una nuova compilazione.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Codice non gestito (.NET) o codice nativo (C++)

Analisi: verificare che vengano eseguiti alcuni test sul codice gestito o C++.

Spiegazione: l'analisi di code coverage in Visual Studio è disponibile solo nel codice gestito e nativo (C++). Se si usano strumenti di terze parti, il codice può essere eseguito parzialmente o totalmente su una piattaforma diversa.

Risoluzione: non disponibile.

### <a name="assembly-has-been-installed-by-ngen"></a>L'assembly è stato installato da NGen

Analisi: verificare che l'assembly non venga caricato dalla cache delle immagini native.

Spiegazione: per motivi di prestazioni, gli assembly di immagini native non vengono analizzati. Per altre informazioni, vedere [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Risoluzione: usare una versione MSIL dell'assembly. Non elaborarlo con NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>File personalizzato con estensione runsettings con sintassi non valida

Analisi: in un file personalizzato con estensione *runsettings* potrebbe contenere un errore di sintassi. Il code coverage non viene eseguito e la finestra di code coverage non viene visualizzata alla fine dell'esecuzione del test oppure vengono visualizzati risultati obsoleti.

Spiegazione È possibile eseguire gli unit test con un file con estensione &mdash; *runsettings* personalizzato per configurare code coverage opzioni. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md).

Risoluzione: esistono due possibili tipi di errori:

- **Errore XML**

     Aprire il file *con estensione runsettings* nell Visual Studio editor XML. Individuare le indicazioni degli errori.

- **Errore di espressione regolare**

  Ogni stringa del file è un'espressione regolare. Rivederle singolarmente per individuare gli errori, in particolare cercare:

  - Parentesi non corrispondenti (...) o parentesi non precedute da un carattere di escape \\(...\\). Se si desidera trovare la corrispondenza con una parentesi nella stringa di ricerca, è necessario utilizzare caratteri di escape. Ad esempio, per trovare la corrispondenza con una funzione, usare `.*MyFunction\(double\)`

  - L'asterisco o il segno più all'inizio di un'espressione. Per cercare una stringa di caratteri, utilizzare un punto seguito da un asterisco: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>File personalizzato con estensione runsettings con esclusioni non corrette

Analisi: se si usa un file personalizzato con estensione *runsettings*, verificare che sia incluso nell'assembly.

Spiegazione È possibile eseguire gli unit test con un file con estensione &mdash; *runsettings* personalizzato per configurare code coverage opzioni. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md).

Risoluzione &mdash; Rimuovere tutti i nodi dal file con estensione `Include` *runsettings* e quindi rimuovere tutti i `Exclude` nodi. Se in tal modo si risolve il problema, riportare i nodi nelle fasi.

Assicurarsi che il nodo DataCollectors specifichi Code coverage. Confrontarlo con l'esempio presente in [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Il codice verrà sempre visualizzato come parzialmente non analizzato

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Il codice di inizializzazione nelle DLL native viene eseguito prima della strumentazione

Analisi: nel codice nativo collegato in modo statico, parte della funzione di inizializzazione **DllMain** e il codice che chiama vengono talvolta visualizzati come non analizzati, anche se il codice è stato eseguito.

Spiegazione: lo strumento di code coverage funziona inserendo la strumentazione in un assembly immediatamente prima dell'avvio dell'applicazione. Nell'assembly caricato in precedenza il codice di inizializzazione in **DllMain** viene eseguito non appena viene caricato l'assembly e prima che venga eseguita l'applicazione. Il codice risulta non analizzato, il che in genere si applica agli assembly caricati in modo statico.

Risoluzione: nessuna.

## <a name="see-also"></a>Vedi anche

- [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
