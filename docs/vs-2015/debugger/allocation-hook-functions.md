---
title: Funzioni Hook di allocazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 9d201f22d461a04890899ac1cebc177cb1521555
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743343"
---
# <a name="allocation-hook-functions"></a>Funzioni hook di allocazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una funzione di hook di allocazione, installata tramite [CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), viene chiamato ogni volta che viene allocata, riallocata o liberata memoria. Questo tipo di funzione è utilizzabile per numerosi scopi differenti. È possibile usare le funzioni hook per verificare come un'applicazione gestisce situazioni di memoria insufficiente, ad esempio, oppure per esaminare schemi di allocazione o per registrare informazioni di allocazione da analizzare in seguito.  
  
> [!NOTE]
>  Tenere presente le restrizioni sull'utilizzo di funzioni della libreria di runtime C in una funzione di hook di allocazione, descritto nella [hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una funzione hook di allocazione dovrebbe avere un prototipo analogo al seguente:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Il puntatore passato a [CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) JE typu **CRT_ALLOC_HOOK**, come definito in CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nAllocType* l'argomento indica quali allocazione operazione sta per essere eseguite (**HOOK_ALLOC**, **HOOK_REALLOC**, o **HOOK_FREE**). Nel caso di una liberazione o di una riallocazione, `pvData` conterrà un puntatore all'argomento utente del blocco che sarà liberato. Nel caso di un'allocazione, tuttavia, questo puntatore è nullo, poiché l'allocazione non ha ancora avuto luogo. I restanti argomenti contengono la dimensione dell'allocazione in questione, il tipo di blocco, il numero di richiesta sequenziale associato all'allocazione e un puntatore al nome file e al numero di riga in cui l'allocazione è stata effettuata, se tali informazioni sono disponibili. Dopo la funzione hook eseguito l'analisi e altre attività definite dall'autore, mentre deve restituire **TRUE**, che indica che l'operazione di allocazione può continuare, o **FALSE**, a indicare che la operazione non riuscirà. Una semplice funzione hook di questo tipo potrebbe controllare la quantità di memoria allocata fino ad ora e restituire **FALSE** se tale quantità eccede il limite di piccole dimensioni. L'applicazione sarà quindi soggetta agli errori di allocazione che in genere si verificano solo quando la memoria disponibile è molto scarsa. Funzioni hook più complesse possono tenere traccia degli schemi di allocazione, analizzare l'uso della memoria o informare del verificarsi di determinate situazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Scrittura di funzioni Hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



