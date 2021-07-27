---
title: Finestra REPL interattiva per R
description: Come usare l'ambiente REPL interattivo per R in Visual Studio, integrato nelle finestre dell'editor.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 40ecca9e6381095d292b9a5205419acc9957499c
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679672"
---
# <a name="work-with-the-r-interactive-window"></a>Usare la finestra R interattivo

R Tools per Visual Studio (RTVS) offre una finestra R interattivo, nota anche come finestra **REPL** (Read-Evaluate-Print-Loop), in cui è possibile immettere codice R e vedere immediatamente i risultati. Tutti i moduli, la sintassi e le variabili, così come IntelliSense, sono disponibili nella finestra interattiva.

La finestra interattiva è anche integrata con le finestre regolari dell'editor di R. È possibile selezionare il codice e premere **CTRL** INVIO oppure fare clic con il pulsante destro del mouse e scegliere Esegui in interattivo. Il codice viene eseguito riga per riga nella finestra interattiva come se fosse stato digitato + direttamente.  Quando il cursore si trova su una singola riga in una finestra dell'editor, **CTRL** INVIO invia tale riga alla finestra interattiva e quindi sposta il +  cursore sulla riga successiva. In questo modo è sufficiente premere **ripetutamente CTRL** + **INVIO** per eseguire il codice un'istruzione alla volta.

Per sperimentare queste funzionalità, seguire la procedura dettagliata illustrata in [Introduzione a R](getting-started-with-r.md) o le sezioni in questo articolo. I [frammenti di codice](code-snippets-for-r.md) funzionano anche nella finestra interattiva così come avviene nelle finestre dell'editor di R.

## <a name="overview-of-the-interactive-window"></a>Panoramica della finestra interattiva

Se si digita un codice R valido e si preme **INVIO** alla fine della riga, viene eseguito il codice di tale riga:

```repl
> 3 + 3
[1] 6
```

Se **si preme INVIO** in un punto qualsiasi di un input a riga singola, viene eseguita anche tale riga.

Tutti gli input e output precedenti di REPL sono di sola lettura e non possono essere modificati. Tuttavia, è possibile selezionare, copiare e incollare testo dalla finestra in qualsiasi momento. Il codice incollato viene eseguito come se fosse stato immesso riga per riga.

Infatti, quando si inizia a digitare un'istruzione e si preme **INVIO**, RTVS riconosce se l'istruzione deve essere continuata e passa alla modalità a più righe aggiungendo un prompt + a sinistra della riga e un rientro appropriato. RTVS completa anche le parentesi tonde, le parentesi quadre e le parentesi graffe:

![Immissione di istruzioni a più righe nella finestra interattiva](media/repl-multiline-entry.png)

In questa modalità a più righe, il tasto **INVIO** esegue il blocco di codice solo quando è posizionato alla fine del blocco, altrimenti inserisce una nuova riga. È tuttavia possibile premere **CTRL** + **INVIO in** qualsiasi posizione per eseguire immediatamente il blocco di codice.

### <a name="toolbar-commands"></a>Comandi della barra degli strumenti

Ecco la finestra interattiva con relativa barra degli strumenti:

![Finestra interattiva con la barra degli strumenti](media/repl-window.png)

I comandi della barra degli strumenti sono i seguenti, la maggior parte dei quali ha equivalenti da tastiera e sono disponibili anche nei menu Sessione di **R Tools** e Directory di lavoro di R Tools (o come  >     >   indicato):

