---
title: Hook di allocazione e allocazioni di memoria di runtime C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433106"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Hook di allocazione e allocazioni di memoria di runtime C
Una restrizione molto importante per le funzioni di hook di allocazione è che esse devono esplicitamente ignorare `_CRT_BLOCK` blocchi. Questi blocchi sono le allocazioni di memoria effettuate internamente dalle funzioni della libreria di runtime C se vengono effettuate chiamate alle funzioni della libreria di runtime C che allocano memoria interna. È possibile ignorare `_CRT_BLOCK` funzione hook di blocchi, includendo il codice seguenti all'inizio il raggiungimento dell'allocazione:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Se la funzione di hook di allocazione non ignora `_CRT_BLOCK` si blocca, quindi qualsiasi funzione di libreria run-time C chiamata nella funzione hook rischia di intrappolare il programma in un ciclo infinito. Ad esempio, `printf` crea un'allocazione interna. Se il codice hook chiama `printf`, quindi l'allocazione effettuata farà sì che l'hook venga nuovamente chiamata che chiamerà **printf** anche in questo caso, e così via, fino all'overflow dello stack. Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output. Poiché le API di Windows non usa l'heap della libreria run-time C, essi non intercettare l'hook di allocazione in un ciclo infinito.  
  
 Se si esaminano i file di origine della libreria run-time, si noterà che l'allocazione predefinita funzione hook, **CrtDefaultAllocHook** (che restituisce semplicemente **TRUE**), si trova in un file separato proprio, DBGHOOK. C. Se si desidera che l'hook di allocazione venga chiamato anche per le allocazioni effettuate dal codice di avvio in fase di esecuzione che viene eseguito prima dell'applicazione **principale** (funzione), è possibile sostituire questa funzione predefinita con uno personalizzato, invece di usando [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
