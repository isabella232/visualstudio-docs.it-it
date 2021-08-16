---
title: Come usare Boost.Test per C++
description: Usare Boost.Test per creare unit test in Visual Studio.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 11cf28dcbb62144c59ee44b3cbc548fcf3fcbdc203261efa6073865afb5a53ef
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366595"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Come usare Boost.Test per C++ in Visual Studio

In Visual Studio 2017 e versioni successive, l'adattatore di test Boost.Test è integrato nell'IDE Visual Studio. Si tratta di un componente del carico di **lavoro Sviluppo di applicazioni desktop con C++.**

![Adattatore di test per Boost.Test](media/cpp-boost-component.png)

Se il carico di lavoro **Sviluppo di applicazioni desktop con C++** non è installato, aprire il **programma di installazione di Visual Studio**. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere il pulsante **Modifica**.

## <a name="install-boost"></a>Installare Boost

Per usare Boost.Test è necessario installare [Boost](https://www.boost.org/). Se Boost non è installato, è consigliabile usare Gestione pacchetti Vcpkg.

1. Seguire le istruzioni in [Vcpkg: gestione pacchetti C++](/cpp/vcpkg) per Windows per installare vcpkg (se non è già presente).

1. Installare la libreria statica o dinamica Boost.Test:

    - Eseguire `vcpkg install boost-test` per installare la libreria dinamica Boost.Test.

       -OPPURE-

    - Eseguire `vcpkg install boost-test:x86-windows-static` per installare la libreria statica Boost.Test.

1. Eseguire `vcpkg integrate install` per configurare Visual Studio con la libreria e includere i percorsi delle intestazioni e dei file binari di Boost.

È possibile scegliere come configurare i test all'interno della soluzione in Visual Studio: è possibile includere il codice di test nel progetto sotto test oppure creare un progetto di test separato per i test. Entrambe le scelte presentano vantaggi e svantaggi.

## <a name="add-tests-inside-your-project"></a>Aggiungere test all'interno del progetto

In Visual Studio 2017 versione 15.6 e successive, è possibile aggiungere un modello di elemento per i test nel progetto. Sia i test che il codice sono presenti nello stesso progetto. Sarà necessario creare una configurazione di compilazione separata per generare una compilazione di test. È inoltre necessario mantenere i test fuori delle build di debug e di rilascio.

In Visual Studio 2017 versione 15.5 non sono disponibili progetti di test preconfigurati o modelli di elementi per Boost.Test. Usare le istruzioni per creare e configurare un progetto di test separato.

### <a name="create-a-boosttest-item"></a>Creare un elemento Boost.Test

1. Per creare un file *con estensione cpp* per i test, fare clic con il pulsante destro del mouse sul **nodo** del progetto in Esplora soluzioni e scegliere **Aggiungi**  >  **nuovo elemento**.

1. Nella finestra **di dialogo Aggiungi nuovo elemento** espandere Installato   >  **Visual C++**  >  **Test**. Selezionare **Boost.Test** e quindi **scegliere Aggiungi** per aggiungere *Test.cpp* al progetto.

   ![Modello di elemento Boost.Test](media/boost_test_item_template.png)

Il nuovo file *Test.cpp* contiene un metodo di test di esempio. In questo file è possibile includere file di intestazione personalizzati e scrivere test per l'app.

Il file di test usa anche macro per definire una nuova `main` routine per le configurazioni di test. Se si compila ora il progetto, verrà visualizzato un errore LNK2005, ad esempio "_main già definito in main.obj".

### <a name="create-and-update-build-configurations"></a>Creare e aggiornare le configurazioni di compilazione

1. Per creare una configurazione di test, nella barra dei menu **selezionare**  >  **Compila** Gestione configurazione . Nella finestra **Gestione configurazione** dialogo apri l'elenco a discesa in **Configurazione soluzione attiva** e scegli **Nuovo.** Nella finestra **di dialogo Nuova configurazione** soluzione immettere un nome, ad esempio "Debug UnitTests". In **Copia impostazioni da** selezionare **Debug** e quindi scegliere **OK.**

1. Escludere il codice di test dalle configurazioni di debug **e versione:** in Esplora soluzioni fare clic con il pulsante destro del mouse su Test.cpp e scegliere **Proprietà**. Nella finestra **di dialogo Pagine delle** proprietà selezionare Tutte le **configurazioni** nell'elenco **a discesa** Configurazione. Selezionare **Proprietà di configurazione**  >  **Generale** e aprire l'elenco a discesa per la proprietà **Escluso dalla** compilazione. Selezionare **Sì,** quindi scegliere **Applica** per salvare le modifiche.

1. Per includere il codice di test nella configurazione  di Debug UnitTests, nella finestra di dialogo Pagine delle proprietà selezionare **Debug UnitTests** nell'elenco **a discesa** Configurazione. Selezionare **No** nella **proprietà Escluso dalla** compilazione e quindi scegliere **OK** per salvare le modifiche.

1. Escludere il codice principale dalla configurazione di Debug UnitTests. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file che contiene la `main` funzione e scegliere **Proprietà**. Nella finestra **di dialogo Pagine** delle proprietà selezionare Debug **UnitTests nell'elenco** a **discesa** Configurazione. Selezionare **Proprietà di configurazione**  >  **Generale** e aprire l'elenco a discesa per la proprietà **Escluso dalla** compilazione. Selezionare **Sì,** quindi scegliere **OK** per salvare le modifiche.

1. Impostare Configurazione soluzione su **Debug UnitTests**, quindi compilare il progetto per consentire a **Esplora test** di individuare il metodo.

Se il nome di configurazione creato inizia con le parole "Debug" o "Release", le librerie Boost.Test corrispondenti vengono prelevate automaticamente.

Il modello di elemento usa la variante con singola intestazione di Boost.Test, ma è possibile modificare il percorso #include per usare la variante con libreria autonoma. Per altre informazioni vedere [Aggiungere direttive include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Creare un progetto di test separato

In molti casi, è più semplice usare un progetto separato per i test. Non sarà necessario creare una configurazione di test speciale per il progetto. In caso contrario, escludere i file di test dalle build di debug e versione.

### <a name="to-create-a-separate-test-project"></a>Per creare un progetto di test separato

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **Nuovo progetto**.

1. Nella finestra **di dialogo Aggiungi un nuovo** progetto scegliere **C++** **, Windows** e **Console** negli elenchi a discesa dei filtri. Selezionare il **modello App console** e quindi scegliere **Avanti.**

1. Specificare un nome per il progetto e scegliere **Crea**.

1. Eliminare la funzione `main` nel file *CPP*.

1. Se si usa la versione a intestazione singola o a libreria dinamica di Boost.Test, passare ad [Aggiungi direttive include](#add-include-directives). Se si usa la versione della libreria statica, è necessario eseguire alcune operazioni di configurazione aggiuntive:

   a. Per modificare il file di progetto, per prima cosa scaricarlo. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica progetto**. Quindi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Modifica <nome\>.vcxproj**.

   b. Aggiungere due righe al gruppo di proprietà **Variabili globali** come illustrato di seguito:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Salvare e chiudere il file *\* con estensione vcxproj* e quindi ricaricare il progetto.

   d. Per aprire le **pagine delle proprietà**, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

   e. Espandere **Generazione di codice C/C++** e quindi selezionare Libreria di  >   **runtime**. Selezionare **/MTd** per la libreria di runtime statica di debug o **/MT** per la libreria di runtime statica di versione.

   f. Espandere **Sistema del linker**  >  . Verificare **che SubSystem** sia impostato su **Console**.

   g. Scegliere **OK** per chiudere le pagine delle proprietà.

## <a name="add-include-directives"></a>Aggiungere direttive include

1. Nel file *con estensione cpp di* test aggiungere le direttive necessarie per rendere visibili al codice di test i tipi e le funzioni del `#include` programma. Se si usa un progetto di test separato, in genere il programma si trova a un livello di pari livello nella gerarchia di cartelle. Se si digita `#include "../"`, viene visualizzata una finestra di IntelliSense che consente di selezionare il percorso completo del file di intestazione.

   ![Aggiungere direttive #include](media/cpp-gtest-includes.png)

   È possibile usare la libreria autonoma con:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   In alternativa, usare la versione a una sola intestazione con:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Quindi, definire `BOOST_TEST_MODULE`.

L'esempio seguente è sufficiente per rendere individuabile il test in **Esplora test**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Scrivere ed eseguire i test

È ora possibile scrivere ed eseguire i Boost Test. Per informazioni [sulle macro di test,](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) vedere la documentazione della libreria di test boost. Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedi anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
