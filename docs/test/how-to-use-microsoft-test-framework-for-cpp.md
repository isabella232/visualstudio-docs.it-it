---
title: Usare il framework di testing unità Microsoft per C++
description: Usare il Framework di testing unità Microsoft per C++ per creare unit test per il codice C++.
ms.date: 01/08/2020
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a9393fd248f4e6520c261d405bc624a75d8cf69f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287116"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usare il framework di testing unità Microsoft per C++ in Visual Studio

Per impostazione predefinita il framework di testing unità Microsoft per C++ è incluso nel carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Per scrivere unit test in un progetto separato

In genere, il codice di test viene eseguito nel relativo progetto nella stessa soluzione del codice da testare. Per impostare e configurare un nuovo progetto di test, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Per scrivere unit test nello stesso progetto

In alcuni casi, ad esempio durante il test di funzioni non esportate in una DLL, può essere necessario creare i test nello stesso progetto del programma che si sta testando. Per scrivere unit test nello stesso progetto:

1. Modificare le proprietà del progetto per includere le intestazioni e i file di libreria necessari per il testing unità.

   1. In Esplora soluzioni scegliere **Proprietà**dal menu di scelta rapida del progetto che si sta testando. Verrà visualizzata la finestra delle proprietà del progetto.

   1. Nella finestra di dialogo Pagine delle proprietà selezionare **proprietà di configurazione**  >  **directory di VC + +**.

   1. Fare clic sulla freccia verso il basso nelle righe seguenti e scegliere **\<Edit>** . Aggiungere questi percorsi:

      | Directory | Proprietà |
      |-| - |
      | **Directory di inclusione** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Directory delle librerie** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Aggiungere un file di unit test C++:

   - Fare clic con il pulsante destro del mouse sul nodo di progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo elemento** > **File di C++ (.cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Per collegare i test all'oggetto o a file di libreria

Se il codice sottoposto a test non Esporta le funzioni che si desidera testare, è possibile aggiungere il file con **estensione obj** o **lib** di output alle dipendenze del progetto di test. Modificare le proprietà del progetto di test per includere le intestazioni e i file di libreria o oggetto necessari per il testing unità.

1. In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del progetto di test. Verrà visualizzata la finestra delle proprietà del progetto.

1. Selezionare la **Configuration Properties**  >  pagina di input del**linker**proprietà  >  **Input** di configurazione, quindi selezionare **dipendenze aggiuntive**.

   Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non usare i nomi di percorso completi.

1. Selezionare la **Configuration Properties**  >  pagina generale del**linker**proprietà  >  **General** di configurazione, quindi selezionare **Directory librerie aggiuntive**.

   Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

1. Selezionare la pagina **proprietà di configurazione**  >  **directory di VC + +** , quindi selezionare **Includi directory**.

   Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

## <a name="write-the-tests"></a>Scrivere i test

Tutti i file *CPP* con classi di test devono includere "CppUnitTest.h" e avere un'istruzione using per `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Il progetto di test è già configurato. Include anche una definizione dello spazio dei nomi e una TEST_CLASS con un TEST_METHOD per iniziare. È possibile modificare il nome dello spazio dei nomi e i nomi tra parentesi nelle macro di classi e metodi.

Il Framework di test definisce macro speciali per l'inizializzazione di moduli, classi e metodi di test e per la pulizia delle risorse dopo il completamento dei test. Queste macro generano il codice da eseguire prima che venga eseguito il primo accesso a una classe o a un metodo e dopo l'esecuzione dell'ultimo test. Per altre informazioni, vedere [Initialize and cleanup](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup) (Inizializzare ed eseguire la pulizia).

Usare i metodi statici nella classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) per definire le condizioni di test. Usare la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) per scrivere messaggi nella **finestra di output**. Aggiungere attributi ai metodi di test

## <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**.

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul nodo in **Esplora soluzioni** e scegliendo **Compila** o **ricompila**.

1. In **Esplora test**scegliere **Esegui tutto**oppure selezionare i test specifici che si desidera eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati.

1. Nella **finestra di output** scegliere **test** nell'elenco a discesa per visualizzare i messaggi scritti dalla `Logger` classe:

   ![Finestra di output di C++ con messaggi di test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definire i tratti per abilitare il raggruppamento

È possibile definire i tratti nei metodi di test, che consentono di categorizzare e raggruppare i test in **Esplora test**. Per definire un tratto, usare la macro `TEST_METHOD_ATTRIBUTE`. Ad esempio, per definire un tratto denominato `TEST_MY_TRAIT`:

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

I tratti predefiniti seguenti sono disponibili in `CppUnitTest.h`. Per altre informazioni, vedere le [informazioni di riferimento sulle API del framework di testing unità Microsoft per C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Descrizione|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Usare la macro TEST_METHOD_ATTRIBUTE per definire un tratto.|
|`TEST_OWNER(ownerAlias)`|Usare il tratto Owner predefinito per specificare un proprietario del metodo di test.|
|`TEST_PRIORITY(priority)`|Usare il tratto Priority predefinito per assegnare priorità relative ai metodi di test.|

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)
