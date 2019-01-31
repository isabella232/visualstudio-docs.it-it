---
title: Uso di Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4315e4008c3a4f14e8d9124da5d7ff83c8275a65
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796928"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Utilizzo di Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento sono elencati i membri pubblici dello spazio dei nomi `Microsoft::VisualStudio::CppUnitTestFramework`.  
  
 I file di intestazione sono disponibili nella cartella _VisualStudio2012[x86]InstallFolder_**\VC\UnitTest\include**.  
  
 I file lib sono disponibili nella cartella _VisualStudio2012[x86]InstallFolder_**\VC\UnitTest\lib**.  
  
##  <a name="BKMK_In_this_topic"></a> Contenuto dell'argomento  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
- [Creare classi e metodi di test](#BKMK_Create_test_classes_and_methods)  
  
- [Eseguire l'inizializzazione e la pulizia](#BKMK_Initialize_and_cleanup)  
  
  -   [Metodi di test](#BKMK_Test_methods)  
  
  -   [Classi di test](#BKMK_Test_classes)  
  
  -   [Moduli di test](#BKMK_Test_modules)  
  
- [Creare attributi di test](#BKMK_Create_test_attributes)  
  
  - [Attributi del metodo di test](#BKMK_Test_method_attributes)  
  
  - [Attributi della classe di test](#BKMK_Test_class_attributes)  
  
  - [Attributi del modulo di test](#BKMK_Test_module_attributes)  
  
  - [Attributi predefiniti](#BKMK_Pre_defined_attributes)  
  
    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
  - [Asserzioni generali](#BKMK_General_Asserts)  
  
    -   [AreEqual](#BKMK_General_Are_Equal)  
  
    -   [AreNotEqual](#BKMK_General_Are_Not_Equal)  
  
    -   [AreSame](#BKMK_General_Are_Same)  
  
    -   [AreNotSame](#BKMK_General_Are_Not_Same)  
  
    -   [IsNull](#BKMK_General_Is_Null)  
  
    -   [IsNotNull](#BKMK_General_Is_Not_Null)  
  
    -   [IsTrue](#BKMK_General_Is_True)  
  
    -   [IsFalse](#BKMK_General_Is_False)  
  
    -   [Fail](#BKMK_General_Fail)  
  
  - [Asserzioni di Windows Runtime](#BKMK_WinRT_Asserts)  
  
    -   [AreEqual](#BKMK_WinRT_Are_Equal)  
  
    -   [AreSame](#BKMK_WinRT_Are_Same)  
  
    -   [AreNotEqual](#BKMK_WinRT_Are_Not_Equal)  
  
    -   [AreNotSame](#BKMK_WinRT_Are_Not_Same)  
  
    -   [IsNull](#BKMK_WinRT_Is_Null)  
  
    -   [IsNotNull](#BKMK_WinRT_Is_Not_Null)  
  
  - [Asserzioni di eccezione](#BKMK_Exception_Asserts)  
  
    - [ExpectException](#BKMK_Expect_Exception)  
  
      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
    - [Logger](#BKMK_Logger)  
  
    - [WriteMessage](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Creare classi e metodi di test  
  
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
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Eseguire l'inizializzazione e la pulizia  
  
####  <a name="BKMK_Test_methods"></a> Metodi di test  
  
```cpp  
TEST_METHOD_INITIALIZE(methodName)   
{  
    // method initialization code  
}  
  
```  
  
 Definisce *methodName* come un metodo eseguito prima dell'esecuzione di ogni metodo di test. `TEST_METHOD_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nella classe di test.  
  
```cpp  
TEST_METHOD_CLEANUP(methodName)   
{  
    // test method cleanup  code  
}  
  
```  
  
 Definisce *methodName* come un metodo eseguito dopo l'esecuzione di ogni metodo di test. `TEST_METHOD_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.  
  
####  <a name="BKMK_Test_classes"></a> Classi di test  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Definisce *methodName* come un metodo eseguito dopo la creazione di ogni classe di test. `TEST_CLASS_INITIALIZE` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Definisce *methodName* come un metodo eseguito dopo la creazione di ogni classe di test. `TEST_CLASS_CLEANUP` può essere definito una sola volta in una classe di test e deve essere definito nell'ambito della classe di test.  
  
####  <a name="BKMK_Test_modules"></a> Moduli di test  
  
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
  
###  <a name="BKMK_Create_test_attributes"></a> Creare attributi di test  
  
####  <a name="BKMK_Test_method_attributes"></a> Attributi del metodo di test  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con una o più macro `TEST_METHOD_ATTRIBUTE` al metodo di test *testClassName*.  
  
 Una macro `TEST_METHOD_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Attributi della classe di test  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con una o più macro `TEST_CLASS_ATTRIBUTE` alla classe di test *testClassName*.  
  
 Una macro `TEST_CLASS_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Attributi del modulo di test  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Aggiunge gli attributi definiti con una o più macro `TEST_MODULE_ATTRIBUTE` al metodo di test *testModuleName*.  
  
 Una macro `TEST_MODULE_ATTRIBUTE` definisce un attributo con il nome *attributeName* e il valore *attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Attributi predefiniti  
 È possibile sostituire queste macro di attributo predefinite alle macro `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` o `TEST_MODULE_ATTRIBUTE` descritte in precedenza.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Definisce un attributo con il nome `Owner` e il valore di attributo *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Definisce un attributo con il nome `Description` e il valore di attributo *description*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Definisce un attributo con il nome `Priority` e il valore di attributo *priority*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Definisce un attributo con il nome `WorkItem` e il valore di attributo *workItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Definisce un attributo con il nome `Ignore` e il valore di attributo `true`.  
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Asserzioni generali  
  
####  <a name="BKMK_General_Are_Equal"></a> AreEqual  
 Verificare che due oggetti siano uguali  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due valori Double siano uguali  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due valori Float siano uguali  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due stringhe char* siano uguali  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due stringhe w_char* siano uguali  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> AreNotEqual  
 Verificare che i due valori Double non siano uguali  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che i due valori Float non siano uguali  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due stringhe char* non siano uguali  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che due stringhe w_char* non siano uguali  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Verificare che i due riferimenti non siano uguali in base all'operatore ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> AreSame  
 Verificare che due riferimenti puntino alla stessa istanza di oggetto (identità).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> AreNotSame  
 Verificare che due riferimenti non puntino alla stessa istanza di oggetto (identità).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> IsNull  
 Verificare che un puntatore sia NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> IsNotNull  
 Verificare che un puntatore non sia NULL  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> IsTrue  
 Verificare che una condizione sia True  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> IsFalse  
 Verificare che una condizione sia False  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Fail  
 Forza il risultato del test case come non superato  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Asserzioni di Windows Runtime  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> AreEqual  
 Verifica che due puntatori di Windows Runtime siano uguali.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Verifica che due stringhe Platform::String^ siano uguali.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> AreSame  
 Verifica che due riferimenti di Windows Runtime puntino allo stesso oggetto.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> AreNotEqual  
 Verifica che due puntatori di Windows Runtime non siano uguali.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Verifica che due stringhe Platform::String^ non siano uguali.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> AreNotSame  
 Verifica che due riferimenti di Windows Runtime non puntino allo stesso oggetto.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> IsNull  
 Verifica che un puntatore di Windows Runtime sia un nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> IsNotNull  
 Verifica che un puntatore di Windows Runtime non sia un nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Asserzioni di eccezione  
  
####  <a name="BKMK_Expect_Exception"></a> ExpectException  
 Verificare che una funzione generi un'eccezione:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Verificare che una funzione generi un'eccezione:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Logger  
 La classe Logger contiene metodi statici in cui eseguire la scrittura  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> WriteMessage  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## <a name="example"></a>Esempio  
 Questo codice è un esempio di  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Unit test di codice nativo con Esplora test](http://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
