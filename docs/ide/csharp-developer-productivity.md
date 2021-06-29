---
title: Aumentare la produttività per lo sviluppo .NET
description: Panoramica di esplorazione, analisi del codice, testing unità e altre funzionalità che consentono di scrivere codice .NET in modo più efficiente e veloce.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 09a33db9df8e1309792cd6a3722bb82333348d84
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038655"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Guida per la produttività di Visual Studio per gli sviluppatori C#

Informazioni su come Visual Studio consente agli sviluppatori di essere ancora più produttivi, grazie ai miglioramenti che interessano prestazioni e produttività, come l'esplorazione di assembly decompilati, suggerimenti di nomi di variabili durante la digitazione, una visualizzazione della gerarchia in **Esplora test**, l'uso di Vai a tutti (**CTRL**+**T**) per passare alle dichiarazioni di file/tipo/membro/simbolo, un **Helper eccezioni** intelligente, configurazione e imposizione dello stile del codice e molti refactoring e correzioni del codice.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Utente abituato a usare i tasti di scelta rapida di un altro editor

::: moniker range="vs-2017"

**Novità in Visual Studio 2017 versione 15.8**

::: moniker-end

Se si è abituati a usare un IDE o un ambiente di codifica diverso, è possibile modificare lo schema della tastiera per *Visual Studio Code* o *ReSharper (Visual Studio)*:

