---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 5, installare pacchetti
titleSuffix: ''
description: Passaggio 5 della procedura dettagliata di base sulle funzionalità di Visual Studio, che illustra le funzionalità di Visual Studio per la gestione dei pacchetti in un ambiente Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: be201d5d9897dd803f9eac3c012d3124c141c26e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711454"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Passaggio 5: Installare i pacchetti nell'ambiente Python

**Passaggio precedente: [Eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La community degli sviluppatori di Python produce migliaia di pacchetti utili che è possibile incorporare nei propri progetti. Visual Studio offre un'interfaccia utente per gestire i pacchetti nei propri ambienti Python.

## <a name="view-environments"></a>Visualizzare gli ambienti

1. Selezionare il **comando di** menu  >  **Visualizza Windows** ambienti  >  **Python.** La **finestra Ambienti Python** si apre come peer per Esplora soluzioni e mostra i diversi ambienti disponibili.  L'elenco mostra sia gli ambienti installati usando il Visual Studio installato separatamente che quelli installati separatamente. Inclusi gli ambienti globali, virtuali e conda. L'ambiente in grassetto è l'ambiente predefinito che viene usato per i nuovi progetti. Per altre informazioni sull'uso degli ambienti, vedere Come creare e gestire ambienti [Python in Visual Studio ambienti](managing-python-environments-in-visual-studio.md).

   ![Finestra Ambienti Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > È anche possibile aprire la finestra Ambienti Python selezionando la finestra Esplora soluzioni e usando i tasti di scelta rapida **CTRL+K, CTRL+'.** Se il collegamento non funziona e non è possibile trovare la finestra Ambienti Python nel menu, è possibile che il carico di lavoro Python non sia stato installato. Per [istruzioni su come installare Python, Visual Studio](installing-python-support-in-visual-studio.md) vedere Come installare il supporto python in Visual Studio.

2. La scheda  Panoramica dell'ambiente consente di accedere rapidamente a una **finestra** interattiva per tale ambiente insieme alla cartella di installazione e agli interpreti dell'ambiente. Ad esempio, selezionare **Apri finestra interattiva** e viene visualizzata una **finestra** interattiva per l'ambiente specifico Visual Studio.

3. Creare ora un nuovo progetto con **File**  >  **nuovo**  >  **Project**, selezionando il **modello Applicazione Python.** Nel file di codice visualizzato incollare il codice seguente, che crea un'ondata coseno come i passaggi precedenti dell'esercitazione, solo questa volta tracciata graficamente. In alternativa, è possibile usare il progetto creato in precedenza e sostituire il codice.

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

4. Con un progetto Python aperto, è anche possibile aprire la finestra Ambienti Python da Esplora soluzioni facendo clic con il pulsante destro del mouse su **Ambienti Python** e scegliendo Visualizza tutti gli **ambienti Python**

   ![Ambiente](media/environments/environments-view-all-2019.png)

5. Osservando la finestra dell'editor, si noterà che se si passa il mouse sulle istruzioni e import si `numpy` `matplotlib` noterà che non vengono risolte. Questo perché i pacchetti non sono stati installati nell'ambiente globale predefinito.

   ![Importazione del pacchetto non risolta](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installare pacchetti usando la finestra Ambienti Python

1. Nella finestra Ambienti Python selezionare l'ambiente predefinito per i nuovi progetti Python e scegliere la **scheda** Pacchetti. Verrà quindi visualizzato un elenco di pacchetti attualmente installati nell'ambiente.

   ![Pacchetti installati in un ambiente](media/environments/environments-installed-packages-2019.png)

2. Installare `matplotlib` immettendo il nome nel campo di ricerca e quindi selezionando **l'opzione Esegui comando: pip install matplotlib.** Verrà installato `matplotlib` , nonché tutti i pacchetti da cui dipende (in questo caso che include `numpy` ).

   ![Installazione di matplotlib nell'ambiente](media/environments/environments-add-matplotlib-2019.png)

5. Se richiesto, dare il consenso per l'elevazione dei privilegi.

6. Dopo l'installazione, il pacchetto viene visualizzato nella **finestra Ambienti Python.** La **X**, a destra del pacchetto, lo disinstalla.

   ![Completamento dell'installazione matplotlib nell'ambiente](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Sotto l'ambiente potrebbe essere visualizzato un piccolo indicatore di stato per indicare che Visual Studio sta creando il database IntelliSense per il pacchetto appena installato. La scheda **IntelliSense** offre anche informazioni più dettagliate. Tenere presente che fino al completamento del database, le funzionalità di IntelliSense come il completamento automatico e il controllo della sintassi non saranno attive nell'editor per il pacchetto.
   >
   > Visual Studio 2017 versione 15.6 e successive usa un metodo diverso e più veloce per l'uso di IntelliSense e visualizza un messaggio a tale effetto nella **scheda IntelliSense.**

## <a name="run-the-program"></a>Eseguire il programma

1. Ora che [matplotlib](https://matplotlib.org/) è installato, eseguire il programma con (**F5**) o senza il debugger (**CTRL** + **F5**) per visualizzare l'output:

   ![Output di esempio matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Usare Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondimento

- [Ambienti Python](managing-python-environments-in-visual-studio.md)
- [Informazioni su Django in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Informazioni su Flask in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
