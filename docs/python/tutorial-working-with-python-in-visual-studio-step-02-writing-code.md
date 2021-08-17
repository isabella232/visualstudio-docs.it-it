---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 2, scrivere ed eseguire codice
titleSuffix: ''
description: Passaggio 2 della procedura dettagliata di base sulle funzionalità di Visual Studio, dedicato alla modifica del codice e all'esecuzione di un progetto.
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
ms.openlocfilehash: c7b6b985e53809bb3941246e66c2bdb24df3c9cdb4adecdc58b8eedec910113a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229494"
---
# <a name="step-2-write-and-run-code"></a>Passaggio 2: Scrittura ed esecuzione del codice

**Passaggio precedente: [Creare un nuovo progetto Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Anche se **Esplora soluzioni** si trova nell'area di gestione dei file di progetto, la finestra *Editor* si trova in genere dove si lavora con i *contenuti* dei file, come il codice sorgente. L'editor è sensibile al contesto del tipo di file che si sta modificando, anche per quanto riguarda il linguaggio di programmazione (in base all'estensione del file) e offre le funzionalità appropriate per tale linguaggio, come la colorazione della sintassi e il completamento automatico tramite IntelliSense.

1. Dopo aver creato un nuovo progetto "Python Application" (Applicazione Python), nell'editor di Visual Studio viene aperto un file vuoto predefinito denominato *PythonApplication1.py*.

1. Nell'editor iniziare a digitare `print("Hello, Visual Studio")`. Si noti che IntelliSense di Visual Studio visualizza le opzioni di completamento automatico durante la digitazione. L'opzione descritta nell'elenco a discesa è il completamento predefinito usato quando si preme **TAB.** Il completamento è utile soprattutto in presenza di istruzioni o identificatori più lunghi.

    ![Popup di completamento automatico IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. In IntelliSense vengono mostrate informazioni diverse a seconda dell'istruzione usata, della funzione chiamata e così via. Con la funzione `print`, digitare `(` dopo `print` per indicare che una chiamata di funzione consente di visualizzare informazioni complete sull'uso di tale funzione. Il popup IntelliSense visualizza anche l'argomento corrente in grassetto (**valore** come illustrato di seguito):

    ![Popup di completamento automatico IntelliSense per una funzione](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Completare l'istruzione in modo che corrisponda alla seguente:

    ```python
    print("Hello, Visual Studio")
    ```

1. Si noti la colorazione della sintassi che consente di distinguere l'istruzione `print` dall'argomento `"Hello Visual Studio"`. Inoltre, eliminare temporaneamente l'ultimo elemento `"` nella stringa. Si noti come Visual Studio visualizza una sottolineatura rossa per il codice che contiene errori di sintassi. Quindi sostituire `"` per correggere il codice.

    ![Colorazione della sintassi ed evidenziazione degli errori di IntelliSense](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Poiché l'ambiente di sviluppo è molto personale, Visual Studio offre un controllo completo sull'aspetto e sul comportamento di Visual Studio. Selezionare il **comando di** menu  >  **Opzioni** strumenti ed esplorare le impostazioni nelle **schede Ambiente** e Editor **di** testo. Per impostazione predefinita viene visualizzato solo un numero limitato di opzioni. Per visualizzare tutte le opzioni per ogni linguaggio di programmazione, selezionare **Mostra tutte le impostazioni** nella parte inferiore della finestra di dialogo.

1. Eseguire il codice scritto a questo punto premendo **CTRL** F5 o selezionando la voce di menu Avvia debug +    >  **senza** eseguire debug. Se sono ancora presenti errori nel codice Visual Studio genera degli avvisi.

1. Quando si esegue il programma, viene visualizzata una finestra di console con i risultati, come se fosse stato eseguito un interprete Python con *PythonApplication1.py* dalla riga di comando. Premere un tasto per chiudere la finestra e tornare all'editor di Visual Studio.

    ![Output per la prima esecuzione del programma](media/vs-getting-started-python-07-output.png)

1. Oltre ai completamenti per istruzioni e funzioni, IntelliSense offre completamenti per le istruzioni `import` e `from` di Python. I completamenti delle istruzioni consentono di individuare facilmente i moduli disponibili nell'ambiente e i membri disponibili in ogni modulo. Nell'editor eliminare la riga `print` e iniziare a digitare `import`. Quando si preme la barra spaziatrice, viene visualizzato un elenco dei moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione import](media/vs-getting-started-python-08-import1.png)

1. Completare la riga digitando o selezionando `sys`.

1. Nella riga successiva digitare `from` per visualizzare nuovamente un elenco di moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione from](media/vs-getting-started-python-09-import2.png)

1. Selezionare o digitare `math`, quindi continuare a digitare uno spazio e `import` per visualizzare i membri del modulo:

    ![IntellSense che mostra i membri del modulo](media/vs-getting-started-python-10-import3.png)

1. Completare l'importazione dei membri `sin`, `cos` e `radians`, osservando i completamenti automatici disponibili per ogni membro. Al termine, il codice dovrebbe essere simile al seguente:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > I completamenti si basano su sottostringhe durante la digitazione, cercando corrispondenze per parti di parole, lettere all'inizio delle parole e anche caratteri saltati. Per altri dettagli, vedere [Modificare il codice - Completamenti](editing-python-code-in-visual-studio.md#completions).

1. Aggiungere altro codice per visualizzare i valori di coseno per 360 gradi:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Eseguire di nuovo il programma premendo + **CTRL F5** o **Avvia debug** senza eseguire  >  **debug**. Al termine, chiudere la finestra di output.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Usare la finestra REPL interattiva](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Approfondimento

- [Modifica codice](editing-python-code-in-visual-studio.md)
- [Codice formato](formatting-python-code.md)
- [Effettuare il refactoring del codice](refactoring-python-code.md)
- [Usare PyLint](linting-python-code.md)
