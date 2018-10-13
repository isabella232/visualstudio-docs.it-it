---
title: 'Procedura: specificare informazioni aggiuntive sul codice usando analysis_assume | Microsoft Docs'
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
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 608ae6383f95122d5e4b85658b12d454dec24d4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202540"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire suggerimenti per lo strumento di analisi codice per codice C/C++ che guida il processo di analisi e ridurre gli avvisi. Per fornire informazioni aggiuntive, usare la funzione seguente:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -qualsiasi espressione che si presuppone restituisca true.  
  
 Lo strumento di analisi di codice si presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui la funzione viene visualizzata e rimanga true finché non viene modificata espressione, ad esempio, mediante l'assegnazione alla variabile.  
  
> [!NOTE]
>  `__analysis_assume` non influisce sull'ottimizzazione del codice. Lo strumento di analisi codice, di fuori `__analysis_assume` viene definito come no-op.  
  
## <a name="example"></a>Esempio  
 Il codice seguente usa `__analysis_assume` per risolvere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



