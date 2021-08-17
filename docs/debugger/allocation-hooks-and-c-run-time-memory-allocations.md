---
title: Hook di allocazione e allocazioni di memoria di runtime C
description: Informazioni su hook di allocazione e allocazioni di memoria di run-time C Visual Studio debug. Le funzioni hook di allocazione devono ignorare in modo _CRT_BLOCK blocchi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a5e921b5bac52d74bd1b2358bfc3f302c4d96f3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121890"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Hook di allocazione e allocazioni di memoria di runtime C
Una restrizione molto importante per le funzioni hook di allocazione è che devono ignorare in modo esplicito i `_CRT_BLOCK` blocchi. Questi blocchi sono le allocazioni di memoria effettuate internamente dalle funzioni della libreria di runtime C se eseguono chiamate alle funzioni della libreria di runtime C che allocano memoria interna. È possibile ignorare i `_CRT_BLOCK` blocchi includendo il codice seguente all'inizio della funzione hook di allocazione:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Se l'hook di allocazione non ignora i blocchi, qualsiasi funzione della libreria di runtime C chiamata nell'hook può intercettare il programma `_CRT_BLOCK` in un ciclo infinito. Ad esempio, `printf` crea un'allocazione interna. Se il codice hook chiama `printf`, l'allocazione effettuata farà sì che la funzione hook venga nuovamente chiamata ed essa chiamerà a sua volta nuovamente **printf** e così via fino all'overflow dello stack. Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output. Poiché le WINDOWS api non usano l'heap della libreria di runtime C, non intercetterà l'hook di allocazione in un ciclo infinito.

Se si esaminano i file di origine della libreria di runtime, si noterà che la funzione hook di allocazione predefinita, **CrtDefaultAllocHook** (che restituisce semplicemente **TRUE**) si trova in un file separato, DBGHOOK.C. Se si desidera che l'hook di allocazione venga chiamato anche per le allocazioni effettuate dal codice di avvio di runtime, che viene eseguito prima della funzione **main** dell'applicazione, è possibile sostituire questa funzione predefinita con una personalizzata, anziché utilizzare [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Vedi anche
- [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)
