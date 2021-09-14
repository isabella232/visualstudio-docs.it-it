---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 3, finestra interattiva REPL
titleSuffix: ''
description: Passaggio 3 della procedura dettagliata di base sulle funzionalità di Visual Studio, dedicato alla finestra interattiva REPL di Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7d2d8684759b56b577402840ee4a748e618e6a39
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628277"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Passaggio 3: Usare la finestra interattiva REPL

**Passaggio precedente: [Scrivere ed eseguire codice](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La Visual Studio **interattiva** per Python offre un'esperienza REPL (Read-Evaluate-Print-Loop) ricca che abbrevia notevolmente il consueto ciclo edit-build-debug. La finestra **Interattiva** offre tutte le funzionalità dell'esperienza REPL della riga di comando di Python. Rende anche molto semplice lo scambio di codice con i file di origine dell'editor di Visual Studio, che altrimenti risulta eccessivamente complessa con la riga di comando.

> [!NOTE]
> Per i problemi relativi a REPL, verificare che i pacchetti `ipython` e `ipykernel` siano installati. Per informazioni sull'installazione dei pacchetti, vedere la [scheda Packages (Pacchetti) in Python Environments (Ambienti Python)](./python-environments-window-tab-reference.md#packages-tab).

1. Aprire la finestra **Interattiva** facendo clic col pulsante destro del mouse sull'ambiente Python del progetto in **Esplora soluzioni**, come **Python 3.6 (32 bit)** illustrato in precedenza, e selezionando **Apri finestra interattiva**. In alternativa, è possibile selezionare **Visualizza** Windows python interactive Windows dal menu Visual Studio  >    >   principale.

1. La finestra **Interattiva** si apre sotto l'editor con il prompt REPL standard **>>>** Python. L'elenco a discesa **Ambiente** consente di selezionare un interprete specifico da utilizzare. In alcuni casi può essere necessario ingrandire la finestra **Interattiva**. A tale scopo, trascinare il separatore tra le due finestre:

    ![Finestra interattiva di Python e trascinamento per ridimensionarla](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > In Visual Studio è possibile ridimensionare tutte le finestre trascinando i separatori confinanti. È anche possibile trascinare le finestre in modo indipendente dal frame di Visual Studio e ridisporle come si vuole all'interno della cornice. Per altre informazioni, vedere [Personalizzare il layout delle finestre](../ide/customizing-window-layouts-in-visual-studio.md).

1. Immettere alcune istruzioni (ad esempio `print("Hello, Visual Studio")`) ed espressioni (ad esempio `123/456`) per visualizzare i risultati immediati:

    ![Risultati immediati nella finestra interattiva di Python](media/vs-getting-started-python-12-interactive2.png)

1. Quando si inizia a scrivere un'istruzione su  più righe,  ad esempio una definizione di funzione, nella finestra interattiva viene visualizzato il prompt ... di Python per le righe continue, che, a differenza della riga di comando REPL, fornisce il rientro automatico. Per aggiungere una nuova **riga ...** , premere `Shift+Enter` :

    ![Finestra interattiva di Python con continuazione dell'istruzione](media/vs-getting-started-python-13-interactive3.png)

1. La **finestra Interattiva** fornisce una cronologia completa di tutti gli elementi immessi e migliora la rePL della riga di comando con elementi della cronologia su più righe. Ad esempio, è possibile chiamare facilmente l'intera definizione della funzione `f` come singola unità e modificare in modo semplice il nome in `make_double`, invece di dover ricreare la funzione riga per riga.

1. Visual Studio può inviare più righe di codice da una finestra dell'editor alla finestra **Interattiva**. Questa funzionalità consente di mantenere il codice in un file di origine e di inviarne facilmente parti selezionate alla finestra **Interattiva**. È quindi possibile usare questi frammenti di codice nell'ambiente REPL rapido piuttosto che dover eseguire l'intero programma. Per visualizzare questa funzionalità, sostituire il ciclo `for` nel file *PythonApplication1.py* con le operazioni seguenti:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Selezionare le istruzioni di funzione , e `import` nel file con estensione `from` `make_dot_string` *py.* Fare clic con il pulsante destro del mouse sul testo selezionato e **scegliere Invia a interattivo** (oppure premere CTRL  + **INVIO).** Il frammento di codice viene incollato immediatamente nella finestra **Interattiva** ed eseguito. Poiché il codice ha definito una funzione, è possibile testarla rapidamente chiamandola alcune volte:

    ![Invio del codice alla finestra interattiva e test](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Se **si usa CTRL** INVIO nell'editor senza una selezione, viene eseguita la riga di codice corrente nella finestra Interattiva e il punto di inserimento viene inserito +  automaticamente nella riga  successiva.  Con questa funzionalità, la pressione ripetuta di **CTRL** INVIO offre un modo pratico per eseguire il codice un'istruzione alla volta che non è possibile solo con +  la riga di comando python. Consente anche di esaminare il codice senza eseguire il debugger e senza avviare necessariamente il programma dall'inizio.

1. È anche possibile copiare e incollare più righe di codice nella finestra **Interattiva** da qualsiasi origine, come il frammento di codice riportato di seguito, che è difficile eseguire con le transazioni di replica della riga di comando di Python. Quando il codice viene incollato, la finestra **Interattiva** lo esegue, come se fosse stato digitato:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Incollare più righe di codice tramite l'invio alla finestra interattiva](media/vs-getting-started-python-15-interactive5.png)

1. Come è possibile vedere, questo codice funziona correttamente, tuttavia l'output non è molto evocativo. Un valore passaggio diverso nel ciclo `for` potrebbe visualizzare più dell'onda coseno. Dato che l'intero ciclo `for` è presente nella cronologia REPL come singola unità, è facile tornare indietro e apportare qualsiasi modifica, per poi testare di nuovo la funzione. Premere la freccia in su per chiamare il ciclo `for`. Premere quindi sulle frecce verso sinistra o destra per avviare l'esplorazione del codice (fino a tale momento, le frecce su e giù continuano a scorrere la cronologia). Individuare e modificare la specifica `range` in `range(0, 360, 12)`. Premere quindi **CTRL** + **INVIO** (in qualsiasi punto del codice) per eseguire di nuovo l'intera istruzione:

    ![Modifica di un'istruzione precedente nella finestra interattiva](media/vs-getting-started-python-16-interactive6.png)

1. Ripetere il processo per sperimentare con impostazioni diverse i passaggi fino a individuare un valore desiderato. È anche possibile rendere la ripetizione dell'onda aumentando l'intervallo, ad esempio, `range(0, 1800, 12)`.

1. Quando si è soddisfatti del codice scritto nella **finestra Interattiva,** selezionarlo. Fare quindi clic con il pulsante destro del mouse sul codice e scegliere **Copia codice** (**CTRL** + **MAIUSC** + **C**). Infine, incollare il codice selezionato nell'editor. Questa funzionalità speciale di Visual Studio omette automaticamente qualsiasi output, così come i prompt `>>>` e `...`. Ad esempio, nell'immagine seguente viene illustrato l'uso del comando **Copia codice** su una selezione che include prompt e output:

    ![Comando copia codice della finestra interattiva su una selezione con prompt e output](media/vs-getting-started-python-17-interactive7.png)

    Quando si procede con la funzione incolla nell'editor, si ottiene solo il codice:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Per copiare il contenuto esatto di una finestra **Interattiva** compresi output e prompt, usare il comando standard **Copia**.

1. Le modifiche appena apportate consentono di usare l'ambiente REPL rapido della finestra **Interattiva** per elaborare i dettagli di una piccola parte di codice e aggiungerla facilmente al file di origine del progetto. Quando si esegue di nuovo il codice con **CTRL** F5 (o Avvia debug senza debug +  ), vengono visualizzati i   >  risultati esatti desiderati.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Approfondimento

- [Usare la finestra Interattiva](python-interactive-repl-in-visual-studio.md)
- [Usare REPL IPython](interactive-repl-ipython.md)