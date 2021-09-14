---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 4, esecuzione del debug
titleSuffix: ''
description: Passaggio 4 della procedura dettagliata di base sulle funzionalità di Visual Studio, dedicato a come eseguire il codice Python nel debugger.
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
ms.openlocfilehash: d4ec2aacb6ba0eb06e6603928da623c7b5bb9d7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636939"
---
# <a name="step-4-run-code-in-the-debugger"></a>Passaggio 4: Eseguire il codice nel debugger

**Passaggio precedente: [Usare la finestra Interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Oltre a gestire i progetti, offrendo un'esperienza di modifica completa e la finestra interattiva, Visual Studio il debug completo per il codice Python.  Nel debugger, è possibile eseguire il codice in dettaglio, incluse le interazioni di un ciclo. È anche possibile sospendere il programma ogni volta che vengono soddisfatte determinate condizioni. Quando il programma viene sospeso nel debugger, è possibile esaminare in qualsiasi momento lo stato dell'intero programma e modificare il valore di variabili. Tali azioni sono essenziali per individuare i bug del programma e offrire supporto per seguire attentamente il flusso esatto del programma.

1. Sostituire il codice nel file *PythonApplication1.py* con il codice seguente. Questa variante del codice espande `make_dot_string` in modo da poter esaminare i passaggi discreti nel debugger. Inserisce anche il ciclo `for` in una funzione `main` e lo esegue in modo esplicito chiamando la funzione:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Controllare che il codice funzioni correttamente. A tale scopo, premere **F5** o selezionare il comando di menu **Debug** > **Avvia debug**. Il comando esegue il codice nel debugger. Dato che non sono impostate pause per l'esecuzione del programma, stampa semplicemente un motivo ondulato per alcune iterazioni. Premere un tasto qualsiasi per chiudere la finestra di output.

    > [!Tip]
    > Per chiudere automaticamente la finestra di output al termine del programma, selezionare il comando di menu Strumenti Opzioni, espandere il  >   **nodo Python,** selezionare **Debug** e quindi deselezionare l'opzione Attendi input quando il processo viene chiuso **normalmente:**
    >
    > ![Opzione di debug di Python per chiudere la finestra di output alla normale uscita dal programma](media/vs-getting-started-python-22-debugging5.png)
    >
    > Per altre informazioni sul debug, incluse attività come l'impostazione di argomenti di script e interprete, vedere Eseguire il [debug del codice Python.](debugging-python-in-visual-studio.md)

1. Impostare un punto di interruzione nell'istruzione facendo clic una volta sul margine grigio di tale riga oppure posizionando il punto di inserimento nella riga e usando il comando `for` **Debug** Attiva/Disattiva punto di interruzione  >   (**F9**). Sul margine grigio viene visualizzato un punto rosso per indicare il punto di interruzione, come indicato dalla freccia blu di seguito:

    ![Impostazione di un punto di interruzione](media/vs-getting-started-python-18-debugging1.png)

1. Avviare di nuovo il debugger (**F5**) e verificare che l'esecuzione del codice si arresti nella riga con tale punto di interruzione. È così possibile analizzare lo stack di chiamate ed esaminare le variabili locali. Le variabili incluse nell'ambito, quando definite, vengono visualizzati nella finestra **Auto** ; è anche possibile passare alla visualizzazione **Variabili locali** nella parte inferiore della finestra per visualizzare tutte le variabili che Visual Studio individua nell'ambito attuale (funzioni incluse), comprese quelle non ancora definite:

    ![Esperienza dell'interfaccia utente per i punti di interruzione per Python](media/vs-getting-started-python-19-debugging2b.png)

1. Osservare la barra degli strumenti di debug (visualizzata di seguito) nella parte superiore della finestra di Visual Studio. Questa barra degli strumenti consente di accedere rapidamente ai comandi di debug più comuni (disponibili nel menu **Debug**):

    ![Pulsanti essenziali della barra degli strumenti di debug](media/vs-getting-started-python-20-debugging3.png)

    I pulsanti da sinistra a destra nel modo seguente:
    - **Continue** (**F5**) esegue il programma fino al punto di interruzione successivo o fino al completamento del programma.
    - **Interrompi tutto** **(CTRL** +  + **ALT+INTERR)** sospende un programma a esecuzione lunga.
    - **Arresta debug** (**MAIUSC** + **F5**) arresta il programma ovunque si trova e chiude il debugger.
    - **Restart** (**CTRL** MAIUSC F5 ) arresta il programma ovunque si trova e +  + lo riavvia dall'inizio nel debugger.
    - **Show Next Statement** (**ALT** + **NUM** **&#42;**) passa alla riga di codice successiva da eseguire. Questo è particolarmente utile per spostarsi all'interno del codice durante una sessione di debug e tornare rapidamente al punto in cui il debugger si è interrotto.
    - **Istruzione (** **F11**) esegue la riga di codice successiva, immettendo nelle funzioni chiamate.
    - **Esegui istruzione/routine** (**F10**) esegue la riga successiva del codice, senza inserirsi nelle funzioni chiamate.
    - **Esci da istruzione/routine** (**MAIUSC**+**F11**) esegue la parte restante della funzione corrente e le pause nel codice chiamante.

1. Eseguire l'istruzione/routine `for` usando **Esegui istruzione/routine**. L'*esecuzione di istruzioni* prevede l'esecuzione della linea di codice corrente da parte del debugger, incluse le chiamate di funzione, e poi di nuovo una pausa immediata. Si noti come la variabile `i` è ora definita nelle finestre **Variabili locali** e **Auto**.

1. Eseguire l'istruzione/routine alla riga successiva del codice che chiama `make_dot_string` e si sospende. **Esegui istruzione/routine** in questo caso indica in modo specifico che il debugger esegue l'intero `make_dot_string` e dopo la restituzione si sospende. Il debugger non si arresta all'interno della funzione a meno che non sia presente un punto di interruzione separato.

1. Ripetere altre volte l'esecuzione dell'istruzione/routine e osservare in che modo si modificano i valori **Variabili locali** o **Auto**.

1. Nella finestra **Variabili locali** o **Auto** fare doppio clic sulla colonna **Valore** per le variabili `i` o `s` per modificare il valore. Premere **INVIO o** fare clic su un'area esterna a tale valore per applicare le modifiche.

1. Continuare l'esecuzione nel codice usando **Esegui istruzione**. **Esegui istruzione** indica che il debugger viene inserito all'interno di una qualsiasi chiamata di funzione per la quale ha informazioni di debug, ad esempio `make_dot_string`. Una volta dentro a `make_dot_string` è possibile esaminare le variabili locali ed eseguire i passaggi nel codice.

1. Continuare l'esecuzione con **Esegui istruzione**. Si noti che quando si raggiunge la fine di `make_dot_string`, il passaggio successivo restituisce al ciclo `for` il nuovo valore restituito nella variabile `s`. Mentre si esegue di nuovo l'istruzione `print`, si noti che **Esegui istruzione** in `print` non entra in tale funzione. Questo si verifica perché `print` non è scritto in Python ma è un codice nativo che si trova all'interno del runtime di Python.

1. Continuare a usare **Esegui istruzione** fino a quando non si è nuovamente in `make_dot_string`. Quindi usare **Esci da istruzione/routine**. Si noti che si è fatto ritorno al ciclo `for`. Con **Esci da istruzione/routine**, il debugger esegue il resto della funzione e quindi si sospende automaticamente nel codice chiamante. Ciò è molto utile per quelle porzioni delle funzioni di lunga durata su cui si vuole eseguire il debug ma senza eseguire il resto della funzione un'istruzione alla volta né impostare un punto di interruzione esplicito nel codice chiamante.

1. Per continuare l'esecuzione del programma, fino a quando non viene raggiunto il punto di interruzione successivo, usare **Continua** (**F5**). Dato che il ciclo `for` contiene un punto di interruzione, l'esecuzione viene interrotta nell'iterazione successiva.

1. Scorrere centinaia di iterazioni di un ciclo può risultare noioso, pertanto in Visual Studio è possibile aggiungere una *condizione* a un punto di interruzione. Il debugger sospende quindi il programma nel punto di interruzione solo quando la condizione viene soddisfatta. Ad esempio, è possibile usare una condizione con il punto di interruzione sull'istruzione `for` in modo che non venga sospeso solo quando il valore di `i` supera 1600. Per impostare questa condizione, fare clic con il pulsante destro del mouse sul punto rosso del punto di interruzione e scegliere **Condizioni** (**ALT**+**F9** > **C**). Nella finestra **Impostazioni punto di interruzione** visualizzata immettere `i > 1600` come espressione e selezionare **Chiudi**. Premere **F5** per continuare e osservare che il programma esegue diverse iterazioni prima del punto di interruzione successivo.

    ![Impostazione di una condizione per il punto di interruzione](media/vs-getting-started-python-21-debugging4.png)

1. Per eseguire il programma fino al completamento, disabilitare il punto di interruzione facendo clic con il pulsante destro del mouse sul punto nel margine e scegliendo **Disabilita** punto di interruzione **(CTRL** + **F9).** Quindi selezionare **Continua** (o premere **F5**) per eseguire il programma. Quando termina, Visual Studio arresta la sessione di debug e restituisce la modalità di modifica. Si noti che è anche possibile eliminare il punto di interruzione selezionando il relativo punto o facendo clic con il pulsante destro del mouse sul punto e scegliendo Elimina punto di interruzione **,** ma vengono eliminate anche tutte le condizioni impostate.

> [!Tip]
> In alcune situazioni, come ad esempio quando si verifica un errore durante l'avvio dell'interprete Python stesso, la finestra di output potrebbe essere visualizzata solo per pochissimo tempo e poi chiudersi automaticamente, impedendo la visualizzazione dei messaggi di errore. In questo caso, fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni**, scegliere Proprietà **,** selezionare la scheda **Debug** e quindi aggiungere al campo `-i` Argomenti **dell'interprete.** Questo argomento fa sì che l'interprete entri in modalità interattiva dopo il completamento di un programma, mantenendo la finestra aperta fino a quando non si preme **CTRL** + **Z**  >  **INVIO** per uscire.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Installare i pacchetti nell'ambiente Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Approfondimento

- [Debug](debugging-python-in-visual-studio.md)
- Vedere [Debug in Visual Studio](../debugger/debugger-feature-tour.md) per la documentazione completa sulle funzionalità di debug di Visual Studio.
