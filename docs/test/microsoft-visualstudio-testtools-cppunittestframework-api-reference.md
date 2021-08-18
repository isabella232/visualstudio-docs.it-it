---
title: API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework
description: Questo articolo descrive i membri CppUnitTestFramework, che è possibile usare per scrivere unit test C++ basati su Microsoft Native Unit Test Framework.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8530bcdcdd47a57d97260a1b48f05df1e8661b80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092241"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Informazioni di riferimento sulle API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework

In questo argomento sono elencati i membri pubblici dello spazio dei nomi `Microsoft::VisualStudio::CppUnitTestFramework`. Usare queste API per scrivere unit test C++ in base a Microsoft Native Unit Test Framework. È disponibile un [esempio di utilizzo](#example) alla fine dell'argomento.

I file di intestazione e lib si trovano in *\<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest*.

I percorsi dei file di intestazione e lib vengono configurati automaticamente in un progetto di test nativo.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> In questo argomento

[CppUnitTest.h](#cppUnitTest_h)

- [Creare classi e metodi di test](#create_test_classes_and_methods)

- [Inizializzare e pulire](#Initialize_and_cleanup)

  - [Metodi di test](#test_methods)

  - [Classi di test](#test_classes)

  - [Moduli di test](#test_modules)

- [Creare attributi di test](#create_test_attributes)

  - [Attributi del metodo di test](#test_method_attributes)

  - [Attributi della classe di test](#test_class_attributes)

  - [Attributi del modulo di test](#test_module_attributes)

  - [Attributi predefiniti](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Asserzioni generali](#general_asserts)

    - [AreEqual](#general_are_equal)

    - [Non sono uguali](#general_are_not_equal)

    - [Sono uguali](#general_are_same)

    - [AreNotSame](#general_are_not_same)

    - [È Null](#general_is_null)

    - [Non è Null](#general_is_not_null)

    - [È true](#general_is_True)

    - [È False](#general_is_false)

    - [Errato](#general_Fail)

  - [Windows Asserzioni di runtime](#winrt_asserts)

    - [AreEqual](#winrt_are_equal)

    - [Sono uguali](#winrt_are_same)

    - [Non sono uguali](#winrt_are_not_equal)

    - [AreNotSame](#winrt_are_not_same)

    - [È Null](#winrt_is_null)

    - [Non è Null](#winrt_is_not_null)

  - [Asserzioni di eccezione](#exception_asserts)

    - [ExpectException](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Logger](#logger)

    - [WriteMessage](#write_message)

  - [Esempio di utilizzo](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Creare classi e metodi di test

```cpp
TEST_CLASS(className)
```

Obbligatorio per ogni classe che contiene metodi di test. Identifica *className* come una classe di test. `TEST_CLASS` deve essere dichiarato nell'ambito dello spazio dei nomi.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definisce *methodName* come metodo di test. `TEST_METHOD` deve essere dichiarato nell'ambito della classe del metodo.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Eseguire l'inizializzazione e la pulizia

#### <a name="test-methods"></a><a name="test_methods"></a> Metodi di test

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definisce *methodName* come un metodo eseguito prima dell'esecuzione di ogni metodo di test. `TEST_METHOD_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definisce *methodName* come un metodo eseguito dopo l'esecuzione di ogni metodo di test. `TEST_METHOD_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.

#### <a name="test-classes"></a><a name="test_classes"></a> Classi di test

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definisce *methodName* come un metodo eseguito prima della creazione di ogni classe di test. `TEST_CLASS_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definisce *methodName* come un metodo eseguito dopo la creazione di ogni classe di test. `TEST_CLASS_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.

#### <a name="test-modules"></a><a name="test_modules"></a> Moduli di test

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definisce il metodo *methodName* eseguito quando viene caricato un modulo. `TEST_MODULE_INITIALIZE` può essere definito una sola volta in un modulo di test e deve essere dichiarato nell'ambito dello spazio dei nomi.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definisce il metodo *methodName* eseguito quando viene scaricato un modulo. `TEST_MODULE_CLEANUP` può essere definito una sola volta in un modulo di test e deve essere dichiarato nell'ambito dello spazio dei nomi.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Creare attributi di test

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Attributi del metodo di test

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Aggiunge gli attributi definiti con una o più macro `TEST_METHOD_ATTRIBUTE` al metodo di test *testMethodName*.

Una macro `TEST_METHOD_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Attributi della classe di test

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Aggiunge gli attributi definiti con una o più macro `TEST_CLASS_ATTRIBUTE` alla classe di test *testClassName*.

Una macro `TEST_CLASS_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Attributi del modulo di test

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Aggiunge gli attributi definiti con una o più macro `TEST_MODULE_ATTRIBUTE` al metodo di test *testModuleName*.

Una macro `TEST_MODULE_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Attributi predefiniti

Queste macro di attributi predefiniti vengono fornite per maggiore praticità nella gestione dei casi comuni. Possono essere sostituire con la macro `TEST_METHOD_ATTRIBUTE` descritta in precedenza.

```cpp
TEST_OWNER(ownerAlias)
```

Definisce un oggetto `TEST_METHOD_ATTRIBUTE` con il nome `Owner` e il valore di attributo *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definisce un oggetto `TEST_METHOD_ATTRIBUTE` con il nome `Description` e il valore di attributo *description*.

```cpp
TEST_PRIORITY(priority)
```

Definisce un oggetto `TEST_METHOD_ATTRIBUTE` con il nome `Priority` e il valore di attributo *priority*.

```cpp
TEST_WORKITEM(workitem)
```

Definisce un oggetto `TEST_METHOD_ATTRIBUTE` con il nome `WorkItem` e il valore di attributo *workItem*.

```cpp
TEST_IGNORE()
```

Definisce un oggetto `TEST_METHOD_ATTRIBUTE` con il nome `Ignore` e il valore di attributo `true`.

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a> Asserzioni generali

#### <a name="are-equal"></a><a name="general_are_equal"></a> Sono uguali
Verificare che due oggetti siano uguali

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due valori Double siano uguali

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due valori Float siano uguali

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due stringhe char* siano uguali

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due stringhe w_char* siano uguali

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> AreNotEqual
Verificare che i due valori Double non siano uguali

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che i due valori Float non siano uguali

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due stringhe char* non siano uguali

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che due stringhe w_char* non siano uguali

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Verificare che i due riferimenti non siano uguali in base all'operatore ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> AreSame
Verificare che due riferimenti puntino alla stessa istanza di oggetto (identità).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Non sono uguali
Verificare che due riferimenti non puntino alla stessa istanza di oggetto (identità).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> È Null
Verificare che un puntatore sia NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> Non è Null
Verificare che un puntatore non sia NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> È true
Verificare che una condizione sia True

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> Is False
Verificare che una condizione sia False

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Fallire
Forza il risultato del test case come non superato

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Asserzioni di Windows Runtime

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Sono uguali
Verifica che due puntatori di Windows Runtime siano uguali.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Verifica che due stringhe Platform::String^ siano uguali.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> AreSame
Verifica che due riferimenti di Windows Runtime puntino allo stesso oggetto.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> AreNotEqual
Verifica che due puntatori di Windows Runtime non siano uguali.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Verifica che due stringhe Platform::String^ non siano uguali.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Non sono uguali
Verifica che due riferimenti di Windows Runtime non puntino allo stesso oggetto.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> È Null
Verifica che un puntatore di Windows Runtime sia un nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> Non è Null
Verifica che un puntatore di Windows Runtime non sia un nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Asserzioni di eccezioni

#### <a name="expect-exception"></a><a name="expect_exception"></a> Eccezione prevista
Verificare che una funzione generi un'eccezione:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Verificare che una funzione generi un'eccezione:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a><a name="logger"></a> Logger
La classe Logger contiene metodi statici per scrivere nella **finestra di output**.

### <a name="write-message"></a><a name="write_message"></a> Scrivere un messaggio
Scrivere una stringa nella **finestra di output**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a>Esempio
Questo codice è un esempio di utilizzo di VSCppUnit. Include esempi di metadati di attributi, fixture, unit test con asserzioni e registrazione personalizzata.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
