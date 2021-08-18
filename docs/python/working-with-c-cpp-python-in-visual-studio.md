---
title: Scrivere estensioni C++ per Python
description: Questo articolo illustra come creare un'estensione C++ per Python usando Visual Studio, CPython e PyBind11, incluso il debug in modalità mista.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a93dee3e00df6b98afe41306af079302e1017bc4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140297"
---
# <a name="create-a-c-extension-for-python"></a>Creare un'estensione C++ per Python

I moduli scritti in C++ (o C) vengono comunemente usati per estendere le funzionalità di un interprete Python. Vengono usati anche per abilitare l'accesso alle funzionalità del sistema operativo di basso livello. 

I moduli sono disponibili in tre tipi principali:

- **Moduli acceleratore:** poiché Python è un linguaggio interpretato, è possibile scrivere moduli acceleratore in C++ per prestazioni superiori.
- **Moduli wrapper:** questi moduli espongono le interfacce C/C++ esistenti al codice Python o espongono un'API più "pythonica" facile da usare da Python.
- **Moduli di accesso al sistema di** basso livello: è possibile creare questi moduli per accedere alle funzionalità di livello inferiore del runtime, del sistema operativo o `CPython` dell'hardware sottostante.

Questo articolo illustra come compilare un modulo di estensione C++ per calcolare una `CPython` tangente iperbolica e chiamarla dal codice Python. La routine viene implementata prima in Python per illustrare il miglioramento relativo delle prestazioni dell'implementazione della routine stessa in C++.

L'articolo illustra anche due modi per rendere disponibile l'estensione C++ per Python:

