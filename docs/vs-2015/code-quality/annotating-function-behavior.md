---
title: Annotazione del comportamento della funzione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 13
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1be20fed5e7fd98860a4a62c3d59fc458bed04ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234390"
---
# <a name="annotating-function-behavior"></a>Annotazione del comportamento delle funzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oltre ad annotare [i parametri di funzione e restituire valori](../code-quality/annotating-function-parameters-and-return-values.md), è possibile annotare le proprietà dell'intera funzione.  
  
## <a name="function-annotations"></a>Annotazioni (funzione)  
 Le seguenti annotazioni si applicano all'intera funzione e descrivono come si comporta o il valore previsto per restituire true.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Non inteso singolarmente; è un predicato da utilizzare con l'annotazione `_When_`. Per altre informazioni, vedere [specificando quando e dove un'annotazione applica](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Il `name` parametro è una stringa arbitraria che è presente anche in un `_Function_class_` annotazione nella dichiarazione di alcune funzioni.  `_Called_from_function_class_` Restituisce diversi da zero se la funzione attualmente analizzata viene annotata con `_Function_class_` che ha lo stesso valore di `name`; in caso contrario, restituisce zero.|  
|`_Check_return_`|Annota un valore restituito e dichiara che il chiamante deve esaminarlo. La verifica restituisce un errore se la funzione viene chiamata in un contesto void.|  
|`_Function_class_(name)`|Il parametro `name` è una stringa arbitraria definita dall'utente.  Esiste in uno spazio dei nomi distinto da tutti gli altri spazi dei nomi. Una funzione, un puntatore a funzione o, più utile, un tipo di puntatore a funzione può essere definito come appartenente a una o più classi di funzione.|  
|`_Raises_SEH_exception_`|Annota una funzione che genera sempre un'eccezione del gestore eccezioni strutturate soggetta alle condizioni `_When_` e `_On_failure_`. Per altre informazioni, vedere [specificando quando e dove un'annotazione applica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Annota una funzione che può facoltativamente generare un'eccezione del gestore eccezioni strutturate soggetta alle condizioni `_When_` e `_On_failure_`.|  
|`_Must_inspect_result_`|Annota qualsiasi valore di output, tra cui il valore restituito, i parametri e variabili globali.  L'analizzatore segnala un errore se il valore dell'oggetto annotato non è controllato in seguito. "L'ispezione" include se viene utilizzata in un'espressione condizionale, viene assegnata a un parametro di output o globale o viene passata come parametro.  Per i valori restituiti, `_Must_inspect_result_` implica `_Check_return_`.|  
|`_Use_decl_annotations_`|Può essere utilizzata con una definizione di funzione (noto anche come il corpo di una funzione) al posto dell'elenco di annotazioni nell'intestazione.  Quando `_Use_decl_annotations_` viene utilizzato, le annotazioni visualizzate in un'intestazione dell'ambito per la stessa funzione vengono utilizzate come se fossero anche presenti nella definizione del che dispone di `_Use_decl_annotations_` annotazione.|  
  
## <a name="successfailure-annotations"></a>Annotazioni di esito positivo o negativo  
 Una funzione può non riuscire e, quando questo accade, i risultati possono essere incompleti o differire dai risultati della funzione con ha esito positivo.  Le annotazioni nell'elenco seguente forniscono le modalità per esprimere il comportamento dell'errore.  Per utilizzare ognuna di queste annotazioni, è necessario consentire loro di determinare l'esito positivo; pertanto è necessaria un'annotazione `_Success_`.  Si noti che `NTSTATUS` e `HRESULT` già includono un'annotazione `_Success_` compilata. Tuttavia, se si specifica un'annotazione `_Success_` in `NTSTATUS` o `HRESULT`, viene eseguito l'override dell'annotazione incorporata.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Analogamente a `anno_list _On_failure_(anno_list)`, le annotazioni in `anno_list` si applicano indipendentemente dall'esito della funzione.|  
|`_On_failure_(anno_list)`|Da utilizzare solo quando si usa anche `_Success_` per annotare la funzione, esplicitamente o implicitamente, mediante `_Return_type_success_` in un typedef. Quando l'annotazione `_On_failure_` è presente in un parametro di funzione o un valore restituito, ciascuna annotazione in `anno_list` (anno) si comporta come se fosse codificata come `_When_(!expr, anno)`, dove `expr` è il parametro dell'annotazione `_Success_` richiesta. Ciò significa che l'applicazione implicita di `_Success_` per tutte le post-condizioni non è applicabile per `_On_failure_`.|  
|`_Return_type_success_(expr)`|Può essere applicato a un typedef. Indica che tutte le funzioni che restituiscono quel tipo e non includono `_Success_` in modo esplicito, sono contrassegnate come se includessero `_Success_(expr)`. `_Return_type_success_` non può essere utilizzato in una funzione o in un typedef di puntatore a funzione.|  
|`_Success_(expr)`|`expr` è un'espressione che produce un rvalue. Quando l'annotazione `_Success_` è presente in una dichiarazione di funzione o una definizione, ciascuna annotazione (`anno`) nella funzione e in post-condizione si comporta come se fosse codificata come `_When_(expr, anno)`. L'annotazione `_Success_` può essere utilizzata solo in una funzione e non nei relativi parametri o nel tipo restituito. Ci può essere al massimo un'annotazione `_Success_` in una funzione e non può trovarsi all'interno di qualsiasi `_When_`, `_At_` o `_Group_`. Per altre informazioni, vedere [specificando quando e dove un'annotazione applica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurre i difetti del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare quando e dove applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)



