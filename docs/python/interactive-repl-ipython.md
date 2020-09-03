---
title: REPL IPython (finestra interattiva)
description: Usare la finestra interattiva di Visual Studio in modalità IPython per un ambiente di sviluppo interattivo intuitivo e semplice da usare con funzionalità di elaborazione parallela interattiva.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b1fe36a4ee74ca1b41c1db1d79a6e4683c1f2b1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542428"
---
# <a name="use-ipython-in-the-interactive-window"></a>Usare IPython nella finestra interattiva

La finestra **interattiva** di Visual Studio in modalità IPython costituisce un ambiente di sviluppo interattivo avanzato e al contempo semplice da usare che include funzionalità di elaborazione parallela interattiva. Questo articolo illustra l'uso di IPython nella finestra **interattiva** di Visual Studio, in cui sono anche disponibili tutte le funzionalità della [finestra interattiva](python-interactive-repl-in-visual-studio.md) normale.

Per questa procedura dettagliata è necessario aver installato l'ambiente [Anaconda](https://www.continuum.io), che include IPython e le librerie necessarie.

> [!Note]
> IronPython non supporta IPython, anche se è possibile selezionarlo nel modulo delle **opzioni interattive**. Per altre informazioni, vedere la pagina relativa alla [richiesta di funzionalità](https://github.com/Microsoft/PTVS/issues/84).

1. Aprire Visual Studio, passare alla finestra **Ambienti Python** (**Visualizza** > **Altre finestre** > **Ambienti Python**) e selezionare un ambiente Anaconda.

2. Esaminare la scheda **Pacchetti (Conda)** (che può essere visualizzata come **pip** o **Pacchetti**) relativa all'ambiente per verificare la presenza di `ipython` e `matplotlib`. In caso contrario, installarli qui. Vedere la pagina relativa alla [finestra Ambienti Python - Scheda Pacchetti](python-environments-window-tab-reference.md).

3. Selezionare la scheda **Panoramica** e quindi **Usa la modalità interattiva IPython.** In Visual Studio 2015 selezionare **Configure interactive options** (Configura opzioni interattive) per aprire la finestra di dialogo **Opzioni** e quindi impostare **Modalità interattiva** su **IPython** e selezionare **OK**.

4. Selezionare **Apri finestra interattiva** per visualizzare la finestra **interattiva** in modalità IPython. Se la modalità interattiva è stata appena modificata può essere necessario reimpostare la finestra. Se viene visualizzato solo un prompt >>> potrebbe anche essere necessario premere **INVIO** in modo da visualizzare un prompt simile a **In [2]**.

    ![Finestra interattiva in modalità IPython](media/ipython-repl-03.png)

5. Immettere il codice seguente:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Dopo aver immesso l'ultima riga, verrà visualizzato un grafico inline, che è possibile eventualmente ridimensionare trascinando nell'angolo inferiore destro.

    ![Grafico inline nella finestra interattiva](media/ipython-repl-04.png)

7. Invece di digitare in REPL, è possibile scrivere codice nell'editor, selezionarlo, fare clic con il pulsante destro del mouse e scegliere il comando **Invia a finestra interattiva** o premere **CTRL**+**INVIO**. Provare a incollare il codice seguente in un nuovo file nell'editor, selezionandolo con **CTRL** + **a**, quindi inviando la finestra **interattiva** . Visual Studio invia il codice alla finestra in un unico blocco per evitare che vengano visualizzati grafici intermedi o parziali. Se non è aperto un progetto Python con un altro ambiente selezionato, Visual Studio apre una finestra **interattiva** per qualsiasi ambiente sia selezionato come predefinito nella finestra **Ambienti Python**.

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Invio di codice dall'editor alla finestra interattiva](media/ipython-repl-05.png)

8. Per visualizzare i grafici all'esterno della finestra **interattiva**, eseguire il codice invece di usare il comando **Debug** > **Avvia senza eseguire debug**.

IPython dispone di molte altre funzionalità utili, ad esempio l'escape alla shell di sistema, la sostituzione delle variabili, l'acquisizione dell'output e così via. Per ulteriori informazioni, vedere la [documentazione di IPython](https://ipython.org/documentation.html) .

## <a name="see-also"></a>Vedere anche

- Per usare Jupyter facilmente e senza installazione, provare la versione gratuita del [servizio ospitato Azure Notebooks](https://notebooks.azure.com/) che consente di mantenere e condividere i blocchi appunti con altri utenti.

- Il servizio [Data Science Virtual Machine di Azure](/azure/machine-learning/data-science-virtual-machine/overview) viene pre-configurato anche per eseguire i notebook Jupyter con un'ampia gamma di altri strumenti di data science.
