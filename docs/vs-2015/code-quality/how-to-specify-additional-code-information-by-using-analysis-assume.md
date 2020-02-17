---
title: 'Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277978"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire suggerimenti allo strumento di analisi del codice per CC++ /code che consente il processo di analisi e la riduzione degli avvisi. Per fornire informazioni aggiuntive, utilizzare la funzione seguente:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`: qualsiasi espressione che si presuppone restituisca true.  
  
 Lo strumento di analisi del codice presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui viene visualizzata la funzione e rimanga true fino a quando l'espressione non viene modificata, ad esempio per assegnazione a una variabile.  
  
> [!NOTE]
> `__analysis_assume` non influisca sull'ottimizzazione del codice. Al di fuori dello strumento di analisi del codice, `__analysis_assume` viene definito come no-op.  
  
## <a name="example"></a>Esempio  
 Il codice seguente usa `__analysis_assume` per correggere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
