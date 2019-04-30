---
title: 'Procedura: Specificare informazioni aggiuntive sul codice usando _Analysis_assume'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 25ce2a97acd248e546fdfab1a1b5c3f22e085f0c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403110"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedura: Specificare informazioni aggiuntive sul codice usando _Analysis_assume
È possibile fornire suggerimenti per lo strumento di analisi codice per codice C/C++ che guida il processo di analisi e ridurre gli avvisi. Per fornire informazioni aggiuntive, usare la funzione seguente:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -qualsiasi espressione che si presuppone restituisca true.

 Lo strumento di analisi di codice si presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui la funzione viene visualizzata e rimanga true finché non viene modificata espressione, ad esempio, mediante l'assegnazione alla variabile.

> [!NOTE]
> `_Analysis_assume` non influisce sull'ottimizzazione del codice. Lo strumento di analisi codice, di fuori `_Analysis_assume` viene definito come no-op.

## <a name="example"></a>Esempio
 Il codice seguente usa `_Analysis_assume` per risolvere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):

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
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Vedere anche
 [__assume](/cpp/intrinsics/assume)