---
title: Risoluzione dei problemi di code coverage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660367"
---
# <a name="troubleshooting-code-coverage"></a>Risoluzione dei problemi di code coverage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lo strumento di analisi della copertura del codice in Visual Studio raccoglie dati per assembly nativo e gestito (file .dll o .exe). Tuttavia, in alcuni casi, nella finestra Risultati code coverage viene visualizzato un errore simile a "i risultati vuoti generati:...". Esistono diversi possibili motivi per cui questo potrebbe verificarsi. Questo argomento è progettato per aiutare a risolvere quei problemi.

## <a name="what-you-should-see"></a>Cosa si dovrebbe vedere
 Se si sceglie un comando **Analizza code coverage** dal menu Test e se la compilazione e i test vengono eseguiti correttamente, nella finestra di code coverage verrà visualizzato un elenco di risultati. Potrebbe essere necessario espandere gli elementi per visualizzare il dettaglio.

 ![Risultati del code coverage con colorazione](../test/media/codecoverage1.png "CodeCoverage1")

 Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Cause possibili per la restituzione di nessun risultato o di risultati obsoleti

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>L'edizione di Visual Studio in uso è corretta?
 È necessario Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nessun test è stato eseguito
 Analisi controllare la finestra di output. Nell'elenco a discesa **Mostra output di** scegliere **Test**. Verificare se sono presenti avvisi o errori registrati.

 Spiegazione dell'analisi del code coverage eseguita durante l'esecuzione dei test. Include solo gli assembly caricati in memoria quando i test vengono eseguiti. Se nessun test viene eseguito allora il code coverage non ha nulla da riportare.

 Risoluzione in Esplora test, scegliere **Esegui tutto** per verificare che i test vengano eseguiti correttamente. Correggere eventuali errori prima di usare l'opzione **Analizza code coverage**.

### <a name="youre-looking-at-a-previous-result"></a>Si sta cercando un risultato precedente
 Quando si modificano e si rieseguono i test, i risultati di un code coverage precedente possono rimanere visibile, inclusa la colorazione del codice dell'esecuzione precedente.

1. Eseguire Analizza code coverage.

2. Verificare che sia stato selezionato il set di risultati più recente nella finestra dei risultati del code coverage.

### <a name="pdb-symbol-files-are-unavailable"></a>I file con estensione pdb (simbolo) non sono disponibili
 L'analisi apre la cartella di destinazione della compilazione (in genere bin\Debug) e verifica che per ogni assembly esista un file con estensione PDB nella stessa directory del file con estensione dll o exe.

 Spiegazione il motore di code coverage richiede che ogni assembly abbia il file con estensione pdb associato accessibile durante l'esecuzione dei test. Se non esiste alcun file con estensione pdb per un particolare assembly, tale assembly non verrà analizzato.

 Il file con estensione pdb deve essere generato dalla stessa compilazione dei file con estensione dll o exe.

 Risoluzione assicurarsi che le impostazioni di compilazione generino il file con estensione pdb. Se i file con estensione pdb non vengono aggiornati quando viene compilato il progetto, aprire le proprietà del progetto, selezionare la pagina **Compila**, scegliere **Avanzate** e controllare **Informazioni di debug**.

 Se i file con estensione pdb e dll o exe sono in posizioni diverse, copiare il file con estensione pdb nella stessa directory. È inoltre possibile configurare il motore di code coverage per cercare i file con estensione pdb in un'altra posizione. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Utilizzo di un binario instrumentato o ottimizzato
 L'analisi determina se il file binario è stato sottoposto a una qualsiasi forma di ottimizzazione avanzata, come l'ottimizzazione PGO, o è stato instrumentato da uno strumento di profilatura come VSInstr. exe o VSPerfMon. exe.

 Spiegazione se un assembly è già stato instrumentato o ottimizzato da un altro strumento di profilatura, l'assembly viene omesso dall'analisi del code coverage.

 L'analisi di code coverage non può essere eseguita su tali assembly.

 Risoluzione disattivare l'ottimizzazione e usare una nuova compilazione.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Codice non gestito (.NET) o codice nativo (C++)
 Analisi verificare che vengano eseguiti alcuni test sul codice gestito o C++ .

 La spiegazione dell'analisi del code coverage in Visual Studio è disponibile solo nelC++codice gestito e nativo (). Se si utilizzano strumenti di terze parti, il codice può essere eseguito parzialmente o totalmente su una piattaforma diversa.

 Risoluzione nessuno disponibile.

