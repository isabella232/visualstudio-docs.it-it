---
title: Hook di allocazione e allocazioni di memoria di runtime C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9faacefd4fc0817f5dd5cae31392017458ede49e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968432"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Hook di allocazione e allocazioni di memoria di runtime C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una restrizione molto importante che riguarda le funzioni hook di allocazione è che esse devono esplicitamente ignorare i blocchi `_CRT_BLOCK` (le allocazioni di memoria effettuate internamente dalle funzioni dalla libreria di runtime del linguaggio C) se tali blocchi effettuano chiamate a funzioni della libreria di runtime del linguaggio C che allocano memoria interna. È possibile far sì che i blocchi `_CRT_BLOCK` vengano ignorati includendo, all'inizio della funzione hook di allocazione, un codice del seguente tipo:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Se la funzione hook di allocazione non ignora i blocchi `_CRT_BLOCK`, qualsiasi funzione della libreria di runtime del linguaggio C chiamata nella funzione hook rischia di intrappolare il programma in un ciclo senza termine. Ad esempio, `printf` crea un'allocazione interna. Se il codice hook chiama `printf`, quindi l'allocazione effettuata farà sì che l'hook venga nuovamente chiamata che chiamerà **printf** anche in questo caso, e così via fino all'overflow dello stack. Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output. Dal momento che le API Windows non utilizzano l'heap della libreria di runtime del linguaggio C, esse non bloccheranno la funzione hook di allocazione in un ciclo senza termine.  
  
 Se si esaminano i file di origine della libreria di runtime, si noterà che la funzione hook di allocazione predefinita, **CrtDefaultAllocHook** (che restituisce semplicemente **TRUE**) si trova in un file separato, DBGHOOK.C. Se si desidera che l'hook di allocazione venga chiamato anche per le allocazioni effettuate dal codice di avvio di runtime, che viene eseguito prima della funzione **main** dell'applicazione, è possibile sostituire questa funzione predefinita con una personalizzata, anziché utilizzare [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio di crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
