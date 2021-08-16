---
title: Funzioni hook di allocazione | Microsoft Docs
description: Informazioni su come usare le funzioni hook di allocazione, che vengono installate usando _CrtSetAllocHook, quando è necessario eseguire il debug in fase di esecuzione C (CRT) in Visual Studio.
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5406cf76eee3ae81ea629e2bc41b4d97cb7d68cdae5e4f9cb48a43b24547fc6e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346375"
---
# <a name="allocation-hook-functions"></a>Funzioni hook di allocazione
Una funzione hook di allocazione, installata [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), viene chiamata ogni volta che la memoria viene allocata, riallocata o liberata. È possibile usare questo tipo di hook per molti scopi diversi. Usarlo per testare il modo in cui un'applicazione gestisce situazioni di memoria insufficienti, ad esempio per esaminare i modelli di allocazione o registrare le informazioni di allocazione per analisi successive.

> [!NOTE]
> Tenere presente le restrizioni sull'utilizzo delle funzioni della libreria di runtime del linguaggio C in una funzione hook di allocazione descritte in [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Una funzione hook di allocazione deve avere un prototipo simile all'esempio seguente:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Il puntatore passato a [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) è del tipo **_CRT_ALLOC_HOOK**, come definito in CRTDBG.H:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Quando la libreria di runtime chiama l'hook, l'argomento *nAllocType* indica l'operazione di allocazione che sta per essere eseguita (**_HOOK_ALLOC,** **_HOOK_REALLOC** o **_HOOK_FREE**). In un oggetto gratuito o in una riallocazione, ha un puntatore all'articolo utente del blocco `pvData` che sta per essere liberato. Tuttavia, per un'allocazione, questo puntatore è Null, perché l'allocazione non si è verificata. Gli argomenti rimanenti contengono le dimensioni dell'allocazione in questione, il tipo di blocco, il numero di richiesta sequenziale associato e un puntatore al nome file. Se disponibili, gli argomenti includono anche il numero di riga in cui è stata effettuata l'allocazione. Dopo che la funzione hook ha eseguito l'analisi specifica nonché altre attività definite dall'autore della funzione stessa, essa dovrà restituire il valore **TRUE**, a indicare che l'operazione di allocazione può continuare, oppure il valore **FALSE**, a indicare che l'operazione deve essere interrotta. Una semplice funzione hook di questo tipo può controllare la quantità di memoria allocata fino a tale momento e restituire **FALSE** se tale quantità eccede, anche se di poco, il limite. L'applicazione sarà quindi soggetta agli errori di allocazione che in genere si verificano solo quando la memoria disponibile è molto scarsa. Funzioni hook più complesse possono tenere traccia degli schemi di allocazione, analizzare l'utilizzo della memoria o informare del verificarsi di determinate situazioni.

## <a name="see-also"></a>Vedi anche

- [Hook di allocazione e allocazioni di memoria Run-Time C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)