- Usare le estensioni `CPython` standard, come descritto nella documentazione [di Python.](https://docs.python.org/3/c-api/)
- Usare [PyBind11,](https://github.com/pybind/pybind11)che è consigliabile per C++11 per motivi di semplicità.

L'esempio completo di questa procedura dettagliata GitHub in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 o versione successiva, con il carico di lavoro Sviluppo Python installato. Il carico di lavoro include gli strumenti di sviluppo nativi Python, che includono il carico di lavoro C++ e i set di strumenti necessari per le estensioni native.

    ![Screenshot di un elenco di opzioni di sviluppo Python, con l'evidenziazione dell'opzione Degli strumenti di sviluppo nativi Python.](media/cpp-install-native.png)

    > [!NOTE]
    > Quando si installa il **carico di lavoro Analisi scientifica dei** dati e applicazioni analitiche, Python e l'opzione Strumenti di sviluppo nativi **Python** vengono installati per impostazione predefinita.

Per altre informazioni sulle opzioni di installazione, vedere [Installare il supporto python per Visual Studio](installing-python-support-in-visual-studio.md). Se si installa Python separatamente, assicurarsi di selezionare Scarica simboli **di debug** in **Opzioni avanzate** nel programma di installazione. Questa opzione è necessaria per usare il debug in modalità mista tra il codice Python e il codice nativo.

## <a name="create-the-python-application"></a>Creare un'applicazione Python

1. Creare un nuovo progetto Python in Visual Studio selezionando **File**  >  **nuovo**  >  **Project**. Cercare **Python,** selezionare il modello **Applicazione Python,** immettere un nome e un percorso e quindi selezionare **OK.**

1. Nel file con estensione *py del* progetto incollare il codice seguente. Per provare alcune delle funzionalità [di modifica di Python,](editing-python-code-in-visual-studio.md)provare a immettere il codice manualmente.  

   Questo codice calcola una tangente iperbolica senza usare la libreria matematica ed è ciò che si accelera con le estensioni native.

    > [!Tip]
    > Scrivere il codice in Python puro prima di riscriverlo in C++. In questo modo, è possibile verificare più facilmente che il codice nativo sia corretto.

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

1. Per visualizzare i risultati, eseguire il programma selezionando **Avvia** debug senza eseguire debug  >   o premendo CTRL+F5. 

   È possibile cambiare la variabile `COUNT` per modificare il tempo impiegato per l'esecuzione del benchmark. Ai fini di questa procedura dettagliata, impostare il conteggio in modo che il benchmark impiega circa due secondi.

   > [!TIP]
   > Quando si eseguono benchmark, usare sempre **Avvia debug**  >  **senza eseguire debug**. Ciò consente di evitare l'overhead che si verifica quando si esegue il codice all'interno del debugger Visual Studio di esecuzione.

## <a name="create-the-core-c-projects"></a>Creare i progetti C++ di base

Seguire le istruzioni in questa sezione per creare due progetti C++ identici, *superfastcode* e *superfastcode2.* Successivamente, si userà un approccio separato in ogni progetto per esporre il codice C++ a Python.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione e quindi scegliere **Aggiungi**  >  **nuovo Project**. Una Visual Studio può contenere progetti Python e C++, uno dei vantaggi dell'uso di Visual Studio per Python.

1. Cercare in **C++,** selezionare **Progetto vuoto,** specificare **superfastcode** per il primo progetto o **superfastcode2** per il secondo progetto e quindi selezionare **OK.**

    > [!Tip]
    > In alternativa, con gli strumenti di sviluppo nativi Python installati in Visual Studio, è possibile iniziare con il modello Modulo di estensione Python. Il modello include gran parte di ciò che è già stato descritto qui. 
    > 
    > Questa procedura dettagliata, tuttavia, inizia da un progetto vuoto e illustra la creazione del modulo di estensione in modo dettagliato. Dopo aver compreso il processo, è possibile usare il modello per risparmiare tempo quando si scrivono estensioni personalizzate.

1. Per creare un file C++ nel nuovo progetto, fare clic con il pulsante destro del mouse sul nodo **File di** origine e quindi scegliere **Aggiungi**  >  **nuovo elemento**.

1. Selezionare **File C++,** assegnare il nome *module.cpp* e quindi **selezionare OK.**

    > [!Important]
    > Un file con estensione *cpp* è necessario per attivare le pagine delle proprietà C++ nei passaggi che seguono.

1. Sulla barra degli strumenti principale usare il menu a discesa per eseguire una delle operazioni seguenti:

   * Per un runtime Python a 64 bit, attivare la **configurazione x64.** 
   * Per un runtime Python a 32 bit, attivare la **configurazione Win32.**

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto C++, scegliere **Proprietà** e quindi eseguire le operazioni seguenti: 

   a. Per **Configurazione** immettere **Active (Debug)**.  
   b. Per **Piattaforma** immettere **Active (x64)** o **Active (Win32)**, a seconda della selezione effettuata nel passaggio precedente.

    > [!NOTE]
    > Quando si creano progetti personalizzati, è necessario configurare sia le configurazioni *di debug* che *di* versione. In questa unità si configura solo la configurazione di debug e la si imposta per l'uso di una build di rilascio di CPython. Questa configurazione disabilita alcune funzionalità di debug del runtime C++, incluse le asserzioni. L'uso dei file binari di debug CPython (*python_d.exe*) richiede impostazioni diverse.

1. Impostare le proprietà come descritto nella tabella seguente:

    ::: moniker range=">=vs-2019"

    | Scheda | Proprietà | Valore |
    | --- | --- | --- |
    | **Generale** | **Nome destinazione** | Specificare il nome del modulo a cui fare riferimento da Python nelle `from...import` istruzioni . Lo stesso nome viene utilizzato nel codice C++ quando si definisce il modulo per Python. Per usare il nome del progetto come nome del modulo, lasciare il valore predefinito **$\<ProjectName>** .  Per `python_d.exe` , aggiungere alla fine del `_d` nome. |
    | | **Tipo configurazione** | **Libreria dinamica (.dll)** |
    | | **Avanzate** > **Estensione di file di destinazione** | **.pyd** |
    | | **Project predefinite** > **Tipo di configurazione** | **Libreria dinamica (.dll)** |
    | **C/C++** > **Generale** | **Directory di inclusione aggiuntive** | Aggiungere la cartella *python include* in base alle esigenze di installazione (ad esempio, `c:\Python36\include` ).  |
    | **C/C++** > **Preprocessore** | **Definizioni del preprocessore** | Se è presente, modificare il valore _DEBUG **in** **NDEBUG** in modo che corrisponda alla versione non di debug di CPython. Quando si usa *python_d.exe*, lasciare invariato questo valore. |
    | **C/C++** > **Generazione del codice** | **Libreria di runtime** | **DLL multi-thread (/MD) in** modo che corrisponda alla versione non di debug di CPython. Quando si usa *python_d.exe*, lasciare questo valore come DLL di **debug multi-thread (/MDd).** |
    | **Linker** > **Generale** | **Directory librerie aggiuntive** | Aggiungere la cartella Python *libs* che contiene i file con estensione *lib,* in base alle esigenze dell'installazione , ad esempio *c:\Python36\libs*. Assicurarsi di puntare alla cartella *libs* che contiene  i file *lib* e non alla *cartella Lib* che contiene i file con *estensione py.* |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Scheda | Proprietà | Valore |
    | --- | --- | --- |
    | **Generale** | **Generale** > **Nome destinazione** | Specificare il nome del modulo a cui fare riferimento da Python nelle `from...import` istruzioni . Lo stesso nome viene utilizzato nel codice C++ quando si definisce il modulo per Python. Per usare il nome del progetto come nome del modulo, lasciare il valore predefinito **$\<ProjectName>** . Per `python_d.exe` , aggiungere alla fine del `_d` nome. |
    | | **Generale** > **Estensione di destinazione** | **.pyd** |
    | | **Project impostazioni predefinite** > **Tipo di configurazione** | **Libreria dinamica (.dll)** |
    | **C/C++** > **Generale** | **Directory di inclusione aggiuntive** | Aggiungere la cartella *include* di Python, in base alle esigenze di installazione, ad esempio *c:\Python36\include*.  |
    | **C/C++** > **Preprocessore** | **Definizioni del preprocessore** | Se è presente, modificare il **valore** _DEBUG in **NDEBUG** in modo che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **C/C++** > **Generazione di codice** | **Libreria di runtime** | **DLL multi-thread (/MD) in modo** che corrisponda alla versione non di debug di `CPython` . Quando si usa `python_d.exe` , lasciare invariato questo valore. |
    | **Linker** > **Generale** | **Directory librerie aggiuntive** | Aggiungere la cartella *libs* di Python che contiene i file con estensione *lib,* in base alle esigenze di installazione, ad esempio *c:\Python36\libs.* Assicurarsi di puntare alla cartella *libs* che contiene  i file con estensione *lib* e non alla *cartella Lib* che contiene i file con *estensione py.* |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > Se la **scheda C/C++** non viene visualizzata nelle proprietà del progetto, il progetto non contiene file identificati come file di origine C/C++. Questa condizione può verificarsi se si crea un file di origine senza estensione *c* *o cpp.* 
    > 
    > Ad esempio, se in precedenza è stato immesso *module.coo* anziché *module.cpp* in precedenza nella finestra di dialogo del nuovo elemento, Visual Studio crea il file ma non imposta il tipo di file su *Codice C/C++*, che attiva la scheda delle proprietà C/C++. Questo tipo di identificazioni rimane anche se si rinomina il file con estensione *cpp.* 
    > 
    > Per impostare correttamente il tipo di file, in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file e **scegliere Proprietà**. Quindi, per **Tipo di** file selezionare **Codice C/C++.**

1. Selezionare **OK**.

1. Per testare le configurazioni *(sia di debug* che *di versione),* fare clic con il pulsante destro del mouse sul progetto C++ e quindi **scegliere Compila.** 

   I file con estensione *pyd* sono presenti nella cartella *della* soluzione, in *Debug* e *rilascio,* non nella cartella del progetto C++.

1. Nel file *module.cpp* del progetto C++ aggiungere il codice seguente:

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

1. Se non è già stato fatto, ripetere i passaggi precedenti per creare un secondo progetto denominato *superfastcode2* con una configurazione identica.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertire i progetti C++ in estensioni per Python

Per rendere la DLL C++ un'estensione per Python, è prima necessario modificare i metodi esportati per interagire con i tipi Python. Aggiungere quindi una funzione che esporti il modulo, insieme alle definizioni dei metodi del modulo.

Le sezioni seguenti illustrano come eseguire questi passaggi usando le estensioni CPython e PyBind11.

### <a name="use-cpython-extensions"></a>Usare le estensioni CPython

Per altre informazioni sul codice illustrato in questa sezione, vedere il manuale di riferimento [dell'API Python/C](https://docs.python.org/3/c-api/index.html) e, in particolare, la [pagina Oggetti](https://docs.python.org/3/c-api/module.html) modulo. Assicurarsi di selezionare la versione di Python nell'elenco a discesa in alto a destra.

1. All'inizio del file *module.cpp* includere *Python.h:*

    ```cpp
    #include <Python.h>
    ```

1. Modificare il `tanh_impl` metodo in modo da accettare e restituire i tipi Python , ovvero `PyObject*` :

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

1. Aggiungere una struttura che definisce il modulo a cui si vuole fare riferimento nel codice Python, in particolare quando si usa `from...import` l'istruzione . 

   Il nome importato in questo codice deve corrispondere al valore nelle proprietà del progetto in Proprietà **di** configurazione  >  **Nome destinazione**  >  **generale**. 

   Nell'esempio seguente il `"superfastcode"` nome del modulo indica che è possibile usare in `from superfastcode import fast_tanh` Python, perché è definito `fast_tanh` all'interno di `superfastcode_methods` . I nomi di file interni al progetto C++, ad esempio *module.cpp,* non sono sequenziali.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Aggiungere un metodo che Python chiama quando carica il modulo, che deve essere denominato , dove corrisponde esattamente alla proprietà General Target Name del progetto `PyInit_<module-name>` *\<module-name>*   >   C++. Ciò significa che corrisponde al nome del file *con estensione pyd* compilato dal progetto.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compilare di nuovo il progetto C++ per verificare il codice. Se si verificano errori, vedere la [sezione "Risoluzione dei](#troubleshoot-compiling-failures) problemi".

### <a name="use-pybind11"></a>Usare PyBind11

Se è stata completata la procedura della sezione precedente, si sarà notato l'uso di una grande quantità di codice boilerplate per creare le strutture di modulo necessarie per il codice C++. PyBind11 semplifica il processo tramite macro in un file di intestazione C++ che ottiene lo stesso risultato, ma con una quantità di codice molto inferiore. 

Per altre informazioni sul codice in questa sezione, vedere [PyBind11 basics (Nozioni di base su PyBind11).](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)

1. Installare PyBind11 usando pip: `pip install pybind11` o `py -m pip install pybind11` . 

   In alternativa, è possibile installare PyBind11 usando la finestra Ambienti Python e quindi usare il comando Apri **in PowerShell** per il passaggio successivo.

1. Nello stesso terminale eseguire `python -m pybind11 --includes` o `py -m pybind11 --includes` . 

   Verrà visualizzato un elenco di percorsi da aggiungere alla proprietà Directory di inclusione aggiuntive generali **C/C++** del  >    >   progetto. Assicurarsi di rimuovere il `-I` prefisso, se presente.

1. All'inizio di un *file module.cpp* nuovo che non include alcuna modifica della sezione precedente, includere *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Nella parte inferiore di *module.cpp* usare la `PYBIND11_MODULE` macro per definire il punto di ingresso alla funzione C++:

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

1. Compilare il progetto C++ per verificare il codice. Se si verificano errori, vedere la sezione successiva "Risolvere gli errori di compilazione" per le soluzioni.

### <a name="troubleshoot-compiling-failures"></a>Risolvere i problemi di compilazione degli errori

La compilazione del modulo C++ potrebbe non riuscire per i motivi seguenti:

- Errore: Impossibile individuare *Python.h* (**E1696: cannot open source file "Python.h"** and/or **C1083: Cannot open include file: "Python.h": No such file or directory**) 

  Soluzione: verificare che il percorso in Directory di inclusione aggiuntive generali di **C/C++** nelle proprietà del progetto punti alla cartella di inclusione  >    >   *dell'installazione di* Python. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Errore: Impossibile individuare le librerie Python 
 
   Soluzione: verificare che il percorso in Directory librerie aggiuntive generali del **linker** nelle proprietà del progetto punti alla cartella  >    >   *libs dell'installazione di* Python. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Errori del linker correlati all'architettura di destinazione
   
   Soluzione: modificare l'architettura del progetto della destinazione C++ in modo che corrisponda a quella dell'installazione di Python. Ad esempio, se la destinazione è Win32 con il progetto C++ ma l'installazione di Python è a 64 bit, modificare il progetto C++ in x64.

## <a name="test-the-code-and-compare-the-results"></a>Testare il codice e confrontare i risultati

Ora che la libreria è strutturata con le estensioni per Python, è possibile fare riferimento a tali estensioni dal progetto Python, importare il modulo e usare i metodi delle estensioni.

### <a name="make-the-dll-available-to-python"></a>Rendere disponibile la DLL per Python

È possibile rendere la DLL disponibile per Python in diversi modi. Ecco due approcci da considerare: 

* Questo primo metodo funziona se il progetto Python e il progetto C++ sono nella stessa soluzione. Eseguire le operazioni seguenti: 

   1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto Python e quindi scegliere **Aggiungi riferimento.** 
   1. Nella finestra di dialogo visualizzata selezionare la scheda **Progetti**, selezionare il progetto **superfastcode** e il progetto **superfastcode2**, quindi fare clic su **OK**.

      ![Screenshot che mostra come aggiungere un riferimento al progetto "superfastcode".](media/cpp-add-reference.png)

* Un metodo alternativo installa il modulo nell'ambiente Python, che lo rende disponibile anche per altri progetti Python. Per altre informazioni, vedere la documentazione [ **del progetto setuptools.**](https://setuptools.readthedocs.io/) Eseguire le operazioni seguenti:

    1. Creare un file denominato *setup.py* nel progetto C++ facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Aggiungi** > **Nuovo elemento**. 
    
    1. Selezionare **File C++ (.cpp),** assegnare al *file* setup.py e quindi selezionare **OK.**
    
       Denominare il file con l'estensione *py* Visual Studio riconoscerlo come file Python nonostante l'uso del modello di file C++. 

       Quando il file viene visualizzato nell'editor, incollare il codice seguente al suo interno, in base al metodo di estensione:
    
        **Per `CPython` le estensioni (progetto superfastcode):**
    
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
    
        **Per `PyBind11` (progetto superfastcode2):**
    
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
    
    1. Creare un secondo file denominato *pyproject.toml* nel progetto C++ e incollarne il codice seguente:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Per compilare l'estensione, fare clic con il pulsante destro del mouse sulla scheda *open pyproject.toml* e quindi **scegliere Copy Full Path (Copia percorso completo).** Si eliminerà il nome *pyproject.toml* dal percorso prima di usarlo.
    
    1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sull'ambiente Python attivo e quindi **scegliere Gestisci pacchetti Python.**
    
        > [!Tip]
        > Se il pacchetto è già stato installato, verrà visualizzato qui. Prima di continuare, fare clic sulla **X** per disinstallarla.
    
    1. Nella casella di ricerca incollare il percorso copiato, eliminare *pyproject.toml* dalla fine e quindi premere INVIO per installare il modulo da tale directory.
    
        > [!Tip]
        > Se l'installazione non riesce a causa di un errore di autorizzazione, aggiungere *--user* alla fine e riprovare.


### <a name="call-the-dll-from-python"></a>Chiamare la DLL da Python

Dopo aver reso disponibile la DLL per Python, come descritto nella sezione precedente, è possibile chiamare le funzioni e dal codice Python e confrontarne le prestazioni con `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` l'implementazione di Python. Per chiamare la DLL, eseguire le operazioni seguenti:

1. Aggiungere le righe seguenti nel file con estensione *py* per chiamare i metodi esportati dalle DLL e visualizzarne gli output:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Eseguire il programma Python selezionando **Avvia debug**  >  **senza eseguire** debug o premendo CTRL+F5.

    > [!NOTE]
    > Se il **comando Avvia** senza eseguire debug è disabilitato, **in** Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Python e quindi scegliere Imposta come avvio **Project**.  

    Si noti che le routine C++ vengono eseguite circa da cinque a venti volte più veloci rispetto all'implementazione di Python. In genere l'output ha l'aspetto seguente:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Provare a incrementare la variabile `COUNT` in modo che le differenze siano più evidenti. 

    Anche *una* build di debug del modulo C++ viene eseguita più lentamente rispetto *a* una build di versione, perché la build di debug è meno ottimizzata e contiene vari controlli degli errori. È possibile passare da una configurazione all'altro per il confronto, ma ricordarsi di tornare indietro e aggiornare le proprietà impostate in precedenza per la configurazione della versione.

Nell'output si potrebbe vedere che l'estensione PyBind11 non è veloce come l'estensione CPython, anche se dovrebbe essere notevolmente più veloce dell'implementazione python pura. Questa differenza si verifica in gran parte perché è stata usata la chiamata , che non supporta più parametri, nomi di parametro `METH_O` o argomenti di parole chiave. PyBind11 genera codice leggermente più complesso per fornire un'interfaccia più simile a Python ai chiamanti. Tuttavia, poiché il codice di test chiama la funzione 500.000 volte, i risultati potrebbero aumentare notevolmente il sovraccarico.

È possibile ridurre ulteriormente il sovraccarico spostando `for` il ciclo nel codice nativo. Questo approccio comporta l'uso del protocollo [iterator](https://docs.python.org/c-api/iter.html) (o del tipo PyBind11 per il parametro della funzione ) per `py::iterable` elaborare [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)ogni elemento. La rimozione delle transizioni ripetute tra Python e C++ è un modo efficace per ridurre il tempo necessario per elaborare la sequenza.

### <a name="troubleshoot-importing-errors"></a>Risolvere i problemi relativi agli errori di importazione

Se si riceve un `ImportError` messaggio quando si tenta di importare il modulo, è possibile risolverlo in uno dei modi seguenti:

* Quando si compila tramite un riferimento al progetto, assicurarsi che le proprietà del progetto C++ corrispondano all'ambiente Python attivato per il progetto Python, in particolare le directory *Include* *e Library.*

* Assicurarsi che il file di output sia *denominato superfastcode.pyd*. Qualsiasi altro nome o estensione ne impedirà l'importazione.

* Se il modulo è stato installato usando il file *setup.py,* verificare di aver eseguito il comando *pip* nell'ambiente Python attivato per il progetto Python. Espandendo l'ambiente Python in Esplora soluzioni dovrebbe essere visualizzata una voce *per superfastcode*.

## <a name="debug-the-c-code"></a>Eseguire il debug del codice C++

Visual Studio supporta il debug di codice Python e C++ insieme. In questa sezione viene illustrata la procedura usando il *progetto superfastcode.* Il processo è lo stesso per il *progetto superfastcode2.*

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto Python, scegliere **Proprietà,** selezionare la scheda **Debug** e quindi selezionare l'opzione **Debug** Abilita  >  **debug codice** nativo.

    > [!Tip]
    > Quando si abilita il debug del codice nativo, la finestra di output di Python potrebbe chiudersi immediatamente dopo il termine del programma senza fornire il consueto premere qualsiasi tasto **per continuare a sospendere.** 
    >
    > Soluzione: per forzare una sospensione dopo aver abilitato il debug del codice nativo, aggiungere l'opzione al campo Esegui `-i`   >  **argomenti dell'interprete** nella **scheda** Debug. Questo argomento imposta l'interprete Python in modalità interattiva dopo l'esecuzione del codice, a questo punto attende che si seleziona CTRL+Z e quindi INVIO per chiudere la finestra. 
    >
    > In alternativa, se non si vuole modificare il codice Python, è possibile aggiungere istruzioni `import os` e alla fine del `os.system("pause")` programma. Questo codice duplica il prompt di sospensione originale.

1. Selezionare **Salva**  >  **file per** salvare le modifiche alle proprietà.

1. Sulla barra Visual Studio, impostare la configurazione di compilazione su **Debug**.

    ![Screenshot dell'impostazione "Debug" sulla barra Visual Studio strumenti.](media/cpp-set-debug.png)

1. Poiché l'esecuzione del codice in genere richiede più tempo nel debugger, potrebbe essere necessario modificare la variabile nel file py in un valore di circa cinque volte inferiore al `COUNT` valore predefinito.  Ad esempio, modificarlo da **500000 a** **100000**.

1. Nel codice C++ impostare un punto di interruzione nella prima riga del metodo e quindi avviare il debugger selezionando `tanh_impl` **F5** o **Avvia**  >  **debug.** 

    Il debugger si arresta quando viene chiamato il codice del punto di interruzione. Se il punto di interruzione non viene raggiunto, verificare che la configurazione sia impostata su **Debug** e che il progetto sia stato salvato, che non si verifica automaticamente all'avvio del debugger.

    ![Screenshot del codice C++ che contiene un punto di interruzione.](media/cpp-debugging.png)

1. In corrispondenza del punto di interruzione è possibile eseguire il codice C++, esaminare le variabili e così via. Per altre informazioni su queste funzionalità, vedere [Eseguire il debug di Python e C++ insieme.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

## <a name="alternative-approaches"></a>Approcci alternativi

È possibile creare estensioni Python in diversi modi, come descritto nella tabella seguente. Le prime due righe, `CPython` e , sono illustrate in questo `PyBind11` articolo.

| Approccio | Vintage | Utenti rappresentativi | 
| --- | --- | --- |
| Moduli di estensione C/C++ per `CPython` | 1991 | Libreria standard | 
| [PyBind11](https://github.com/pybind/pybind11) (scelta consigliata per C++) | 2015 |  |
| [Cython](https://cython.org) (consigliato per C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/), [pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Vedi anche

L'esempio completo di questa procedura dettagliata GitHub in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).
