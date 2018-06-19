---
title: 'Procedura: specificare informazioni aggiuntive sul codice utilizzando _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031527"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedura: specificare informazioni aggiuntive sul codice utilizzando _Analysis_assume
È possibile fornire suggerimenti per lo strumento di analisi codice per il codice C/C++ che guida il processo di analisi e ridurre gli avvisi. Per fornire informazioni aggiuntive, utilizzare la funzione seguente:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -qualsiasi espressione che si presuppone che restituiscono true.

 Lo strumento di analisi del codice si presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui la funzione viene visualizzata e rimanga true finché l'espressione viene modificata, ad esempio, tramite l'assegnazione alla variabile.

> [!NOTE]
>  `_Analysis_assume` non influisce sulla ottimizzazione del codice. Lo strumento di analisi del codice, di fuori `_Analysis_assume` è definito come alcuna operazione.

## <a name="example"></a>Esempio
 Il codice seguente usa `_Analysis_assume` per correggere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):

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