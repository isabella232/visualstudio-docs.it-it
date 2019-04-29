---
title: Hook di allocazione e allocazioni di memoria di runtime C | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1840f6f5650b3491cf7898c1d8d6a6fcae19f906
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564974"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Hook di allocazione e allocazioni di memoria di runtime C
Una restrizione molto importante per le funzioni di hook di allocazione è che esse devono esplicitamente ignorare `_CRT_BLOCK` blocchi. Questi blocchi sono le allocazioni di memoria effettuate internamente dalle funzioni della libreria di runtime C se vengono effettuate chiamate alle funzioni della libreria di runtime C che allocano memoria interna. È possibile ignorare `_CRT_BLOCK` funzione hook di blocchi, includendo il codice seguente all'inizio il raggiungimento dell'allocazione:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Se la funzione di hook di allocazione non ignora `_CRT_BLOCK` si blocca, quindi qualsiasi funzione di libreria run-time C chiamata nella funzione hook rischia di intrappolare il programma in un ciclo infinito. Ad esempio, `printf` crea un'allocazione interna. Se il codice hook chiama `printf`, l'allocazione effettuata farà sì che la funzione hook venga nuovamente chiamata ed essa chiamerà a sua volta nuovamente **printf** e così via fino all'overflow dello stack. Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output. Poiché le API di Windows non usa l'heap della libreria run-time C, essi non intercettare l'hook di allocazione in un ciclo infinito.

Se si esaminano i file di origine della libreria di runtime, si noterà che la funzione hook di allocazione predefinita, **CrtDefaultAllocHook** (che restituisce semplicemente **TRUE**) si trova in un file separato, DBGHOOK.C. Se si desidera che l'hook di allocazione venga chiamato anche per le allocazioni effettuate dal codice di avvio di runtime, che viene eseguito prima della funzione **main** dell'applicazione, è possibile sostituire questa funzione predefinita con una personalizzata, anziché utilizzare [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Vedere anche
- [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)
