---
title: Uso di C++ e Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
description: Processo e passaggi per scrivere un modulo o un'estensione di C++ per Python in Visual Studio
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 08f91846340e2acc993e5302badfc846db5f4a9c
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="creating-a-c-extension-for-python"></a>Creazione di un'estensione C++ per Python

I moduli scritti in C++ (o in C) vengono comunemente usati per estendere le funzionalità di un interprete Python e anche per abilitare l'accesso alle funzionalità di basso livello del sistema operativo. Sono disponibili tre tipi primari di moduli:

- Moduli acceleratori: dato che Python è un linguaggio interpretato, determinati frammenti di codice possono essere scritti in C++ per ottenere migliori prestazioni. 
- Moduli wrapper: i wrapper espongono al codice Python le interfacce C/C++ esistenti o un'API più facilmente utilizzabile da Python.
- Moduli di accesso al sistema di basso livello: creati per accedere alle funzionalità di basso livello del runtime di CPython, al sistema operativo o all'hardware sottostante. 

Questo argomento illustra la creazione di un modulo di estensione C++ per CPython per calcolare una tangente iperbolica e per chiamare il codice Python. La routine viene implementata prima in Python per illustrare il miglioramento delle prestazioni dell'implementazione della routine stessa in C++.

L'approccio adottato in questo argomento è quello per le estensioni CPython standard come illustrato nella [documentazione di Python](https://docs.python.org/3/c-api/). Un confronto tra questo e altri approcci viene illustrato in [Approcci alternativi](#alternative-approaches) alla fine di questo argomento.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 con i carichi di lavoro **Sviluppo di applicazioni desktop con C++** e **Sviluppo Python** installati con le opzioni predefinite. 
- Nel carico di lavoro **Sviluppo Python** attivare la casella **Strumenti di sviluppo nativi Python** a destra per impostare la maggior parte delle opzioni descritte in questo argomento. Questa opzione include automaticamente anche il carico di lavoro C++. 

