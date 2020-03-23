---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 3, finestra interattiva REPL
titleSuffix: ''
description: Passaggio 3 della procedura dettagliata di base sulle funzionalità di Visual Studio, dedicato alla finestra interattiva REPL di Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986224"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Passaggio 3: Usare la finestra interattiva REPL

**Passaggio precedente: [Scrivere ed eseguire codice](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La finestra **interattiva** di Visual Studio per Python offre un'esperienza REPL (Read-Evaluate-Print-loop) avanzata che riduce notevolmente il normale ciclo di modifica-build-debug. La finestra **Interattiva** offre tutte le funzionalità dell'esperienza REPL della riga di comando di Python. Rende anche molto semplice lo scambio di codice con i file di origine dell'editor di Visual Studio, che altrimenti risulta eccessivamente complessa con la riga di comando.

> [!NOTE]
> Per i problemi relativi a REPL, verificare che i pacchetti `ipython` e `ipykernel` siano installati. Per informazioni sull'installazione dei pacchetti, vedere la [scheda Packages (Pacchetti) in Python Environments (Ambienti Python)](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Aprire la finestra **Interattiva** facendo clic col pulsante destro del mouse sull'ambiente Python del progetto in **Esplora soluzioni**, come **Python 3.6 (32 bit)** illustrato in precedenza, e selezionando **Apri finestra interattiva**. È possibile selezionare alternativamente Visualizza altre**finestre interattive** di Windows Python dal menu principale di Visual Studio.You can alternately select **View** > **Other Windows** > Python Interactive Windows from the main Visual Studio menu.

1. La finestra **Interattiva** si apre sotto l'editor con il prompt REPL standard **>>>** Python. L'elenco a discesa **Ambiente** consente di selezionare un interprete specifico da utilizzare. In alcuni casi può essere necessario ingrandire la finestra **Interattiva**. A tale scopo, trascinare il separatore tra le due finestre:

    ![Finestra interattiva di Python e trascinamento per ridimensionarla](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > In Visual Studio è possibile ridimensionare tutte le finestre trascinando i separatori confinanti. È anche possibile trascinare le finestre in modo indipendente dal frame di Visual Studio e ridisporle come si vuole all'interno della cornice. Per altre informazioni, vedere [Personalizzare il layout delle finestre](../ide/customizing-window-layouts-in-visual-studio.md).

1. Immettere alcune istruzioni (ad esempio `print("Hello, Visual Studio")`) ed espressioni (ad esempio `123/456`) per visualizzare i risultati immediati:

    ![Risultati immediati nella finestra interattiva di Python](media/vs-getting-started-python-12-interactive2.png)

1. Quando si inizia a scrivere un'istruzione su più righe, ad esempio una definizione di funzione, la finestra **Interattiva** mostra il prompt **...** di Python per le righe di continuazione, per le quali è disponibile il rientro automatico, diversamente dall'ambiente REPL dalla riga di comando:

    ![Finestra interattiva di Python con continuazione dell'istruzione](media/vs-getting-started-python-13-interactive3.png)

1. La finestra **interattiva** fornisce una cronologia completa di tutto ciò che hai inserito e migliora la riga di comando REPL con elementi di cronologia su più righe. Ad esempio, è possibile chiamare facilmente l'intera definizione della funzione `f` come singola unità e modificare in modo semplice il nome in `make_double`, invece di dover ricreare la funzione riga per riga.

1. Visual Studio può inviare più righe di codice da una finestra dell'editor alla finestra **Interattiva**. Questa funzionalità consente di mantenere il codice in un file di origine e di inviarne facilmente parti selezionate alla finestra **Interattiva**. È quindi possibile usare questi frammenti di codice nell'ambiente REPL rapido piuttosto che dover eseguire l'intero programma. Per visualizzare questa funzionalità, sostituire il ciclo `for` nel file *PythonApplication1.py* con le operazioni seguenti:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Selezionare `import` `from`le `make_dot_string` istruzioni , e nella funzione nel file *.py,* fare clic con il pulsante destro del mouse e **scegliere Invia a interattivo** (o premere **CTRL**+**INVIO**). Il frammento di codice viene incollato immediatamente nella finestra **Interattiva** ed eseguito. Poiché il codice ha definito una funzione, è possibile testarla rapidamente chiamandola un paio di volte:Because the code has defined a function, you can quickly test that function by calling it a few times:

    ![Invio del codice alla finestra interattiva e test](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Se si utilizza **CTRL**+**Invio** nell'editor *senza* una selezione, viene eseguita la riga di codice corrente nella finestra **Interattiva** e il punto di inserimento viene automaticamente inserito nella riga successiva. Con questa funzione, premendo **ripetutamente Ctrl**+**Invio** fornisce un modo pratico per scorrere il codice che non è possibile solo con la riga di comando Python. Consente anche di esaminare il codice senza eseguire il debugger e senza avviare necessariamente il programma dall'inizio.

1. È anche possibile copiare e incollare più righe di codice nella finestra **Interattiva** da qualsiasi origine, come il frammento di codice riportato di seguito, che è difficile eseguire con le transazioni di replica della riga di comando di Python. Quando il codice viene incollato, la finestra **Interattiva** lo esegue, come se fosse stato digitato:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Incollare più righe di codice tramite l'invio alla finestra interattiva](media/vs-getting-started-python-15-interactive5.png)

1. Come è possibile vedere, questo codice funziona correttamente, tuttavia l'output non è molto evocativo. Un valore passaggio diverso nel ciclo `for` potrebbe visualizzare più dell'onda coseno. Dato che l'intero ciclo `for` è presente nella cronologia REPL come singola unità, è facile tornare indietro e apportare qualsiasi modifica, per poi testare di nuovo la funzione. Premere la freccia in su per chiamare il ciclo `for`. Premere quindi sulle frecce verso sinistra o destra per avviare l'esplorazione del codice (fino a tale momento, le frecce su e giù continuano a scorrere la cronologia). Individuare e modificare la specifica `range` in `range(0, 360, 12)`. Quindi premere **Ctrl**+**Invio** (in qualsiasi punto del codice) per eseguire nuovamente l'intera istruzione:

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

1. Le modifiche appena apportate consentono di usare l'ambiente REPL rapido della finestra **Interattiva** per elaborare i dettagli di una piccola parte di codice e aggiungerla facilmente al file di origine del progetto. Quando si esegue nuovamente il codice con **Ctrl**+**F5** (o **Avvia debug** > **senza eseguire debug**), vengono visualizzati i risultati esatti desiderati.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Approfondimento

- [Usare la finestra Interattiva](python-interactive-repl-in-visual-studio.md)
- [Usare REPL IPython](interactive-repl-ipython.md)
