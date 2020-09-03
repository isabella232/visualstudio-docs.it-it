---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 5, installare pacchetti
titleSuffix: ''
description: Passaggio 5 della procedura dettagliata di base sulle funzionalità di Visual Studio, che illustra le funzionalità di Visual Studio per la gestione dei pacchetti in un ambiente Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 32e85f39c4acf9466def24bcfea59bbfd6807a1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801659"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Passaggio 5: Installare i pacchetti nell'ambiente Python

**Passaggio precedente: [Eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La community degli sviluppatori di Python produce migliaia di pacchetti utili che è possibile incorporare nei propri progetti. Visual Studio offre un'interfaccia utente per gestire i pacchetti nei propri ambienti Python.

## <a name="view-environments"></a>Visualizzare gli ambienti

1. Selezionare il comando di menu **Visualizza**  >  **altri**  >  **ambienti Python** Windows. La finestra **ambienti Python** viene visualizzata come peer per **Esplora soluzioni** e Mostra i diversi ambienti disponibili. L'elenco Mostra entrambi gli ambienti installati usando il programma di installazione di Visual Studio e quelli installati separatamente. Inclusi gli ambienti globali, virtuali e conda. L'ambiente in grassetto è l'ambiente predefinito che viene usato per i nuovi progetti. Per altre informazioni sull'uso degli ambienti, vedere [How to create and Manage Python environments in Visual Studio environments](managing-python-environments-in-visual-studio.md).

   ![Finestra Ambienti Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > È anche possibile aprire la finestra ambienti Python selezionando la finestra Esplora soluzioni e usando il tasto di scelta rapida **CTRL + K, CTRL +'** . Se il collegamento non funziona e non è possibile trovare la finestra ambienti Python nel menu, è possibile che non sia stato installato il carico di lavoro Python. Per istruzioni su come installare Python, vedere [come installare il supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md) .

2. La scheda **Panoramica** dell'ambiente consente di accedere rapidamente a una finestra **interattiva** per tale ambiente insieme alla cartella di installazione e agli interpreti dell'ambiente. Ad esempio, selezionare **Apri finestra interattiva** e in Visual Studio viene visualizzata una finestra **interattiva** per quell'ambiente specifico.

3. A questo punto, creare un nuovo progetto con **file**  >  **nuovo**  >  **progetto**, selezionando il modello **applicazione Python** . Nel file di codice che viene visualizzato incollare il codice seguente che crea un'onda coseno come i passaggi precedenti dell'esercitazione, solo questa volta tracciato graficamente. In alternativa, è possibile usare il progetto creato in precedenza e sostituire il codice.

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

4. Con un progetto Python aperto, è anche possibile aprire la finestra ambienti Python da Esplora soluzioni facendo clic con il pulsante destro del mouse su **ambienti Python** e selezionando **Visualizza tutti gli ambienti Python**

   ![Environment](media/environments/environments-view-all-2019.png)

5. Osservando la finestra dell'editor, si noterà che se si passa il mouse `numpy` sulle `matplotlib` istruzioni Import e non vengono risolte. Ciò è dovuto al fatto che i pacchetti non sono stati installati nell'ambiente globale predefinito.

   ![Importazione pacchetto non risolto](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installare i pacchetti usando la finestra ambienti Python

1. Dalla finestra ambienti Python selezionare l'ambiente predefinito per i nuovi progetti python e scegliere la scheda **pacchetti** . Verrà visualizzato un elenco di pacchetti attualmente installati nell'ambiente.

   ![Pacchetti installati in un ambiente](media/environments/environments-installed-packages-2019.png)

2. Installare inserendo il `matplotlib` nome nel campo di ricerca e quindi selezionando l'opzione **Esegui comando: pip install matplotlib** . In questo modo, vengono installati e `matplotlib` tutti i pacchetti da cui dipende (in questo caso, incluso `numpy` ).

   ![Installazione di matplotlib nell'ambiente](media/environments/environments-add-matplotlib-2019.png)

5. Se richiesto, dare il consenso per l'elevazione dei privilegi.

6. Una volta installato, il pacchetto viene visualizzato nella finestra **ambienti Python** . La **X**, a destra del pacchetto, lo disinstalla.

   ![Completamento dell'installazione matplotlib nell'ambiente](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > È possibile che venga visualizzato un piccolo indicatore di stato sotto l'ambiente per indicare che Visual Studio sta creando il proprio database IntelliSense per il pacchetto appena installato. La scheda **IntelliSense** offre anche informazioni più dettagliate. Tenere presente che finché il database non sarà completo, le funzionalità di IntelliSense come il completamento automatico e il controllo della sintassi non saranno attive nell'editor per il pacchetto.
   >
   > Visual Studio 2017 versione 15,6 e successive usa un metodo diverso e più veloce per l'uso di IntelliSense e visualizza un messaggio a tale effetto nella scheda **IntelliSense** .

## <a name="run-the-program"></a>Eseguire il programma

1. Ora che [matplotlib](https://matplotlib.org/) è installato, eseguire il programma con (**F5**) o senza il debugger (**CTRL** + **F5**) per visualizzare l'output:

   ![Output di esempio matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Usare git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondimento

- [Ambienti Python](managing-python-environments-in-visual-studio.md)
- [Informazioni su Django in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Informazioni su Flask in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
