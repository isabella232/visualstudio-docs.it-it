---
title: Funzionalità dell'editor del codice
description: Informazioni sulle funzionalità disponibili nell'editor di Visual Studio per semplificare la scrittura e la gestione del codice e del testo.
ms.custom: SEO-VS-2020
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 428c86247686987c6b32c1b6dc109c338f590cd50593c41144e880add7c73b03
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288984"
---
# <a name="features-of-the-code-editor"></a>Funzionalità dell'editor del codice

L'editor di Visual Studio include diverse funzionalità che semplificano la scrittura e la gestione di codice e testo. È possibile espandere e comprimere diversi blocchi di codice usando la struttura. Per altre informazioni sul codice, usare IntelliSense, **Visualizzatore oggetti** e Gerarchia di chiamata. Per trovare il codice, è possibile usare funzionalità quali **Vai a**, **Vai a definizione** e **Trova tutti i riferimenti**. È possibile inserire i blocchi di codice con i frammenti di codice e generare il codice usando funzionalità come **Generazione dall'utilizzo**. Se non è mai stato usato l'editor Visual Studio, vedere [Imparare a usare l'editor di codice.](../get-started/tutorial-editor.md)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor).

Il codice può essere visualizzato in diversi modi. Per impostazione predefinita, **Esplora soluzioni** visualizza il codice organizzato in base ai file. È possibile fare clic sulla scheda **Visualizzazione classi** nella parte inferiore della finestra per visualizzare il codice organizzato in base alle classi.

È possibile cercare e sostituire il testo in singoli file o più file. Per altre informazioni, vedere [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md). È possibile usare espressioni regolari per la ricerca e la sostituzione di testo. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

I diversi linguaggi di Visual Studio offrono set di funzionalità diversi e, in alcuni casi, le funzionalità si comportano in modo diverso a seconda del linguaggio. Molte di queste differenze sono specificate nelle descrizioni delle funzionalità, ma per altre informazioni è possibile vedere le sezioni su linguaggi specifici di Visual Studio.

## <a name="editor-features"></a>Funzionalità dell'editor