### <a name="assembly-has-been-installed-by-ngen"></a>L'assembly è stato installato da NGen
 Analisi verificare che l'assembly non venga caricato dalla cache delle immagini native.

 Spiegazione per motivi di prestazioni, gli assembly di immagini native non vengono analizzati. Per altre informazioni, vedere [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Risoluzione utilizzare una versione MSIL dell'assembly. Non elaborarlo con NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>File personalizzato con estensione runsettings con sintassi non valida
 Analisi se si utilizza un file con estensione runsettings personalizzato, potrebbe contenere un errore di sintassi.

 Di conseguenza, nessun code coverage verrà eseguito. La finestra di code coverage non viene visualizzata alla fine dell'esecuzione del test oppure vengono visualizzati risultati obsoleti.

 Spiegazione è possibile eseguire gli unit test con un file con estensione runsettings personalizzato per configurare le opzioni di code coverage. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).

 Risoluzione sono possibili due tipi di errori:

- **Errore XML**

     Aprire il file con estensione runsettings nell'editor XML di Visual Studio. Individuare le indicazioni degli errori.

- **Errore di espressione regolare**

  Ogni stringa del file è un'espressione regolare. Rivederle singolarmente per individuare gli errori, in particolare cercare:

  - Parentesi non corrispondenti (...) o parentesi non precedute da un carattere di escape \\(...\\). Se si desidera trovare la corrispondenza con una parentesi nella stringa di ricerca, è necessario utilizzare caratteri di escape. Ad esempio, per trovare la corrispondenza con una funzione, usare `.*MyFunction\(double\)`

  - L'asterisco o il segno più all'inizio di un'espressione. Per cercare una stringa di caratteri, utilizzare un punto seguito da un asterisco: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>File personalizzato con estensione runsettings con esclusioni non corrette
 Analisi se si usa un file con estensione runsettings personalizzato, assicurarsi che includa l'assembly.

 Spiegazione è possibile eseguire gli unit test con un file con estensione runsettings personalizzato per configurare le opzioni di code coverage. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).

 Risoluzione rimuovere tutti i nodi `Include` dal file con estensione runsettings, quindi rimuovere tutti i nodi del `Exclude`. Se in tal modo si risolve il problema, riportare i nodi nelle fasi.

 Assicurarsi che il nodo DataCollectors specifichi Code coverage. Confrontarlo con l'esempio presente in [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Il codice verrà sempre visualizzato come parzialmente non analizzato

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Il codice di inizializzazione nelle DLL native viene eseguito prima della strumentazione
 Nell'analisi del codice nativo collegato in modo statico, parte della funzione di inizializzazione **DllMain** e il codice che chiama vengono talvolta visualizzati come non analizzati, anche se il codice è stato eseguito.

 Spiegazione dello strumento di code coverage funziona inserendo la strumentazione in un assembly immediatamente prima dell'avvio dell'esecuzione dell'applicazione. Nell'assembly caricato in precedenza, il codice di inizializzazione in **DllMain** viene eseguito non appena viene caricato l'assembly e prima che venga eseguita l'applicazione. Il codice risulterà non analizzato.

 In genere, questo si applica agli assembly caricati in modo statico.

 Risoluzione nessuno.

## <a name="see-also"></a>Vedere anche
 [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