![Schemi della tastiera di Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Alcune estensioni offrono anche gli schemi della tastiera:

- [HotKeys per Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulazione Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Di seguito sono riportate alcune combinazioni di tasti di scelta rapida comuni di Visual Studio:

| Tasti di scelta rapida (tutti i profili) | Comando | Descrizione |
|-|-|-|
| **CTRL** + **T** | Vai a tutti | Consente di passare a qualsiasi dichiarazione di file, tipo, membro o simbolo |
| **F12** (anche  + **CTRL+CLIC)** | Vai a definizione | Consente di passare al punto in cui si trova la definizione di un simbolo |
| **CTRL** + **F12** | Vai all'implementazione | Consente di passare da un tipo o membro di base alle varie implementazioni di questo. |
| **MAIUSC** + **F12** | Trova tutti i riferimenti | Consente di visualizzare tutti i riferimenti di simboli o valori letterali |
| **ALT** + **Home page** | Vai a base | Spostarsi verso l'alto nella catena di ereditarietà |
| **CTRL** + **.** (anche **ALT)** + **Immettere** nel profilo C#) | Azioni rapide e refactoring | Visualizza le correzioni e le azioni di generazione di codice, i refactoring e altre azioni rapide disponibili in corrispondenza della posizione del cursore o del codice selezionato |
| **CTRL** + **D** | Duplicare una riga | Duplica la riga di codice in cui si trova il cursore (disponibile in **Visual Studio 2017 versione 15.6** e versioni successive) |
| **MAIUSC** + **ALT**+**+**/**-** | Espandi/Comprimi selezione | Espande o comprime la selezione corrente nell'editor (disponibile in **Visual Studio 2017 versione 15.5** e versioni successive) |
| **MAIUSC**  +  **ALT**  +  **.** | Inserisci punto di inserimento corrispondente successivo | Aggiunge una selezione e un punto di inserimento nella posizione successiva che corrisponde alla selezione corrente (disponibile in **Visual Studio 2017 versione 15.8** e versioni successive) |
| **CTRL** + **Q** | Ricerca | Consente di effettuare una ricerca all'interno di tutte le impostazioni di Visual Studio |
| **F5** | Avvia debug | Avvia il debug dell'applicazione |
| **CTRL** + **F5** | Esecuzione senza debug | Esegue l'applicazione in locale senza debug |
| **CTRL** + **K**,**D** (profilo predefinito) o **CTRL** + **E**,**D** (profilo C#) | Formatta documento | Corregge le violazioni alle regole di formattazione nel file in base alle impostazioni relative alle nuove righe, alla spaziatura e ai rientri |
| **CTRL,** + **\\** **CTRL** + **E** (profilo predefinito) o **CTRL** + **W**,**E** (profilo C#) | Visualizzazione dell'elenco errori | Consente di visualizzare tutti gli errori nel documento, nel progetto o nella soluzione |
| **ALT**  +  **PgUp/PgDn** | Passa a problema successivo/precedente | Passa all'errore, avviso, suggerimento precedente/successivo nel documento (disponibile in **Visual Studio 2017 versione 15.8** e versioni successive) |
| **CTRL** + **K**,**/** | Attiva/Disattiva commento a riga singola/Rimuovi commento | Questo comando aggiunge o rimuove un commento a riga singola a seconda che la selezione sia o meno già commentata |
| **CTRL** + **MAIUSC**+**/** | Attiva/Disattiva commento per il blocco/Rimuovi commento | Questo comando aggiunge o rimuove commenti per il blocco a seconda dell'elemento selezionato |

> [!NOTE]
> Alcune estensioni separano i tasti di scelta rapida predefiniti di Visual Studio. Per usare i comandi precedenti, ripristinare i tasti di scelta rapida Visual Studio impostazioni predefinite del menu Strumenti Importa/Esporta Impostazioni Reimposta tutte le impostazioni o Reimpostazione della tastiera in Opzioni  >    >     >    >    >  **strumenti**.

Per altre informazioni sui tasti di scelta rapida e i comandi, vedere [Tasti di scelta rapida per la produttività](../ide/productivity-shortcuts.md) e [Tasti di scelta rapida più comuni](default-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Passare rapidamente a file o tipi

Visual Studio offre una funzionalità denominata **Vai a tutti** (**CTRL**+**T**). **Vai a tutti consente** di passare rapidamente a qualsiasi dichiarazione di file, tipo, membro o simbolo.

- Per cambiare la posizione di questa barra di ricerca o disattivare l'anteprima della funzionalità di spostamento in tempo reale, usare l'icona a forma di **ingranaggio**.
- Filtrare i risultati usando sintassi come `t mytype`.
- Limitare l'ambito di ricerca al documento corrente.
- La corrispondenza camelCase è supportata.

![Vai a tutti in Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Applicare le regole di stile del codice

È possibile usare un file EditorConfig per codificare le convenzioni per la scrittura del codice e spostarle con l'origine.

![Imposizione dello stile del codice in Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Aggiungere un valore predefinito o . File EditorConfig di tipo NET nel progetto scegliendo **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** cercare "editorconfig". Selezionare uno dei due modelli di elemento **File editorconfig** e quindi scegliere **Aggiungi**.

   ![Modelli di elemento EditorConfig in Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Creare automaticamente un file *con estensione editorconfig* in base alle impostazioni di stile del codice in **Strumenti** Opzioni Editor di >  > **testo** Stile codice >  > **C#.**

   ![Generare un file con estensione editorconfig dalle impostazioni in Visual Studio 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- La [funzionalità di inferenza del codice](/visualstudio/intellicode/code-style-inference) di IntelliCode per Visual Studio deduce gli stili del codice dal codice esistente. Viene quindi creato un file EditorConfig non vuoto con le preferenze di stile del codice già definite.

- Configurare il livello di gravità di una regola di stile del codice direttamente tramite l'editor. Se attualmente non si dispone di un file con estensione editorconfig, ne verrà generato uno automaticamente. Posizionare il cursore sull'errore, sull'avviso o sul suggerimento e digitare  + **CTRL.** per aprire il menu Azioni rapide e refactoring. Selezionare **Configura o Elimina problemi.** Selezionare quindi la regola e scegliere il livello di gravità che si vuole configurare per la regola. Il file EditorConfig esistente verrà così aggiornato con la nuova gravità della regola.

   ![Configurare il livello di gravità di una regola di stile del codice direttamente nell'editor](../ide/media/configure-severity-level.png)

Vedere la documentazione relativa alle [opzioni delle convenzioni per la scrittura del codice .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options), che contiene anche un esempio di file EditorConfig completo.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Pulizia del codice

Visual Studio offre la formattazione on-demand del file di codice, incluse le preferenze di stile per il codice, attraverso la funzionalità **Pulizia del codice**. Per eseguire Pulizia codice, fare clic sull'icona della scope nella parte inferiore dell'editor o premere **CTRL** + **K**, **CTRL** + **E**.

![Pulsante Pulizia del codice in Visual Studio 2019](media/execute-code-cleanup.png)

È anche possibile eseguire la pulizia del codice per l'intero progetto o soluzione. Fare clic con il pulsante destro del mouse sul nome del progetto o della soluzione in **Esplora soluzioni**, selezionare **Analizza ed esegui pulizia del codice** e quindi selezionare **Esegui pulizia del codice**.

![Eseguire Pulizia del codice per l'intero progetto o soluzione](media/run-code-cleanup-project-solution.png)

Oltre alla formattazione del file in termini di spazi, rientri e così via, **Pulizia del codice** applica anche gli stili del codice selezionati. Le preferenze per ogni stile del codice vengono lette dal [file EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), se ce n'è uno per il progetto, o dalle [impostazioni di stile del codice](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) nella finestra di dialogo **Opzioni**.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refactoring e correzioni del codice

Visual Studio include numerosi refactoring, azioni di generazione del codice e correzioni del codice. Le sottolineature rosse rappresentano errori, quelle verdi rappresentano gli avvisi e tre punti grigi rappresentano suggerimenti per il codice. È possibile accedere alle correzioni del codice facendo clic sulla lampadina o sull'icona del cacciavite o premendo + **CTRL.** o  + **ALT+INVIO.** Ogni correzione è dotata di una finestra di anteprima che mostra come funziona la correzione in un diff di codice live.

Le correzioni rapide e i refactoring più comuni includono:

- Rinominare
- Estrai metodo
- Cambia firma metodo
- Genera costruttore
- Genera metodo
- Sposta il tipo nel file
- Aggiungi il controllo Null
- Aggiungi parametro
- Rimuovi istruzioni using non necessarie
- Ciclo foreach verso query o metodi LINQ
- Pull di membri

Per altre informazioni, vedere Funzionalità [di generazione del codice](code-generation-in-visual-studio.md).

È possibile [installare gli analizzatori FxCop](../code-quality/install-fxcop-analyzers.md) per contrassegnare i problemi del codice. Oppure è possibile scrivere refactoring o correzioni del codice propri con gli [analizzatori Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md).

Diversi membri della community hanno scritto estensioni gratuite che aggiungono controlli aggiuntivi del codice:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint per Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint per Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refactoring in Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Accesso agli utilizzi, all'implementazione e agli assembly decompilati

Visual Studio include molte funzionalità che consentono di eseguire ricerche e di [esplorare il codice](../ide/navigating-code.md).

| Funzionalità | Tasto di scelta rapida | Dettagli/Miglioramenti |
|- | - | -|
| Trova tutti i riferimenti | **MAIUSC** + **F12**| I risultati sono colorati e possono essere raggruppati per progetto, definizione e tipo riferimento, ad esempio lettura o scrittura. È anche possibile "bloccare" i risultati. |
| Vai all'implementazione | **CTRL** + **F12** | È possibile usare Vai a definizione nella parola chiave `override` per passare al membro sostituito |
| Vai a definizione | **F12 o** **CTRL+CLIC** + | Premere **CTRL** mentre si fa clic per passare alla definizione |
| Visualizza definizione | **ALT** + **F12** | Visualizzazione inline di una definizione |
| Visualizzatore di struttura | Linee grigie tratteggiate tra parentesi graffe | Passare il mouse per visualizzare la struttura del codice |
| Spostamento agli assembly decompilati | **F12 o** **CTRL+CLIC** +  | Passare all'origine esterna (decompilata con ILSpy) abilitando la **funzionalità:** Opzioni degli strumenti Editor di testo C# Avanzate Abilitare lo spostamento alle  >    >    >    >    >  **origini decompilate.** |

![Vai a tutti e Trova tutti i riferimenti](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Funzionalità IntelliSense migliorata

Usare IntelliCode per Visual Studio per ottenere il [completamento del codice con riconoscimento del contesto](/visualstudio/intellicode/intellicode-visual-studio) invece di un semplice elenco in ordine alfabetico. È possibile anche eseguire il training di un [modello IntelliSense personalizzato](/visualstudio/intellicode/custom-model-faq) basato su librerie specifiche del dominio.

## <a name="unit-testing"></a>Unit test

A partire da Visual Studio 2017, esistono numerosi miglioramenti per l'esperienza di test. È possibile eseguire test con i framework MSTest v1, MSTest v2, NUnit o XUnit.

- L'individuazione dei test in **Esplora test** è veloce.

- È possibile organizzare i test in **Esplora test** con l'*ordinamento gerarchico*.

   ![Visualizzazione della gerarchia per Esplora test in Visual Studio](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md) esegue continuamente i test influenzati dalle modifiche del codice e aggiorna le icone dell'editor inline per conoscere lo stato dei test. Includere o escludere progetti di test o test specifici dal set di test attivi. (Solo per Visual Studio Enterprise Edition.)

## <a name="debugging"></a>Debug

Alcune delle funzionalità di debug di Visual Studio includono:

::: moniker range=">=vs-2019"

- La possibilità di cercare una stringa all'interno delle finestre **Espressioni di controllo**, **Auto** e **Variabili locali**.
- L'*esecuzione fino alla riga selezionata* che consente di passare il puntatore del mouse accanto a una riga di codice, fare clic sull'icona verde di riproduzione ed eseguire il programma fino a raggiungere tale riga.
- L'**Helper eccezioni** che inserisce le informazioni più importanti al primo livello della finestra di dialogo, ad esempio quale variabile è `null` in una `NullReferenceException`.
- Il [debug Torna indietro](../debugger/view-historical-application-state.md) che consente di tornare ai punti di interruzione o ai passaggi precedenti e visualizzare lo stato precedente dell'applicazione.
- Il [debug di snapshot](/azure/application-insights/app-insights-snapshot-debugger) che consente di esaminare lo stato di un'applicazione Web attiva nel momento in cui viene generata un'eccezione (è necessario essere in Azure).

::: moniker-end

::: moniker range="vs-2017"

- L'*esecuzione fino alla riga selezionata* che consente di passare il puntatore del mouse accanto a una riga di codice, fare clic sull'icona verde di riproduzione ed eseguire il programma fino a raggiungere tale riga.
- L'**Helper eccezioni** che inserisce le informazioni più importanti al primo livello della finestra di dialogo, ad esempio quale variabile è `null` in una `NullReferenceException`.
- Il [debug Torna indietro](../debugger/view-historical-application-state.md) che consente di tornare ai punti di interruzione o ai passaggi precedenti e visualizzare lo stato precedente dell'applicazione.
- Il [debug di snapshot](/azure/application-insights/app-insights-snapshot-debugger) che consente di esaminare lo stato di un'applicazione Web attiva nel momento in cui viene generata un'eccezione (è necessario essere in Azure).

::: moniker-end

![Helper eccezioni in Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Controllo della versione

È possibile usare Git o il controllo della versione di Team Foundation per archiviare e aggiornare il codice in Visual Studio.

::: moniker range=">=vs-2019"

- Installare le [richieste pull per Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) per creare, rivedere, eseguire il checkout ed eseguire le richieste pull senza uscire da Visual Studio.

::: moniker-end

- Organizzare le modifiche locali in [Team Explorer](reference/team-explorer-reference.md) e usare la barra di stato per tenere traccia di commit e modifiche in sospeso.

- Configurare l'integrazione e il recapito continui per i progetti ASP.NET all'interno di Visual Studio con l'estensione [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Controllo del codice sorgente in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Quali altre funzionalità occorre conoscere

Ecco un elenco di funzionalità editor e di produttività per rendere più efficiente la scrittura del codice. È possibile che alcune funzionalità debbano essere abilitate perché disabilitate per impostazione predefinita in quanto potrebbero indicizzare elementi del computer, essere controverse o essere ancora in forma sperimentale.

| Funzionalità | Dettagli | Abilitazione |
|-|-|-|
| Individuare il file in Esplora soluzioni | Evidenzia il file attivo in **Esplora soluzioni** | **Strumenti**  >  **Opzioni**  >  **Progetti e soluzioni**  >  **Tenere traccia dell'elemento attivo in Esplora soluzioni** |
| Aggiungere le direttive using per i tipi in assembly di riferimento e pacchetti NuGet | Visualizza una lampadina di errore con una correzione del codice per installare un pacchetto NuGet per un tipo senza riferimenti | **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Avanzate**  >  **Suggerire using per i tipi negli assembly di riferimento e** **Suggerisci using per i tipi nei pacchetti NuGet** |
| Abilita analisi della soluzione completa | Visualizzare tutti gli errori nella soluzione **nell'Elenco errori** | **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Avanzate**  >  **Abilitare l'analisi completa della soluzione** |
| Abilita spostamento a origini decompilate | Consente l'uso di Vai a definizione per tipi o membri di origini esterne e del decompilatore ILSpy per visualizzare i corpi dei metodi | **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Avanzate**  >  **Abilitare la navigazione nelle origini decompilate** |
| Modalità di terminazione/suggerimento | Modifica il comportamento di completamento in IntelliSense. Gli sviluppatori con esperienza di IntelliJ tendono a usare un'impostazione non predefinita in questo caso. | **Menu**  >  **Modifica**  >  **IntelliSense**  >  **Attiva/Disattiva modalità di completamento** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Visualizza le informazioni di riferimento del codice e la cronologia modifiche nell'editor (gli indicatori CodeLens del controllo del codice sorgente non sono disponibili nell'edizione Visual Studio Community). | **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **Tutti i linguaggi**  >  **CodeLens** |
| [Frammenti di codice](../ide/visual-csharp-code-snippets.md) | Utili per di generare codice boilerplate comune | Digitare il nome di un frammento di codice e **premere TAB due** volte. |