![Selezione dell'opzione Strumenti di sviluppo nativo Python](media/cpp-install-native.png)

- L'installazione del carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati** include anche Python e l'opzione **Strumenti di sviluppo nativi Python** per impostazione predefinita.

Per altre informazioni, vedere [Installazione del supporto di Python in Visual Studio](installation.md), che illustra l'uso di altre versioni di Visual Studio. Se si installa Python separatamente, assicurarsi di selezionare **Download debugging symbols** (Scarica i simboli di debug) e **Download debug binaries** (Scarica file binari di debug) nella sezione **Opzioni avanzate** del programma di installazione. Questa opzione consente di avere a disposizione le librerie di debug necessarie se si sceglie di eseguire una build di debug.

## <a name="create-the-python-application"></a>Creare un'applicazione Python

1. Creare un nuovo progetto di Python in Visual Studio selezionando **File > Nuovo > Progetto**. Cercare "Python", selezionare il modello **Applicazione Python**, assegnare a questo un nome e un percorso appropriati e selezionare **OK**.

1. Nel file `.py` del progetto, incollare il codice seguente che effettua il benchmark del calcolo di una tangente iperbolica, implementato senza usare la libreria matematica per un confronto più semplice. È anche possibile immettere il codice manualmente per provare alcune delle [funzionalità di modifica Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Eseguire il programma usando **Debug > Avvia senza eseguire debug** (CTRL + F5) per visualizzare i risultati. È possibile modificare la variabile `COUNT` per modificare il tempo impiegato per l'esecuzione dei benchmark. Ai fini di questa procedura dettagliata, impostare il conteggio in modo che ogni benchmark richieda circa due secondi.

## <a name="create-the-core-c-project"></a>Creare un progetto di base C++

1. Fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e selezionare **Aggiungi > Nuovo progetto**. Una soluzione di Visual Studio può includere progetti Python e C++ insieme.

1. Ricercare "C++", selezionare **Progetto vuoto**, specificare un nome (ad esempio TanhBenchmark) e fare clic su **OK**. Nota: se sono stati installati gli **strumenti di sviluppo nativo Python** con Visual Studio 2017, è possibile iniziare con il modello **Modulo di estensione Python**, che include quasi tutti gli elementi descritti in questo argomento. Questa procedura dettagliata, tuttavia, inizia da un progetto vuoto e illustra la creazione del modulo di estensione in modo dettagliato.

1. Creare un file C++ nel nuovo progetto facendo clic con il pulsante destro del mouse sul nodo **File di origine**, selezionare **Aggiungi > Nuovo elemento**, selezionare **File C++**, assegnargli un nome (ad esempio `module.cpp`) e fare clic su **OK**. Questo passaggio è obbligatorio per attivare le pagine delle proprietà C++ nei passaggi successivi.

1. Fare clic con il pulsante destro del mouse sul nuovo progetto e selezionare **Proprietà**, nella parte superiore della finestra di dialogo **Pagine delle proprietà** impostare **Configurazione** a **Tutte le configurazioni**.

1. Impostare le proprietà specifiche, come descritto di seguito, quindi selezionare **OK**.

    | Tab | Proprietà | Valore | 
    | --- | --- | --- |
    | Generale | Generale > Nome di destinazione | Impostare questo campo in modo che corrisponda esattamente al nome del modulo nella forma in cui lo vede Python. |
    | | Generale > Estensione di destinazione | .pyd |
    | | Impostazioni predefinite del progetto > Tipo di configurazione | Libreria dinamica (.dll) |
    | C/C++ > Generale | Directory di inclusione aggiuntive | Aggiungere la cartella `include` di Python nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\include` |     
    | C/C++ > Preprocessore | Definizioni del preprocessore | L'aggiunta di `Py_LIMITED_API;` all'inizio della stringa limita alcune delle funzioni che è possibile chiamare da Python e rende il codice più portatile tra versioni diverse di Python. |
    | C/C++ > Generazione codice | Libreria di runtime | DLL multithread (/MD) (vedere l'avviso di seguito) |
    | Linker > Generale | Directory librerie aggiuntive | Aggiungere la cartella `libs` di Python che include i file `.lib` nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\libs`. Assicurarsi di indicare la cartella `libs` che contiene i file `.lib`, e *non* la cartella `Lib` che contiene i file `.py`. | 

    > [!Tip]
    > Se non viene visualizzata la scheda C/C++, significa che il progetto non include nessun file identificato come file di origine C/C++. Questa condizione può verificarsi se si crea un file di origine senza un'estensione `.c` o `.cpp`. Ad esempio, se viene digitato per errore `module.coo` invece di `module.cpp` nella precedente finestra di dialogo del nuovo elemento, Visual Studio crea il file ma non imposta il tipo di file su "Codice C/C+," che attiva la scheda delle proprietà C/C++. Questo errore di identificazione permane anche se si rinomina il file con l'estensione `.cpp`. Per impostare correttamente il tipo di file, fare clic con il pulsante destro del mouse sul file in Esplora soluzioni, selezionare **Proprietà** e quindi impostare **Tipo di file** su **Codice C/C++**.

    > [!Warning]
    > Non impostare l'opzione **C/C++ > Generazione codice > Libreria di runtime** su "DLL di debug multithread (/MDd)" nemmeno per una configurazione di debug. Selezionare il runtime "DLL multithread (/MD)" perché i file binari Python non debug vengono compilati con questa opzione. Se si imposta l'opzione /MDd, viene restituito l'errore *C1189: Py_LIMITED_API non è compatibile con Py_DEBUG, Py_TRACE_REFS e Py_REF_DEBUG* quando si compila una configurazione di debug della libreria. In aggiunta, se si rimuove `Py_LIMITED_API` per evitare l'errore di compilazione, l'esecuzione di Python si arresta in modo anomalo quando prova a importare il modulo. L'arresto anomalo del sistema si verifica all'interno della chiamata della DLL a `PyModule_Create`, come descritto più avanti, con il messaggio di output *Fatal Python error: PyThreadState_Get: no current thread* (Errore irreversibile di Python: PyThreadState_Get: nessun thread corrente).
    >
    > Si noti che l'opzione /MDd viene usata per compilare file binari di debug di Python (ad esempio python_d.exe), ma la selezione di questa opzione per una DLL di estensione causa sempre un errore di compilazione con `Py_LIMITED_API`.
   
1. Fare clic con il pulsante destro del mouse sul progetto C++ e selezionare **Compila** per testare le configurazioni sia di debug che di versione. I file `.pyd` si trovano nella cartella *solution* all'interno delle sottocartelle **Debug** e **Release**, non nella cartella del progetto C++.

1. Aggiungere il codice seguente al file `.cpp` del progetto C++ principale:

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Compilare di nuovo il progetto C++ per confermare che il codice sia corretto.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertire il progetto C++ in un'estensione per Python

Per rendere disponibile la DLL C++ in un'estensione per Python, è necessario modificare i metodi esportati in modo che interagiscano con i tipi di Python. È quindi necessario aggiungere una funzione che esporti il modulo, insieme alle definizioni dei metodi del modulo. Per informazioni generali su quanto illustrato di seguito, vedere [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) (Manuale di riferimento all'API Python/C) e in particolare [Module Objects](https://docs.python.org/3/c-api/module.html) (Oggetti del modulo) in python.org. Ricordarsi di selezionare la versione di Python dal controllo a discesa in alto a destra.

1. Nel file C++, includere `Python.h` nella parte superiore:

    ```cpp
    #include <Python.h>
    ```

1. Modificare il metodo `tanh_impl` in modo che accetti e restituisca i tipi di Python:

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Aggiungere una struttura che definisca come la funzione `tanh` di C++ viene presentata a Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Aggiungere una struttura che definisca il modulo nella forma in cui lo si vede tramite il codice Python. (I nomi di file interni del progetto C++, come module.cpp, sono irrilevanti.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name as Python sees it
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Aggiungere un metodo che verrà chiamato da Python quando carica il modulo, che deve essere denominato `PyInit_<module-name>` dove *&lt;module_name&gt;* corrisponde esattamente alla proprietà **Generale > Nome di destinazione** del progetto C++ (ovvero corrisponde al nome del file `.pyd` compilato dal progetto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compilare di nuovo il progetto C++ per verificare il codice.

## <a name="test-the-code-and-compare-the-results"></a>Testare il codice e confrontare i risultati

Ora che la libreria è strutturata come estensione per Python, è possibile fare riferimento a tale libreria dal progetto Python, importare il modulo e usare i metodi.

### <a name="make-the-dll-available-to-python"></a>Rendere disponibile la DLL per Python

Ci sono due modi per rendere disponibile la DLL per Python.

In primo luogo, è possibile aggiungere un riferimento dal progetto Python al progetto C++, purché si trovino nella stessa soluzione di Visual Studio:

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto Python e scegliere **Aggiungi riferimento**. Nella finestra di dialogo visualizzata selezionare la scheda **Progetti**, selezionare il progetto **superfastcode** (o qualsiasi nome usato) e quindi fare clic su **OK**.

In secondo luogo, è possibile installare il modulo nell'ambiente globale di Python, rendendolo disponibile anche per altri progetti Python. Questo in genere richiede di aggiornare il database di completamento IntelliSense per tale ambiente. L'aggiornamento è necessario anche quando si rimuove il modulo dall'ambiente.

1. Se si usa Visual Studio 2017, eseguire il programma di installazione di Visual Studio, selezionare **Modifica**, selezionare **Singoli componenti > Compilatori, strumenti di compilazione e runtime > Set di strumenti di Visual C++ 2015.3 v140**. Questo passaggio è necessario perché Python (per Windows) è esso stesso compilato con Visual Studio 2015 (versione 14.0) e richiede la disponibilità di questi strumenti quando compila un'estensione tramite il metodo descritto in questo argomento.

1. Creare un file denominato `setup.py` nel progetto C++ facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Aggiungi > Nuovo elemento**. Selezionare quindi "File di C++ (.cpp)", assegnare il nome `setup.py` al file e selezionare **OK**. L'assegnazione di un nome al file con estensione `.py` consente di fare in modo che Visual Studio lo riconosca come Python nonostante l'uso del modello di file C++. Quando il file viene visualizzato nell'editor, incollarvi il codice seguente:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Per documentazione su questo script, vedere [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (Compilazione di estensioni C e C++) in python.org.

1. Il codice `setup.py` indica a Python di compilare l'estensione usando il set di strumenti di Visual Studio 2015 C++ dalla riga di comando. Aprire un prompt dei comandi con privilegi elevati, passare alla cartella contenente il progetto C++ (e `setup.py`) e digitare il comando seguente:

    ```
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Chiamare la DLL da Python

Dopo aver completato uno dei metodi precedenti, è ora possibile chiamare la funzione `fast_tanh` e confrontarne le prestazioni con l'implementazione Python:

1. Aggiungere le righe seguenti nel file `.py` per chiamare il metodo `fast_tanh` esportato dalla DLL e visualizzarne l'output. Se si digita l'istruzione `from s` manualmente, `superfastcode` compare nell'elenco di completamento e quando si digita `import` appare il metodo `fast_tanh`.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Eseguire il programma Python. La routine C++ viene seguita da 5 a 20 volte più velocemente rispetto all'implementazione Python. Provare di nuovo a incrementare la variabile `COUNT` in modo che le differenze siano più evidenti. Si noti inoltre che una build di versione del modulo C++ viene eseguita più velocemente rispetto a una build di debug perché quest'ultima è meno ottimizzata e contiene vari controlli degli errori. È possibile alternare liberamente queste configurazioni ai fini del confronto.

## <a name="debug-the-c-code"></a>Eseguire il debug del codice C++

Visual Studio supporta il debug di codice Python e C++ insieme.

1. Fare clic con il pulsante destro del mouse sul progetto Python in Esplora soluzioni, selezionare **Proprietà**, selezionare la scheda **Debug** e quindi selezionare l'opzione **Debug > Abilita debug codice nativo** .

    > [!Tip]
    > Quando si abilita il debug del codice nativo, è possibile che la finestra di output di Python venga chiusa quando il programma avrà terminato l'operazione, senza che venga visualizzato il consueto messaggio "Premere un tasto qualsiasi per continuare". Per specificare una pausa, aggiungere l'opzione `-i` al campo **Esegui > Argomenti dell'interprete** della scheda **Debug** quando si abilita il debug del codice nativo. Questo argomento fa passare l'interprete di Python in modalità interattiva al termine del codice e attende che vengano premuti CTRL+Z, INVIO per uscire. In alternativa, se si vuole modificare il codice Python, è possibile aggiungere le istruzioni `import os` e `os.system("pause")` alla fine del programma. Questo codice duplica la richiesta di pausa originale.

1. Selezionare **File > Salva** per salvare le modifiche delle proprietà.

1. Impostare la configurazione di build su Debug sulla barra degli strumenti di Visual Studio. 

    ![Impostazione della configurazione di build su Debug](media/cpp-set-debug.png)

1. Dato che l'esecuzione del codice richiede in genere più tempo nel debugger, può essere utile modificare la variabile `COUNT` nel file `.py` impostando un valore inferiore di circa 5 volte (ad esempio, modificarlo da `500000` a `100000`).

1. Nel codice C++ impostare un punto di interruzione nella prima riga del metodo `tanh_impl` e quindi avviare il debugger (F5 or **Debug > Avvia debug**). Il debugger interrompe l'esecuzione quando viene chiamato tale codice. Se non viene raggiunto il punto di interruzione, controllare che la configurazione sia impostata su Debug e di aver salvato il progetto, operazione che non viene eseguita automaticamente all'avvio del debugger.

    ![Interruzione in un punto del codice C++](media/cpp-debugging.png)

1. A questo punto è possibile eseguire il codice C++ istruzione per istruzione, esaminare le variabili e così via. Queste funzionalità sono descritte in dettaglio in [Debug di codice Python e C++ in contemporanea](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Approcci alternativi 

Esistono svariati modi per creare estensioni di Python, come descritto nella tabella seguente. La prima voce per CPython corrisponde a ciò che è già stato illustrato in questo argomento.

| Approccio | Anno | Utenti rappresentanti | Vantaggi | Svantaggi |
| --- | --- | --- | --- | --- |
| Moduli di estensione C/C++ per CPython | 1991 | Libreria standard | [Documentazione ampia ed esercitazioni](https://docs.python.org/3/c-api/). Controllo totale. | Compilazione, portabilità, gestione dei riferimenti. Conoscenza elevata di C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Genera associazioni per molte lingue contemporaneamente. | Sovraccarico eccessivo se Python è l'unica destinazione. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nessuna compilazione, ampia disponibilità. | Accesso e modifica di strutture C complesse e soggette a errori. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Simile a Python. Altamente maturo. Prestazioni elevate. | Compilazione, nuova sintassi e toolchain. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilità di integrazione, compatibilità PyPy. | Nuovo, meno maturo. |
