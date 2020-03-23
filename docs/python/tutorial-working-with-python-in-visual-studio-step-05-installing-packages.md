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
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372921"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Passaggio 5: Installare i pacchetti nell'ambiente Python

**Passaggio precedente: [Eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La community degli sviluppatori di Python produce migliaia di pacchetti utili che è possibile incorporare nei propri progetti. Visual Studio offre un'interfaccia utente per gestire i pacchetti nei propri ambienti Python.

## <a name="view-environments"></a>Visualizzare gli ambienti

1. Selezionare il comando di menu **Visualizza** > **altri** > ambienti Windows**Python.** La finestra **Ambienti Python** si apre come un peer di **Esplora soluzioni** e mostra i diversi ambienti disponibili. L'elenco mostra sia gli ambienti installati utilizzando il programma di installazione di Visual Studio che quelli installati separatamente. Sono inclusi gli ambienti globali, virtuali e conda. L'ambiente in grassetto è l'ambiente predefinito che viene usato per i nuovi progetti. Per ulteriori informazioni sull'utilizzo degli ambienti, vedere [Come creare e gestire ambienti Python in ambienti Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Finestra Ambienti Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > È anche possibile aprire la finestra Ambienti Python facendo clic sulla finestra Esplora soluzioni e utilizzando la scorciatoia da tastiera Ctrl , K , Ctrl . Se il collegamento non funziona e non riesci a trovare la finestra Ambienti Python nel menu, è possibile che tu non abbia installato il carico di lavoro Python. Per istruzioni su come installare Python, vedere Come installare il [supporto Python in Visual Studio.See How to install Python support in Visual Studio](installing-python-support-in-visual-studio.md) for guidance about how to install Python.

2. La scheda **Panoramica** dell'ambiente consente di accedere rapidamente a una finestra **interattiva** per l'ambiente, insieme alla cartella di installazione dell'ambiente e agli interpreti. Ad esempio, selezionare **Apri finestra interattiva** e una finestra **interattiva** per l'ambiente specifico viene visualizzata in Visual Studio.For example, select Open interactive window and an Interactive window for that specific environment appears in Visual Studio.

3. A questo punto, creare un nuovo progetto con **File** > **Nuovo** > **progetto**, selezionando il modello **Applicazione Python.** Nel file di codice visualizzato incollare il codice seguente, che crea un'onda coseno come i passaggi dell'esercitazione precedente, solo questa volta tracciata graficamente. In alternativa, è possibile utilizzare il progetto creato e sostituire il codice in precedenza. 

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

4. Con un progetto Python aperto, è anche possibile aprire la finestra Ambienti Python da Esplora soluzioni facendo clic con il pulsante destro del mouse su Ambienti Python e selezionando **Visualizza tutti gli ambienti Python**

   ![Environment](media/environments/environments-view-all-2019.png)

5. Esaminando la finestra dell'editor, si noterà `numpy` che `matplotlib` se si passa il mouse sopra le istruzioni e importare che non vengono risolti. Questo perché i pacchetti non sono stati installati nell'ambiente globale predefinito.

   ![Importazione di pacchetti non risolti](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installare i pacchetti utilizzando la finestra Ambienti Python

1. Dalla finestra Ambienti Python, fare clic sull'ambiente predefinito per i nuovi progetti Python e selezionare la scheda **Pacchetti.** Verrà quindi visualizzato un elenco dei pacchetti attualmente installati nell'ambiente.

   ![Pacchetti installati in un ambiente](media/environments/environments-installed-packages-2019.png)

2. Installa `matplotlib` immettendo il nome nel campo di ricerca e selezionando l'opzione **Esegui comando: pip install matplotlib.** Verrà installato `matplotlib`, così come tutti i pacchetti da `numpy`cui dipende (in questo caso che include ).

   ![Installazione di matplotlib nell'ambiente](media/environments/environments-add-matplotlib-2019.png)

5. Se richiesto, dare il consenso per l'elevazione dei privilegi.

6. Dopo aver installato, il pacchetto viene visualizzato nella finestra **Ambienti Python.After** the package is installed, it appears in the Python Environments window. La **X**, a destra del pacchetto, lo disinstalla.

   ![Completamento dell'installazione matplotlib nell'ambiente](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Una piccola barra di stato potrebbe essere visualizzata sotto l'ambiente per indicare che Visual Studio sta compilando il proprio database IntelliSense per il pacchetto appena installato. La scheda **IntelliSense** offre anche informazioni più dettagliate. Tenere presente che fino al completamento del database, le funzionalità IntelliSense come il completamento automatico e il controllo della sintassi non saranno attive nell'editor per tale pacchetto.
   > 
   > Visual Studio 2017 versione 15.6 e successive usa un metodo diverso e più veloce per l'utilizzo di IntelliSense e visualizza un messaggio a tal fine nella scheda **IntelliSense.**

## <a name="run-the-program"></a>Eseguire il programma

1. Ora che [matplotlib](https://matplotlib.org/) sia installato, eseguire il programma con (**F5**) o senza il debugger (**Ctrl**+**F5**) per visualizzare l'output:

   ![Output di esempio matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Lavorare con Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondimento

- [Ambienti Python](managing-python-environments-in-visual-studio.md)
- [Informazioni su Django in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Informazioni su Flask in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
