---
title: Usare il framework di testing unità Microsoft per C++
description: Usare il framework di testing unità Microsoft per C++ per creare unit test per il codice C++.
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: f1df2935fba013a9eaafab17d9fc66fa650e2ca7242e79fbd75c598220aac358
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395173"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usare il framework di testing unità Microsoft per C++ in Visual Studio

Per impostazione predefinita il framework di testing unità Microsoft per C++ è incluso nel carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Per scrivere unit test in un progetto separato

In genere, il codice di test viene eseguito nel relativo progetto nella stessa soluzione del codice da testare. Per impostare e configurare un nuovo progetto di test, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Per scrivere unit test nello stesso progetto

In alcuni casi, ad esempio durante il test di funzioni non esportate in una DLL, può essere necessario creare i test nello stesso progetto del programma che si sta testando. Per scrivere unit test nello stesso progetto:

1. Modificare le proprietà del progetto per includere le intestazioni e i file di libreria necessari per il testing unità.

   1. In Esplora soluzioni scegliere Proprietà dal menu di scelta rapida del progetto che si **sta testando.** Verrà visualizzata la finestra delle proprietà del progetto.

   1. Nella finestra di dialogo Pagine delle proprietà selezionare **Proprietà di**  >  **VC++ directory**.

   1. Selezionare la freccia giù nelle righe seguenti e scegliere **\<Edit>** . Aggiungere questi percorsi:

      | Directory | Proprietà |
      |-| - |
      | **Directory di inclusione** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Directory delle librerie** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Aggiungere un file di unit test C++:

   1. Fare clic con il pulsante destro del mouse sul nodo **del Esplora soluzioni** e **scegliere Aggiungi**  >  **nuovo elemento.**

   1. Nella finestra **di dialogo Aggiungi nuovo** elemento selezionare File **C++ (.cpp),** assegnargli un nome appropriato e quindi scegliere **Aggiungi.**

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Per collegare i test all'oggetto o a file di libreria

Se il codice sotto test non esporta le funzioni da testare, è possibile aggiungere il file *obj* o *lib* di output alle dipendenze del progetto di test. Modificare le proprietà del progetto di test per includere le intestazioni e i file di libreria o oggetto necessari per gli unit test.

1. In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del progetto di test. Verrà visualizzata la finestra delle proprietà del progetto.

1. Selezionare la **pagina Configuration Properties** Linker Input (Input linker proprietà di  >    >   configurazione), quindi selezionare **Additional Dependencies (Dipendenze aggiuntive).**

   Scegliere **Modifica** e aggiungere i nomi dei file con estensione *obj* o *lib*. Non usare i nomi di percorso completi.

1. Selezionare la **pagina Generale del**  >  **linker Proprietà**  >  **di** configurazione , quindi selezionare **Directory librerie aggiuntive**.

   Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione *obj* o *lib*. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

1. Selezionare la **pagina Proprietà VC++**  >  **directory** e quindi selezionare Directory **di inclusione**.

   Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

## <a name="write-the-tests"></a>Scrivere i test

Tutti i file *CPP* con classi di test devono includere "CppUnitTest.h" e avere un'istruzione using per `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Il progetto di test è già configurato. Include anche una definizione dello spazio dei nomi e una TEST_CLASS con un TEST_METHOD per iniziare. È possibile modificare il nome dello spazio dei nomi e i nomi tra parentesi nelle macro della classe e del metodo.

Il framework di test definisce macro speciali per l'inizializzazione di moduli, classi e metodi di test e per la pulizia delle risorse al termine dei test. Queste macro generano codice da eseguire prima dell'accesso a una classe o a un metodo e dopo l'esecuzione dell'ultimo test. Per altre informazioni, vedere [Initialize and cleanup](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup) (Inizializzare ed eseguire la pulizia).

Usare i metodi statici nella classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) per definire le condizioni di test. Usare la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) per scrivere messaggi nella **finestra di output**. Aggiungere attributi ai metodi di test

## <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**.

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di  test facendo clic con il pulsante destro del mouse sul relativo nodo Esplora soluzioni e scegliendo **Compila** o **Ricompila**.

1. In **Esplora test** scegliere Esegui **tutto** oppure selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati.

1. **Nell'Finestra di output** **test** nell'elenco a discesa per visualizzare i messaggi scritti dalla `Logger` classe :

   ![Finestra di output di C++ con messaggi di test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definire i tratti per abilitare il raggruppamento

È possibile definire tratti nei metodi di test, che consentono di classificare e raggruppare i test in **Esplora test.** Per definire un tratto, usare la macro `TEST_METHOD_ATTRIBUTE`. Ad esempio, per definire un tratto denominato `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Per usare il tratto definito negli unit test:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Macro di attributo di tratto C++

I tratti predefiniti seguenti sono disponibili in *`CppUnitTest.h`* . Per altre informazioni, vedere le [informazioni di riferimento sulle API del framework di testing unità Microsoft per C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Descrizione|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Usare la macro TEST_METHOD_ATTRIBUTE per definire un tratto.|
|`TEST_OWNER(ownerAlias)`|Usare il tratto Owner predefinito per specificare un proprietario del metodo di test.|
|`TEST_PRIORITY(priority)`|Usare il tratto Priority predefinito per assegnare priorità relative ai metodi di test.|

## <a name="see-also"></a>Vedi anche

- [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)
