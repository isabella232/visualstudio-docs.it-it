---
title: Usare il framework di testing unità Microsoft per C++
description: Utilizzare Microsoft Unit Testing Framework per C , per creare unit test per il codice C .
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755561"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usare il framework di testing unità Microsoft per C++ in Visual Studio

Per impostazione predefinita il framework di testing unità Microsoft per C++ è incluso nel carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Per scrivere unit test in un progetto separato

In genere, il codice di test viene eseguito nel relativo progetto nella stessa soluzione del codice da testare. Per impostare e configurare un nuovo progetto di test, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Per scrivere unit test nello stesso progetto

In alcuni casi, ad esempio durante il test di funzioni non esportate in una DLL, può essere necessario creare i test nello stesso progetto del programma che si sta testando. Per scrivere unit test nello stesso progetto:

1. Modificare le proprietà del progetto per includere le intestazioni e i file di libreria necessari per il testing unità.

   1. In Esplora soluzioni scegliere **Proprietà**dal menu di scelta rapida del progetto che si sta testando. Verrà visualizzata la finestra delle proprietà del progetto.

   1. Nella finestra di dialogo Pagine delle proprietà, selezionare **Proprietà** > di configurazione**VC, Directories**.

   1. Fare clic sulla freccia giù nelle ** \< **righe seguenti e scegliere Modifica>. Aggiungere questi percorsi:

      | Directory | Proprietà |
      |-| - |
      | **Directory di inclusione** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Directory delle librerie** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Aggiungere un file di unit test C++:

   - Fare clic con il pulsante destro del mouse sul nodo di progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo elemento** > **File di C++ (.cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Per collegare i test all'oggetto o a file di libreria

Se il codice sottoposto a test non esporta le funzioni che si desidera testare, è possibile aggiungere il file **obj** o **lib** di output alle dipendenze del progetto di test. Modificare le proprietà del progetto di test per includere le intestazioni e i file di libreria o oggetto necessari per gli unit test.

1. In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del progetto di test. Verrà visualizzata la finestra delle proprietà del progetto.

1. Selezionare la pagina**di input** **del linker** > delle proprietà > di **configurazione,** quindi selezionare **Dipendenze aggiuntive**.

   Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non utilizzare i nomi di percorso completi.

1. Selezionare la pagina Informazioni di **configurazione** > **del linker** > **Generale** , quindi selezionare Directory **aggiuntive libreria**.

   Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

1. Selezionare la pagina **Proprietà** > di configurazione**directory VC e Directory** , quindi selezionare Includi **directory**.

   Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

## <a name="write-the-tests"></a>Scrivere i test

Tutti i file *CPP* con classi di test devono includere "CppUnitTest.h" e avere un'istruzione using per `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Il progetto di test è già configurato. Include anche una definizione dello spazio dei nomi e una TEST_CLASS con un TEST_METHOD per iniziare. È possibile modificare il nome dello spazio dei nomi e i nomi tra parentesi nelle macro di classi e metodi.

Il framework di test definisce macro speciali per l'inizializzazione di moduli di test, classi e metodi e per la pulizia delle risorse dopo il completamento dei test. Queste macro generano codice da eseguire prima che si acceda per la prima volta a una classe o a un metodo e dopo l'esecuzione dell'ultimo test. Per altre informazioni, vedere [Initialize and cleanup](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup) (Inizializzare ed eseguire la pulizia).

Usare i metodi statici nella classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) per definire le condizioni di test. Usare la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) per scrivere messaggi nella **finestra di output**. Aggiungere attributi ai metodi di test

## <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**.

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul relativo nodo in **Esplora soluzioni** e scegliendo **Compila** o **Ricompila**.

1. In **Esplora test**scegliere Esegui **tutto**oppure selezionare i test specifici che si desidera eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati.

1. Nella **finestra di output** scegliere **Test** nell'elenco a `Logger` discesa per visualizzare i messaggi scritti dalla classe:

   ![Finestra di output di C++ con messaggi di test](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definire i tratti per abilitare il raggruppamento

È possibile definire tratti nei metodi di test, che consentono di classificare e raggruppare i test in **Esplora test**. Per definire un tratto, usare la macro `TEST_METHOD_ATTRIBUTE`. Ad esempio, per definire un tratto denominato `TEST_MY_TRAIT`:

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
