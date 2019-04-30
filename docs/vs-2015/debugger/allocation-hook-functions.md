---
title: Funzioni Hook di allocazione | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b617f0c154c14113370fff257c6837ce8314134a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439946"
---
# <a name="allocation-hook-functions"></a>Funzioni hook di allocazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una funzione di hook di allocazione, installata tramite [CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), viene chiamato ogni volta che viene allocata, riallocata o liberata memoria. Questo tipo di funzione è utilizzabile per numerosi scopi differenti. È possibile usare le funzioni hook per verificare come un'applicazione gestisce situazioni di memoria insufficiente, ad esempio, oppure per esaminare schemi di allocazione o per registrare informazioni di allocazione da analizzare in seguito.  
  
> [!NOTE]
> Tenere presente le restrizioni sull'utilizzo delle funzioni della libreria di runtime del linguaggio C in una funzione hook di allocazione descritte in [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una funzione hook di allocazione dovrebbe avere un prototipo analogo al seguente:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Il puntatore passato a [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) è del tipo **_CRT_ALLOC_HOOK**, come definito in CRTDBG.H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nAllocType* l'argomento indica quali allocazione operazione sta per essere eseguite (**HOOK_ALLOC**, **HOOK_REALLOC**, o **HOOK_FREE**). Nel caso di una liberazione o di una riallocazione, `pvData` conterrà un puntatore all'argomento utente del blocco che sarà liberato. Nel caso di un'allocazione, tuttavia, questo puntatore è nullo, poiché l'allocazione non ha ancora avuto luogo. I restanti argomenti contengono la dimensione dell'allocazione in questione, il tipo di blocco, il numero di richiesta sequenziale associato all'allocazione e un puntatore al nome file e al numero di riga in cui l'allocazione è stata effettuata, se tali informazioni sono disponibili. Dopo che la funzione hook ha eseguito l'analisi specifica nonché altre attività definite dall'autore della funzione stessa, essa dovrà restituire il valore **TRUE**, a indicare che l'operazione di allocazione può continuare, oppure il valore **FALSE**, a indicare che l'operazione deve essere interrotta. Una semplice funzione hook di questo tipo può controllare la quantità di memoria allocata fino a tale momento e restituire **FALSE** se tale quantità eccede, anche se di poco, il limite. L'applicazione sarà quindi soggetta agli errori di allocazione che in genere si verificano solo quando la memoria disponibile è molto scarsa. Funzioni hook più complesse possono tenere traccia degli schemi di allocazione, analizzare l'utilizzo della memoria o informare del verificarsi di determinate situazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio di crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
