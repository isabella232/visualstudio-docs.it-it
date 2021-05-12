---
title: Scrivere estensioni C++ per Python
description: Procedura dettagliata per la creazione di un'estensione C++ per Python con Visual Studio, CPython e PyBind11, incluso il debug in modalità mista.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 286d5f2c316379316b1a1cf55334cab39cdc247c
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782634"
---
# <a name="create-a-c-extension-for-python"></a>Creare un'estensione C++ per Python

I moduli scritti in C++ (o in C) vengono comunemente usati per estendere le funzionalità di un interprete Python e anche per abilitare l'accesso alle funzionalità di basso livello del sistema operativo. Sono disponibili tre tipi primari di moduli:

- Moduli acceleratori: dato che Python è un linguaggio interpretato, determinati frammenti di codice possono essere scritti in C++ per ottenere migliori prestazioni.
- Moduli wrapper:espongono al codice Python le interfacce C/C++ esistenti o un'API più facilmente utilizzabile da Python.
- Moduli di accesso al sistema di basso livello: creati per accedere alle funzionalità di livello inferiore del runtime, del sistema operativo `CPython` o dell'hardware sottostante.

Questo articolo illustra la compilazione di un modulo di estensione C++ per che calcola una `CPython` tangente iperbolica e la chiama dal codice Python. La routine viene implementata prima in Python per illustrare il miglioramento relativo delle prestazioni dell'implementazione della routine stessa in C++.

Questo articolo illustra anche due modi per rendere C++ disponibile a Python:

- Le estensioni standard `CPython` come descritto nella documentazione di [Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), scelta consigliata per C++ 11 per la sua semplicità.

