---
title: Codice Python negli unit test
description: Configurazione di unit test per il codice Python in Visual Studio per usufruire delle funzionalità di Esplora test per l'individuazione, l'esecuzione e il debug dei test.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933452"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Selezionare il framework di test per un progetto Python

Visual Studio supporta due framework di test per Python, [unittest](https://docs.python.org/3/library/unittest.html) e [pytest](https://pytest.org/en/latest/) (disponibile in Visual Studio 2019 a partire dalla versione 16.3). Per impostazione predefinita, non viene selezionato alcun framework quando si crea un progetto Python.By default, no framework is selected when you create a Python project. Per specificare un framework, fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni e selezionare l'opzione **Proprietà.To** specify a framework, right-click on the project name in Solution Explorer and select the Properties option. Verrà visualizzata la finestra di progettazione del progetto, che consente di configurare i test tramite la scheda **Test.** Da questa scheda è possibile selezionare il framework di test che si desidera utilizzare per il progetto. 

* Per il framework **unittest,** la directory radice del progetto viene utilizzata per l'individuazione dei test. Questa posizione, così come il modello di testo per l'identificazione dei test, può essere modificato nella scheda **Test** in base ai valori specificati dall'utente.
* Per il framework **pytest,** le opzioni di test, ad esempio il percorso di test e i modelli di nome file, vengono specificate utilizzando il file di configurazione .ini standard pytest. Per ulteriori dettagli, consultare la documentazione di riferimento di [pytest.](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)

Dopo aver salvato la selezione e le impostazioni del framework, l'individuazione dei test viene avviata in Esplora test. Se la finestra Esplora test non è già aperta, passare alla barra degli strumenti e **selezionare** > **Esplora test**.

## <a name="configure-testing-for-python-without-a-project"></a>Configurare i test per Python senza un progetto
Visual Studio consente di eseguire e testare il codice Python esistente senza un progetto, [aprendo una cartella](../../quickstart-05-python-visual-studio-open-folder.md) con codice Python.Visual Studio allows you to run and test existing python code without a project, by opening a folder with Python code. In queste circostanze, è necessario utilizzare un file **PythonSettings.json** per configurare il test. 
1. Aprire il codice Python esistente utilizzando l'opzione **Apri cartella locale.** 

   ![Schermata iniziale di Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Nella finestra Esplora soluzioni fare clic sull'icona **Mostra tutti i file** per visualizzare tutti i file nella cartella corrente.

   ![Pulsante Mostra tutti i file](../../media/unit-test-show-files.png)

1. Passare al file **PythonSettings.json** all'interno della cartella **Local Settings.** Se questo file non viene visualizzato nella cartella **Impostazioni locali,** crearlo manualmente.
   
1. Aggiungere il campo **TestFramework** al file di impostazioni e impostarlo su **pytest** o **unittest** a seconda del framework di test che si desidera utilizzare.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Per il framework **unittest,** se i campi **UnitTestRootDirectory** e **UnitTestPattern** non sono specificati nel file PythonSettings.json, vengono aggiunti e vengono assegnati i valori predefiniti di "." e "test.py" rispettivamente.

1. Se la cartella contiene una directory **src** separata dalla cartella che contiene i test, specificare il percorso della cartella **src** utilizzando il campo **SearchPaths** nel file **PythonSettings.json.**

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Salvare le modifiche apportate al file PythonSettings.json per avviare l'individuazione dei test per il framework specificato. 
   > [!Note]
   > Se la finestra Esplora test è già aperta **CTRL** + **R, A** attiva anche l'individuazione.

## <a name="discover-and-view-tests"></a>Individuare e visualizzare i test

Per impostazione predefinita, Visual Studio identifica i test `test` **unittest** e **pytest** come metodi i cui nomi iniziano con . Per visualizzare l'individuazione dei test, eseguire le operazioni seguenti:To see test discovery, do the following:

1. Aprire un [progetto Python](../../managing-python-projects-in-visual-studio.md).

1. Dopo aver caricato il progetto in Visual Studio, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e selezionare il framework di **unittest** o **pytest** dalla scheda **Test** delle proprietà.
   > [!Note]
   > Se si utilizza il framework pytest, è possibile specificare il percorso di test e i modelli di nome file utilizzando il file di configurazione .ini pytest standard. Per impostazione predefinita, viene utilizzata la cartella `test_*py` `*_test.py`dell'area di lavoro/progetto, con un modello di e . Per ulteriori dettagli, consultare la documentazione di riferimento di [pytest.](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)

1. Dopo aver selezionato il framework, fare di nuovo clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi** > **nuovo elemento**, quindi selezionare Test unit test Pit esep() seguito da **Aggiungi**. **Python Unit Test**

1. Questa azione crea un file *test_1.py* con `unittest` codice che importa il `unittest.TestCase`modulo standard, deriva una classe di test da e richiama `unittest.main()` se si esegue direttamente lo script:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Se necessario, salvare il file, quindi aprire **Esplora test** con il comando di menu **Esplora** > **test** .

1. **Esplora test** cerca i test nel progetto e li visualizza come illustrato di seguito. Fare doppio clic su un test per aprirne il file di origine.

    ![Esplora test con test_A predefinito](../../media/unit-test-a-2.png) 

1. Quando si aggiungono altri test al progetto, è possibile organizzare la visualizzazione in **Esplora test** utilizzando il menu **Raggruppa** per sulla barra degli strumenti:

    ![Menu Raggruppa per della barra degli strumenti in Esplora test](../../media/unit-test-group-menu-2.png) 

1. È anche possibile immettere testo nel campo di **Cerca** per filtrare i test in base al nome.

Per altre informazioni `unittest` sul modulo e sulla scrittura di test, vedere la documentazione di [Python 2.7](https://docs.python.org/2/library/unittest.html) o la documentazione di [Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Esecuzione dei test

In Esplora test è possibile eseguire test in diversi modi:In **Test Explorer** you can run tests in a variety of ways:

- L'opzione **Esegui tutto** esegue chiaramente tutti i test visualizzati, tenendo conto degli eventuali filtri applicati.
- Il menu **Esegui** consente di eseguire i comandi non riusciti, superati o non eseguiti test come gruppo.
- È possibile selezionare uno o più test, fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.

I test vengono eseguiti in background e Esplora test aggiorna lo stato di ogni test al completamento:Test run in the background and **Test Explorer** updates each test's status as it completes:

- I test superati sono contraddistinti da un segno di spunta verde, nonché dall'indicazione del tempo necessario per eseguirli:

    ![test_A superato](../../media/unit-test-A-pass.png)

- I test non superati sono contraddistinti da una croce rossa e includono un collegamento **Output** che mostra l'output della console e l'output di `unittest` restituito dall'esecuzione dei test:

    ![test_A non superato](../../media/unit-test-A-fail.png)

    ![test_A non superato con motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Esecuzione del debug dei test

Dal momento che gli unit test sono parti di codice, sono soggetti a bug esattamente come qualsiasi altro tipo di codice e a volte può essere necessario eseguirli in un debugger, in cui è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice istruzione per istruzione. Visual Studio include anche strumenti di diagnostica per gli unit test.

> [!Note]
> Per impostazione predefinita, il debug di test utilizza il debugger ptvsd 4. Se si desidera utilizzare invece ptvsd 3, è possibile selezionare l'opzione **Usa debugger legacy** in Opzioni degli **strumenti** > **Python** > **Python** > **Debugging**. 

Per avviare il debug, impostare un punto di interruzione iniziale nel codice, fare clic con il pulsante destro del mouse sul test (o su una selezione) in **Esplora test** e quindi scegliere **Esegui debug test selezionati**. Visual Studio avvia il debugger di Python come farebbe per il codice dell'applicazione.

![Debug di un test](../../media/unit-test-debugging.png)

È inoltre possibile utilizzare **Analizza code coverage per i test selezionati**. Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
