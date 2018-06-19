---
title: Esercitazione sull'uso di Python, passaggio 5, installazione di pacchetti
description: Passaggio 5 della procedura dettagliata di base sulle funzionalità di Visual Studio, che illustra le funzionalità di Visual Studio per la gestione dei pacchetti in un ambiente Python.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 18a4f274de38bab160144a9e13d6a6963168fff1
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33875318"
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Passaggio 5: Installazione dei pacchetti nell'ambiente Python

**Passaggio precedente: [Esecuzione del codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La community degli sviluppatori di Python produce migliaia di pacchetti utili che è possibile incorporare nei propri progetti. Visual Studio offre un'interfaccia utente per gestire i pacchetti nei propri ambienti Python.

1. Selezionare il comando di menu **Visualizza > Altre finestre > Ambienti Python**. La finestra **Ambienti Python** viene visualizzata come peer in Esplora soluzioni e visualizza i diversi ambienti disponibili per l'utente. L'elenco include entrambi gli ambienti installati usando il programma di installazione di Visual Studio e quelli installati separatamente. L'ambiente in grassetto è l'ambiente predefinito che viene usato per i nuovi progetti.

  ![Finestra Ambienti Python](media/environments-default-view-blue.png)

1. La scheda **Panoramica** dell'ambiente consente di accedere rapidamente a una finestra interattiva per quell'ambiente insieme alla cartella di installazione e agli interpreti. Ad esempio, selezionare **Open interactive window** (Apri finestra interattiva) per visualizzare una finestra interattiva in Visual Studio per quell'ambiente specifico.

1. Selezionare la scheda **Pacchetti** e verrà visualizzato un elenco di pacchetti installati attualmente nell'ambiente.

  ![Pacchetti installati in un ambiente](media/environments-installed-packages-blue.png)

1. Installare `matplotlib` immettendo il relativo nome nel campo di ricerca, quindi selezionare `pip install`

  ![Installazione di matplotlib nell'ambiente](media/environments-add-matplotlib1.png)

1. Se richiesto, dare il consenso per l'elevazione dei privilegi.

1. Una volta installato, il pacchetto comparirà nella finestra Ambienti Python. La **X**, a destra del pacchetto, lo disinstalla.

  ![Completamento dell'installazione matplotlib nell'ambiente](media/environments-add-matplotlib2.png)

  Sotto l'ambiente potrebbe essere visualizzato un indicatore di stato di piccole dimensioni a indicare che Visual Studio sta compilando il database di IntelliSense per il pacchetto appena installato. La scheda **IntelliSense** offre anche informazioni più dettagliate. Si noti che, fino al completamento del database, le funzionalità di IntelliSense come il completamento automatico e la verifica della sintassi non saranno attive nell'editor del pacchetto.

  Si noti che **Visual Studio 2017 15.6** e versioni successive usano un metodo diverso e più veloce per l'utilizzo di IntelliSense e visualizzano un messaggio in merito nella scheda **IntelliSense**.

1. Creare un nuovo progetto con **File > Nuovo > Progetto**, selezionando il modello "Applicazione Python". Nel file di codice che viene visualizzato incollare il codice seguente che crea una cosinusoide come nei passaggi dell'esercitazione precedente, questa volta tracciata graficamente:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Eseguire il programma con (F5) o senza il debugger (Ctrl+F5) per visualizzare l'output:

  ![Output di esempio matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Uso di Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>Approfondimenti

- [Ambienti Python](managing-python-environments-in-visual-studio.md)
