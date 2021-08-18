---
title: Codice Python negli unit test
description: Configurazione di unit test per il codice Python in Visual Studio per usufruire delle funzionalità di Esplora test per l'individuazione, l'esecuzione e il debug dei test.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 307a82b346f1fead5c78091544d0ccdfe8509e6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156408"
---
## <a name="discover-and-view-tests"></a>Individuare e visualizzare i test

Per convenzione, Visual Studio identifica i test come metodi il cui nome inizia con `test`. Per vedere questo comportamento, attenersi alla procedura seguente:

1. Aprire un [progetto Python](../../managing-python-projects-in-visual-studio.md) caricato in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi** > **Nuovo elemento**, quindi selezionare **Unit test Python** seguito da **Aggiungi**.

1. Verrà creato un file *test1.py* contenente il codice che importa il modulo standard `unittest`, deriva una classe di test da `unittest.TestCase` e richiama `unittest.main()` se si esegue lo script direttamente:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Se necessario, salvare il file e aprire **Esplora test** con il comando di menu **Test** > **Windows** > **Esplora test**.

1. **Esplora test** cerca i test nel progetto e li visualizza come illustrato di seguito. Fare doppio clic su un test per aprirne il file di origine.

    ![Esplora test con test_A predefinito](../../media/unit-test-A.png)

1. Quando si aggiungono altri test al progetto, è possibile organizzare la visualizzazione in **Esplora test** usando il **menu** Raggruppa per sulla barra degli strumenti:

    ![Menu Raggruppa per della barra degli strumenti in Esplora test](../../media/unit-test-group-menu.png)

1. È anche possibile immettere testo nel campo di **Cerca** per filtrare i test in base al nome.

Per altre informazioni sul modulo e sulla scrittura di test, vedere la documentazione di `unittest` [Python 2.7](https://docs.python.org/2/library/unittest.html) o la documentazione di [Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Esecuzione dei test

In **Esplora test** è possibile eseguire i test in diversi modi:

- L'opzione **Esegui tutto** esegue chiaramente tutti i test visualizzati, tenendo conto degli eventuali filtri applicati.
- Il menu **Esegui** visualizza i comandi per eseguire test non riusciti, superati o non eseguiti come gruppo.
- È possibile selezionare uno o più test, fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.

I test vengono eseguiti in background **e Esplora test** aggiorna lo stato di ogni test al completamento:

- I test superati sono contraddistinti da un segno di spunta verde, nonché dall'indicazione del tempo necessario per eseguirli:

    ![test_A superato](../../media/unit-test-A-pass.png)

- I test non superati sono contraddistinti da una croce rossa e includono un collegamento **Output** che mostra l'output della console e l'output di `unittest` restituito dall'esecuzione dei test:

    ![test_A non superato](../../media/unit-test-A-fail.png)

    ![test_A non superato con motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Esecuzione del debug dei test

Dal momento che gli unit test sono parti di codice, sono soggetti a bug esattamente come qualsiasi altro tipo di codice e a volte può essere necessario eseguirli in un debugger, in cui è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice istruzione per istruzione. Visual Studio include anche strumenti di diagnostica per gli unit test.

Per avviare il debug, impostare un punto di interruzione iniziale nel codice, fare clic con il pulsante destro del mouse sul test (o su una selezione) in **Esplora test** e quindi scegliere **Esegui debug test selezionati**. Visual Studio avvia il debugger di Python come farebbe per il codice dell'applicazione.

![Debug di un test](../../media/unit-test-debugging.png)

È anche possibile usare **l'opzione Analizza code coverage per test selezionati**. Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Problemi noti

- Quando si avvia il debug, Visual Studio sembra avviare e arrestare il debug e quindi avviarlo di nuovo. Si tratta di un comportamento previsto.
- Durante il debug di più test, ognuno di essi viene eseguito in modo indipendente e questo causa l'interruzione della sessione di debug.
- Di tanto in tanto Visual Studio non riesce ad avviare un test durante il debug. In genere, il problema si risolve ripetendo il debug del test.
- Durante il debug, è possibile uscire da un test nell'implementazione di `unittest`. Di solito il passaggio successivo viene eseguito alla fine del programma e arresta il debug.
