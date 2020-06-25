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
ms.openlocfilehash: e84b9de4eca681812209eb17f492d5e07522d3b5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292166"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Selezionare il Framework di test per un progetto Python

Visual Studio supporta due Framework di test per Python, [unittest](https://docs.python.org/3/library/unittest.html) e [pytest](https://pytest.org/en/latest/) (disponibile in Visual Studio 2019 a partire dalla versione 16,3). Per impostazione predefinita, quando si crea un progetto Python non viene selezionato alcun Framework. Per specificare un Framework, fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni e selezionare l'opzione **Proprietà** . Verrà visualizzata la finestra Progettazione progetti, che consente di configurare i test tramite la scheda **test** . Da questa scheda è possibile selezionare il Framework di test che si vuole usare per il progetto. 

* Per il Framework **unittest** , la directory radice del progetto viene usata per l'individuazione dei test. Questo percorso, nonché il modello di testo per l'identificazione dei test, può essere modificato nella scheda **test** per i valori specificati dall'utente.
* Per il Framework **pytest** , le opzioni di test, ad esempio la posizione dei test e i modelli di nome file, vengono specificati usando il file di configurazione pytest. ini standard. Per ulteriori informazioni, vedere la [documentazione di riferimento di pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Dopo aver salvato le impostazioni e la selezione del Framework, l'individuazione dei test viene avviata in Esplora test. Se la finestra Esplora test non è già aperta, passare alla barra degli strumenti e selezionare **test**  >  **Esplora test**.

## <a name="configure-testing-for-python-without-a-project"></a>Configurare i test per Python senza un progetto
Visual Studio consente di eseguire e testare il codice Python esistente senza un progetto, [aprendo una cartella con il](../../quickstart-05-python-visual-studio-open-folder.md) codice Python. In questi casi, è necessario usare un **PythonSettings.jssu** file per configurare i test. 
1. Aprire il codice Python esistente usando l'opzione **Apri una cartella locale** . 

   ![Schermata iniziale di Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Nella finestra Esplora soluzioni fare clic sull'icona **Mostra tutti i file** per visualizzare tutti i file nella cartella corrente.

   ![Pulsante Mostra tutti i file](../../media/unit-test-show-files.png)

1. Passare alla **PythonSettings.js** nel file all'interno della cartella **impostazioni locali** . Se questo file non viene visualizzato nella cartella **impostazioni locali** , crearlo manualmente.
   
1. Aggiungere il campo **TestFramework** al file di impostazioni e impostarlo su **pytest** o **unittest** a seconda del Framework di test che si vuole usare.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Per **unittest** Framework, se i campi **UnitTestRootDirectory** e **UnitTestPattern** non sono specificati nel PythonSettings.jsfile, vengono aggiunti e assegnati rispettivamente i valori predefiniti "." e "test *. py".

1. Se la cartella contiene una directory **src** che è separata dalla cartella che contiene i test, specificare il percorso della cartella **src** usando il campo **SearchPaths** nel **PythonSettings.jssu** file.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Salvare le modifiche apportate al file PythonSettings.jsper avviare l'individuazione dei test per il Framework specificato. 
   > [!Note]
   > Se la finestra Esplora test è già aperta **CTRL**  +  **R,** viene attivato anche l'individuazione.

## <a name="discover-and-view-tests"></a>Individuare e visualizzare i test

Per impostazione predefinita, Visual Studio identifica i test **unittest** e **pytest** come metodi i cui nomi iniziano con `test` . Per visualizzare l'individuazione dei test, eseguire le operazioni seguenti:

1. Aprire un [progetto Python](../../managing-python-projects-in-visual-studio.md).

1. Una volta caricato il progetto in Visual Studio, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e selezionare il Framework **unittest** o **pytest** dalla scheda **test** proprietà.
   > [!Note]
   > Se si usa pytest Framework, è possibile specificare il percorso e i modelli di nome file del test usando il file di configurazione pytest. ini standard. Per impostazione predefinita, viene usata la cartella area di lavoro/progetto con un modello di `test_*py` e `*_test.py` . Per ulteriori informazioni, vedere la [documentazione di riferimento di pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Dopo aver selezionato il Framework, fare di nuovo clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi**  >  **nuovo elemento**, quindi selezionare **Python unit test** seguito da **Aggiungi**.

1. Questa azione crea un file *test_1. py* con il codice che importa il `unittest` modulo standard, deriva una classe di test da `unittest.TestCase` e richiama `unittest.main()` se si esegue lo script direttamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Salvare il file, se necessario, quindi aprire **Esplora test** con **il**  >  comando di menu**Esplora** test test.

1. **Esplora test** Cerca i test nel progetto e li Visualizza come illustrato di seguito. Fare doppio clic su un test per aprirne il file di origine.

    ![Esplora test con test_A predefinito](../../media/unit-test-a-2.png) 

1. Quando si aggiungono altri test al progetto, è possibile organizzare la visualizzazione in **Esplora test** usando il menu **Raggruppa per** sulla barra degli strumenti:

    ![Menu Raggruppa per della barra degli strumenti in Esplora test](../../media/unit-test-group-menu-2.png) 

1. È anche possibile immettere testo nel campo di **Cerca** per filtrare i test in base al nome.

Per ulteriori informazioni sul `unittest` modulo e sulla scrittura di test, vedere la [documentazione di Python 2,7](https://docs.python.org/2/library/unittest.html) o la [documentazione di Python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Esecuzione dei test

In **Esplora test** è possibile eseguire test in diversi modi:

- L'opzione **Esegui tutto** esegue chiaramente tutti i test visualizzati, tenendo conto degli eventuali filtri applicati.
- Il menu **Run (Esegui** ) fornisce i comandi per eseguire i test non riusciti, superati o non eseguiti come gruppo.
- È possibile selezionare uno o più test, fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.

I test vengono eseguiti in background e **Esplora test** aggiorna lo stato di ogni test dopo il completamento:

- I test superati sono contraddistinti da un segno di spunta verde, nonché dall'indicazione del tempo necessario per eseguirli:

    ![test_A superato](../../media/unit-test-A-pass.png)

- I test non superati sono contraddistinti da una croce rossa e includono un collegamento **Output** che mostra l'output della console e l'output di `unittest` restituito dall'esecuzione dei test:

    ![test_A non superato](../../media/unit-test-A-fail.png)

    ![test_A non superato con motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Esecuzione del debug dei test

Dal momento che gli unit test sono parti di codice, sono soggetti a bug esattamente come qualsiasi altro tipo di codice e a volte può essere necessario eseguirli in un debugger, in cui è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice istruzione per istruzione. Visual Studio include anche strumenti di diagnostica per gli unit test.

> [!Note]
> Per impostazione predefinita, il debug di test usa il debugger ptvsd 4 per Visual Studio 2017 (versioni 15,8 e successive) e debugpy per Visual Studio 2019 (versioni 16,5 e successive). Se si vuole usare invece ptvsd 3, è possibile selezionare l'opzione **USA debugger legacy** in **strumenti**  >  **Opzioni**  >  **Python**  >  **debug**di Python. 

Per avviare il debug, impostare un punto di interruzione iniziale nel codice, fare clic con il pulsante destro del mouse sul test (o su una selezione) in **Esplora test** e quindi scegliere **Esegui debug test selezionati**. Visual Studio avvia il debugger di Python come farebbe per il codice dell'applicazione.

![Debug di un test](../../media/unit-test-debugging.png)

È anche possibile usare il **code coverage analizza per i test selezionati**. Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
