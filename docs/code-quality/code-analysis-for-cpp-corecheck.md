---
title: Riferimento di controllo linee guida per la base di C++
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fc6c7c1dbc5009129e9e793f3b8eea1f7927b2bb
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018446"
---
# <a name="c-core-guidelines-checker-reference"></a>Riferimento di controllo linee guida per la base di C++

In questa sezione elenca gli avvisi di controllo di linee guida di base di C++. Per informazioni sull'analisi del codice, vedere [/Analyze (analisi codice)](/cpp/build/reference/analyze-code-analysis) e [Quick Start: Analisi del codice per CC++/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Alcuni avvisi appartengono a più di un gruppo e non tutti gli avvisi sono un argomento di riferimento completa.

## <a name="owner_pointer-group"></a>Gruppo OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) restituiscono un oggetto con ambito invece un'allocazione dell'heap se include un costruttore di spostamento. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) ripristinare o eliminare in modo esplicito un proprietario\<T > puntatore '% variabile %'. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) non si elimina un proprietario\<T > che potrebbe essere in stato non valido. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) non assegnare a un proprietario\<T > che potrebbe essere in uno stato valido. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) non si assegna un puntatore non elaborato a un proprietario\<T >. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferire oggetti con ambito, non dell'heap-allocare inutilmente. Visualizzare [linee guida di base di C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) simbolo '% simbolo %' non viene mai testato per verificare se, può essere contrassegnato come not_null. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) simbolo '% simbolo %' non è stato testato per verificare se in tutti i percorsi. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) il tipo dell'espressione '% expr %' è già gsl:: Not_Null. Non testare la presenza di null. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Gruppo RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) non assegnare il risultato di un'allocazione o una chiamata di funzione con un proprietario\<T > restituisce il valore a un puntatore non elaborato, usare owner\<T > in alternativa. Visualizzare [linee guida di base di C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) non si elimina un puntatore non elaborato che non è un proprietario\<T >. Visualizzare [linee guida di base di C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   restituiscono un oggetto con ambito invece un'allocazione dell'heap se include un costruttore di spostamento. Visualizzare [linee guida di base di C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) evitare malloc () e Free (), la versione nothrow di new con delete. Visualizzare [linee guida di base di C++ R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) evitare di chiamare di nuovo ed eliminare in modo esplicito, usare std:: make_unique\<T > in alternativa. Visualizzare [linee guida di base di C++ R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) simbolo '% simbolo %' non viene mai testato per verificare se, può essere contrassegnato come not_null. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) simbolo '% simbolo %' non è stato testato per verificare se in tutti i percorsi. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) il tipo dell'espressione '% expr %' è già gsl:: Not_Null. Non testare la presenza di null. Visualizzare [linee guida di base di C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) non usano l'aritmetica dei puntatori. In alternativa, usare span. Visualizzare [Bounds.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Espressione '% expr%': Nessuna matrice al decadimento del puntatore. Visualizzare [Bounds.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Gruppo UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) il parametro '% parametro %' è un riferimento a `const` puntatore univoco, usare const T * o const T &. Visualizzare [linee guida di base di C++ R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) il parametro '% parametro %' è un riferimento a puntatore univoco e viene mai riassegnato o reimpostato, usare T * o T &. Visualizzare [linee guida di base di C++ R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Visualizzare [linee guida di base di C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) puntatore intelligente parametro '% simbolo %' viene utilizzato solo per accedere a puntatore indipendente. Usare T * o T &. Visualizzare [linee guida di base di C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Gruppo SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Visualizzare [linee guida di base di C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) puntatore intelligente parametro '% simbolo %' viene utilizzato solo per accedere a puntatore indipendente. Usare T * o T &. Visualizzare [linee guida di base di C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parametro del puntatore condiviso '% simbolo %' è passato per riferimento rvalue. Passare invece per valore. Visualizzare [linee guida di base di C++ R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parametro del puntatore condiviso '% simbolo %' è passato per riferimento e non reimpostato o riassegnato. Usare T * o T &. Visualizzare [linee guida di base di C++ R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parametro del puntatore condiviso '% simbolo %' non viene copiato o spostato. Usare T * o T &. Visualizzare [linee guida di base di C++ R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Gruppo di dichiarazione

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) inizializzatore globale chiama una funzione non constexpr '% simbolo %'. Visualizzare [linee guida di base di C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inizializzatore globale accede all'oggetto extern '% simbolo %'. Visualizzare [linee guida di base di C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) evitare senza nome oggetti con costruzione e distruzione personalizzate. Vedere [ES. 84: Non (provare a) dichiarare una variabile locale senza nome @ no__t-0.

## <a name="class-group"></a>Gruppo di classi

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) se si definisce o elimina qualsiasi operazione predefinita nel tipo '% simbolo %', definirle o eliminarle tutte. Visualizzare [linee guida di base di C++ C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) funzione '% % symbol' deve essere contrassegnata con 'override'. Vedere [C. 128: Le funzioni virtuali devono specificare esattamente uno dei parametri Virtual, override o Final @ no__t-0.

[C26434 DONT_HIDE_METHODS](C26434.md) funzione '% symbol_1% ' nasconde una funzione non virtuale '% symbol_2% '. Visualizzare [linee guida di base di C++ C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funzione '% % symbol' deve specificare esattamente uno di 'virtual', 'override' o 'final'. Vedere [C. 128: Le funzioni virtuali devono specificare esattamente uno dei parametri Virtual, override o Final @ no__t-0.

[C26436 NEED_VIRTUAL_DTOR](C26436.md) il tipo '% simbolo % con una funzione virtual deve entrambi distruttore non virtuale pubblico, virtuale o protetto. Visualizzare [linee guida di base di C++ C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) distruttore di override non deve usare identificatori 'virtuali' o 'override' esplicito. Vedere [C. 128: Le funzioni virtuali devono specificare esattamente uno dei parametri Virtual, override o Final @ no__t-0.

## <a name="type-group"></a>TIPO di gruppo

[C26437 DONT_SLICE](C26437.md) non sezionare. Visualizzare [linee guida di base di C++ ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Gruppo di stili

[C26438 NO_GOTO](C26438.md) evitare `goto`. Visualizzare [linee guida di base di C++ ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Gruppo di funzioni

[C26439 SPECIAL_NOEXCEPT](C26439.md) non generino questo tipo di funzione. Dichiararla `noexcept`. Visualizzare [linee guida di base di C++ F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) funzione '% simbolo %' può essere dichiarata `noexcept`. Visualizzare [linee guida di base di C++ F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) la funzione viene dichiarata **noexcept** ma chiama una funzione che potrebbe generare eccezioni.
Vedere linee guida diC++ base [:  F. 6: Se non è possibile generare la funzione, dichiararla noexcept @ no__t-0.

## <a name="concurrency-group"></a>Gruppo di concorrenza

[C26441 NO_UNNAMED_GUARDS](C26441.md) gli oggetti Guard devono essere denominati. Visualizzare [cp.44 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Gruppo CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) l'argomento di riferimento '% argomento %' per la funzione '% % di funzione' può essere contrassegnato come `const`. Visualizzare [con.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): L'argomento '% argument%' del puntatore per la funzione '% Function%' può essere contrassegnato come puntatore a `const`. Visualizzare [con.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) solo una volta assegnato il valore a cui fa riferimento '% variabile %', contrassegnarlo come puntatore a `const`. Visualizzare [con.4 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) gli elementi di matrice 'matrice % %' assegnati una sola volta, gli elementi di mark `const`. Visualizzare [con.4 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) i valori a cui puntano gli elementi della matrice '% % di matrice' vengono assegnati una sola volta, gli elementi di contrassegno come puntatore a `const`. Visualizzare [con.4 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) la variabile '% variabile %' è assegnata una sola volta, contrassegnarlo come `const`. Visualizzare [con.4 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) potrebbe essere contrassegnata come questa funzione della funzione % % `constexpr` se si desidera la valutazione in fase di compilazione. Visualizzare [linee guida di base di C++ F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) possibile usare questa funzione chiamata % funzione % `constexpr` se si desidera la valutazione in fase di compilazione. Visualizzare [con.5 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO di gruppo

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) non usano `const_cast` eseguire il cast `const`. `const_cast` non è necessaria; dichiarazione const o la volatilità non verrà rimosso da questa conversione. Visualizzare [Type.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) non usare `static_cast` downcast. Un cast da un tipo polimorfico deve usare dynamic_cast. Visualizzare [Type.2 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) non usare `reinterpret_cast`. Un cast da void * può usare `static_cast`. Visualizzare [Type.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) non usare un `static_cast` per le conversioni aritmetiche. Usare l'inizializzazione con parentesi graffe, gsl:: narrow_cast o gsl:: Narrow. Visualizzare [Type.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) non eseguire il cast tra tipi di puntatore in cui il tipo di origine e il tipo di destinazione sono uguali. Visualizzare [Type.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) non eseguire il cast tra tipi di puntatore quando la conversione potrebbe essere implicita. Visualizzare [Type.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) non usare il tipo di funzione i cast C. Visualizzare [linee guida di base di C++ ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) non usare `reinterpret_cast`. Visualizzare [Type.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) non usare `static_cast` downcast. Visualizzare [Type.2 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) non usano `const_cast` eseguire il cast `const`. Visualizzare [Type.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) non usare cast di tipo C. Visualizzare [Type.4 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) variabile '% variabile %' non è inizializzata. Inizializzare sempre un oggetto. Visualizzare [Type.5 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) variabile '% variabile %' non è inizializzata. Inizializzare sempre una variabile membro. Visualizzare [Type.6 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Gruppo di limiti

[C26446 USE_GSL_AT](c26446.md) preferiscono usare `gsl::at()` anziché l'operatore di indice è deselezionata. Vedere linee guida diC++ base [:  Limiti. 4: Non usare funzioni e tipi della libreria standard che non sono associati: checked @ no__t-0.

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Non usare l'aritmetica dei puntatori. In alternativa, usare span. Vedere [Bounds.1 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) indicizzare solo in matrici usando espressioni costanti. Vedere [Bounds.2 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valore % value % non è compreso nei limiti (0, % associato %) della variabile '% variabile %'. Indicizzare solo in matrici usando espressioni costanti comprese nei limiti della matrice. Vedere [Bounds.2 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[NO_ARRAY_TO_POINTER_DECAY C26485](C26485.md) Espressione '% expr%': Nessuna matrice al decadimento del puntatore. Vedere [Bounds.3 linee guida di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Gruppo GSL

[C26445 NO_SPAN_REF](c26445.md) un riferimento a `gsl::span` o `std::string_view` potrebbe essere un'indicazione di un problema di durata.
Vedere le linee guidaC++ di base [ GSL. View: Visualizzazioni @ no__t-0

[C26446 USE_GSL_AT](c26446.md) preferiscono usare `gsl::at()` anziché l'operatore di indice è deselezionata. Vedere linee guida diC++ base [:  Limiti. 4: Non usare funzioni e tipi della libreria standard che non sono associati: checked @ no__t-0.

[USE_GSL_FINALLY C26448](c26448.md) Si consiglia di utilizzare `gsl::finally` se l'azione finale è intenzionale. Vedere linee guida diC++ base [:  GSL.util: Utilità @ no__t-0.

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` o `std::string_view` creato da una variabile temporanea non saranno validi quando il file temporaneo viene invalidato. Vedere linee guida diC++ base [: GSL.view: Visualizzazioni @ no__t-0.

## <a name="deprecated-warnings"></a>Avvisi deprecati

I seguenti avvisi sono presenti in un set di regole sperimentale anticipata del correttore linee guida per core, ma ora sono deprecati e possono essere tranquillamente ignorati. Gli avvisi vengono sostituiti da avvisi nell'elenco precedente.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- VALID_OWNER_LEAVING_SCOPE 26422
- ALLOCATION_NOT_ASSIGNED_TO_OWNER 26423
- VALID_ALLOCATION_LEAVING_SCOPE 26424
- 26425 ASSIGNING_TO_STATIC
- NO_LIFETIME_TRACKING 26499

## <a name="see-also"></a>Vedere anche
[Uso dei correttori linee guida di base di C++](using-the-cpp-core-guidelines-checkers.md)