|Funzionalità|Descrizione|
|-|-|
|Colorazione della sintassi|Alcuni elementi della sintassi del codice e dei file di markup sono colorati in modo diverso per distinguerli. Ad esempio, le parole chiave (ad esempio `using` in C# e `Imports` in Visual Basic) sono di un colore, mentre i tipi (ad esempio `Console` e `Uri`) sono di un altro colore. Anche altri elementi della sintassi sono colorati, ad esempio i valori letterali stringa e i commenti. C++ usa i colori per distinguere i tipi, le enumerazioni e le macro dagli altri token.<br /><br /> È possibile visualizzare il colore predefinito per ogni tipo ed è possibile modificare il colore per qualsiasi elemento della sintassi specifico nella finestra di dialogo Tipi di carattere e [colori, Ambiente,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)Opzioni , che è possibile aprire dal **menu** Strumenti .|
|Contrassegni di errore e di avviso|Quando si aggiunge codice e si compila la soluzione, vengono visualizzate (a) sottolineature ondulate con diversi colori (note come sottolineature a zigzag) o (b) lampadine nel codice. Le sottolineature rosse denotano errori di sintassi, quelle blu errori del compilatore, quelle verdi gli avvisi e quelle viola altri tipi di errore. Le [Azioni rapide](../ide/quick-actions.md) suggeriscono correzioni dei problemi e ne semplificano l'applicazione.<br /><br /> È possibile visualizzare il colore predefinito per ogni linea onnivaia di errori e avvisi nella finestra di dialogo Tipi di carattere e colori  >    >    >   dell'ambiente Opzioni strumenti . Cercare **Errore di sintassi**, **Errore del compilatore**, **Avviso** e **Altro errore**.|
|Corrispondenza parentesi graffe|Quando il punto di inserimento viene inserito in una parentesi graffa di apertura in un file di codice, il punto e la parentesi graffa di chiusura vengono evidenziati. Questa funzionalità consente di ottenere un feedback immediato sulle parentesi graffe inserite non correttamente o mancanti. È possibile attivare o disattivare la corrispondenza tra parentesi graffe con l'impostazione Evidenziazione **delimitatore** automatica ( Editor **di** testo  >  **opzioni**  >  **strumenti**). È possibile modificare il colore di evidenziazione **nell'impostazione Tipi di** carattere e colori (**Strumenti**  >  **Opzioni**  >  **Ambiente**). Cercare **Corrispondenza parentesi (evidenziate)** o **Corrispondenza parentesi (rettangolo)**.|
|Visualizzatore di struttura|Per facilitare l'individuazione delle coppie di parentesi graffe di apertura e chiusura corrispondenti nel file di codice, vengono visualizzate linee tratteggiate che connettono le parentesi corrispondenti. In questo modo è possibile individuare più rapidamente il codice nella codebase. È possibile attivare o disattivare queste linee nell'opzione **Mostra guide per strutture** nella sezione **Visualizza** della pagina **Strumenti** > **Opzioni** > **Editor di testo** > **Generale**.|
|Numeri di riga|I numeri di riga possono essere visualizzati nel margine sinistro della finestra del codice. Non vengono visualizzati per impostazione predefinita. È possibile attivare questa opzione nelle impostazioni Tutti i linguaggi **dell'editor** di testo **(** Strumenti  >  **Opzioni**  >  **Editor di testo** Tutti i  >  **linguaggi**). È possibile visualizzare i numeri di riga per isingoli linguaggi di programmazione modificando le impostazioni per tali linguaggi  >    >  **(Editor** di testo opzioni strumenti  >  **\<language>** ). Per stampare i numeri di riga, è necessario selezionare **Includi numeri di riga** nella finestra di dialogo **Stampa**.|
|Rilevamento modifiche|Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Le modifiche apportate dall'apertura del file ma non ancora salvate vengono contrassegnate con una barra gialla nel margine sinistro (noto come margine di selezione). Dopo aver salvato le modifiche, ma prima di chiudere il file, la barra diventa verde. Se si annulla una modifica dopo aver salvato il file, la barra diventa arancione. Per attivare e disattivare questa funzionalità, modificare **l'opzione** Rileva modifiche nelle impostazioni dell'editor **di** testo **(** Strumenti  >  **Opzioni**  >  **Editor di testo**).|
|Selezione di codice e testo|È possibile selezionare il testo con la modalità standard a flusso continuo oppure con la modalità riquadro, in cui non viene selezionato un set di righe, ma una porzione rettangolare di testo. Per effettuare una selezione in modalità casella, premere **ALT** mentre si trascina il mouse sulla selezione (o premere **ALT** +  + **\<arrow key>** MAIUSC). La selezione include tutti i caratteri nel rettangolo definiti dal primo e dall'ultimo carattere nella selezione. Tutto ciò che viene digitato o incollato nell'area selezionata viene inserito nello stesso punto di ogni riga.|
|Zoom|È possibile ingrandire o ridurre qualsiasi finestra del codice tenendo premuto il tasto **CTRL** e muovendo la rotellina del mouse (oppure **CTRL**+**MAIUSC**+**.** per aumentare e **CTRL** + **MAIUSC** + **per** diminuire). Per impostare una specifica percentuale di zoom, è anche possibile usare la casella **Zoom** nell'angolo in basso a sinistra della finestra del codice. La funzionalità di zoom non funziona nelle finestre degli strumenti.|
|Spazio virtuale|Per impostazione predefinita, le righe nell'editor di Visual Studio terminano dopo l'ultimo carattere, quindi il tasto **freccia DESTRA** alla fine della riga sposta il cursore all'inizio della riga successiva. In altri editor, una riga non termina dopo l'ultimo carattere ed è possibile posizionare il cursore in qualsiasi punto della riga. È possibile abilitare lo spazio virtuale nell'editor nelle **impostazioni** Strumenti  >  **Opzioni** Editor  >  **di testo** Tutti  >  **i** linguaggi. È possibile abilitare **Spazio virtuale** o **A capo automatico**, ma non entrambi.|
|Stampa|È possibile usare le opzioni nella finestra di dialogo **Stampa** per includere i numeri di riga o nascondere le aree di codice compresse quando si stampa un file. Nella finestra di dialogo **Imposta pagina** è possibile scegliere di stampare il percorso completo e il nome del file scegliendo **Intestazione pagina**.<br /><br /> È possibile impostare le opzioni di stampa a colori nella finestra **di** dialogo Opzioni strumenti  >    >  **Ambiente**  >  **Tipi di** carattere e colori . Scegliere **Stampante** nell'elenco **Mostra impostazioni per** per personalizzare la stampa a colori. Per la stampa di un file è possibile specificare colori diversi rispetto alla modifica di un file.|
|Fasi di rollforward e rollback globali|I comandi **Annulla ultima azione globale** e **Ripeti ultima azione globale** nel menu **Modifica** annullano o ripetono le azioni globali che interessano più file. Le azioni globali includono la ridenominazione di una classe o di uno spazio dei nomi, l'esecuzione di un'operazione di ricerca e sostituzione in una soluzione, il refactoring di un database o altre azioni che modificano più file. È possibile applicare questi comandi globali alle azioni nella sessione corrente di Visual Studio anche dopo aver chiuso la soluzione alla quale è stata applicata un'azione.|

## <a name="advanced-editing-features"></a>Funzionalità di modifica avanzate

È possibile trovare diverse funzionalità avanzate nel menu  >  **Modifica** avanzate sulla barra degli strumenti. Non tutte le funzionalità sono disponibili per tutti i tipi di file di codice.

|Funzionalità|Descrizione|
|-|-|
|Formatta documento|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nel documento.|
|Formatta selezione|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nella selezione.|
|Inserisci tabulazione in righe selezionate|Cambia gli spazi iniziali in tabulazioni dove appropriato.|
|Rimuovi tabulazione da righe selezionate|Cambia le tabulazioni iniziali in spazi. Per convertire tutti gli spazi nel file in tabulazioni (o tutte le tabulazioni in spazi), è possibile usare i comandi `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Questi comandi non vengono visualizzati nei Visual Studio, ma è possibile  chiamarli dalla finestra accesso rapido o dalla finestra di comando.|
|Maiuscole|Converte in maiuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in maiuscolo il carattere nel punto di inserimento. Scelta rapida: + **CTRL+MAIUSC+U.** + |
|Minuscole|Converte in minuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in minuscolo il carattere nel punto di inserimento. Collegamento:  + **CTRL+U.**|
|Sposta in alto righe selezionate|Sposta la riga selezionata di una riga verso l'alto. Collegamento: **ALT FRECCIA** + **SU.**|
|Sposta in basso righe selezionate|Sposta la riga selezionata di una riga verso il basso. Collegamento: **ALT FRECCIA** + **GIÙ.**|
|Elimina spazio vuoto superfluo|Elimina le tabulazioni o gli spazi alla fine della riga corrente. Collegamento:  + **CTRL+K,** **CTRL**+**\\**|
|Mostra/Nascondi spazi|Visualizza gli spazi sotto forma di punti mediani e le tabulazioni sotto forma di frecce. La fine di un file viene visualizzata come un glifo rettangolare. Se **l'opzione** Strumenti Opzioni Editor di testo Tutti i linguaggi Mostra glifi visibili per il ritorno a capo automatico è selezionata, viene visualizzato anche tale  >    >    >    >    >   glifo.|
|A capo automatico|Rende visibili tutte le righe di un documento nella finestra del codice. È possibile attivare e disattivare il ritorno a capo nelle impostazioni **Tutti i linguaggi dell'editor di testo** (**Strumenti** > **Opzioni** > **Editor di testo** > **Tutti i linguaggi**).|
|Commenta selezione|Aggiunge caratteri di commento alla selezione o alla riga corrente. Collegamento: **CTRL** + **K,** **CTRL** + **C**|
|Rimuovi commento selezione|Rimuove tutti i caratteri di commento dalla selezione o dalla riga corrente. Collegamento: **CTRL** + **K,** **CTRL** + **U**|
|Aumenta rientro riga|Aggiunge una tabulazione (o gli spazi equivalenti) alle righe selezionate o alla riga corrente.|
|Riduci rientro riga|Rimuove una tabulazione (o gli spazi equivalenti) dalle righe selezionate o dalla riga corrente.|
|Seleziona tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il tag.|
|Seleziona contenuto tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il contenuto.|

## <a name="navigate-and-find-code"></a>Eseguire ricerche e spostarsi nel codice

È possibile spostarsi nell'editor di codice in diversi modi, tra cui navigare avanti e indietro fino ai punti di inserimento precedenti, visualizzare la definizione di un tipo o membro e passare a un metodo specifico usando la barra di spostamento. Per altre informazioni, vedere [Spostarsi all'interno del codice](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Cercare riferimenti nella codebase

Per trovare i riferimenti a elementi specifici del codice presenti nella codebase, è possibile usare il comando **Trova tutti i riferimenti** o premere **MAIUSC**+**F12**. Inoltre, quando si sceglie un tipo o un membro, la funzionalità di **evidenziazione dei riferimenti** evidenzia automaticamente tutti i riferimenti a quel tipo o membro. Per altre informazioni, vedere [Ricerca di riferimenti nel codice](finding-references.md).

## <a name="customize-the-editor"></a>Personalizzare l'editor

È possibile condividere le impostazioni di Visual Studio con un altro sviluppatore, renderle conformi a uno standard o ripristinare le impostazioni predefinite con il comando **Importazione/Esportazione guidata delle impostazioni** nel menu **Strumenti**. Nell'**Importazione/Esportazione guidata delle impostazioni** è possibile modificare impostazioni generali selezionate oppure impostazioni specifiche di un linguaggio e di un progetto.

Per definire nuovi tasti di scelta rapida o ridefinire i tasti di scelta rapida esistenti, passare a **Strumenti**  >  **Opzioni**  >  **Tastiera**  >  **ambiente**. Per altre informazioni sui tasti di scelta rapida, vedere [Tasti di scelta rapida predefiniti.](../ide/default-keyboard-shortcuts-in-visual-studio.md)

Per le opzioni dell'editor specifiche per JavaScript, vedere le [opzioni dell'editor JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Vedi anche

- [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor)
- [IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Introduzione a C++ in Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Introduzione a C# e ad ASP.NET Core in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Introduzione a Python in Visual Studio](../ide/quickstart-python.md)
