---
title: Come usare Boost.Test per C++
description: Usare Boost.Test per creare unit test in Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922916"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Come usare Boost.Test per C++ in Visual Studio

In Visual Studio 2017 and later, the Boost.Test test adapter is integrated into the Visual Studio IDE. Si tratta di un componente dello **sviluppo di desktop con** carico di lavoro C .

![Adattatore di test per Boost.Test](media/cpp-boost-component.png)

Se il carico di lavoro **Sviluppo di applicazioni desktop con C++** non è installato, aprire il **programma di installazione di Visual Studio**. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere il pulsante **Modifica**.

## <a name="install-boost"></a>Installare Boost

Per usare Boost.Test è necessario installare [Boost](https://www.boost.org/). Se Boost non è installato, si consiglia di utilizzare il gestore di pacchetti Vcpkg.

1. Seguire le istruzioni disponibili su [Vcpkg: un gestore di pacchetti di C, per Windows,](/cpp/vcpkg) per installare vcpkg (se non è già presente).

1. Installare la libreria statica o dinamica Boost.Test:

    - Eseguire `vcpkg install boost-test` per installare la libreria dinamica Boost.Test.

       -OPPURE-

    - Eseguire `vcpkg install boost-test:x86-windows-static` per installare la libreria statica Boost.Test.

1. Eseguire `vcpkg integrate install` per configurare Visual Studio con la libreria e includere i percorsi delle intestazioni e dei file binari di Boost.

È possibile scegliere come configurare i test all'interno della soluzione in Visual Studio: è possibile includere il codice di test nel progetto sottoposto a test oppure creare un progetto di test separato per i test. Entrambe le scelte hanno vantaggi e svantaggi.

## <a name="add-tests-inside-your-project"></a>Aggiungere test all'interno del progetto

In Visual Studio 2017 versione 15.6 e successive, è possibile aggiungere un modello di elemento per i test nel progetto. Sia i test che il codice risiedono nello stesso progetto. È necessario creare una configurazione di compilazione separata per generare una compilazione di test. Inoltre, è necessario mantenere i test fuori dalle build di debug e rilascio.

In Visual Studio 2017 versione 15.5 non sono disponibili progetti di test preconfigurati o modelli di elementi per Boost.Test. Utilizzare le istruzioni per creare e configurare un progetto di test separato.

### <a name="create-a-boosttest-item"></a>Creare un elemento Boost.TestCreate a Boost.Test item

1. Per creare un file *con estensione cpp* per i test, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** , espandere**Test** **di** > **Visual C,** >  Selezionare **Boost.Test**, quindi scegliere **Aggiungi** per aggiungere *Test.cpp* al progetto.

   ![Modello di elemento Boost.Test](media/boost_test_item_template.png)

Il nuovo file *Test.cpp* contiene un metodo di test di esempio. Questo file è dove è possibile includere i propri file di intestazione e scrivere test per l'app.

Il file di test utilizza anche `main` macro per definire una nuova routine per le configurazioni di test. Se si compila il progetto ora, verrà visualizzato un errore LNK2005, ad esempio "_main già definito in main.obj".

### <a name="create-and-update-build-configurations"></a>Creare e aggiornare le configurazioni della buildCreate and update build configurations

1. Per creare una configurazione di test, nella barra dei menu selezionare Gestione**configurazione** **compilazione** > . Nella finestra di dialogo **Gestione configurazione** aprire l'elenco a discesa in Configurazione **soluzione attiva** e scegliere **Nuovo**. Nella finestra di dialogo **Nuova configurazione soluzione** immettere un nome, ad esempio "Debug UnitTests". In **Copia impostazioni da** selezionare **Debug**, quindi scegliere **OK**.

1. Escludere il codice di test dalle configurazioni Debug e Release: in **Esplora soluzioni**fare clic con il pulsante destro del mouse su Test.cpp e scegliere **Proprietà**. Nella finestra di dialogo Pagine delle proprietà selezionare **Tutte le configurazioni** nell'elenco a discesa Configurazione.In the **Property Pages** dialog, select All Configurations in the **Configuration** dropdown. Selezionare **Proprietà** > di configurazione**generali** e aprire l'elenco a discesa per la proprietà **Escluso dalla compilazione.** Seleziona **Sì**, quindi scegli **Applica** per salvare le modifiche.

1. Per includere il codice di test nella configurazione Debug UnitTests, nella finestra di dialogo **Pagine delle proprietà** selezionare Debug Unittests nell'elenco a discesa Configurazione.To include the test code in your Debug UnitTests configuration, in the Property Pages dialog, select **Debug UnitTests** in the **Configuration** dropdown. Selezionare **No** nella proprietà **Escluso dalla compilazione,** quindi scegliere **OK** per salvare le modifiche.

1. Escludere il codice principale dalla configurazione Debug UnitTests. In **Esplora soluzioni**fare clic con `main` il pulsante destro del mouse sul file contenente la funzione e scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** selezionare Debug Unittests nell'elenco a discesa Configurazione.In the Property Pages dialog, select **Debug UnitTests** in the **Configuration** dropdown. Selezionare **Proprietà** > di configurazione**generali** e aprire l'elenco a discesa per la proprietà **Escluso dalla compilazione.** Selezionare **Sì**, quindi scegliere **OK** per salvare le modifiche.

1. Impostare Configurazione soluzione su **Debug Unittests**, quindi compilare il progetto per abilitare **Esplora test** per individuare il metodo.

Finché il nome di configurazione creato inizia con le parole "Debug" o "Release", le librerie Boost.Test corrispondenti vengono prelevate automaticamente.

Il modello di elemento usa la variante con singola intestazione di Boost.Test, ma è possibile modificare il percorso #include per usare la variante con libreria autonoma. Per altre informazioni vedere [Aggiungere direttive include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Creare un progetto di test separatoCreate a separate test project

In molti casi, è più semplice utilizzare un progetto separato per i test. Non è necessario creare una configurazione di test speciale per il progetto. In alternativa, escludere i file di test dalle build di debug e rilascio.

### <a name="to-create-a-separate-test-project"></a>Per creare un progetto di test separatoTo create a separate test project

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **Nuovo progetto**.

1. Nella finestra di dialogo **Aggiungi un nuovo progetto,** scegliere **C,** **Windows**e **Console** negli elenchi a discesa dei filtri. Selezionare il modello **App console** , quindi scegliere **Avanti**.

1. Specificare un nome per il progetto e scegliere **Crea**.

1. Eliminare la funzione `main` nel file *CPP*.

1. Se si utilizza la versione a intestazione singola o libreria dinamica di Boost.Test, passare a [Aggiungere direttive di inclusione](#add-include-directives). Se si usa la versione della libreria statica, è necessario eseguire alcune operazioni di configurazione aggiuntive:If you're using the static library version, then you have to do some additional configuration:

   a. Per modificare il file di progetto, per prima cosa scaricarlo. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica progetto**. Quindi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Modifica <nome\>.vcxproj**.

   b. Aggiungere due righe al gruppo di proprietà **Variabili globali** come illustrato di seguito:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Salvare e chiudere il * \*file con estensione vcxproj,* quindi ricaricare il progetto.

   d. Per aprire le **pagine delle proprietà**, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

   e. Espandere la**generazione**di > codice **C/C,** quindi selezionare Libreria di **runtime**. Selezionare **/MTd** per la libreria di runtime statica di debug o **/MT** per la libreria di runtime statica di versione.

   f. Espandere **Linker** > **System**. Verificare che **SubSystem** sia impostato su **Console**.

   g. Scegliere **OK** per chiudere le pagine delle proprietà.

## <a name="add-include-directives"></a>Aggiungere direttive include

1. Nel file *con estensione cpp* `#include` di test aggiungere le direttive necessarie per rendere i tipi e le funzioni del programma visibili al codice di test. Se si utilizza un progetto di test separato, in genere, il programma si trova a un livello di pari livello nella gerarchia di cartelle. Se si digita `#include "../"`, viene visualizzata una finestra di IntelliSense che consente di selezionare il percorso completo del file di intestazione.

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

È ora possibile scrivere ed eseguire i Boost Test. Per informazioni sulle macro di test, vedere la [documentazione](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) relativa alla libreria di test Boost. Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedere anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
