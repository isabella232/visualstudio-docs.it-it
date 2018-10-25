---
title: Funzioni Hook di allocazione | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d49bbff482683c4ac3e0f5f6a4060b176db0d94
ms.sourcegitcommit: 97204b85caadbcf14baeb6738710e287a196673e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "37433356"
---
# <a name="allocation-hook-functions"></a>Funzioni hook di allocazione
Una funzione di hook di allocazione, installata tramite [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), viene chiamato ogni volta che viene allocata, riallocata o liberata memoria. È possibile usare questo tipo di hook per numerosi scopi differenti. Usato per verificare come un'applicazione gestisce situazioni di memoria insufficiente, ad esempio per esaminare schemi di allocazione o registrare le informazioni di allocazione per analisi successive.  
  
> [!NOTE]
>  Tenere presente le restrizioni sull'utilizzo di funzioni della libreria di runtime C in una funzione di hook di allocazione, descritto nella [hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una funzione di hook di allocazione dovrebbe avere un prototipo analogo al seguente:  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Il puntatore passato a [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) JE typu **CRT_ALLOC_HOOK**, come definito in CRTDBG. H:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nAllocType* l'argomento indica quali allocazione operazione deve essere reso (**HOOK_ALLOC**, **HOOK_REALLOC**, o **HOOK_FREE**). In una versione gratuita o in una riallocazione, `pvData` dispone di un puntatore all'articolo di utente del blocco verrà liberato. Tuttavia per un'allocazione, questo puntatore è null, perché non è stata eseguita l'allocazione. I restanti argomenti contengono la dimensione dell'allocazione in questione, il tipo di blocco, il numero di richiesta sequenziale associato e un puntatore al nome del file. Se disponibile, i argomenti includono anche il numero di riga in cui è stato effettuato l'allocazione. Dopo la funzione hook eseguito l'analisi e altre attività definite dall'autore, mentre deve restituire **TRUE**, che indica che l'operazione di allocazione può continuare, o **FALSE**, a indicare che la operazione non riuscirà. Una semplice funzione hook di questo tipo potrebbe controllare la quantità di memoria allocata fino ad ora e restituire **FALSE** se tale quantità eccede il limite di piccole dimensioni. L'applicazione sarà quindi soggetta agli errori di allocazione che in genere si verificano solo quando la memoria disponibile è molto scarsa. Funzioni hook più complesse possono tenere traccia degli schemi di allocazione, analizzare l'uso della memoria o informare del verificarsi di determinate situazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