| Button | Comando | Combinazione di tasti | Descrizione |
| --- | --- | --- | --- |
| ![Pulsante di reset](media/repl-toolbar-01-reset.png) | Reset | **CTRL** + **MAIUSC** + **F10** | Reimposta la sessione della finestra interattiva, cancellando tutte le variabili e la cronologia. |
| ![Pulsante Cancella](media/repl-toolbar-02-clear.png) | Cancella | **CTRL** + **L** | Cancella l'output visualizzato nella finestra interattiva. Non ha alcun effetto sulle variabili della sessione o sulla cronologia. |
| ![Pulsanti Cronologia](media/repl-toolbar-03-history.png) | Comando Cronologia precedente<br/>Comando Cronologia successiva | **Freccia SU**, **Freccia GIÙ**<br/>**ALT** + **Su,** **ALT in** + **basso** | Scorre la cronologia, con determinati comportamenti per i blocchi di codice su più righe. Vedere [Cronologia](#history). |
| ![Pulsante Carica area di lavoro](media/repl-toolbar-04-load-workspace.png) | Carica area di lavoro | n/d | Carica un'area di lavoro precedentemente salvata (vedere [Aree di lavoro e sessioni](#workspaces-and-sessions). |
| ![Pulsante Salva area di lavoro come](media/repl-toolbar-05-save-workspace-as.png)| Salva area di lavoro come | n/d | Salva lo stato corrente della sessione come area di lavoro (vedere [Aree di lavoro e sessioni](#workspaces-and-sessions). |
| ![Pulsante Script R di origine](media/repl-toolbar-06-source-r-script.png) | Script R di origine | **CTRL** + **MAIUSC** + **S** | Chiama `source` con lo script R attualmente attivo nell'editor di Visual Studio, che esegue il codice.  Questo pulsante viene visualizzato solo se è aperto un file R nell'editor di Visual Studio. |
| ![Pulsante Script R di origine con eco](media/repl-toolbar-07-source-r-script-with-echo.png) | Script R di origine con eco | **CTRL** + **MAIUSC** + **Immettere** | È simile allo script R di origine, ma visualizza il contenuto dello script nella finestra interattiva. |
| ![Pulsante Interrompi R](media/repl-toolbar-08-interrupt-r.png)| Interrompi R | **ESC** | Arresta qualsiasi codice in esecuzione nella finestra interattiva, ad esempio il ciclo `while` illustrato nella schermata all'inizio di questa sezione. |
| ![Pulsante Collega debugger](media/repl-toolbar-09b-attach-debugger.png)| Collega debugger | n/d | Disponibile anche tramite il **comando Debug** attach  >  **to R interattivo** . |
| ![Pulsante Imposta la directory di lavoro sul percorso del file di origine](media/repl-toolbar-10-set-working-directory-source.png)| Imposta la directory di lavoro sul percorso del file di origine | **CTRL** + **MAIUSC** + **E** | Imposta la directory di lavoro sul file di origine più recentemente caricato nella finestra interattiva tramite `source`. Vedere [Directory di lavoro](#working-directory). |
| ![Pulsante Imposta la directory di lavoro sul percorso del progetto](media/repl-toolbar-11-set-working-directory-to-project.png) | Imposta la directory di lavoro sul percorso del progetto | **CTRL** + **MAIUSC** + **P** | Imposta la directory di lavoro sulla radice del progetto attualmente caricato in Visual Studio. Vedere [Directory di lavoro](#working-directory). |
| (Campo testo) | Seleziona directory di lavoro | n/d | Campo di input diretto per la directory di lavoro. Vedere [Directory di lavoro](#working-directory). |

## <a name="workspaces-and-sessions"></a>Aree di lavoro e sessioni

L'esecuzione di codice nella finestra interattiva crea un contesto nella sessione corrente. Il contesto è costituito da variabili globali, definizioni di funzione, carichi di libreria e così via. Questo contesto viene collettivamente denominato *area di lavoro*. È possibile salvare e caricare aree di lavoro in qualsiasi momento.

La selezione del pulsante **Salva area di lavoro come** o l'uso del comando **R Tools** > **Sessione** > **Salva area di lavoro come** richiede un percorso e un nome file (l'estensione predefinita è *RData*).

Per salvare un'area di lavoro con un nome file specifico (il nome predefinito è *.RData*), fare clic sul pulsante **Salva area di lavoro** in REPL:

Per ricaricare un'area di lavoro salvata in precedenza, selezionare il pulsante **Carica area di lavoro** oppure usare **R Tools** > **Sessione** > **Carica area di lavoro** e passare al file dell'area di lavoro.

Il pulsante **Reimposta** o il comando **R Tools** > **Sessione** > **Reimposta** cancella il contesto della sessione. Se si usa una sessione remota, la procedura di reimpostazione elimina anche il profilo utente nel computer remoto per cancellare tutti i file in esso archiviati. Vedere [Aree di lavoro](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).

## <a name="working-directory"></a>Directory di lavoro

Gli sviluppatori vogliono in genere modificare la directory di lavoro durante una sessione interattiva. Vari comandi, disponibili sulla barra degli strumenti, il menu directory di lavoro di **R Tools** e il menu di scelta rapida del progetto consentono di impostare facilmente una directory di lavoro sul percorso di un file di origine, il percorso o il progetto o qualsiasi altro percorso  >   arbitrario. In questo modo è possibile evitare di digitare percorsi completi o percorsi lunghi quando si fa riferimento ai file.

## <a name="history"></a>Cronologia

Ogni riga immessa nella finestra interattiva, incluse le righe inviate da un editor, viene mantenuta nella cronologia di REPL. È quindi possibile spostarsi nella cronologia con la freccia GIÙ o SU, come avviene nella riga di comando.

Una differenza consiste nel fatto che, se si inizia a digitare nella riga corrente e si preme la freccia SU, tale riga corrente viene mantenuta nella cronologia anche se non è stata ancora eseguita.

La cronologia nella finestra interattiva funziona anche in modo intelligente con le istruzioni di un altro blocco di codice che si estendono su righe. Quando si scorre la cronologia con freccia SU e freccia GIÙ, i blocchi di codice a più righe vengono recuperati come unità intera e visualizzati come voce corrente. A questo punto, i tasti di direzione scorrono il blocco di codice riga per riga, fino a quando non viene raggiunto l'inizio o la fine del blocco. All'inizio del blocco di codice, la freccia SU recupera l'elemento precedente nella cronologia. Nell'ultima riga del blocco, la freccia GIÙ recupera l'elemento successivo.

Questo comportamento si adatta al caso tipico di rieseguire l'ultimo elemento della cronologia con una combinazione di tasti Freccia SU e INVIO, consentendo naturalmente la modifica di un blocco di codice su più righe premendo la freccia SU per spostarsi al suo interno. 

Per evitare di spostarsi all'interno di blocchi di codice su più righe, usare i pulsanti della barra degli strumenti o **ALT** SU e ALT GIÙ e tutti questi blocchi vengono considerati +  come una  - singola riga.

Il modo più semplice per sperimentare le funzionalità della cronologia è provarle nella finestra interattiva. Il codice riportato di seguito include diverse istruzioni a una riga e a più righe. Copiare e incollare ogni istruzione individualmente per creare la cronologia appropriata. È anche possibile incollare il codice in un file di codice separato e quindi inviare le righe alla finestra interattiva con **CTRL** + **Immettere**.

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```