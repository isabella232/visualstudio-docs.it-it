---
title: Esercitazione sull'uso di Python, passaggio 3, uso della finestra interattiva REPL
description: Passaggio 3 della procedura dettagliata di base sulle funzionalità di Visual Studio, dedicato alla finestra interattiva REPL di Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 00a66cb56fb3ada8f48018c644a37189b494cc98
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511756"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Passaggio 3: Usare la finestra interattiva REPL

**Passaggio precedente: [Scrivere ed eseguire codice](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La finestra **Interattiva** di Visual Studio per Python offre un'esperienza completa REPL (Read–Eval–Print Loop), che consente di ridurre notevolmente il normale ciclo di modifica-compilazione-debug. La finestra **Interattiva** offre tutte le funzionalità dell'esperienza REPL della riga di comando di Python. Rende anche molto semplice lo scambio di codice con i file di origine dell'editor di Visual Studio, che altrimenti risulta eccessivamente complessa con la riga di comando.

1. Aprire la finestra **Interattiva** facendo clic col pulsante destro del mouse sull'ambiente Python del progetto in **Esplora soluzioni**, come **Python 3.6 (32 bit)** illustrato in precedenza, e selezionando **Apri finestra interattiva**. In alternativa, è possibile selezionare **Visualizza** > **Altre finestre** > **Finestre interattive Python** dal menu principale di Visual Studio.

1. La finestra **Interattiva** si apre sotto l'editor con il prompt REPL standard **>>>** Python. L'elenco a discesa **Ambiente** consente di selezionare un interprete specifico da utilizzare. In alcuni casi può essere necessario ingrandire la finestra **Interattiva**. A tale scopo, trascinare il separatore tra le due finestre:

    ![Finestra interattiva di Python e trascinamento per ridimensionarla](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > In Visual Studio è possibile ridimensionare tutte le finestre trascinando i separatori confinanti. È anche possibile trascinare le finestre in modo indipendente dal frame di Visual Studio e ridisporle come si vuole all'interno della cornice. Per altre informazioni, vedere [Personalizzare il layout delle finestre](../ide/customizing-window-layouts-in-visual-studio.md).

1. Immettere alcune istruzioni (ad esempio `print("Hello, Visual Studio")`) ed espressioni (ad esempio `123/456`) per visualizzare i risultati immediati:

    ![Risultati immediati nella finestra interattiva di Python](media/vs-getting-started-python-12-interactive2.png)

1. Quando si inizia a scrivere un'istruzione su più righe, ad esempio una definizione di funzione, la finestra **Interattiva** mostra il prompt **...** di Python per le righe di continuazione, per le quali è disponibile il rientro automatico, diversamente dall'ambiente REPL dalla riga di comando:

    ![Finestra interattiva di Python con continuazione dell'istruzione](media/vs-getting-started-python-13-interactive3.png)

1. La finestra **Interattiva** offre una cronologia completa di tutti gli elementi immessi e migliora l'ambiente REPL dalla riga di comando con elementi della cronologia su più righe. Ad esempio, è possibile chiamare facilmente l'intera definizione della funzione `f` come singola unità e modificare in modo semplice il nome in `make_double`, invece di dover ricreare la funzione riga per riga.

1. Visual Studio può inviare più righe di codice da una finestra dell'editor alla finestra **Interattiva**. Questa funzionalità consente di mantenere il codice in un file di origine e di inviarne facilmente parti selezionate alla finestra **Interattiva**. È quindi possibile usare questi frammenti di codice nell'ambiente REPL rapido piuttosto che dover eseguire l'intero programma. Per visualizzare questa funzionalità, sostituire il ciclo `for` nel file *PythonApplication1.py* con le operazioni seguenti:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Selezionare solo le istruzioni `import` e `from` nel file con estensione *py*, fare clic con il pulsante destro del mouse e selezionare **Invia a Interattiva** o premere **CTRL**+**INVIO**. Il frammento di codice viene incollato immediatamente nella finestra **Interattiva** ed eseguito. Selezionare la funzione `make_dot_string` e ripetere il comando stesso, che esegue di nuovo tale frammento di codice. Dato che il codice definisce una funzione, è possibile testare rapidamente la funzione chiamandola più volte:

    ![Invio del codice alla finestra interattiva e test](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > L'uso di **CTRL**+**INVIO** nell'editor *senza* effettuare una selezione esegue la riga corrente di codice nella finestra **Interattiva** e posiziona automaticamente il punto di inserimento nella riga successiva. Con questa funzionalità, se si preme ripetutamente **CTRL**+**INVIO** si ottiene un modo pratico per esaminare il codice che non è possibile eseguire con solo la riga di comando di Python. Consente anche di esaminare il codice senza eseguire il debugger e senza avviare necessariamente il programma dall'inizio.

1. È anche possibile copiare e incollare più righe di codice nella finestra **Interattiva** da qualsiasi origine, come il frammento di codice riportato di seguito, che è difficile eseguire con le transazioni di replica della riga di comando di Python. Quando il codice viene incollato, la finestra **Interattiva** lo esegue, come se fosse stato digitato:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Incollare più righe di codice tramite l'invio alla finestra interattiva](media/vs-getting-started-python-15-interactive5.png)

1. Come è possibile vedere, questo codice funziona correttamente, tuttavia l'output non è molto evocativo. Un valore passaggio diverso nel ciclo `for` potrebbe visualizzare più dell'onda coseno. Dato che l'intero ciclo `for` è presente nella cronologia REPL come singola unità, è facile tornare indietro e apportare qualsiasi modifica, per poi testare di nuovo la funzione. Premere la freccia in su per chiamare il ciclo `for`. Premere quindi sulle frecce verso sinistra o destra per avviare l'esplorazione del codice (fino a tale momento, le frecce su e giù continuano a scorrere la cronologia). Individuare e modificare la specifica `range` in `range(0, 360, 12)`. Premere **CTRL**+**INVIO** in qualsiasi punto nel codice per eseguire di nuovo l'intera istruzione:

    ![Modifica di un'istruzione precedente nella finestra interattiva](media/vs-getting-started-python-16-interactive6.png)

1. Ripetere il processo per sperimentare con impostazioni diverse i passaggi fino a individuare un valore desiderato. È anche possibile rendere la ripetizione dell'onda aumentando l'intervallo, ad esempio, `range(0, 1800, 12)`.
 
1. Quando si è soddisfatti del codice scritto nella finestra **Interattiva**, selezionarlo, fare clic con il pulsante destro del mouse e scegliere **Copia codice** (**CTRL**+**MAIUSC**+**C**) quindi incollarlo nell'editor. Questa funzionalità speciale di Visual Studio omette automaticamente qualsiasi output, così come i prompt `>>>` e `...`. Ad esempio, nell'immagine seguente viene illustrato l'uso del comando **Copia codice** su una selezione che include prompt e output:

    ![Comando copia codice della finestra interattiva su una selezione con prompt e output](media/vs-getting-started-python-17-interactive7.png)

    Quando si procede con la funzione incolla nell'editor, si ottiene solo il codice:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Per copiare il contenuto esatto di una finestra **Interattiva** compresi output e prompt, usare il comando standard **Copia**.

1. Le modifiche appena apportate consentono di usare l'ambiente REPL rapido della finestra **Interattiva** per elaborare i dettagli di una piccola parte di codice e aggiungerla facilmente al file di origine del progetto. Quando si esegue nuovamente il codice con **CTRL**+**F5** (o **Debug** > **Avvia senza eseguire debug**), viene visualizzato il risultato previsto.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Approfondimento

- [Usare la finestra Interattiva](python-interactive-repl-in-visual-studio.md)
- [Usare REPL IPython](interactive-repl-ipython.md)