L'esempio completato di questa procedura dettagliata è disponibile in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 o versioni successive con il carico di lavoro Sviluppo **Python** installato, inclusi gli strumenti di sviluppo nativi **Python**, che introduce il carico di lavoro C++ e i set di strumenti necessari per le estensioni native.

    ![Selezione dell'opzione Strumenti di sviluppo nativo Python](media/cpp-install-native.png)

    > [!Tip]
    > L'installazione del carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati** include anche Python e l'opzione **Strumenti di sviluppo nativi Python** per impostazione predefinita.

Per altre informazioni sulle opzioni di installazione, vedere [Installare il supporto python per Visual Studio](installing-python-support-in-visual-studio.md). Se si installa Python separatamente, assicurarsi di selezionare Scarica simboli **di debug** in **Opzioni avanzate** nel programma di installazione. Questa opzione è necessaria per usare il debug in modalità mista tra il codice Python e il codice nativo.

## <a name="create-the-python-application"></a>Creare un'applicazione Python

1. Creare un nuovo progetto Python in Visual Studio selezionando **File**  >  **nuovo**  >  **progetto**. Cercare "Python", selezionare il **modello Applicazione Python,** assegnargli un nome e un percorso a scelta e selezionare **OK.**

1. Nel file con estensione *py del* progetto incollare il codice seguente (o immetterlo manualmente per visualizzare alcune delle funzionalità di [modifica python).](editing-python-code-in-visual-studio.md) Questo codice calcola una tangente iperbolica senza usare la libreria matematica ed è ciò che verrà accelerato con le estensioni native.

    > [!Tip]
    > Scrivere il codice in Python puro prima di riscrivere in C++. In questo modo è possibile verificare più facilmente che il codice nativo sia corretto

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Eseguire il programma usando **Avvia**  >  **debug senza eseguire debug** (**CTRL** + **F5**) per visualizzare i risultati. È possibile cambiare la variabile `COUNT` per modificare il tempo impiegato per l'esecuzione del benchmark. Ai fini di questa procedura dettagliata, impostare il conteggio in modo che il benchmark richieda circa due secondi.

> [!TIP]
> Quando si eseguono benchmark, usare sempre Avvia debug senza debug per evitare l'overhead generato durante l'esecuzione di codice all'interno del  >   debugger Visual Studio debug.

## <a name="create-the-core-c-projects"></a>Creare i progetti C++ di base

Seguire le istruzioni in questa sezione per creare due progetti C++ identici denominato "superfastcode" e "superfastcode2". In seguito si useranno due approcci diversi in ogni progetto per esporre il codice C++ a Python.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, quindi scegliere **Aggiungi** > **Nuovo progetto**. Una soluzione Visual Studio può contenere progetti Python e C++ contemporaneamente. Questo è uno dei vantaggi offerti dall'uso di Visual Studio per Python.

1. Cercare "C++", selezionare **Progetto vuoto**, specificare il nome "superfastcode" ("superfastcode2" per il secondo progetto) e selezionare **OK**.

    > [!Tip]
    > Con gli **strumenti di sviluppo nativo Python** installati in Visual Studio è possibile iniziare con il modello **Modulo di estensione Python**, che include gran parte degli elementi descritti di seguito. Questa procedura dettagliata, tuttavia, inizia da un progetto vuoto e illustra la creazione del modulo di estensione in modo dettagliato. Dopo che si è compreso il processo, il modello consente di risparmiare tempo durante la scrittura di estensioni personalizzate.

1. Creare un file C++ nel nuovo progetto facendo clic con il pulsante destro del mouse sul nodo **File di origine**, quindi scegliere **Aggiungi** > **Nuovo elemento**, selezionare **File C++**, assegnare al file il nome `module.cpp` e fare clic su **OK**.

    > [!Important]
    > Un file con estensione *cpp* è necessario per attivare le pagine delle proprietà C++ nei passaggi che seguono.

1. Se si usa un runtime Python a 64 bit, attivare la configurazione **x64** usando il menu a discesa nella barra degli strumenti principale. Per un runtime Python a 32 bit, attivare la **configurazione Win32.**

1. Fare clic con il pulsante destro del mouse sul progetto C++ in **Esplora soluzioni** e scegliere **Proprietà**. Il valore di **Configurazione** deve essere  Attivo **(Debug)** e Piattaforma sarà Attivo **(x64)** o Attivo **(Win32)** a seconda della selezione effettuata nel passaggio precedente.

    > [!Tip]
    > Per i propri progetti, è necessario configurare sia le configurazioni di debug che di versione. In questo caso viene configurata solo la configurazione debug e impostata per l'uso di una *build* di versione di , che disabilita alcune funzionalità di debug del `CPython` runtime C++, incluse le asserzioni. `CPython` *L'uso* di file binari di debug ( `python_d.exe` ) richiede impostazioni diverse.

1. Impostare le proprietà specifiche, come descritto nella tabella seguente e quindi selezionare **OK**.
    ::: moniker range=">=vs-2019"
    | Scheda | Proprietà | Valore |
    | --- | --- | --- |
    | **Generale** | **Nome destinazione** | Specificare il nome del modulo quando si vuole fare riferimento a esso da Python in istruzioni `from...import`. Questo stesso nome viene usato in C++ quando si definisce il modulo per Python. Se si vuole usare il nome del progetto come nome del modulo, lasciare il valore predefinito di **$(ProjectName)**. Per `python_d.exe` , aggiungere alla fine del `_d` nome. |
    | | **Tipo configurazione** | **Libreria dinamica (.dll)** |
    | **Funzionalità avanzate** | **Estensione di file di destinazione** | **.pyd** |
    | **C/C++** > **Generale** | **Directory di inclusione aggiuntive** | Aggiungere la cartella *include* di Python nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\include`.  |
    | **C/C++** > **Preprocessore** | **Definizioni del preprocessore** | Se presente, modificare il **valore _DEBUG** in **NDEBUG** in modo che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **C/C++** > **Generazione codice** | **Libreria di runtime** | **DLL multi-thread (/MD) in modo** che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **Linker** > **Generale** | **Directory librerie aggiuntive** | Aggiungere la cartella *libs* di Python che include i file con estensione *lib* nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\libs`. Assicurarsi di indicare la cartella *libs* che contiene i file con estensione *lib* e *non* la cartella *Lib* che contiene i file con estensione *py*. |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Scheda | Proprietà | Valore |
    | --- | --- | --- |
    | **Generale** | **Generale** > **Nome di destinazione** | Specificare il nome del modulo quando si vuole fare riferimento a esso da Python in istruzioni `from...import`. Questo stesso nome viene usato in C++ quando si definisce il modulo per Python. Se si vuole usare il nome del progetto come nome del modulo, lasciare il valore predefinito di **$(ProjectName)**. Per `python_d.exe` , aggiungere alla fine del `_d` nome. |
    | | **Generale** > **Estensione di destinazione** | **.pyd** |
    | | **Impostazioni predefinite progetto** > **Tipo di configurazione** | **Libreria dinamica (.dll)** |
    | **C/C++** > **Generale** | **Directory di inclusione aggiuntive** | Aggiungere la cartella *include* di Python nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\include`.  |
    | **C/C++** > **Preprocessore** | **Definizioni del preprocessore** | Se presente, modificare il **valore _DEBUG** in **NDEBUG** in modo che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **C/C++** > **Generazione codice** | **Libreria di runtime** | **DLL multi-thread (/MD) in modo** che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **Linker** > **Generale** | **Directory librerie aggiuntive** | Aggiungere la cartella *libs* di Python che include i file con estensione *lib* nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\libs`. Assicurarsi di indicare la cartella *libs* che contiene i file con estensione *lib* e *non* la cartella *Lib* che contiene i file con estensione *py*. |
    ::: moniker-end
    
    > [!Tip]
    > Se la scheda C/C++ non è visualizzata nelle proprietà del progetto, il progetto non include alcun file identificato come file di origine C/C++. Questa condizione può verificarsi se si crea un file di origine senza un'estensione *c* o *cpp*. Ad esempio, se si è immesso accidentalmente anziché nella finestra di dialogo del nuovo elemento in precedenza, Visual Studio crea il file ma non imposta il tipo di file su "Codice C/C+", che attiva la scheda `module.coo` `module.cpp` delle proprietà C/C++. Tale errata identificazione rimane il caso anche se si rinomina il file con `.cpp` . Per impostare correttamente il tipo di file, fare clic con il pulsante destro del mouse sul file in **Esplora soluzioni**, scegliere **Proprietà** e quindi impostare **Tipo di file** su **Codice C/C++**.

1. Fare clic con il pulsante destro del mouse sul progetto C++ e scegliere **Compila** per testare le configurazioni **(debug** **e versione**). I file con estensione *pyd* si trovano nella cartella **solution** all'interno delle sottocartelle **Debug** e **Release**, non nella cartella del progetto C++.

1. Aggiungere il codice seguente al file *module.cpp* del progetto C++:

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

1. Se non già stato fatto, ripetere i passaggi precedenti per creare un secondo progetto denominato "superfastcode2" con contenuto identico.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertire i progetti C++ in estensioni per Python

Per rendere disponibile la DLL C++ in un'estensione per Python, modificare prima i metodi esportati in modo che interagiscano con i tipi di Python. Aggiungere quindi una funzione che esporti il modulo, insieme alle definizioni dei metodi del modulo.

Le sezioni seguenti illustrano come eseguire questi passaggi usando entrambe le estensioni `CPython` e PyBind11.

### <a name="cpython-extensions"></a>Estensioni CPython

Per altre informazioni su quanto illustrato in questa sezione, fare riferimento [](https://docs.python.org/3/c-api/module.html) al manuale di riferimento dell'API [Python/C](https://docs.python.org/3/c-api/index.html) e in particolare agli oggetti modulo in python.org (ricordarsi di selezionare la versione di Python dall'elenco a discesa in alto a destra per visualizzare la documentazione corretta).

1. All'inizio di *module.cpp* includere *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Modificare il metodo `tanh_impl` in modo che accetti e restituisca tipi di Python (ovvero un `PyObject*`):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Aggiungere una struttura che definisca come la funzione `tanh_impl` di C++ viene presentata a Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Aggiungere una struttura che definisca il modulo come si vuole farvi riferimento nel codice Python, in particolare quando si usa l'istruzione `from...import`. (Fare in modo che corrisponda al valore nelle proprietà del progetto in **Proprietà di configurazione**  >  **Generale**  >  **Nome destinazione.** Nell'esempio seguente il nome del modulo "superfastcode" indica che è possibile usare in Python, perché `from superfastcode import fast_tanh` è definito `fast_tanh` all'interno di `superfastcode_methods` . I nomi di file interni al progetto C++, ad *esempio module.cpp,* sono inconsequenziali.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Aggiungere un metodo che Python chiama quando carica il modulo, che deve essere denominato , dove module-name corrisponde esattamente alla proprietà General Target Name del progetto `PyInit_<module-name>` &lt; &gt; C++,   >    ovvero corrisponde al nome file del file con estensione pyd compilato dal progetto.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compilare di nuovo il progetto C++ per verificare il codice. Se si verificano errori, vedere la sezione [Risoluzione dei problemi](#troubleshooting) di seguito.

### <a name="pybind11"></a>PyBind11

Se è stata completata la procedura della sezione precedente, si sarà notato l'uso di una grande quantità di codice boilerplate per creare le strutture di modulo necessarie per il codice C++. PyBind11 semplifica il processo tramite macro in un file di intestazione C++ che ottiene lo stesso risultato con un volume di codice molto più ridotto. Per informazioni generali su quanto illustrato in questa sezione, vedere [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (Informazioni di base su PyBind11) in github.com.

1. Installare PyBind11 usando pip: `pip install pybind11` o `py -m pip install pybind11`. In alternativa, è possibile eseguire l'installazione usando la finestra Ambienti Python e quindi usare il comando "Apri in PowerShell" per il passaggio successivo.

1. Nello stesso terminale eseguire `python -m pybind11 --includes` o `py -m pybind11 --includes` . Verrà visualizzato un elenco di percorsi da aggiungere alla proprietà Directory di inclusione aggiuntive generali **C/C++** del progetto (rimuovendo il  >    >   `-I` prefisso, se presente).

1. All'inizio di un *file module.cpp* nuovo, che non include alcuna modifica rispetto alla sezione precedente, includere *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Alla fine di *module.cpp* usare la macro `PYBIND11_MODULE` per definire il punto di ingresso per la funzione C++:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Compilare il progetto C++ per verificare il codice. Se si verificano errori, vedere la sezione Risoluzione dei problemi di seguito.

### <a name="troubleshooting"></a>Risoluzione dei problemi

La compilazione del modulo C++ potrebbe non riuscire per i motivi seguenti:

- Non è possibile individuare *Python.h* (**E1696: Impossibile aprire il file di origine "Python.h"** e/o **C1083: Impossibile aprire il file di inclusione "Python.h": file o directory non esistente**): verificare che il percorso in **C/C++** > **Generale** > **Directory di inclusione aggiuntive** nelle proprietà del progetto punti alla cartella *include* dell'installazione di Python in uso. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Impossibile individuare le librerie Python: verificare che il percorso in Directory librerie aggiuntive generali del **linker** nelle proprietà del progetto punti alla cartella  >    >   *libs dell'installazione di* Python. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Errori del linker correlati all'architettura di destinazione: modificare l'architettura di progetto della destinazione C++ in modo che corrisponda a quella dell'installazione di Python in uso. Ad esempio, se la destinazione è **Win32** con il progetto C++ ma l'installazione di Python è a 64 bit, modificare il progetto C++ in **x64.**

## <a name="test-the-code-and-compare-the-results"></a>Testare il codice e confrontare i risultati

Ora che la libreria è strutturata con le estensioni per Python, è possibile fare riferimento a tali estensioni dal progetto Python, importare il modulo e usare i metodi delle estensioni.

### <a name="make-the-dll-available-to-python"></a>Rendere disponibile la DLL per Python

Ci sono due modi per rendere disponibile la DLL per Python.

Il primo metodo funziona se il progetto Python e il progetto C++ sono nella stessa soluzione. Passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto Python e quindi scegliere **Aggiungi riferimento**. Nella finestra di dialogo visualizzata selezionare la scheda **Progetti**, selezionare il progetto **superfastcode** e il progetto **superfastcode2**, quindi fare clic su **OK**.

![Aggiunta di un riferimento al progetto superfastcode](media/cpp-add-reference.png)

Il metodo alternativo, descritto nei passaggi seguenti, installa il modulo nell'ambiente Python, rendendolo disponibile anche per altri progetti Python. Per una documentazione più completa, visitare il progetto [ **setuptools.**](https://setuptools.readthedocs.io/)

1. Creare un file denominato *setup.py* nel progetto C++ facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Aggiungi** > **Nuovo elemento**. Selezionare quindi **File di C++ (.cpp)**, assegnare il nome `setup.py` al file e selezionare **OK**. L'assegnazione di un nome al file con estensione *py* consente di fare in modo che Visual Studio lo riconosca come Python nonostante l'uso del modello di file C++. Quando il file viene visualizzato nell'editor, incollare nel file il codice seguente in base al metodo di estensione:

    **`CPython` extensions (progetto superfastcode):**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (progetto superfastcode2):**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. Creare un secondo file denominato *pyproject.toml* nel progetto C++ e incollarne il codice seguente.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Per compilare l'estensione, fare clic con il pulsante destro del mouse sulla scheda *apri pyproject.toml* e scegliere "Copia percorso completo" (il nome *pyproject.toml* verrà eliminato dal percorso prima di usarlo).

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sull'ambiente Python attivo e *scegliere Gestisci pacchetti Python*.

    > [!Tip]
    > Se il pacchetto è già stato installato, verrà visualizzato nell'elenco qui. Fare clic sulla "X" per disinstallarla prima di continuare.

1. Incollare il percorso copiato nella casella di ricerca ed eliminare `pyproject.toml` dalla fine. Premere quindi INVIO per eseguire l'installazione da tale directory.

    > [!Tip]
    > Se l'installazione non riesce a causa di un errore di autorizzazione, aggiungere `--user` e provare di nuovo il comando.


### <a name="call-the-dll-from-python"></a>Chiamare la DLL da Python

Dopo aver reso disponibili a Python le DLL come descritto nella sezione precedente, è ora possibile chiamare le funzioni `superfastcode.fast_tanh` e `superfastcode2.fast_tanh2` dal codice Python e confrontarne le prestazioni con l'implementazione Python:

1. Aggiungere le righe seguenti al file con estensione *py* per chiamare i metodi esportati dalle DLL e visualizzarne l'output:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Eseguire il programma Python (**Avvia** debug senza debug o CTRL F5 ) e osservare che le routine C++ vengono eseguite circa da cinque a venti volte più veloci rispetto all'implementazione  >    + di Python. In genere l'output ha l'aspetto seguente:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Se il **comando Avvia senza eseguire debug** è disabilitato, fare clic con il pulsante destro del mouse sul progetto Python in Esplora soluzioni e scegliere Imposta come progetto di **avvio**. 

1. Provare a incrementare la variabile `COUNT` in modo che le differenze siano più evidenti. Anche **una** build di debug del modulo C++ viene  eseguita più lentamente rispetto **a** una build di versione perché la build di debug è meno ottimizzata e contiene vari controlli degli errori. È possibile passare da una configurazione all'altro per il confronto ,ma ricordarsi di tornare indietro e aggiornare le proprietà di una versione precedente per la **configurazione di** versione.

Nell'output si può vedere che l'estensione PyBind11 non è veloce come l'estensione, anche se dovrebbe essere notevolmente più veloce dell'implementazione `CPython` python pura. Questa differenza si verifica in gran parte perché è stata usata la chiamata , che non supporta più parametri, nomi di parametro `METH_O` o argomenti di parole chiave. PyBind11 genera codice leggermente più complesso per fornire un'interfaccia più simile a Python ai chiamanti, ma poiché il codice di test chiama la funzione 500.000 volte, i risultati possono aumentare notevolmente il sovraccarico.

È possibile ridurre ulteriormente il sovraccarico spostando `for` il ciclo nel codice nativo. Ciò comporterebbe l'uso del protocollo [iterator](https://docs.python.org/c-api/iter.html) (o del tipo pyBind11 per il parametro della funzione ) per `py::iterable` elaborare [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)ogni elemento. La rimozione delle transizioni ripetute tra Python e C++ è un modo efficace per ridurre il tempo necessario per elaborare la sequenza.

### <a name="troubleshooting"></a>Risoluzione dei problemi

Se si riceve un messaggio quando si tenta di importare il modulo, è probabile che la causa sia uno `ImportError` dei problemi seguenti:

* Quando si compila tramite un riferimento al progetto, assicurarsi che le proprietà del progetto C++ corrispondano all'ambiente Python attivato per il progetto Python, in particolare le directory Include e Library.

* Assicurarsi che il file di output sia denominato `superfastcode.pyd` . Un nome o un'estensione diversa ne impedirà l'importazione.

* Se il modulo è stato installato usando il file *setup.py,* verificare di aver eseguito il comando *pip* nell'ambiente Python attivato per il progetto Python. Espandendo l'ambiente Python in Esplora soluzioni dovrebbe essere presente una voce per `superfastcode` .

## <a name="debug-the-c-code"></a>Eseguire il debug del codice C++

Visual Studio supporta il debug di codice Python e C++ insieme. Questa sezione illustra il processo usando il progetto **superfastcode**. I passaggi sono identici per il progetto **superfastcode2**.

1. Fare clic con il pulsante destro del mouse sul progetto Python in **Esplora soluzioni**, scegliere **Proprietà**, selezionare la scheda **Debug** e quindi selezionare l'opzione **Debug** > **Abilita debug codice nativo**.

    > [!Tip]
    > Quando si abilita il debug del codice nativo, la finestra di output python potrebbe scomparire immediatamente al termine del programma senza fornire il consueto premere un tasto qualsiasi **per continuare a sospendere.** Per forzare una sospensione, aggiungere l'opzione al campo Esegui argomenti interprete nella scheda Debug quando `-i` si abilita il debug del codice   >   nativo.  Questo argomento imposta l'interprete Python in modalità interattiva al termine del codice, a quel punto attende di premere **CTRL** + **Z**  >  **INVIO** per uscire. In alternativa, se si vuole modificare il codice Python, è possibile aggiungere le istruzioni `import os` e `os.system("pause")` alla fine del programma. Questo codice duplica la richiesta di pausa originale.

1. Selezionare **Salva file**  >  **per** salvare le modifiche alle proprietà.

1. Impostare la configurazione della build su **Debug** nella barra Visual Studio strumenti.

    ![Impostazione della configurazione di build su Debug](media/cpp-set-debug.png)

1. Dato che l'esecuzione del codice richiede in genere più tempo nel debugger, può essere utile modificare la variabile `COUNT` nel file con estensione *py* impostando un valore inferiore di circa cinque volte, ad esempio modificarlo da `500000` a `100000`.

1. Nel codice C++ impostare un punto di interruzione nella prima riga del metodo `tanh_impl` e quindi avviare il debugger (**F5** o **Debug** > ). Il debugger interrompe l'esecuzione quando viene chiamato tale codice. Se il punto di interruzione non viene raggiunto, verificare che la configurazione sia impostata su **Debug** e che il progetto sia stato salvato( ciò non avviene automaticamente all'avvio del debugger).

    ![Interruzione in un punto del codice C++](media/cpp-debugging.png)

1. A questo punto è possibile eseguire il codice C++ istruzione per istruzione, esaminare le variabili e così via. Queste funzionalità sono descritte in dettaglio in [Debug contemporaneo di codice Python e C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Approcci alternativi

Esistono svariati modi per creare estensioni di Python, come descritto nella tabella seguente. Le prime due voci per `CPython` e sono già state illustrate in questo `PyBind11` articolo.

| Approccio | Vintage | Utenti rappresentanti | 
| --- | --- | --- |
| Moduli di estensione C/C++ per `CPython` | 1991 | Libreria standard | 
| [PyBind11](https://github.com/pybind/pybind11) (scelta consigliata per C++) | 2015 |  |
| [Cython](https://cython.org) (scelta consigliata per C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/), [pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Vedi anche

L'esempio completato di questa procedura dettagliata è disponibile in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
